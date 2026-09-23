# How to Learn AI Agents (Part 5): The Full Landscape of the Transformer

**Source:** [@Tedli8](https://x.com/Tedli8/status/2101161125266305062)

In 2017, "Attention Is All You Need" proposed the Transformer. After that, models did not develop along a single fixed structural diagram: some kept the encoder and strengthened understanding; some kept the decoder and focused on generation; some carried on the encoder–decoder to handle clear input-to-output tasks. Today's LLMs keep making trade-offs across attention, normalization, feed-forward networks, positional representations, and training systems.

If you only want to remember one "family tree," start with three main lines: Encoder-only handles understanding, Decoder-only excels at word-by-word generation, and Encoder-Decoder connects the two. This is an entry-level view, not a capability boundary; actual results still depend on training data, scale, and training method.

## The Starting Point: the Original Transformer

The original Transformer uses an encoder to read the input and a decoder to generate the output. The encoder builds connections among input tokens through bidirectional self-attention; the decoder, through causally masked self-attention, reads only the current position and earlier tokens. The decoder also references the encoder's output through cross-attention: Query comes from the decoder, while Key and Value come from the encoder.

Each layer also contains a feed-forward network, residual connections, and layer normalization. Compared to RNNs that must recurse step by step, self-attention parallelizes sequence processing more easily; multi-head attention lets the model model relationships from different representation subspaces; and positional encoding supplies order information. The original paper used machine translation as its main experimental scenario.

## Three Architectural Lines

**Encoder-only:** leaning on understanding. Models like BERT keep the encoder's bidirectional attention and are often pretrained via masked language modeling. Each token can use context from both sides, making it suitable for tasks that need judgment and representation — classification, retrieval, entity extraction, and the like. It can also do question answering, but that doesn't mean it can only "understand" and can't participate in generation.

**Decoder-only:** leaning on autoregressive generation. GPT, LLaMA, Qwen and others mainly develop along this line. Causal attention ensures the current position can't see future tokens; during training it predicts the next token, and during inference it generates step by step. When the decoder is used alone, it usually lacks the cross-attention of the original encoder–decoder. KV Cache caches historical Key/Value to reduce recomputation during token-by-token generation.

**Encoder-Decoder:** handling input-to-output mapping. T5 unifies tasks into text-to-text, and BART uses denoising pretraining. The encoder understands the input, the decoder generates the output, and cross-attention links the two ends. Such structures remain valuable in sequence-to-sequence tasks like translation and summarization.

## How Decoder-Only Evolved

From here, it helps to treat the model as a continuously re-engineered system: information must flow stably through deep networks, generation must control caches, long context must control compute, and more parameters must also account for training cost. Each abbreviation below corresponds to one of these bottlenecks.

### 1. Making Deep Networks Easier to Train

Residual connections provide a path close to identity mapping, so each layer can continue modifying on top of the existing representation. Network degradation and gradient-propagation difficulty are related but different problems — you can't simply equate them. The original Transformer used Post-LN (normalizing after adding the sub-layer output to the residual); many later LLMs use Pre-LN, which lets gradients propagate more easily along the residual path. RMSNorm removes mean-centering and scales only by root-mean-square — another common choice. More recent Hyper-Connections, mHC, and Attention Residuals try to improve how information mixes across layers; they are different research proposals, not the same "add more channels" tweak.

### 2. Reducing Attention's Memory and Compute Cost

Standard multi-head attention (MHA) needs to store each head's historical Key/Value during inference. MQA lets multiple Query heads share one set of KV; GQA lets a group of Query heads share a set of KV, reducing cache; MLA uses low-rank latent representations to compress KV — another route. FlashAttention mainly optimizes memory access patterns in attention computation; the problem it solves isn't quite the same as MQA/GQA/MLA, and it doesn't eliminate the compute burden of full attention growing with sequence length.

Long context also has sparse and hybrid routes. Native Sparse Attention (NSA) combines local windows, compressed representations, and a selection mechanism; DeepSeek Sparse Attention (DSA) further uses an indexer to select relevant historical positions. Kimi Linear mixes Kimi Delta Attention with MLA layer by layer, letting linear attention and full attention each do the work they're suited for. These are all specific designs to reduce long-sequence cost — you can't attribute "million-token context" to any single component, nor treat them as a one-size-fits-all recipe.

### 3. Reworking the Feed-Forward Network

The original Transformer used two linear layers and ReLU. Later common activations or gating structures like GELU and SwiGLU improved expressiveness; SwiGLU is usually paired with hidden-dimension adjustments to control parameters and compute. MoE hands part of the feed-forward computation to multiple experts, with each token activating only a few experts — accommodating more total parameters at lower per-token activation cost, while bringing routing, load-balancing, and communication issues.

### 4. Representing Position

Early models commonly used absolute positional representations. RoPE injects relative-position information by rotating Query and Key, and has been adopted by many models; methods like positional interpolation and scaling can extend context, though actual effects still need training and evaluation to verify. NoPE doesn't explicitly add positional encoding and is a research direction worth watching; the causal mask provides order constraints but doesn't automatically, precisely represent every token distance, so you can't simply declare that positional encoding is no longer needed.

### 5. Making Training and Inference Actually Run

Optimizers like AdamW and Muon decide how parameters update; mixed precision, parameter sharding, parallel training, and gradient checkpointing decide whether large models can be trained on finite hardware. On the inference side there are continuous batching, PagedAttention, speculative decoding, and quantization. They aren't the Transformer's network structure itself, but they directly affect cost, speed, and usability.

## How to Remember It in One Diagram

First look at how information flows: the encoder reads bidirectionally, the decoder generates causally, and cross-attention links the two ends. Then look at where the bottlenecks are: is deep training stable, is the KV Cache too large, is long-context computation too expensive, and must all parameters activate every time. Finally look at the cost of each solution: every optimization trades off among quality, memory, throughput, training stability, and engineering complexity.

Today's Decoder-only LLMs still look like repeated stacking of "attention + feed-forward network"; what actually makes them usable is the long-term iteration of these components and systems. To understand the Transformer you don't need to memorize every abbreviation — first grasp the three main lines, then ask what cost each change solves.

## Further Reading

- Original Transformer: https://arxiv.org/abs/1706.03762
- Native Sparse Attention: https://arxiv.org/abs/2502.11089
- DeepSeek-V3.2 / DSA: https://arxiv.org/abs/2512.02556
- mHC: https://arxiv.org/abs/2512.24880
- Kimi Linear: https://arxiv.org/abs/2510.26692
- Attention Residuals: https://arxiv.org/abs/2603.15031