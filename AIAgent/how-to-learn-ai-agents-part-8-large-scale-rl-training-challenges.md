# How to Learn AI Agents (Part 8): The Challenges of Large-Scale RL Training

**Source:** [@Tedli8](https://x.com/Tedli8/status/2102256438617997555)

Xiaomi recently put the RL training process of MiMo-V2.6 on a public dashboard. Compared with the final leaderboard, what's more valuable about this livestream is that it shows us what large-scale Agent RL is really wrestling with: long trajectories, async execution, environment failures, multi-capability mixed training, reward determination, and the growing gap between the probabilities on the generation side and the training side.

When ChatGPT first appeared, the emphasis of RLHF was usually making the model more aligned with human preferences, safer, and more like a usable chat assistant. Today's post-training has moved to another stage: the model must not only "answer well," but also call tools, modify code, observe results, and revise plans across dozens of interaction turns — and finally get the task done.

Algorithms still matter, but what truly determines whether training can scale is increasingly systems engineering.

## Why Is PPO Strong but Hard to Scale to LLMs

Classic PPO-style RLHF usually involves four roles: the Actor that generates, the Critic that estimates state value, the Reward Model that scores results, and the Reference Model that constrains the policy from drifting too far. Concrete implementations can share, shard, or offload some computation, but overall they still need to maintain several sets of large-model forward passes and training states.

This isn't just "storing a few more copies of the weights." Training must also store gradients, optimizer states, and activations; meanwhile the Actor keeps generating trajectories, the Critic estimates advantage, the Reward Model scores, and the Reference Model computes policy drift. Once the model is large, sequences are long, and concurrency is high, memory and throughput both quickly become bottlenecks.

That's why many early teams chose DPO, rejection sampling, or SFT iteration first. They may not theoretically replace PPO, but the engineering chain is shorter and easier to get running first.

## GRPO and DAPO: Removing the Heaviest Piece First

The key change of GRPO is that it no longer trains a separate Critic; instead it samples a group of answers for the same question and constructs advantage from the relative rewards within the group. This saves the value network and its training state, and suits math, code, and Agent tasks that have verifiable answers.

DAPO continued down this road with several important engineering changes: Clip-Higher with asymmetric upper and lower bounds, dynamic sampling, token-level policy gradient, and a loss aggregation better suited to long answers. Dynamic sampling discards groups that are all-correct or all-wrong, because those groups have no relative difference — advantage is near zero — and continuing to train only wastes compute.

Judging by the metric names on MiMo's public dashboard, this training used a GRPO/DAPO-style skeleton: you can see metrics like the actor's clipping ratio, within-group advantage, dynamic sampling, and token-level updates, but no continuously learned value network. The KL penalty on the dashboard is zero, which also shows it didn't rely on an extra KL loss to hard-pull the policy back toward the reference model.

But saving the Critic is only the start. The hardest part of large-scale Agent RL has shifted from "how to compute advantage" to "how to stably produce trajectories, score them, and send them back to the trainer."

## One Training Step Hides a Distributed Pipeline

An Agent trajectory is no longer "input a question, output an answer." It may enter a sandbox, call tools, read and write files, run tests, retry after failure, and then be scored jointly by multiple rules and models.

One round of training can roughly be decomposed into: sample prompts → generate multiple long trajectories per question concurrently → execute them in the tool environment → score with tests and rubrics → filter out questions with no within-group variance → do trajectory- or token-level credit assignment → update the policy.

This pipeline has three direct consequences.

First, successfully returned trajectories are always fewer than the tasks sent out. Sandboxes may interrupt, tools may time out, environments may preempt resources, and long tasks can be held up by slow nodes. The system must keep resampling, recover partial rollouts, and assemble truly trainable data into stable batches.

Second, multiple capabilities can't simply be trained serially. If code, vision, general tools, dialogue, and safety tasks are optimized in rotating phases, it's easy to learn the later ones and forget the earlier ones. A more realistic approach is to mix multiple harnesses and task domains in the same update round, while simultaneously handling data ratios, reward scales, and difficulty differences.

Third, reward is no longer just a final 0 or 1. Across dozens of turns, which actions truly advanced the task, which merely detoured, and which "gamed the scorer" all need finer credit assignment. Test cases, rubrics, model judges, rule checks, and hacking detection must ultimately decompose the result back to the trajectory or even token level.

## The Biggest System Problem: Generation and Training Are Drifting Apart

RL must first make the model generate, then update the model with the generated results. At small scale you can queue: sample a batch, train one step, then sample the next batch with the new weights.

Once Agent trajectories get long, this synchronous approach creates a lot of waiting. Short tasks finish early, but the training card must wait for the slowest few-dozen-turn trajectory. To improve utilization, systems decouple the Rollouter from the Trainer: the inference cluster keeps generating, and the training cluster starts updating as soon as it has enough samples — the two proceed in parallel in wall-clock time.

Efficiency rises, but samples start to go "stale." The Rollouter may still be generating with an old policy while the Trainer has already updated to a new version. The longer the trajectory and the faster the updates, the larger the version gap.

Furthermore, even if both sides use the same weights, the inference engine's fused operators, precision, sampling truncation, or MoE routing may compute different token logprobs than the training framework. So there are two kinds of divergence: one from weight versions, another from computational implementation.

Policy gradients need to know: relative to the sampling policy at the time, how much did the probability of generating these tokens change under the current policy? If this ratio is computed wrong, the update direction is distorted — actions that should be encouraged may not get enough weight, and unreliable old samples may drag the new policy off course.

Therefore, "fully async" doesn't mean "everyone runs on their own." The system must record which policy version each sample came from, monitor the logprob divergence between rollout and trainer, limit staleness, and correct bias through rollout importance sampling or truncated importance sampling. Samples that drift too far should be down-weighted or discarded.

This can be captured in one sentence: large-scale parallelism is not replicating the same computation, but letting generation and training run forward separately, then constantly reconciling.

## Where Large-Scale Agent RL Is Truly Hard

The difficulty of today's post-training is no longer just "PPO, GRPO, or DAPO." The algorithmic skeleton is increasingly clear; what's genuinely hard is doing the following things well at once:

- Keep producing large numbers of long trajectories without being dragged down by slow tasks and failures;
- Keep multiple task domains balanced within the same training round, avoiding capability overwriting;
- Decompose final success/failure back to key steps for trustworthy credit assignment;
- Run inference and training asynchronously in parallel, while keeping version staleness and logprob bias within an acceptable range;
- Find a dynamic balance among throughput, sample freshness, training stability, and hardware utilization.

The value of Xiaomi's public training process isn't just showing a new checkpoint, but putting real system friction on the table: failed trajectories, unbalanced loads, stale samples, and a training pipeline that needs continuous calibration.

The ceiling of model capability is determined by data and algorithms, but whether large-scale RL can run stably ultimately depends on whether the whole system can ensure that every expensive Agent trajectory is correctly generated, evaluated, and utilized.

## Further Reading

- MiMo-V2.6 RL Live: https://mimo.xiaomi.com/rl/
- MiMo-V2-Flash Technical Report: https://github.com/XiaomiMiMo/MiMo-V2-Flash
- DAPO: An Open-Source LLM Reinforcement Learning System at Scale: https://arxiv.org/abs/2503.14476
- veRL Fully Async Policy Trainer: https://github.com/verl-project/verl/blob/main/docs/advance/fully_async.md
- Uni-Agent: https://github.com/verl-project/uni-agent
- vLLM Trace Replay: https://docs.vllm.ai/en/latest/serving/online_serving/trace_replay/