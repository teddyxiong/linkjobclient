# What Kind of Talent Do Companies Scrambling for FDE Actually Need?

**Source:** [@Ellieorange8 (一只小橘呀)](https://x.com/Ellieorange8/status/2083367958768992718)

Over the past while, "FDE" has suddenly become a hot hiring keyword at many internet and AI companies. ByteDance, Alibaba, Tencent, NIO, Zhipu... nearly every company on the frontier track is scrambling for talent.

But what kind of person does FDE actually need? Recently I went through the FDE JDs of several head companies.

Looking at them together, one interesting trait emerges: though the tech stacks are completely different, their requirements for the "person" are surprisingly consistent.

In this article, I'll use these two JDs as a starting point to talk about my understanding of the FDE role.

## 1. The Essence of FDE: the Trinity of Technology × Business × Customer

The first sentence of almost every FDE JD states the truth: this is a comprehensive role.

"A comprehensive role combining algorithm technology + product engineering + customer-facing work, requiring frequent business travel or on-site presence at the client."

There are three key words in this sentence:

- **Algorithm technology:** understand technology and be able to solve problems independently;
- **Product engineering:** can assemble scattered capabilities into a landable solution;
- **Customer-facing:** can think about value from the customer's perspective.

An FDE is not the top algorithm engineer, not a pure pre-sales consultant, and not a traditional product manager. They are a "special forces soldier" wearing the armor of three roles at once — able to talk strategic value with a CXO in a meeting room, troubleshoot logs alongside engineers in the server room, and demo in front of a whiteboard for the client.

One detail in the JD is spot on:

"Bridge the gap between large-model technology demo and actual business value creation, driving projects from the exploration stage into the formal implementation stage."

This is the FDE's real mission: pushing "technology can do it" forward to "business needs to use it."

## 2. The Core Capability Matrix of FDE

Comparing two JDs from different directions, I distilled the **7 core capabilities** an FDE needs.

**1. Technical depth: can genuinely solve problems on-site**

An FDE is not a PPT engineer. The keywords that keep appearing in JDs are: **independently complete code development and debugging, and have full-stack development capability for simple demos.**

**AI direction requires:**

- Familiar with large-model technical principles, and master methods for evaluating large-model performance and results;
- Familiar with various post-training techniques;
- Familiar with calling APIs of large-model-related products;
- Master the principles and applications of mainstream frameworks like LangChain and AutoGPT;
- Familiar with AI application architecture patterns like RAG, Agent, and Workflow;
- Able to design and implement complex multi-Agent collaboration solutions.

**Embodied-intelligence direction requires:**

- Robot whole-machine debugging, parameter calibration, and sensor joint debugging;
- Joint hardware-software troubleshooting;
- Basic networking, equipment joint debugging, system configuration, log analysis, and interface joint debugging;
- Locating software-hardware system-level issues (log analysis, config checks, communication-link troubleshooting, sensor anomalies, etc.).

**Common point:** understanding technology isn't for showing off — it's for independently getting things done at the client's site.

**2. Business translation: turn customer pain points into landable solutions**

One of the FDE's core values is "translation."

The AI-direction JD writes:

"Based on large-model application thinking, design and implement complex Agent architectures and Workflow workflows, completing the entire process from solution design to code implementation."

This requires the FDE to neither do only technology while ignoring business value, nor only translate requirements while failing to land a solution. An FDE must build a bridge between the client's high-level strategy and the engineer's code.

The embodied-intelligence direction similarly requires "quickly understanding customer needs and turning them into technical solutions or verifiable prototypes"; the "last mile" from requirement to prototype is the FDE's main battlefield.

**3. Communication bridge: connecting the customer with product & R&D**

Almost every JD puts "communication" in the top three. The embodied-intelligence JD even lists a dedicated line:

"Have good customer-communication skills and service awareness, able to manage customer expectations well on-site."

What an FDE does is subtle: they can't fully represent the customer (that would make them "a vendor within the vendor"), nor fully represent the company (that would lose the customer's trust). They are the "interpreter" and "mediator" between the two sides.

Especially after the project moves from PoC into formal development, the FDE must also "help the product-R&D team output technical solutions/flowcharts/use cases to ensure clear understanding," and "regularly review project progress to ensure the product-R&D team's technical direction stays on track" — this is work with a distinctly dual "product + technology" perspective.

**4. On-site execution: creating certainty in uncertainty**

An FDE often has to face the "client site" — an environment full of uncertainty.

The embodied-intelligence JD describes it vividly:

"Complete on-site environment surveys, deployment-condition confirmation, risk identification, and implementation preparation." "Follow up on client-site issues, doing first-line investigation, locating, reproducing, recording, and closing the loop; escalate complex problems promptly and coordinate support from R&D, product, algorithm, and hardware teams."

An AI-direction FDE also travels or stays on-site frequently. This means the FDE must have:

- **Stress tolerance** — on-site problems can't be delayed;
- **Closed-loop awareness** — track the whole process from discovery to resolution;
- **Project-advancement awareness** — don't let things get stuck in your own hands.

**5. Prototype-driven: speak with PoC/Demo**

Both directions' JDs unanimously emphasize "rapid prototype/demo building capability":

"Quickly build minimal functional-validation demos and PoC prototypes based on customer needs (any method — low-code tools, simple scripts, LLM Agent frameworks, etc.)."

This is the FDE's signature capability: **prove "this can be done" in the fastest way possible, then use subsequent projects to turn "it's done" into "it's done well."**

