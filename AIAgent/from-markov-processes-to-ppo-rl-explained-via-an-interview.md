# From Markov Processes to PPO: Reinforcement Learning Explained Through an Interview Story

**Source:** [@Tedli8](https://x.com/Tedli8/status/2100806881535308006)

Suppose you have three years of experience across manufacturing, e-commerce, and the internet. Now you're applying for an internet job, and the interviewer flips open your resume and very likely asks: "Why did you switch industries twice?"

The same experience can be answered in many ways. You have to explain the past while also contending for the next round; with every sentence you say, the interviewer's reaction and his next question may change. Treat this interview as a sequential decision process, and we have a path to understanding reinforcement learning.

Let me be clear up front: the interview is only a metaphor to aid understanding, not a real training environment. We'll ride it all the way to PPO, and stop to explain at points where the analogy could mislead.

## Step One: From "What Happens" to "What I Can Do"

The simplest Markov chain has only states and transitions between them — for example "submitted resume → received invitation → entered first round." It describes what might happen next, but doesn't yet discuss what action you can take. The key of "Markov" is this: if the current state already contains enough information, predicting the next step doesn't require extra dependence on more distant history. In a real interview, just the words "in the first round" aren't enough; what you've discussed earlier should also count as part of the state.

Add a reward to the state transitions and you get a Markov reward process. Receiving an interview invitation can be recorded as positive feedback; receiving a rejection letter can be recorded as negative. It still has no action for you to choose, so the reward isn't something that "appears after you take an action" — it's an evaluation we attach to the outcome of an experience.

Add actions, and you enter the Markov decision process, the MDP. When the interviewer asks why you switched careers, the state s contains the question and prior dialogue; the action a is the answer you choose; the transition rule P determines how they might ask next; the reward r is the feedback we set for the outcome; and the discount factor γ represents how the learner weighs immediate feedback versus future gains — not how "patient" the interviewer is.

At this point our goal isn't winning any single answer, but improving the cumulative return of the whole interview: explaining clearly, holding up under follow-ups, and ultimately contending for a suitable opportunity.

## Step Two: Not Knowing What the Interviewer Thinks

The MDP gives the framework but doesn't hand you the answer. You don't know what the interviewer will ask after hearing a certain sentence, nor their internal scoring rules. In real interaction, you can only adjust your answers through repeated attempts and observation of results. This is a typical "model-free" scenario: you don't have to fully learn the environment's transition rule P and reward rule first — you can learn value or policy directly from experience.

One route is learning "value." V(s) estimates how much return you can expect going forward from the current state; Q(s,a) estimates the return you can expect if you give a certain answer here and then continue. Q-learning and DQN belong to this line of thought. If the actions are a few discrete options, picking the highest-value action is straightforward; but natural-language answers are not a few limited answer cards — you can't easily enumerate every phrasing and take the max one by one.

Another route is learning the "policy" directly: treat πθ(a|s) as the probability of choosing action a in state s. It's not a hard-coded standard answer, but a tendency to generate answers from context. Adjusting the parameter θ to increase the expected return J(θ) of the whole interaction trajectory is the basic direction of policy optimization.

## Step Three: How Much Credit Does One Sentence Actually Earn?

Scoring every sentence directly by the final outcome of the whole interview gives a very noisy signal. If you got the offer, was it the self-introduction, the career-change explanation, or the final counter-question that did it? Conversely, failing once doesn't mean every sentence you said was wrong. This is the high-variance problem common to policy gradients.

So we need a "baseline." The advantage function A(s,a) = Q(s,a) − V(s) asks not "does this answer help," but "how much better is it than what people normally choose in this state." The interviewer nodding doesn't necessarily mean high advantage: if he politely nods no matter what he hears, the signal has no discriminating power.

Who estimates the baseline? Another model. The Actor is the policy that takes actions; the Critic is the model that estimates value and assists evaluation. The Actor adjusts its choices according to the advantage signal, and the Critic corrects its estimate using the actually observed returns. That's the division of labor of Actor–Critic. The Critic isn't the interviewer himself, but an internal "review assistant" within the learner.

The advantage still needs to be estimated. If you only look at immediate feedback, you can be led astray by a smile; if you only wait for the final result, it's hard to judge each step's contribution. GAE (generalized advantage estimation) weights and combines the temporal-difference information of several consecutive steps, striking a compromise between bias and variance. It's usually used together with a value function, providing a smoother advantage estimate for policy updates.

## Step Four: Why "Changing Too Hard" Causes Problems

With the Actor, Critic, and advantage, it seems we can keep optimizing the answers. But the training data was collected under the pre-update policy πold. As you repeatedly tweak the policy on the same batch of data, the further you go, the less those answers resemble what the current policy would actually say.

So we introduce a ratio: ρt(θ) = πθ(at|st) / πold(at|st). It compares "the probability the new policy assigns to this sampled answer" against "the probability the old policy assigned back then." Close to 1 means small change; far from 1 means this old sample is now viewed quite differently by the new policy. This ratio helps us construct the update objective, but it doesn't mean old data can be reused indefinitely; PPO is still an on-policy method that needs to keep collecting fresh data with the current policy.

TRPO's approach is to add a KL-divergence constraint between old and new policies during optimization, trying to keep each update within a trusted region. It has a clean constraint idea, but implementation and computation are relatively complex.

PPO's common variant, PPO-Clip, is more direct: it uses a clipped objective function to reduce the extra benefit from the policy changing too much. Written out, it's L = E[min(ρA, clip(ρ, 1−ε, 1+ε) A)].

This formula can be understood in two halves: if A > 0, this answer is better than the baseline, so raising its probability helps; but once the probability ratio exceeds 1+ε, this sample no longer gains extra benefit in the objective from being raised further. If A < 0, lowering its probability helps; but once the ratio falls below 1−ε, lowering it further yields no extra benefit either.

Note that what's clipped is the incentive inside the objective function, not an absolute wall installed on the policy parameters. The old and new policies can still diverge too much, which is why implementations often also monitor KL divergence and stop updates early if necessary. ε is a hyperparameter controlling the clipping range of the objective — not a precise tolerance the interviewer has for "persona drift."

## Back to That Interview

Now revisit the opening question: you don't need to hide your three stints in manufacturing, e-commerce, and the internet. A better answer explains what you learned at each turn, why the next step was the internet, and how those experiences support this position. The key here is coherence in communication; it's only an analogy to help understand "don't update the policy too hard," and you shouldn't map interview tactics item-by-item onto PPO's probability ratios.

Compress the technical thread into one sentence: Markov processes describe how states change; MDP adds actions, making choice the question; model-free learning finds answers from experience; value methods evaluate actions, while policy gradients directly optimize action tendencies; Actor–Critic and GAE help estimate advantage; TRPO and PPO try to make policy updates more stable.

In LLM post-training, PPO was one of the representative methods for reinforcement learning from human feedback. But "human preference," "reward model," and "PPO" are not one-to-one mappings of interviewer, HR, and candidate, nor does every LLM's post-training have to use PPO. The metaphor should stop here: its job is to build intuition, not to replace the formulas and the actual training process.

Anyway, I should go prepare for my own interview. Next time I'll turn the lens to inference systems and Agents.

## Further Reading

- OpenAI Spinning Up: PPO
- PPO original paper
- GAE original paper