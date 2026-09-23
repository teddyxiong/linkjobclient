# No-Fluff Guide: How Does a Complete Beginner Start as an FDE? Breaking Down the Guancha Course (With Resume, Interview, and Portfolio Tips)

**Source:** [@AmberTreelet (小树)](https://x.com/AmberTreelet/status/2088890051862430040)

An AI industry role with a top salary of $220,000 a year — FDE. Some say it's the role closest to customer outcomes in the AI era; others say it's just on-site outsourcing with an English name.

After finishing the Guancha (观猹) training camp content, I found this role isn't simple. Below, I'll walk beginners through what FDE actually is, how to break in, and how to prepare your resume, portfolio, and interview.

**Table of Contents**

1. What exactly does an FDE do?
2. FDE's specific types: business, product, and engineering
3. How to start your first project
4. SOW, Spec, Demo, MVP: easily overlooked details
5. Skill, CLI, Subagent, and Hook: content distillation and reuse
6. API, MCP, CLI, and UI automation: how do you actually connect enterprise systems?
7. Traditional testing doesn't fit agents: the six-step EDD loop
8. Telling real from fake roles, resume, portfolio, and interview
Finally

## 1. What Exactly Does an FDE Do?

**FDE** stands for **Forward Deployed Engineer**, usually translated as "front-line deployment engineer."

**Here "front line" means the customer's site: an FDE enters the customer's real environment, understands the business, connects data and systems, builds applications quickly on-site, and feeds first-line experience back to the product team.**

First, look at a common scenario:

> A company wants an AI customer service. The AI can explain product features and look up return/exchange policies — everyone is satisfied.

> Once it goes live, the problems arrive.

> A user asks: "Can the snowboard be shipped overnight by SF Express to Xinjiang for a fee?" The AI can calculate shipping, but doesn't know a snowboard counts as an over-length item. You patch in the rule, then realize the delivery time can't actually be met. The more rules you add, the longer the answers get, and the user still doesn't know whether they can buy it. Products, promotions, and after-sales policies keep changing. Who updates the materials and who handles wrong answers were never made clear at the start of the project.

> It's too much trouble, so everyone goes back to the old way of working.

The customer doesn't need an "all-purpose AI customer service." **The FDE is the person who handles the real business, taking end-to-end responsibility for a measurable business result in a real environment.** The complete process looks like this:

- **Requirement identification:** an FDE first needs to see how front-line employees normally get information, complete tasks, collaborate with colleagues, and handle exceptions.
- **Cross-level communication:** get **management**, **middle managers**, and **front-line employees** aligned; management invests resources, middle management cooperates, and front-line staff are willing to hand over real processes and feedback — only then can the project move forward.
- **Engineering & system integration:** only after the problem is clarified do you move to processing data, connecting tools, orchestrating the Agent, completing deployment, and hooking it into the enterprise's existing systems. What you deliver is production-grade capability that runs stably, withstands multi-user use, and is traceable when problems occur.
- **Evaluation & validation:** before the project starts, clarify the goal, test tasks, verification samples, and acceptance criteria, so you don't finish the system only to find both sides understood it completely differently.
- **Distillation:** which rules can be written as templates, which capabilities can be turned into Skills, and which problems should be fed back to the product team — so the work doesn't reset to zero when the project ends, and next time the team can start faster and steadier with a similar client.

## 2. FDE's Specific Types: Business, Product, and Engineering

FDE can be split into three directions that collaborate and also overlap with each other:

- **Business-type FDE:** closer to the customer and commercial front line, responsible for finding project opportunities, identifying who can truly make decisions, pushing the customer to decide, and maintaining relationships. It usually requires understanding business and organization and building trust, so **people from sales, pre-sales, and customer-success backgrounds find it easier to enter this path.**
- **Product-type FDE:** closer to the problem and the solution itself, responsible for breaking the customer's vague expression into clear requirements, deciding what to do and not do this time, designing the solution, building the demo, and pushing the project forward. **People from product management, solution, project management, and design backgrounds usually have an advantage here.**
- **Engineering-type FDE:** closer to system delivery, responsible for actually building the solution, including handling models and data, connecting enterprise systems, completing testing and deployment, and ensuring stable operation after launch. **People from R&D, algorithms, testing, and implementation backgrounds are usually better suited to start here.**

For complex projects, the safest minimal organization is still the "**iron triangle**" of business, product, and engineering.

**Palantir**'s way of dividing work in its FDE team can also serve as a reference —

- **Echo** is **closer to the customer and business front line**, responsible for understanding the customer, discovering the real problem, and translating vague requirements into a plan the team can execute. They need to build trust with the customer, understand industry rules, and determine what to do first this project, to what extent, and who does the final acceptance.
- **Delta is closer to engineering and the delivery front line,** responsible for turning an already-thought-out plan into an actually runnable product. They quickly build a prototype, then integrate data and systems, handle testing and errors, and finally ensure the tool can launch, be used, and that problems are handled.
- **Solo FDE** takes on the core work of both Echo and Delta: **able to understand the business and also turn that business into a system,** and responsible for the final result.

## 3. How to Start Your First Project

Don't start with large clients — work within your means and begin with small-to-medium businesses in an industry you know.

1. **Start with people and industries you already know,** such as friends-and-family businesses, your former work domain, vertical communities, or existing client relationships — this reduces the cost of building trust and understanding the business.
2. Don't try to transform the whole company at once; **first find one specific person, one clear task, and one end-to-end process,** ideally where both input and output can be described clearly.
3. Once chosen, **first do it yourself the original way,** see where the materials come from, how employees make their in-between judgments, and which step is easiest to get wrong, then decide which parts suit AI.
4. At the same time, collect a few real tasks, common samples, and error-prone edge cases; **agree in advance on what counts as "usable" and what counts as "failure,"** rather than finding out after the tool is done that both sides expected different things.
5. For the first project, don't chase full automation; **prioritize starting with tasks like document organization, customer follow-up, and preliminary analysis** — where errors can still be manually reviewed — make a result first, then gradually build trust.
6. **The key to finding clients isn't pitching AI everywhere,** but letting the genuinely relevant people see that you've understood similar problems and have a way to solve them.

## 4. SOW, Spec, Demo, MVP: Easily Overlooked Details

First, explain a few terms:

- **SOW:** the two parties' project agreement. Write down clearly "what exactly we're doing this time, who's responsible for what, what counts as done, and what happens when the client adds requirements on the fly." It's mainly for the client and project lead to see.
- **Spec:** the development spec. SOW says "what to do"; Spec says "how exactly to do it" — e.g., how the page is designed, where data comes from, which steps AI handles, and which cases to test. It's mainly for the development team.
- **Demo:** a demonstration sample. First build a small runnable version to prove the direction is right. It may not be usable by employees long-term; the point is to let the customer see "is this the thing you understood it to be."
- **MVP:** minimum viable product. A step beyond the Demo — it can be handed to a small number of real users and runs one complete workflow end to end; not many features, but it can genuinely help someone finish a task.

In FDE project work, the team doesn't start developing the moment the customer says a sentence. Here are things to note:

- **Which projects not to take:** if the client keeps refusing to let you access the real process, business staff, data samples, or the acceptance owner. It's very likely not yet a formal project — it might just be market research, vendor comparison, or someone wanting AI for an internal report. Don't rush to take it.
- **Winning the client's trust is the core step:** make the client believe you can do it — trade peer case studies, demonstrable results, or industry experience for one deep conversation — rather than demanding the full budget, data, and system permissions up front.

> Large clients may care more about which complex projects you've done; small-to-medium businesses care more about whether peers have succeeded; a client with a clear pain point usually prefers to see a targeted plan or a small demo.

- **Go on-site to see the real problem:** **don't just listen to what the client says** — observe and judge for yourself: who initiated it, who budgets it, who does acceptance; go see how front-line employees actually get information, complete tasks, and handle exceptions, and why this problem has never been solved before.
- **You must confirm the acceptance criteria, or you'll step into a pit:** before the project starts, use the SOW — the Statement of Work — to write out goals, scope, deliverables, each side's responsibilities, data conditions, milestones, testing approach, acceptance criteria, requirement changes, and payment milestones.
- **Translate into development tasks:** only after the SOW clarifies the commercial boundary do you enter the Spec. What the page looks like, where data comes from, how the model is called, which materials can be used, which scenarios to test, and when to launch — all get broken down here. That way engineers and coding agents don't develop by guessing.
- **First build the shortest Demo to align direction:** pick just one most-core process, use real samples to run through input, processing, and output, first prove it's valuable to the boss, usable by business, and integrable by IT, then gradually move to real-user trials and formal production.
- **Formal delivery:** the system plugs into real work; employees know how to use it and who handles errors; approval, payment, deletion, and external publication need someone's confirmation. The client's private information needs desensitization, a private environment, or a client-approved sandbox.
- **Leave capability behind after delivery:** once the system is truly live, you still handle stability, permissions, exceptions, and manual confirmation, and distill the on-site rules, failure cases, testing methods, tool connections, and process templates so the next similar project doesn't start from scratch.

## 5. Skill, CLI, Subagent, and Hook: Content Distillation and Reuse

First explain the terms:

- **Skill** can be understood as the AI's "**job description and work manual**". It tells the AI how to handle a task: which materials to look at first, what steps to judge by, which rules not to touch, when it must escalate to a human, and what result to hand in.
- **CLI** **can open the door.** With it, the AI can open the door to enterprise systems — query the CRM, read orders, check inventory, or write follow-up records back.
- **Subagent is the "work division group" within a project.** A complex task doesn't have to be handled by one AI from start to finish; you can have one look up materials, one make the judgment, another check the result — each only handles its own segment, so when errors happen it's easier to know where it's stuck.
- **Hook** is like the "**automatic switch" or "alarm**" in a process. When a task finishes, it automatically notifies sales; when a high-risk customer is found, it automatically reminds a human to confirm; when the system errors, it automatically logs and notifies the owner — so the process doesn't need to be constantly watched by a human.

As said earlier, an FDE doesn't just finish a project — they leave the project's experience behind.

The most common thing left behind is a Skill, which can be understood as a "**role SOP**" for the AI. For example:

> For instance, an experienced customer-service rep knows: when a user asks about logistics, first check the order and region; if it involves a refund, don't promise directly; if the information is incomplete, ask follow-up questions first; if the reply is too long for the user to understand, give a clear conclusion first.

> Organize it into a Skill (**business rules + work steps + tool entry points + checking criteria**): what problem triggers it, what materials to grab, what steps to judge by, which things to do directly vs. escalate to a person, and the final output.

The best tasks to do first are those that are high-frequency, repetitive, frequently require looking up materials, heavily depend on veteran-employee experience, and whose results can be checked. For example: customer service checking logistics, sales screening leads, finance verifying reimbursements, operations checking for anomalous data. Conversely, if every task is completely different and you can't even define what "done well" means, don't rush to package it into a Skill.

**At the same time, a Skill needs CLI, Subagent, and Hook to cooperate.** String them together, and it becomes:

**Skill tells the AI how to judge a lead
→ CLI helps it query the CRM and customer records
→ Subagent separately handles looking up materials, judging, and checking
→ Hook automatically notifies the relevant person on completion, failure, or high risk**

Only when these parts combine is the AI no longer just "chats" — it starts being able to do things.

A Skill's value also isn't in its first version, but in getting better with use. Every new error, every new rule the client adds, every new exception an employee discovers can become a new test case, used to update the Skill.

When multiple clients repeatedly hit similar problems, the team compiles the common rules, tools, and test cases into Skills, CLIs, and workflows — only then does the gravel road gradually turn into asphalt.

## 6. API, MCP, CLI, and UI Automation: How Do You Actually Connect Enterprise Systems?

**The conclusion: an API is the interface of the system itself; MCP and CLI are the different ways an Agent calls these capabilities; UI automation is the fallback when no interface exists.**

Think of the Agent as a newly hired employee who needs to collaborate with every department in the company.

- **API** is each system's "direct service window" for them. For example, querying orders, checking inventory, or writing customer records — submit the request as specified and the system returns the result.
- **MCP** is the company's "directory plus how-to guide". It tells the Agent: what tools are available in the company, whom to find for querying customers, how to create a ticket, and what information each tool needs.
- **CLI** is the "command terminal" in the Agent's hand. Once it knows what to do, it can enter a clear instruction — e.g., "read this customer's follow-up records" — and the system returns a structured result.
- **UI automation** is when there's no direct window, no how-to guide, and no command terminal — the Agent has to stare at the screen like a human, find buttons, click the mouse, and fill forms. It breaks easily when the page changes, so it's usually the last resort.

### API: Use When the System Already Has a Stable Interface

If the CRM, order system, or inventory system itself provides an API, prioritize the API. It's best for stable, high-volume data reads and writes between systems.

But APIs are fairly low-level; authentication, error handling, call sequencing, and permission control usually have to be handled by the development team itself.

### MCP: Use When You Want the Agent to Discover and Call Tools in a Standardized Way

MCP can be understood as a "tool menu" for the Agent. It's good for handing a set of tools and data resources to the Agent in a standardized way.

But more tools isn't always better. If the menu is too long, the Agent may pick the wrong tool and waste context — so at real launch, try to let it see only the capabilities the current task needs.

### CLI: Use for Local Development, Batch Processing, and Multi-Tool Combination

CLI is a command-line tool. It's more like an "operation panel" in the Agent's hand. For example:

The Agent doesn't need to understand what the web page looks like; as long as it calls by command, it gets structured results and clearly knows whether the operation succeeded or failed.

It suits local Agents, development/ops, batch processing, and chaining multiple tools into one workflow. Under the hood it usually still calls APIs — it just wraps complex interfaces into commands that are easier to discover, combine, and test.

### UI Automation: Use Only When There's No Interface and No Secondary Development

Some legacy systems have neither an API nor open tooling, and can only be operated through a web page or desktop software.

Only then do you consider UI automation — having the Agent look at the screen, find buttons, click, and type.

It can save you in a pinch, but it shouldn't become the default approach.

## 7. Traditional Testing Doesn't Fit Agents: the Six-Step EDD Loop

First explain a few terms:

- **MVP contract:** the work boundary drawn for the first-version Agent. First clarify whom it helps and with what, what counts as done, what it can't do, which materials it can use, and when it must escalate to a human.
- **EDD:** *Evaluation-Driven Development.* It's not "test after you're done" — it's the loop of "build a little → test with real cases → find problems → fix → test again."
- **Evaluation set:** a batch of real questions specifically for checking the Agent. It doesn't just contain normal questions, but also incomplete information, conflicting rules, edge cases, and historical failure cases.
- **Regression testing:** after fixing one problem, re-run the previously passing questions to confirm the new change didn't break old capabilities.
- **LLM Judge:** have another model, following scoring criteria, help judge whether an answer is relevant, complete, and clear. It suits preliminary screening; high-risk judgments involving payment, compliance, and privacy still need human confirmation.
- **Execution trace:** the full-process record of the Agent completing the task, including what materials it looked up, which tools it called, what judgments it made, and at which step it failed. Looking only at the final answer often won't reveal the real problem.

Traditional testing doesn't fit agents — ask the same question, and it may answer well this time, but next time take a different path due to changes in materials, context, or model fluctuation.

So agent testing isn't a final step tacked on at the end, but a process pushed forward **round after round**. This process is called EDD — *Evaluation-Driven Development*.

**How to do it specifically can be broken into six steps.**

**Step one: first write the MVP contract.**

Whom this Agent completes which thing for, what counts as done, what it absolutely must never do, what materials it can look up and tools it can call, and under which circumstances it must escalate to a human.

This **MVP contract** is the basis for all subsequent tests.

**Step two: prepare real test questions.**

Don't just take a few prepared questions and make the AI answer them right in a demo. Real test questions must include normal questions, plus incomplete information, conflicting rules, edge cases, and historical failure cases.

Don't test only with the most ideal questions; put in four types of situations:

- **Questions with complete information that can be answered directly;**
- **Questions with insufficient information that must be clarified first;**
- **Questions that can only be partly answered and need their boundaries stated;**
- **And questions beyond the rules that should be refused or escalated to a human.**

**Step three: first decide who does the scoring.**

Questions like "did the answer hit the key points," "can the user understand it," and "is the tone appropriate" are hard for code to judge. Here you can use an **LLM Judge** — a stronger model that, following pre-written criteria, first filters out answers that are irrelevant, incomplete, or unclear.

But an LLM Judge isn't the final referee. For high-risk matters like payment, contracts, compliance, and customer privacy, business people still have to confirm in the end.

**Step four: first run it once and see where the first version actually goes wrong.**

Don't rush to fix the moment you see a problem. First run the test questions and record which ones it fails on — did it fail to find materials, misunderstand the user, call the wrong tool, or lack permission for it in the first place. Only by knowing which layer the problem is in will you avoid fixing what is actually a system-interface issue by tweaking the Prompt.

**Step five: prioritize fixing the most important problems.**

Not every error needs to be fixed immediately. First see how often it occurs, how big the impact is, whether it could cause refunds, complaints, privilege violations, or heavy manual rework — then decide what to fix first.

The object of the fix might be the Prompt, the Skill, the knowledge base, the tool interface, or the process itself.

**Step six: after fixing, re-run all the old and new questions.**

For example, an AI customer service originally couldn't handle "can the snowboard be delivered to Xinjiang by tomorrow"; after the team patched in over-length-item and delivery-time rules, it can't just re-test that one question — it must also re-ask how ordinary goods ship and how returns are handled. Because **even though the new problem is fixed, the old problem may have been broken.** After fixing a new problem, the old problems must not come back. This step is called **regression testing**.

**As these six steps keep looping, the Agent gradually becomes something that "can stably complete a segment of work."**

## 8. Telling Real From Fake Roles: Resume, Portfolio, and Interview

### 8.1 Identifying the Role

How do you judge whether a job is a real FDE role?

In China this role doesn't yet have a unified name. Besides FDE, you'll also see titles like "solutions architect," "AI application engineer," "Agent product-solution engineer," and "delivery engineer."

**Don't just look at the Title. Ask the hiring side these five questions. Only one that can go on-site, do engineering, correct course, and take responsibility for results looks more like a real FDE.**

- **First, is the salary mainly commission from signing deals?** If so, the job is more like sales or pre-sales; an FDE can participate in winning the project, but shouldn't only be responsible for selling it.
- **Second, how much engineering is involved?** If it barely writes code, doesn't integrate systems, and does no testing or evaluation, it's usually hard to truly own delivery.
- **Third, after the project ends, what remains of the field experience?** Can the client's rules, failure cases, and solutions become the company's components, methods, or product capabilities? If nothing remains and the next client starts from zero, it's more like a one-off on-site gig.
- **Fourth, do you just demo before signing, or keep owning it after?** Only presenting plans and demos up front leans pre-sales; building the system, acceptance, launch, and handling runtime problems after signing is closer to FDE.
- **Fifth, when you find the client stated the wrong requirement at the start, do you have the power to say "no"?** A real FDE isn't someone who executes a checklist. They must point out wrong goals, narrow scope, and help the client trade off between "what they want" and "what should actually be done."

### 8.2 Resume

**An FDE resume should send at least four signals.**

**First, did you own it to the end.** Not "received a clear requirement and started developing," but "joined while the problem was still vague, and carried it through to launch and acceptance — or clearly knew why the project should stop."

**Second, did you face the business directly.** Did you interview clients or business staff, clarify requirements, handle misaligned expectations, and push the other side to decide. An FDE doesn't just deal with code.

**Third, did your work enter a real environment.** Being demo-able doesn't count. State clearly whether real users used it, how permissions were handled, what happens on errors, and where manual fallback was needed.

**Fourth, can you state the result clearly.** You don't have to write revenue; you can write test-pass rate, number of covered scenarios, task duration, human-intervention ratio, or failure types. The point is to let people see: after you finished, what changed.

So write project experience roughly this way:

> **A verb that conveys ownership + what you built + the business scenario + a verifiable result**

"Helped the client build data pipelines." Change it to — "**owned data-pipeline deployment for a retail scenario, integrating multiple scattered data sources and compressing the business-analysis preparation cycle from weeks to days**"

- **What role you can play in what kind of business scenario;**
- **Only list core skills that can hold up under questioning;**
- **Put project experience closer to the front, structured as "business background — requirement boundaries — solution — result — reusable assets";**
- **For work experience, highlight what relationship you had with customers, business, and production systems;**
- **Don't package calling a few tools as engineering capability.** If you write Agent, RAG, or MCP, be able to explain why it's designed that way, where the data comes from, how it handles failures, and how to prove it works.

### 8.3 Portfolio

For an FDE portfolio, what recruiters really want to see: how vague the client's initial problem was, how you scoped it down, what constraints you hit along the way, and whether you produced a verifiable result in the end.

> So, pick your single most complete project. Write it as a delivery story.

- **First explain the business background:** who hit what problem, and why it was worth doing.
- **Then write the requirement boundaries:** what this time solves and doesn't solve, where the risks are, and which assumptions haven't been verified.
- **Then explain the solution and trade-offs.** Why this technical route, why this step is handed to AI and that step stays with humans, and why the first version only does this one process rather than trying to transform the whole company.
- **Next, write the delivery process:** how the prototype was made, how data and systems were connected, how testing was designed, and how real users responded.
- **Finally give the result.** It doesn't have to be revenue; it can be test-pass rate, number of covered scenarios, task duration, human-intervention ratio, or which high-risk situations were successfully intercepted.

For the same project, it's best to organize it into three versions.

- **A long project write-up,** to tell the complete process, your judgment, and the retrospective;
- **A GitHub README,** to show technical interviewers the architecture, how to run it, the evaluations, and known limitations;
- **Also make a one-page PDF,** for quickly explaining the background, responsibilities, solution, results, and links when submitting.

One more thing: change client names to "a manufacturing company in East China" or "an e-commerce team"; replace amounts, accounts, orders, and chat records with mock data; and blur names, contact info, internal domains, and sensitive fields in screenshots. A portfolio shows your capability — not the client's trade secrets.

If you don't have an enterprise client yet —

> A friend's small shop, a colleague's repetitive work, community operations, or even your own workflow. As long as someone actually uses it, you recorded feedback, fixed problems, and did a second round of iteration, it's a more FDE-like portfolio than a Demo built just for show.

### 8.4 Interview

An FDE interview might give you one vague sentence: "Here are 8,000 taxi operation records; make a plan within a week." The problem doesn't say who it's for, or whether to solve pricing, dispatch, or fraud detection.

You should first ask:

> Who are the users? What's their most painful problem right now? Which value is most worth validating within a week? What can be skipped this time? What's the success criterion? Can the data be obtained? Who does the final acceptance?

**This is Scoping — first shrink a big vague problem into a small closed loop you can validate within limited time.**

**What an FDE interviewer mainly wants to see:**

- **Do you clarify first, then act, rather than treating assumptions as facts;**
- **Can you split a big problem into a few independently verifiable parts;**
- **Will you proactively think about dirty data, legacy systems, insufficient permissions, external-interface failures, and manual fallback;**
- **Can you state your assumptions so others know what conditions your plan depends on;**
- **Do you have the ability to make trade-offs.** If it can't be done in a week, what do you do first and why not the rest;
- **When communication pressure rises, can you keep explaining your thinking clearly and adjust when you hear new information;**
- **Finally, do you keep thinking about the person who will actually use this system,** rather than only whether the technical solution is elegant enough.

**Daily preparation —**

> Each week, find a vague requirement and practice explaining the user, goal, boundaries, risks, and success metrics in two minutes; find an unfamiliar project, first guess how it runs, then verify through code and actual results; when you see a new tool or protocol, try explaining it in your own words ten minutes later.

**For behavioral interviews, prepare a few real stories in advance:**

> When you proactively took responsibility, how you handled failure, what difficult trade-offs you made, and how you persuaded a client or team. Keep each one to about two minutes: the background, your task, what you did, and the final result.

## Finally

After finishing Guancha's content, my understanding of FDE changed. None of its steps are actually easy.

> You have to judge which projects are worth doing and which requirements are just a client casually saying "we also want AI"; you have to know which capabilities should be distilled into Skills and which operations must be confirmed by humans; and you have to accept one thing: finishing a Demo is only the beginning — delivering stably and iterating continuously is the harder part.

So FDE isn't a role you can enter by memorizing terminology.

It doesn't hide behind requirements documents, nor stop at a demo page; it enters the real field, understands real constraints, and takes responsibility for the final result.

**What an FDE ultimately delivers isn't an Agent. It's a business process that's already running — and that someone is willing to keep using.**