In the AI era, this is especially important. The client's leadership often holds a romantic imagination about "large models," and the FDE needs 3–5 days to turn that "imagination" into "verifiable expectations" with a runnable demo.

**6. Ownership: treat the project as your own**

This is almost a "soft standard" across all FDE JDs:

"Strong action-oriented, with a sense of project ownership." "Have strong execution ability, stress tolerance, and project-advancement awareness."

Technology can be learned and communication can be practiced, but "ownership" is the hardest to cultivate. An FDE must proactively think "what's the value of this project to me, to the client, and to the company," rather than waiting for the client to assign tasks.

This is essentially an "entrepreneurial mindset" — treating yourself as the CEO of this small project, not an executor.

## 3. A Product Manager's Perspective: How Far Is a PM From FDE?

Writing this far, I wondered: **if a product manager wants to become an FDE, what capabilities do they need to add?**

This question matters because the "adjacency" between PM and FDE is actually very high. Both roles' core work is "understand requirements + translate into solutions + drive implementation." The difference is that FDE's requirements are more extreme — not just "think it through" but also "build it"; not just push the plan in the office, but get to work directly at the client's site.

**Taking stock of a PM's natural advantages:**

- **Business understanding** — this is a PM's basic skill and one of the most scarce foundational abilities FDEs need. Too many engineers can write correct code but don't know why this code is being written.
- **Requirement translation** — turning vague customer problems into structured requirement descriptions: PMs do this every day.
- **Project-advancement awareness** — a PM is naturally a "project-pusher," highly consistent with the "ownership" an FDE needs.
- **Experience spanning multiple roles** — a PM already deals with R&D, design, operations, marketing, sales, and customers, which is exactly the "connector" ability an FDE needs.

**But there are also capabilities that need to be deliberately added:**

- **Hands-on technical ability** — moving from "knowing how it should be done" to "doing it yourself." A PM's biggest shortcoming in transitioning to FDE is writing too little code. Start with low-code tools or LLM Agent frameworks, build 10 runnable demos first, then talk about architecture design.
- **On-site troubleshooting** — a PM habitually analyzes problems in meeting rooms, whereas an FDE's habit is "open the logs, locate the error, give a direction within 5 minutes." This muscle memory can only be trained in real projects.
- **Adjusting tolerance for "perfection"** — a PM tends to make perfect plans; an FDE tends to make "good enough" prototypes. Transitioning to FDE requires mentally accepting "80% that runs > 100% that's still on paper."
- **Stress tolerance** — when a problem happens at the client site, there's only one choice: fix it. There's no "we'll go back and study it."

Simply put, the PM → FDE transition path can be split into three steps:

**Step one: add "technical density" within your current role**

Proactively join technical reviews, build demos by hand instead of only drawing prototypes, and use AI tools (Cursor, codex, etc.) to try building a rough version of the features in the PRD yourself.

**Step two: find opportunities to work at the customer's site**

Apply to go on a few business trips with the pre-sales or delivery team to feel the "on-site atmosphere." If your company has no such opportunities, take on some freelance projects on the side to practice.

**Step three: make "technical implementation" your personal label**

Adding a line to your resume — "capable of independently building AI Agent prototypes" — will make you stand out in FDE interviews.

## 4. In the AI Era, Are the Requirements on People Higher or Lower?

This is a question I've been thinking about too. I believe **the technical entry barrier is lowering, while the comprehensive-capability barrier is rapidly rising.**

The lowering barrier shows in how AI coding assistants, low-code platforms, and LLM Agent frameworks (LangChain, etc.) are making "writing code" unprecedentedly easy. Before, a PM wanting to build a runnable system might need a year of coding. Now, using Coze's drag-and-drop building with AI-generated code, you can produce a prototype in 3 days.

For PMs transitioning to FDE, this is a **huge structural tailwind.** The biggest shortcoming — hands-on technical ability — has been lengthened by AI tools.

The rising barrier comes from "being able to build something" becoming the new baseline, so competition naturally shifts to harder dimensions:

- **Not "can you do it," but "what you can do."** You built a demo in three hours; someone else built one in two. The barrier has moved from "doing" to "understanding requirements, defining the solution, and judging priorities."
- **Not "a single skill," but "a combination of skills."** AI can write code, but it can't talk strategy with a client's leadership on-site, can't calmly troubleshoot when the system crashes, and can't judge "should this requirement be done at all." These **cross-domain decision abilities** are something AI can't replace for now — and they'll only become more valuable.
- **Not a "tool user," but a "problem definer."** AI can generate an Agent's code for you, but it can't tell you "what problem this Agent is actually solving for the customer." **Defining the problem > executing the plan** — this will become increasingly obvious in the AI era.

**Pure executors are depreciating; people who can define problems, understand business, and drive implementation are appreciating.**

The ceiling of the FDE role comes precisely from the fact that it doesn't ask you to score full marks on any single item, but rather requires you to have no short board across the three dimensions of "technical implementation + business understanding + communication & coordination." The scarcity of this kind of T-shaped or even π-shaped talent **won't decrease because of AI — it will become even rarer as the technical barrier is leveled.**

This role has high pressure and high capability requirements, and people who meet those requirements in the job market are very scarce. Everything is uncertain, and everything revolves around satisfying customer needs — it's a bit like entrepreneurship, except you don't need to hunt for customers yourself.

I actually think an excellent FDE often has an "**antifragile**" quality: willing to create certainty within uncertainty, willing to crawl through the customer's real scenarios and proactively treat other people's problems as their own.