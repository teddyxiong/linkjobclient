# How to Learn AI Agents (Part 1)

**Source:** [@Tedli8](https://x.com/Tedli8/status/2099886903638253725)

GPT-3.5 was released in 2022, roughly four years ago. ChatGPT has gone from a chat companion to a tool that can take on and finish real work. Here I want to sort through how this AI wave has unfolded — and how the technology has evolved step by step to where it is today.

## From AlexNet Onward: Deep Learning

To understand this AI wave, you first have to understand the previous one.

In 2012, at the ImageNet competition hosted by Fei-Fei Li, Hinton's lab submitted AlexNet with a top-5 error rate of 15.3% (using extra data from ImageNet Fall 2011). Comparison is everything — to grasp what that number means, look at second place: the University of Tokyo, 26.2%.

Deep learning's enormous success ignited the previous AI revolution. The following year, Google bought DNNresearch — the company Hinton registered with two of his students — for $44 million. The company had no product and no revenue. The person said to have proposed the idea was Demis Hassabis, founder of DeepMind, who would later lead the AlphaGo project.

Now let's turn our gaze back to China.

In 2011, three students from Tsinghua's Yao Class came together: Yin Qi, Tang Wenbin, and Yang Mu. Yin Qi had just finished his undergraduate degree that year and was about to start a master's at Columbia; Tang Wenbin and Yang Mu had come up through various programming competitions. They rented a small office in Tsinghua Science Park, and what they built wasn't called an "AI company" at first, but a face-recognition cloud platform called Face++. You registered an account, uploaded a photo, and the API returned a string of feature values. After the platform launched in 2012, many developers discovered for the first time that recognizing faces could be as simple as calling a function — and it was free. Later they founded Megvii (旷视).

In September 2012, Zhu Long (returning from UCLA) and Lin Chenxi (formerly of Alibaba Cloud) founded Yitu Technology in Shanghai. Zhu Long was a student of Alan Yuille; Lin Chenxi was an ACM/ICPC world champion. The company's earliest orders were vehicle and face recognition for banks and public security.

In March 2014, the lab of Tang Xiao'ou at the Chinese University of Hong Kong produced DeepID on LFW, a recognized face benchmark — the first time accuracy surpassed human performance on the same test. According to reports at the time, the day the paper was posted to arXiv, phone calls from investors started flooding the lab. That November, SenseTime was registered — its name taken from the Shang dynasty.

In 2015, Zhou Xi, who came out of the Chongqing Institute of Green and Intelligent Technology (Chinese Academy of Sciences), founded CloudWalk. Later the media packaged these four together under one label — the "Four AI Dragons": Megvii, Yitu, SenseTime, and CloudWalk.

In March 2015, on stage at CeBIT in Hanover, Germany, Jack Ma made a funny face at a large screen, tapped confirm, and the payment went through. The face-payment technology came from Megvii. Of course, after the honeymoon period, Alibaba built its own face-recognition algorithm and Megvii shifted to security — but that's a story for later.

Back to ImageNet. Fei-Fei Li was undeniably prescient: she was among the first to realize that for AI to simulate humans, it needs both a sufficiently rich dataset and a benchmark standard. The various leaderboards we see in the LLM era trace their earliest origin to ImageNet.

Every coin has two sides. In the early visual-model era of image recognition, leaderboard-chasing was surely widespread, just like today's LLM frenzy. But AI development seems to follow a pattern: as models get stronger, the persuasiveness of leaderboard data only gets weaker — and that capability curve eventually hit its end. In 2017, the ImageNet challenge was discontinued. Regrettable as it was, it also proved one thing: that round started by deep learning had reached the end of what models could extract — the ability to recognize images could no longer be expressed through a leaderboard.

## AlphaGo and OpenAI

DeepMind was a small company founded in London in 2010. Its founder, Hassabis, was a chess prodigy at thirteen, later made games and earned a PhD in neuroscience. This Englishman realized early on that human intelligence has limits; his belief about AI was roughly: create intelligence, then use intelligence to solve everything else. Half a year after the deep-learning revolution erupted and Google bought DNNresearch, it also spent about £400 million on DeepMind, giving it a great deal of freedom to research freely.

There are three major schools in AI: symbolism, connectionism, and behaviorism. DeepMind took the behaviorist route rather than the connectionist one — they believed that through reinforcement learning, machines could face the real world. Hassabis initially worked precisely on game development, and this time too they started with games, stunning the world in another domain.

March 2016, Seoul. DeepMind's AlphaGo faced Lee Sedol, a 9-dan Korean master, in a five-game match; AlphaGo won 4:1. The next year, the battlefield moved from Seoul to Wuzhen. The opponent was the world's No. 1 player, 19-year-old Ke Jie, already a five-time champion — and he lost equally badly, 0:3.

The year 2017 was a sensitive moment. In 2015 China's vision models were still refreshing leaderboards; an AlphaGo appearing out of nowhere put real public-opinion pressure on the country, and Ke Jie's match was only made possible after much compromise from the China Qiyuan (the national Go association).

In October 2017, DeepMind released AlphaGo Zero: no human game records at all — it was only told the rules and left to play itself. Within three days, it beat the version of AlphaGo that had defeated Lee Sedol by 100:0. That December, AlphaZero used the same approach to learn chess and shogi.

The path, plainly stated, isn't complicated: when data isn't enough, generate your own; when no one teaches you, play against yourself; when compute is sufficient and the process repeats enough times, capability grows on its own — just like the RSI (recursive self-improvement) route today's LLMs are expected to take.

Of course we must also face a fact: once AI capability reaches a certain level, returns are diminishing. Tencent's Fine Art (绝艺) now beats essentially all human players, yet our sense of its progress has indeed grown weaker and weaker.

After Google bought DeepMind in 2014, bringing two benchmark talents in AI under its wing, someone raised a question: if all future AI were defined by Google alone, how unsettling would humanity's future be?

That person is Elon Musk, now in charge of Tesla, SpaceX, X, and xAI. He is indeed unsettling now, but it was still fine back then — which is why OpenAI (today's "CloseAI") came to be.

In December 2015, OpenAI was announced in San Francisco. The founders included Sam Altman, Greg Brockman, and Elon Musk, plus one person worth calling out separately: Ilya Sutskever — one of the authors of the AlexNet paper and one of Hinton's three students at DNNresearch. He flew from Toronto to Silicon Valley carrying a set of ideas from the same lineage as AlphaGo.

OpenAI's early research directions were many, and it did a lot of game research at first — that is, reinforcement learning. The Q-learning used in AlphaGo, along with DQN, showed up in many small games.

They used Atari games as a testbed, feeding the DQN approach in over and over, watching the machine go from randomly mashing the controller to learning to play Breakout and Pong. OpenAI's blog at the time was blunt: master the games first, then talk about the real world. Like DeepMind, they believed in the same logic — intelligence isn't taught, it's trained.

The real turning point came in 2017, when Google dropped "Attention Is All You Need" and the Transformer architecture was born. It was originally meant to solve machine translation, but turned out to be a general-purpose sequence-modeling tool: parallelizable, deep-stackable, and able to swallow massive data. OpenAI was among the first to pounce on it. GPT-1 in 2018, GPT-2 in 2019, GPT-3 in 2020 — parameters grew from a hundred million to 175 billion, and capability grew from sentence completion to writing code, translating, and solving simple math. Scale itself became the method. And it was the emergence of GPT-3.5, a phenomenon-level product, that kicked off the current AI revolution.

The Transformer, through the simple combination of next-token prediction and scaling laws, can learn the entire regularity of human language and exhibit super-intelligence.

## Where the Three Schools Converge

On November 30, 2022, ChatGPT went live. Five days to one million users, two months to one hundred million. We know there's a difference between a model and a product: if GPT-3 was a successful model, GPT-3.5 was a phenomenon-level product.

Before moving on to other knowledge, we need to understand how LLMs are trained.

LLM training has three stages: pretraining, SFT (supervised fine-tuning), and RLHF (reinforcement learning from human feedback). Pretraining feeds human knowledge text into a multi-layer Transformer; based on whether the next token matches the actual next token in the text, a loss function is computed, then backpropagation updates the weights, until the model learns the regularity of all human language. This stage gives the model linguistic knowledge.

But finishing pretraining alone doesn't make the model trained. It still can't direct itself to output the next token, nor hold a conversation — if you talk to it now, you'll find it obscure and nothing like human speech. So you enter the next training stage, SFT fine-tuning. Its purpose is to make the model's way of speaking more human; at the same time, because the training data contains a lot of language that doesn't conform to human morality, without control the model would produce many immoral statements, and the SFT stage can correct this to some degree. Of course, AI is trained for higher intelligence, so SFT uses less data and fewer rounds. What truly determines the ceiling of a model's ability — besides pretraining parameter count — is post-training.

Post-training means having the model produce data that meets human expectations, and this part is also a development of reinforcement learning. As mentioned earlier, the earliest RL was Q-learning and DQN, whose approach leaned toward connectionist RL; LLM reinforcement learning is more complex, originating from a different mathematical process: deriving the policy-gradient hypothesis from Markov processes, then refining it into the Actor-Critic model — which is actually quite similar to GANs in image generation. Later, on top of this "actor-critic" model, adding mathematical generalized advantage estimation (GAE) and gradient clipping produced the earliest PPO algorithm. Still later, DeepSeek created GRPO on its own chain of thought, reducing dependence on compute; ByteDance trimmed GRPO to obtain DAPO. Of course, in training long-horizon Agent tasks today, how to define the problem and how to define the reward function (or train a reward model) remain important challenges.

One more thing: distilling trajectories greatly reduces the difficulty of the final reinforcement-learning step.

In image and video generation, the Transformer entered as a component and brought significant improvement there too. The first widely-known breakout, Stable Diffusion, integrated the Transformer architecture into the diffusion model's U-Net — and this field's parameter counts are far smaller than LLMs'.

In this round of LLMs, we see the connectionism of the Transformer; in the post-training stage we combined the behaviorism of reinforcement learning; and from the earliest RAG knowledge bases to today's AI Agents, that's the domain of symbolic rule-ism (symbolism). Curiously, the convergence point of AI's three major schools is gradually becoming visible. That is our AI Agent.