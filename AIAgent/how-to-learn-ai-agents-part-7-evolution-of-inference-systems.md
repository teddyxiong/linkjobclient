# How to Learn AI Agents (Part 7): The Evolution of Inference Systems

**Source:** [@Tedli8](https://x.com/Tedli8/status/2101894247943479775)

Training determines the ceiling of model capability; inference systems determine whether that capability can be delivered to users stably, quickly, and cheaply.

In the small-model era, we often loaded a model locally, completed one prediction, and exited the program. In the LLM era, one model must serve hundreds or thousands of requests simultaneously; each request has a different context, output length, and arrival time. Now "can it run" is only the starting point — the real question becomes: how to reduce memory waste, keep the GPU waiting less, while balancing throughput and latency.

## Transformers: Making the Model Easy to Use First

Hugging Face Transformers wraps pretrained models, tokenizers, and generation interfaces together, letting developers load and run models in a relatively uniform way. It supports both training and inference, and matters greatly for research, fine-tuning, evaluation, and low-concurrency applications.

But "load the model and call generate" and "provide online service to many users" are two different-level problems. The latter also requires request queueing, dynamic batching, KV Cache management, streaming output, distributed parallelism, and fault recovery. Hence, production-oriented inference engines emerged as an independent category of system.

## First Understand One Generation: Prefill and Decode

One autoregressive generation can be roughly divided into two phases.

The Prefill phase processes the entire input at once, building the KV Cache needed for subsequent generation. Because many tokens can be computed in parallel, this phase tends to be compute-intensive and directly affects time-to-first-token (TTFT).

The Decode phase generates new tokens one step at a time. Each step reads the model weights and existing KV Cache, but the parallel compute available per step is relatively limited, so it's usually more constrained by memory bandwidth and determines the token-by-token generation speed users see.

The role of KV Cache is to keep the Key and Value already computed for previous tokens, avoiding recomputing all history from scratch each time a new token is generated. It significantly reduces redundant computation, but also keeps occupying memory as concurrency and context length grow. Much of LLM inference optimization is about working around this cache.

## vLLM: Turning Memory Management and Request Scheduling Into a System

vLLM's most representative design is PagedAttention. Traditional implementations often reserve a contiguous memory block for each request, but at the start of a request we don't know how long it will ultimately generate, so it's easy to over-reserve and fragment memory.

PagedAttention borrows the idea of operating-system paging: it splits KV Cache into fixed-size blocks, and through mapping lets logically contiguous tokens be stored in non-contiguous physical memory. It isn't "not using physical memory," but allocating and reusing memory more finely, reducing waste so larger batches can fit.

Continuous Batching solves another kind of waste. Static batching waits for the slowest request in a batch to finish before starting the next batch. Continuous batching schedules by generation step: as soon as one request completes, a new one from the waiting queue is filled in. Thus the GPU doesn't have to wait alongside the longest request.

## SGLang: From Managing Single Requests to Reusing Prefixes Across Requests

Continuous batching optimizes scheduling between requests, but different requests may still repeatedly compute the same content. For example, many conversations share the same system prompt, Agents carry the same tool descriptions repeatedly, and multi-turn conversations share a large amount of historical prefix with the previous turn.

SGLang's RadixAttention organizes token sequences and their corresponding KV Cache in a radix tree. When a new request arrives, the system finds the longest reusable prefix, and the matched part doesn't need to be Prefilled again. It doesn't conflict with PagedAttention or Continuous Batching — it reduces duplicate work in another dimension.

SGLang also brings structured-output generation control into the runtime. When the system needs JSON, a fixed schema, or constrained text, the goal is no longer just "generate then validate," but to make the decoding process itself obey the constraints.

## Further Out: Speculative Decoding, PD Separation, and Layered Caches

The core of speculative decoding is "draft first, verify later." A faster draft model proposes several candidate tokens at once, and the target model verifies them in parallel. Accepted candidates are kept; mismatched parts regenerate. When the draft is accurate enough and verification cost is controllable, the LLM can produce a same-distribution result with fewer serial steps.

PD separation handles the difference between Prefill and Decode at the cluster-architecture level. The system puts the two phases in different worker pools, each scaling, choosing hardware, and scheduling independently. The benefit is that long-prompt Prefill doesn't easily block Decode that's streaming output; the cost is that after Prefill ends, the KV Cache must be transferred to the Decode worker, and network and scheduling overhead can't be ignored. Thus PD separation isn't always faster for all workloads — it fits long-context, high-concurrency scenarios with strict latency control better.

As context gets longer, KV Cache also evolves from "a block of data in GPU memory" into a layered storage system. Hot data stays on the GPU, colder parts sink to CPU memory, local SSD, or even remote storage; the scheduler must trade off hit rate, transfer cost, and capacity. This is already very much like what operating systems and databases do.

## What Exactly Is the Inference System Optimizing?

On the surface, these systems chase higher tokens/s, lower TTFT, and smaller memory footprint; the deeper main thread is only one: find the waste, then eliminate it.

- PagedAttention reduces memory fragmentation and over-reservation;
- Continuous Batching reduces waiting between batches;
- RadixAttention reduces duplicate computation of identical prefixes;
- Speculative decoding reduces serial decoding steps;
- PD separation reduces interference between two kinds of workload;
- Layered KV Cache trades cheaper storage for larger service capacity.

Inference systems are far from settled. Long context, MoE, multimodality, structured output, and Agent-style workloads all continue to change the optimal design. It's no longer just a "library that runs forward," but the joint optimization of model execution, memory management, request scheduling, cache reuse, and distributed serving.

Training determines what a model can do; the inference system determines at what price and speed those capabilities reach users.

## Further Reading

- Hugging Face Transformers Pipeline: https://huggingface.co/docs/transformers/main/pipeline_tutorial
- vLLM: Easy, Fast, and Cheap LLM Serving with PagedAttention: https://vllm-project.github.io/2023/06/20/vllm.html
- SGLang: Efficient Execution of Structured Language Model Programs: https://arxiv.org/abs/2312.07104
- Mooncake: A KVCache-centric Disaggregated Architecture for LLM Serving: https://arxiv.org/abs/2407.00079