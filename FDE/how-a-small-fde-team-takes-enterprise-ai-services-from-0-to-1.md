# A 10,000-Word Guide: How a Small FDE Team Takes Enterprise AI Services From 0 to 1 — Customer Acquisition, Pricing, Delivery, and Acceptance (With a Complete SOP Framework)

**Source:** [@xiaomanhedy (Hedy Zhang)](https://x.com/xiaomanhedy/status/2093271484311491002)

Many people's first impression of enterprise AI services is that they are purely technical work:

The client states a requirement, we build a knowledge base, an Agent, or a workflow, test that it runs, deploy it, and the project is done.

Once you've actually done it, you realize that technical development is only a very small middle segment of the process.

Before it, there's where customers come from, whether a customer is worth taking on, and whether what the boss says is actually a requirement. After it, there's how to guard scope, who's responsible for errors, how to test, who does acceptance, how to charge when requirements grow, and whether you can smoothly collect the final payment after the work is done.

We've met many business owners. Their perception of AI is stronger than their past perceptions of big data and mobile internet. The most typical case is: the boss has used Doubao himself, starts dabbling with Codex and Claude Code, and then naturally assumes AI should be able to solve every problem in the company.

But when he comes to you, he usually says just one thing:

> "I want to build an Agent in my company."

Or:

> "I want to build a knowledge base and put all my veteran employees' experience into it."

Or, more aggressively:

> "Can AI replace some of my people?"

None of these is a deliverable requirement in itself — they're just a direction, a budget, or the boss's momentary imagination.

What a small team really has to do is find the balance point between the boss's imagination and actual implementation — turning a vague sentence into a result both sides can understand, test, and accept.

This article is not a pretty but unworkable "AI startup story." Based on my past experience with B2B and enterprise AI delivery, I'll break down a single enterprise AI service engagement from start to finish:

**Where customers come from, how to screen them, when to quote, why you must go on-site, how to write the SOW, what technology not to touch, how to build a test set, how to handle requirement changes, and how to avoid not getting paid after the work is done.**

The whole chain can first be summarized in ten steps:

**Lead → Initial screening → On-site research → Requirement boundaries → Quotation → SOW → Development & delivery → Testing & acceptance → Handover & payment → Retrospective & reuse.**

For small teams doing enterprise AI services, the competition isn't about who can demo an Agent more impressively — it's about who can walk through these ten steps steadily.

## 1. A Small Team Sells Not AI, but a Verifiable Result

A business owner won't naturally pay more just because you used a more advanced model.

What he's actually willing to pay for is a specific problem being solved:

- Employees who used to look up product information over and over each day can now find answers faster;
- Customer service, after-sales, and sales no longer interrupt R&D all day long;
- A repetitive data-entry task now takes far less time;
- The process in an operations person's head has become runnable software;
- A task that once depended on some veteran employee now has searchable, handover-ready records.

So when we evaluate a project, the first thing we ask is not which model to use, but:

**Which specific step right now is the most annoying, the slowest, and the most error-prone? After it's done, how will the work change?**

This is also the biggest difference between FDE and ordinary software development.

Ordinary development can wait for a product manager to fully break down requirements before writing code task by task. At the start of an enterprise AI project, the client usually hasn't thought things through either. Materials may not be organized, processes may be passed down by word of mouth, departments may conflict, and the problem the boss imagines may not even be the same as the problem employees actually face every day.

This mess is not something the client is supposed to clean up on their own before the project starts. It is itself part of the delivery.

But that doesn't mean one person has to do everything.

One person can handle some simple, well-bounded scenarios. Once a project becomes somewhat more complex, customer acquisition, product, development, testing, deployment, operations, and client communication can't all be piled onto one person — at that point you need to collaborate with partners who have done delivery before and whom you trust.

A "small team" doesn't mean "one person pretending to be a company." It means having few enough core members and a short enough decision chain, while knowing what you lack and whom to bring in to fill the gap.

## 2. Where Do the First Customers Come From?

I've observed that many people around me who want to do OPC or FDE already have delivery capability; what they truly lack is customer resources and sales ability.

But "where do the first customers come from" can't be answered in just one way.

Someone who has already done B2B and holds customer relationships walks a different path from someone who has just started doing enterprise AI with no case studies and no customer resources.

**Path One: You Have B2B Experience, or Want Mid-to-Large Enterprise Clients**

For mid-to-large enterprise projects, the first opportunities usually come from acquaintances, past clients, and sales partners — not from complete strangers or cold traffic.

The reason is very practical: when an enterprise hands its business materials, internal processes, system permissions, and even operating information to an external small team, the first thing that must be resolved is not technical capability but trust.

Our early customers mainly came from a few categories:

1. Clients we've served before who understand our delivery capability;
2. Companies we've known for years but had never formally worked with;
3. Clients referred by sales partners or other OPCs.

In 2023, we built a knowledge base for a company. The client was an acquaintance — we hadn't worked together before, but we knew each other. Their company was growing at the time and was willing to budget for experimentation, which is why the project actually got off the ground.

These conditions are all indispensable:

- The client trusts you;
- The client genuinely has a problem;
- The company's financial situation allows it to experiment;
- The decision-maker is willing to pay for this experiment.

When expanding into new mid-to-large enterprise clients, I prefer to first find sales partners who already hold customer resources, build long-term cooperation with them, hand them my list of deliverable services, and let them introduce suitable clients.

Because in traditional B2B projects, sales is not just forwarding you a contact.

He knows who calls the shots in that company, what the boss actually cares about, what the relationships between departments are, and roughly where the budget comes from. For slightly larger cross-departmental projects, a purely technical team will struggle with the interpersonal and interest-related issues — you must rely on mature sales resources.

**Path Two: You're a New OPC With No Enterprise Clients, No Case Studies, and No Sales Resources**

If you've never done enterprise delivery and have no acquaintance clients, you can't treat "relying on past clients and sales partners" as your starting point.

A more realistic approach at this point is to first enter the places where real demand actually occurs.

**The first is OPC communities and startup service communities.** This year, OPC communities in many first-tier cities have been very active; some communities offer projects to small teams that have delivery capability but no business sources yet. The price may not be high and the projects may not be perfect, but it gives you your first contact with real clients, real requirements, communication, and acceptance — instead of always making demos at home.

**The second is offline events organized by others.** You can attend events on topics like OPC, AI applications, enterprise services, and the digitalization of traditional industries, or join small gatherings of local entrepreneurs, business owners, and industry practitioners.

The purpose of attending events isn't to immediately pitch "I can build Agents," but to talk through, with people from different fields:

- How they currently work;
- Which step is the most repetitive, slowest, and most error-prone;
- What tools they've tried before;
- Why it wasn't solved;
- Who is responsible for this problem.

Many companies won't publicly post a procurement need like "I need FDE." Real leads usually emerge slowly through concrete conversations.

**The third is to join other people's projects first.** If you're not yet able to independently acquire and take on a complete enterprise client, you can partner with more experienced OPCs or delivery teams and take charge of the part you're good at. First walk through requirement communication, delivery, testing, and acceptance for real, then gradually build up your own case studies and service list.

For a new team, the most important value of the first engagement isn't necessarily maximizing profit, but gaining a complete, reviewable delivery record that you'll later be confident showing as proof of capability.

Social media is an amplifier, not the only starting point.

Whichever path you take, content and personal brand have value. They help strangers understand what you've done and how you think about problems, and they let people you've met offline go back online and keep watching you.

But "getting exposure" is not the same as "completing commercial conversion." Social media is only one part of the acquisition chain; it can't replace the screening, diagnosis, delivery, and trust-building that come afterward.

So when it comes to acquisition, you can't just look at follower count. A real lead must answer at least four things:

- Who they are — an individual or a company;
- What problem is currently happening;
- Whether there's a clear time frame for action;
- Whether they're willing to pay for the assessment and the next step.

Someone who only asks vaguely "how do you build an enterprise Agent" but is unwilling to provide background, materials, and goals should not immediately receive a free, complete plan.

## 3. Choosing the Client Is Often More Important Than Choosing the Technology

In enterprise AI services, if you choose the wrong client, the stronger your technology, the greater your potential loss.

We prioritize looking at whether a company is still growing.

This isn't an absolute rule, but it's very pragmatic.

A growing company usually means it still has customers and budget, and is more willing to improve efficiency through tools. When employees know the business is growing, their resistance to external teams is much lower. When we go in, we don't stand above them declaring we'll use AI to eliminate anyone; instead we crouch down and ask:

- Which part of your current work is the most annoying?
- Where is there the most repetition?
- Where is it easiest to make mistakes?

When we map out processes from the position of supporting employees, they're usually willing to cooperate.

Conversely, if a company's performance keeps declining, it might lay people off even without AI; with AI, AI just becomes a nicer-sounding excuse. The vendor also has to face budget cuts, project termination, and payment risks.

In the past, when doing enterprise projects, we've encountered situations where a client's business deteriorated and it was still hard to collect the final payment after completion. At that stage, contracts and collection procedures can't necessarily conjure money out of a company that has already lost its ability to pay.

So now, when choosing clients, we prioritize:

- Whether the company itself is growing;
- Whether the decision-maker really wants to do it;
- Whether there's a real business owner;
- Whether you can access the actual processes and materials;
- Whether there's someone who can confirm results;
- Whether the client and sales partner are reliable;
- Whether the first phase can be validated within a few weeks.

There are also some projects we simply refuse.

For example, the client's legacy ERP provides no API but they demand the new system read and write to it automatically; no one inside the company is responsible for materials and acceptance; or the boss just says "AI-ify the whole company" but no one can specify who the first batch of users is.

A small team has limited resources and can't prove its capability by accepting every requirement.

**Knowing what not to do is itself part of delivery capability.**

## 4. The Boss Can State the Budget Clearly, but Not the Delivery Boundaries

Once you've truly entered a sales opportunity, don't listen to the boss talk for an hour in a meeting room and then go back and write the contract.

Our approach: for slightly complex projects, go to the client's site and talk for about a week.

Talking with the boss usually clarifies two things: **how much budget he's willing to put up, and whom he wants to choose to do it.**

The delivery boundaries that actually go into the contract can only be determined after you've gone into the office, factory, or R&D site and talked one by one with the team designated by the boss and the people who actually do the work — to figure out what can be done and what can't.

When interviewing, don't just ask "what features do you want."

Reconstruct the real process:

- Who receives what input at what time;
- Which system they open;
- What information they base their judgment on;
- Whom they turn to when there are exceptions;
- Where they finally write the result;
- Which steps are written into policy, and which exist only in group chats, phone calls, and personal spreadsheets;
- Which rules everyone knows but has never been formally documented.

In our 2023 knowledge-base project, we ran into a very typical problem.

After the system went live for testing, the AI answered a product question incorrectly.

We first checked whether the model was hallucinating, then whether the knowledge base had retrieved incorrectly, then whether the scanned document had been parsed incorrectly. Tracing all the way down, we found every part of the technical pipeline was correct.

What was actually wrong was the product design document that had been printed years ago.

The veteran employees in the company all knew that spot was misprinted, so in their daily work they automatically corrected it in their heads. But this fact had never made it into any online system. The AI faithfully read the wrong material and therefore gave the wrong answer with perfect accuracy.

This case made me realize:

**AI can process wrong knowledge with great accuracy.**

Much of the genuinely valuable information in an enterprise isn't in databases but in people's heads. Document versions, historical exceptions, word-of-mouth rules, and special client-handling methods may only surface after the project actually goes into operation.

Therefore, the goal of requirement research isn't to compile a feature list, but to confirm:

- Whether the source knowledge can be trusted;
- Whether the process actually runs as documented;
- Which judgments can be handed to AI;
- Which must be left to humans;
- Which single step the first phase will actually change.

The client's aspirations can be big, but the first phase must be small enough.

## 5. Quotation Is Not Development Days Times a Unit Price

Quoting has to be done in stages.

If both sides are still strangers and the lead is unclear, you can first use your own time cost as a filter. For example: suppose you want your annual income to reach one million yuan; you can work backward — twenty working days per month, eight hours per day — to derive a base hourly price.

This number isn't the final project quote; its purpose is to filter.

If the other side can't even accept this magnitude, there's no need to keep investing a lot of time sorting out their requirements.

Once you reach the sales-opportunity stage, quoting can no longer be just about how many days of development.

You also have to consider:

- The client's budget and ability to pay;
- How much this problem is worth to the client;
- How many alternative vendors exist in the industry;
- How complex the data and system integration is;
- Whether on-site presence is required;
- Accuracy, permission, and security requirements;
- How cooperative the client is;
- The delivery timeline and liability for failure;
- The cost of collaborators for sales, design, testing, hardware, etc.

The principle is straightforward: first establish your own bottom line — figure out how many days the work will take and the minimum you must charge; then know yourself and your counterpart — understand the client's psychological expectations and the competitive landscape.

But this shouldn't be simplistically understood as "just raise the price when you see the client has money."

Different clients may seem to want the same knowledge base, but the actual scope can be completely different. One company has only a few dozen well-organized documents; another has more than a decade of paper records, multiple permission tiers, and legacy system integration. The delivery risk is not the same thing at all.

The price ultimately has to correspond to scope, value, and risk.

There's another principle that must be stated clearly upfront:

**More requirements means more money. It's not "more scope, same price."**

If you only discover the scope has expanded after the contract is signed, it's usually very hard to add budget. So before quoting, the most important thing isn't negotiating the price higher, but getting the boundaries as clear as possible.

## 6. The SOW Is a Small Team's Most Important Safeguard

Enterprise AI projects easily run into a situation where, halfway through, you discover the real blocker isn't technology but that the client hasn't provided the necessary conditions.

For example:

- The materials haven't been organized;
- API permissions haven't been opened;
- No one confirms which document is valid;
- The department lead doesn't participate in testing;
- The legacy ERP has no API at all;
- The client temporarily added several processes that were never discussed.

Clients easily assume that since you promised to deliver the result, all the blockers should be solved by you for free.

So in the early stage of a project you must have an SOW — a Statement of Work. For large projects it goes into the formal contract; for small projects, at minimum confirm it in email, documents, or chat records.

A usable SOW should at minimum specify:

1. What exactly is being delivered this time;
2. Which items are explicitly out of scope;
3. What materials, accounts, APIs, environments, and personnel the client must provide;
4. Which prerequisites, if unmet, will halt the project;
5. The timeline milestones for each phase;
6. How both sides will test;
7. What result counts as acceptance;
8. How to handle changes when requirements grow;
9. Which risks are borne by whom;
10. Where training, after-sales, and maintenance end.

This can be summed up in one plain sentence:

I will deliver these things, I depend on those things, and you have to prepare them for me. If you can't prepare them, I genuinely can't deliver. If you want me to also deliver items outside the contract scope, then we count the person-days separately and charge separately.

The SOW isn't meant to confront the client. It's meant to make both sides share the same understanding of the result before the project begins.

## 7. When Doing Enterprise AI, Don't Force AI Just to Prove the Tech Is Advanced

A small team must accumulate a technology stack it is familiar with.

If the client requires data not to leave the company, discuss private deployment; if they allow cloud models, compare cloud options. When the client has no clear technical preference, we prioritize tools we're familiar with and can fix when something goes wrong.

We've delivered with knowledge-base tools we're familiar with and have handled real problems in them, so when something breaks we know where to start. The same goes for Agents, workflows, and inference frameworks — if you chase a new tool for every single engagement, the project risk becomes very high.

But being familiar with technology doesn't mean every problem must be solved with technology.

Early on, when building knowledge bases, the client's PDFs contained product images, 3D drawings, dimension annotations, and irregular tables. At the time, multimodal recognition was limited and automatic parsing was expensive, so we ended up using manual data entry.

It didn't sound "AI" enough, but it delivered the project as required.

Likewise, if the client's legacy ERP offers no API, our choice isn't to showcase an even more complex workaround, but to simply not touch that part of the business.

Model selection isn't about looking at a parameter table either. First prepare a fixed set of questions and test with real data; if this model can't reach the accuracy, switch to another. If it still can't after switching, tell the client plainly that it can't be done right now.

Enterprises buy reliable results, not an FDE proving that every link can be automated.

## 8. AI Coding Can Accelerate Engineering, but It Can't Eliminate It

I've seen a company leader personally run a very aggressive experiment.

After getting into AI tools and setting up his environment, this leader started writing, by himself, a system that originally would have required long-term collaboration from an R&D team.

At first he was very excited, and progress looked fast.

As modules multiplied, problems began to appear: fixing one bug could introduce a new one; no one could explain why the system was designed this way; and within the project, no one had a complete understanding of every module.

In the end, the work slowly drifted back to the original R&D process: sort out requirements, split into modules, write test cases, and have the R&D team continue maintaining it.

This isn't to say AI coding has no value.

Quite the opposite — it's very well suited to helping business people turn the process in their heads into a demo.

I've worked with an e-commerce team where an operations person first "sprayed" their own workflow into Codex or Claude Code, and the AI produced a demonstrable version. Once that demo reached the developer, the developer immediately understood what they wanted and how the operations flow worked, sharply reducing communication cost.

AI can reduce trial-and-error and expression costs, and may even let a company hire one fewer programmer than originally planned.

But a large system running over the long term still needs engineering structure, module understanding, testing, and maintenance responsibility.

**AI coding can accelerate engineering — it cannot eliminate it.**

## 9. The Test Set Must Be Designed Before Delivery

An AI project can't be accepted with "I tried it a few times and it felt pretty good."

Because the client ultimately does acceptance, we build a test set.

The basic approach is similar to traditional software testing: for each requirement point, design positive tests, negative tests, and boundary tests. The vendor's self-test set is shown to the client for confirmation, to check whether any real-business situation was missed.

After our own tests pass, we hand it to the client. The client usually also keeps a private acceptance set, telling us only whether it ultimately passed or failed and by how much.

In knowledge-base scenarios, roughly 85% of the questions can be designed as ones with definitive answers.

For example: which certifications a product passed, or what the current of a certain interface is. These all have standard answers and can be clearly judged right or wrong.

The remaining questions without standard answers need to be evaluated by business personnel.

The same goes for image generation. Feed-ad images have short life cycles and can tolerate more errors; product-detail-page images stay public for a long time, so details like fingers, model blending, and product structure demand higher standards and must be judged by humans.

An enterprise AI test set should cover at least:

- Whether normal input yields the correct result;
- Whether erroneous input gets rejected;
- Whether it fabricates when materials are insufficient;
- How it handles conflicting document versions;
- Whether unauthorized users can see content they shouldn't;
- Whether it writes repeatedly when a tool call fails;
- Whether it escalates to a human when the model can't meet the standard;
- Whether it's re-tested after switching the model, prompt, or knowledge version.

The technical team is responsible for building the system; the business experts are responsible for defining what "actually answering correctly" means.

## 10. When Requirements Change, at Least One of Budget, Timeline, or Scope Must Move

Real projects always change.

Issues not caught in the POC may surface during formal development; a link you underestimated may need more time; and a certain requirement may even turn out to be impossible right now.

Large projects should go through a formal change-request process. Small projects can directly communicate with the client lead, but you can't pretend the change doesn't exist.

A more realistic way to handle it:

If the client is unwilling to add money, at least extend the time. You can't keep the budget the same, the timeline unchanged, and the scope still expanding — because that genuinely can't be delivered.

Note that most clients won't agree to add budget after the contract is signed. So the smaller the team, the more you should nail down the POC, dependencies, and boundaries up front.

Changes can be classified into three types:

1. The client added requirements not in the original contract: increase budget or trim the original scope;
2. The vendor underestimated the difficulty of the original requirement: explain why, and renegotiate the timeline and approach;
3. Prerequisites didn't hold: the client supplies the missing conditions, or the corresponding scope is paused.

Don't use silence and overtime to cover up scope changes.

If the project drags to the end, both sides' memories of "what was originally agreed" will often be completely different.

## 11. Preparation for Acceptance, Evidence, and Payment Starts on Day One

Many people only start thinking about acceptance and payment after the project is done — that's already too late.

From the start of the project, you should keep contracts, stamped documents, WeChat conversations, emails, phase confirmations, test records, and delivery traces.

These records aren't for suing the client at any moment, but so that in a dispute you can answer:

- What both sides originally confirmed;
- Whether the client provided the prerequisites;
- What content has been delivered;
- Which changes were confirmed;
- Whether the acceptance criteria have been met.

For the small-team projects we do now, because clients mainly come from acquaintances, past clients, or sales-partner referrals, we haven't yet encountered cases of refusing acceptance after completion or not paying after acceptance.

But our past experience with large clients already shows: trust matters, but evidence must not be missing.

The real first step to lowering bad-debt risk isn't studying how to collect debt — it's choosing, in the early stage of the project, clients who are financially healthy, still growing, and reliable in the relationship.

## 12. After Completing One Engagement, the Next Can't Start From a Blank Slate

If a small team starts every engagement from blank documents, blank code, and blank judgment, it will quickly be dragged to death by delivery.

After each project ends, you should at least accumulate:

- Client screening questions;
- An on-site interview checklist;
- A process-reconstruction template;
- Quotation cost items;
- An SOW template;
- Common prerequisites and dependencies;
- Positive, negative, and boundary test structures;
- A go-live and handover checklist;
- Requirement change records;
- Real case studies that can be published anonymously.

Discovering a wrong paper document in a knowledge-base project may later turn into a data-governance requirement; an operations person using Codex to make a demo can become a new way for business people to express requirements; a failed ERP integration can become a question you must ask during the next opportunity's initial screening.

Problems encountered during delivery, once their boundaries are clear, may become a second project.

The methods formed within a project also become the foundation for the next delivery.

A complete business loop is therefore not the simple "post content — someone DMs — close the deal," but rather:

**Real project → Form judgment → Accumulate methods and templates → Share publicly → Gain new leads → Screening and diagnosis → New project delivery → Produce new case studies.**

As of now, we're still validating this newly added path from content to paid consulting, and can't describe it as a reliably working result.

But offline clients, sales partners, and real delivery provide first-hand material; the role of content is to turn experience that used to exist only within acquaintance circles into trust evidence that stranger clients can also understand.

## Finally: What a Small Team Truly Needs Is Not a Universal Agent

Now, answering again "how does a small team take enterprise AI services from 0 to 1" — the answer is fairly clear.

You need to find clients who have real problems and the ability to pay; go on-site and ask the people who actually do the work to clarify the process; narrow the boss's wish down to a result the first phase can accept; in the SOW, write clearly the scope, the client's responsibilities, and how changes are handled; choose technology you can truly maintain; prove delivery with a test set rather than a demo effect; and finally leave evidence, complete acceptance, and accumulate the judgment from this engagement.

A small team doesn't need to pretend to be all-capable.

When you need professional sales, find a sales partner; when you need other technical roles, find OPCs who have done delivery and whom you trust; when a legacy system has no API, don't force it; when a model can't reach the required accuracy, switch models or honestly say it can't be done now; when automatic parsing is too costly, use manual labor to deliver the project.

In the end, what an enterprise wants isn't a solution that sounds advanced.

What an enterprise wants is: does this thing work, who catches it when it's wrong, where does "done" end, and after the delivery team leaves, can they keep running it themselves.

Technology determines whether you can build the thing at all.

Client judgment, scope management, testing and acceptance, and business relationships determine whether you can collect the money and earn the next round of trust.

This is the real 0-to-1 of a small team doing enterprise AI services.

## Appendix: Complete SOP Framework for Enterprise AI Services

**1. Lead Screening**

- Who is the client, what industry are they in, and what is their current role?
- What specific problem do they most want to solve right now?
- How is it currently handled, and how much time, cost, or lost opportunity does it consume each week?
- What tools, vendors, or internal solutions have they already tried?
- Who is responsible for driving it, and who is responsible for acceptance?
- By when do they hope to see what result?
- Is there a clear budget?

**2. Client Assessment**

- Is the company still growing?
- Is the problem causing real costs right now?
- Can you access the real users, processes, and materials?
- Is there an internal owner?
- Can the first phase be validated within a few weeks?
- Are the decision-making, payment, and collaboration relationships reliable?

**3. On-Site Research**

- Reconstruct the current real process, not just what's in the policy;
- Interview the boss, the owner, and the actual users;
- Verify document versions, data locations, and system permissions;
- Uncover word-of-mouth rules, personal spreadsheets, and historical exceptions;
- Mark facts, judgments, assumptions, and items to be confirmed;
- Confirm what can be done and what cannot.

**4. Solution & Quotation**

- Shrink the big wish into one minimal business result;
- Estimate the cost of research, development, testing, deployment, training, and collaboration;
- Confirm accuracy, permission, concurrency, and operations requirements;
- Write out the minimum cost, client value, and project risk clearly;
- When the budget clearly doesn't match, don't keep digging deeper for free.

**5. SOW**

- Goals and users;
- Delivery scope;
- Items explicitly out of scope;
- Client prerequisites and dependencies;
- Technical assumptions and verification items;
- Phase milestones;
- Testing and acceptance criteria;
- Requirement change process;
- Payment milestones;
- After-sales and support boundaries.

**6. Development & Delivery**

- Prioritize technology the team is familiar with and can maintain;
- Use the POC to validate the biggest risk first;
- Don't force integration with legacy systems that have no API;
- When automation costs more than manual work, evaluate a manual approach;
- Keep confirmation records and delivery evidence at every stage;
- Communicate scope changes immediately; don't hide them with overtime.

**7. Testing & Acceptance**

- Design positive, negative, and boundary cases for each requirement point;
- Give the self-test set to the client to confirm nothing is missed;
- The client keeps an independent acceptance set;
- Deterministic questions are judged automatically; open questions are evaluated by people;
- Test for insufficient materials, permissions, refusal to answer, and human takeover;
- Re-test after switching the model, prompt, or knowledge version.

**8. Handover & Retrospective**

- Complete the delivery, training, account, and material handover;
- Let the client know when to trust AI and when to escalate to a human;
- Keep contracts, communication, testing, and acceptance records;
- Review scope deviations, technical risks, and client cooperation;
- Accumulate templates, test structures, and reusable components;
- With the client's permission, turn the project into an anonymized case study.

Going forward, I'll continue sharing more real cases from enterprise AI implementation services: how clients initially raised requirements, what problems surfaced after the project went on-site, which solutions were ultimately abandoned, and the pitfalls that are easy to hit in quotation, delivery, testing, and acceptance.

This content won't just talk about AI concepts or show a runnable demo; it will try to explain, as clearly as possible, how enterprise AI goes from an idea to real business.

**If you're also following enterprise AI, FDE, or small-team delivery, feel free to follow me. My page will keep updating with real enterprise AI implementation cases, practical judgment, and delivery methods.**