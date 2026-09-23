---
title: "Chapter 2 · Solving the Right Problem"
original_title: "第 2 章 解决正确的问题"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "https://fde4.ai/book/02-%E7%AC%AC2%E7%AB%A0-%E8%A7%A3%E5%86%B3%E6%AD%A3%E7%A1%AE%E7%9A%84%E9%97%AE%E9%A2%98"
source_file: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer/blob/main/02-%E7%AC%AC2%E7%AB%A0-%E8%A7%A3%E5%86%B3%E6%AD%A3%E7%A1%AE%E7%9A%84%E9%97%AE%E9%A2%98.md"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [第 2 章 解决正确的问题](https://fde4.ai/book/02-%E7%AC%AC2%E7%AB%A0-%E8%A7%A3%E5%86%B3%E6%AD%A3%E7%A1%AE%E7%9A%84%E9%97%AE%E9%A2%98)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

# Chapter 2 · Solving the Right Problem

> "On the wrong problem, all execution is wasted."

## 2.1 An Autopsy Report on the Proof-of-Concept Graveyard

In Silicon Valley there is a phrase: "PoC purgatory" (PoC — Proof of Concept). Projects go in but don't come out. They're not dead enough to be declared failures, yet not alive enough to justify bigger investment. So they languish year after year in quarterly reports as "ongoing" — like a ward full of patients hooked up to machines.

Researchers at MIT's NANDA Lab performed a systematic autopsy of this graveyard in their report *The GenAI Divide*. They distilled the five biggest obstacles on the road to scaling enterprise AI projects, ranked by frequency of occurrence:

1. Employees unwilling to use the new tools — even though these same people use ChatGPT freely in their personal lives every day
2. Concerns about the quality of model outputs
3. Poor user experience
4. Lack of executive support
5. Difficulties with change management

What is *absent* from this list is more telling than what is in it: the model isn't smart enough, compute isn't cheap enough, the technology isn't advanced enough — none of these made the cut. Almost everything that kills these projects happens at the level of "problem definition" and "organizational reality," not at the level of technology.

A company spent $50,000 on a professional contract-analysis tool, with an impressive feature list. But one of its senior lawyers simply wouldn't use it — she kept drafting contracts with free ChatGPT. The reason was plain: the purchased tool produced summaries that were too rigid, impossible to customize to her habits. The procurement department's report said "deployed," yet the real day-to-day was an official system spinning its wheels while employees went around it. (Source: Appendix C)

This detail reveals the true root cause of the number-one obstacle: it's not that employees are stuck in their ways — it's that consumer products have spoiled their appetites. Someone who uses the good stuff at home every day can't tolerate the "artificial idiocy" at the office.

Here is a more cutting comparison: **projects done with external professional vendors succeed at roughly three times the rate of internally built ones.** Why do outside teams win more often? They can't afford to lose — the people who get paid on results bear the cost of defining the wrong problem themselves.

An internal project at a Japanese company is a textbook counterexample: they pulled three or four of their strongest engineers into a strike team, the demos were dazzling, leadership nodded approval — yet from day one, no one could answer "by what standard is this system's goodness measured." Half a year later the project quietly vanished from the reporting materials. No one announced its failure; it simply died of natural causes. (Source: Appendix C)

This is the first principle: in enterprises, wrong problems are far more numerous than one imagines. So before writing the first line of code, make sure you're solving the right problem.

## 2.2 PSF: Finding Problem–Solution Fit

In internet startup methodology there is a core concept called PMF (Product-Market Fit): when the product is right, the market pulls growth on its own. In the world of the FDE, the corresponding unit is not "product and market" but "problem and solution" — what I call PSF (Problem-Solution Fit).

The distinction is subtle yet critical. PMF asks "is there a market that wants my product," from the supplier's perspective. PSF asks "is this specific problem of the customer's worth solving, and can it be solved by our capabilities," from the demand side's perspective. Inside a single enterprise client there may be hundreds of "where could AI do something" opportunities, but the ones truly worth doing must pass three gates at once.

**Gate one, the pain-point test:** Is this problem the specific pain of a specific person? Note the two "specifics." "Improve customer-service efficiency" is not a pain point, it's a direction. "Every Monday morning the customer-service supervisor spends three hours manually consolidating last week's escalated tickets from four systems, when her real job should be analyzing why they escalated" — *that* is a pain point.

McGrew has offered a sharper standard: go solve one of the CEO's top five concerns. The reasoning is pragmatic — only a problem of that magnitude can help you bulldoze through internal corporate bureaucracy. The standard of Sierra's head of agent engineering, Moeller, is the same principle in different words: only take on two kinds of problems — ones that are genuinely hard, and ones with genuine business impact. Hard without impact is just showing off; impact without difficulty is beneath you.

**Gate two, the economic test:** How much is solving this problem worth? Many pain points are real but not worth much; projects that can't even tally that account won't survive the next budget season.

You can rough it out: how many person-hours does this problem eat each week? What does that translate to in labor cost? What's the penalty for one mistake? What could the freed-up headcount go do instead?

Palantir's Bootcamp goes so far as to put this gate first — before the client even starts, you must lock down the "core battlefield" and give a quantified target: "reduce scheduling conflicts by 30%," "cut inventory-turnover days by 15%." A widely cited finding in the NANDA report neatly shows how easily this gate gets skipped: more than half of enterprise AI budgets go to the front-office sales and marketing functions, yet the returns concentrate in the unglamorous back office — contract review, procurement, risk control. Everyone is solving "problems that demo well," not "problems that pay."

**Gate three, the feasibility test:** Given our current capabilities and this client's data reality, how much can we actually achieve? This gate is the one most easily drowned out by enthusiasm. There are two questions that must be answered on-site. Where is the data, and in what state? The answer is often worse than imagined — scattered across seven systems, three versions that don't reconcile, and the authoritative copy living in some veteran employee's personal spreadsheet.

Colin Jarvis, who leads OpenAI's FDE organization, once summed up the field experience in one line: the problem a client describes during topic selection often fails to match the real data and systems on the ground.

The second question that must be answered on-site: what is the accuracy threshold? Between "99% usable" and "90% usable" lies an order of magnitude of engineering effort, yet many business scenarios are actually optimally solved at 90% plus human review — judging this requires not technology but an understanding of business consequences.

"How much can we achieve" is not guessed — it's measured. That's why seasoned teams put "build the test set first" ahead of "go live." Morgan Stanley did exactly this: starting from three concrete scenarios, wealth advisors and engineers scored the model's outputs item by item, with the scores flowing straight back into iteration; thereafter they reran the old test set every day — to catch the model quietly regressing — intercepting quality decline before it ever reached the front-line advisors.

OpenAI's official enterprise deployment guide lists seven lessons, and the first is likewise "start with a test bank." Why run it every day? Because when an AI system errs, it often doesn't throw an error — it just quietly becomes untrustworthy. By the time users notice on their own, the bill for that trust has already come due.

Only after passing all three gates do you touch Problem-Solution Fit. And these three gates must be passed at the customer site — most of those earlier mistakes grew from making judgments in headquarters conference rooms against secondhand information.

Moreover, these three gates are not something you pass once before entry and then forget. This examination has to become a daily discipline. Ramp, a corporate spend-management company, made "always be selecting topics" the very first principle for its own FDEs: don't accept every client request at face value; with each new requirement, first gather context, validate assumptions, and assess the impact on the overall schedule. This discipline was bought with tuition — they once spent weeks building an Android-side feature for a client, only to discover just before delivery that the company internally mandated iPhones only. Weeks of work, voided. The cost of lax topic-selection discipline is counted in weeks.

## 2.3 Refuse the Expensive "Proof-of-Concept Graveyard"

In 2025, QiMeng Tech, a Chinese service provider focused on the real-estate and facilities-management industry, posted on its website a rather blunt message to talk potential clients down off the ledge: if your scenario isn't validated yet, go to a demo event first; if your data fits in a single spreadsheet, a lightweight service is enough; if you just want to understand AI, use the free option. The harshest line: "The FDE is a heavy investment. We'd rather you start later than start at the wrong time." (Source: Appendix C)

That message states a fact contrary to sales intuition: refusing the wrong projects *is* the FDE model's profitability.

Why are wrong projects dangerous? Because the FDE cost structure is front-loaded — your best engineers, your most expensive travel, your longest on-site commitment, all incurred before any payment arrives. Once you're stuck in the mire, it's not a matter of losing one deal; it's your entire elite team getting dragged down, an avalanche of opportunity cost.

Former Palantir engineer Barry recalls: "We burned millions of dollars on customer pilots, and many of those projects had a profit margin that was literally negative infinity, because we did them for free." The perspective he added right after is the real point: Palantir could afford to burn, because it treated pilots as an R&D portfolio to invest in — like venture capital, where most bets going to zero is fine, so long as the winners win back everything. But if you have neither its capital depth nor a mechanism to "convert failed pilots into product assets," then every wrong pilot is pure blood loss. (Source: Appendix C)

So the FDE team needs a "mechanism for refusal," not just the courage to refuse. Three actionable lines of defense.

- **Defense one: a PoC must have a "graduation standard."** At launch, every validation project writes down: after how many weeks, by what metric, reaching what number, the project "graduates" into paid deployment; if it doesn't, both sides part ways gracefully. Palantir's Bootcamp takes this logic to its extreme — it is not a proof of concept, it is an industrialized *replacement* for one: one to five days, the client brings real data, a deployable prototype is built on-site, and executives decide on the spot. Either see something real within days, or don't start at all. The reason traditional PoCs rot into graveyards is precisely that they are "infinite in duration, metric-less, and referee-less."

- **Defense two:** Watch for three categories of high-risk signals. Drawing on practitioners' experience, if two or more of these three signals appear, be on high alert. The first is "no man's land" — the project has no clear business owner inside the company, only the IT department acting as counterpart. IT cares about compliance and stability, and compliance and stability were never reasons to build something new. The second is "look but don't touch" — the client demands you prove your capability first but refuses to provide real data. Without validation against real data, any success you produce is just an illusion. The third is "cosmic-scale demand" — a client who, in the first meeting, wants to "cover all scenarios across the whole company" is usually not ready to do any single scenario.

- **Defense three:** Leave a graceful off-ramp for "refusal." Refusing is not the same as breaking off. The best move is to translate "we won't do this now" into "when we *will* do it": "This scenario's data foundation is still missing three things; we suggest doing another scenario first, which conveniently fills in those three things, and we'll come back next quarter." Package the refusal as a roadmap — protecting your capacity while preserving the relationship. Chapter 3's "lighthouse client screening" continues along this thread.

These three lines of defense are a sieve written for the vendor. Flip it around and it becomes the buyer's self-checklist — far more people buy FDE services than sell them.

If your project lights up the "no man's land" signal in the vendor's eyes — pushed down by a group-level mandate, led by IT, with no business unit signing on — seasoned vendors will be wary, and you should be even warier than they are: if even the supplier can see this project has no true owner. If your procurement process naturally manufactures "look but don't touch" — security review demands the other side prove capability first, yet not a single piece of real data is offered — then the validation you buy can only be an illusion.

If the requirement you write into the RFP is cosmic-scale — "AI empowering the entire group" — you scare off the most knowledgeable suppliers and attract the biggest talkers.

## 2.4 Pain Points: The First Driving Force Behind Deployment

Where do correct problems come from? The FDE field experience says: from pain. And pain doesn't show up in conference rooms; it only appears at the work site.

Palantir wrote this method out in blood twenty years ago. Recall the Iraq battlefield story from section 1.2: soldiers needed a roadside-bomb early-warning tool — a need no interview could ever surface, because the soldiers didn't know they "could ask software for this"; they thought it was just part of patrol life. Such pain points users can't articulate themselves; they require an engineer sitting beside them, seeing it with their own eyes. The embedded engineer went on patrols with the unit and watched firsthand the hesitation and fear of the convoy before suspicious stretches of road — and that is how the crude mapping tool that changed the battlefield came to be.

This method has a name in anthropology: "participant observation." In the Toyota Production System it's called *genchi genbutsu* — go to the site, see the real thing, get the real facts. The FDE turned it into an operational field method, which I call the "shadowing work method."

Follow a real user through a real day. Not interviewing them, but sitting beside them watching them work — watching which systems they open, what they copy-paste between spreadsheets, where they frown, which "official processes" they circumvent.

OpenAI's FDE team did exactly this on the John Deere project: they flew to Iowa, went into the fields with agronomists and farmers, watched how they made spraying decisions, which information actually entered the decision, and how the hard deadline of the farming season governed everything. The old workflow they wanted to dismantle originally took the form of agronomists calling farmers household by household, giving equipment advice by word of mouth — a workflow that appears in no document, visible only by going into the field. The repeatedly quoted practitioner's maxim describes precisely what this method uncovers: "The hard part is finding the workflow nobody wrote down, the data source people actually trust, and the person who knows why the process is the way it is." Each of those three things can only be found on-site.

Going into the field also confirmed one thing conference rooms can never make clear: what farmers want has never been "AI" — it's less spraying and more yield. The product that later emerged simply charges by the number of acres where the technology is actually enabled, so every dollar the client pays is aligned with the value they receive. Ported to China, the corresponding variant charges by the number of enabled production lines, stores, or outlets — within the project-based acceptance habits of procurement, it is the most procurement-department-acceptable first step toward "pay for results."

Observe the "workarounds," not the "process." The official flowchart tells you how the organization *should* run; the workarounds tell you how it *actually* runs.

Why does an employee insist on exporting data into a spreadsheet to recalculate? Why is it generally agreed within a department that "for this table you go to Xiao Wang"? Why, with a data system clearly in place, does someone always manually reconcile the numbers before the decision meeting? Behind every workaround lies an unmet pain point, a systems failure — and an FDE opportunity.

Beware the "translated pain point." The need you hear, if relayed through the client's IT department, procurement, or a consultant, distorts with every hand it passes through — IT translates the business pain into a technical requirement ("needs a data platform"), procurement translates it into a compliance item ("must satisfy such-and-such standard").

The disaster of traditional software projects often starts right here: the vendor is accountable to the translated document, not to the pain itself. So your first imperative is to bypass the translation and reach the nerve ending of the pain directly. This is also the core duty of "Echo" in Palantir's two-person model — to understand the client's "mission," not their "requirements": what's written in the requirements document is the pain point's relayed version; the client's mission is the pain point's true source.

Having found the real pain point, the next step is to validate at minimal cost: can our solution actually stop this pain?

## 2.5 Validate Value with a "Minimum Viable Deployment"

In internet startup methodology there is a famous concept called MVP (Minimum Viable Product): validate market demand with the smallest possible product. The FDE counterpart, which I call **MVD (Minimum Viable Deployment)**, is: with the smallest engineering investment, in the client's real environment, against a real pain point, validate once that value genuinely occurs.

One word of difference, and the difference is in the referee. The MVP validates "should we build this product," with the market as referee; the MVD validates "can this solution produce value on this specific client," with this specific client's specific business as referee.

A solution validated successfully at ten clients can still fail at the eleventh — different data foundations, different organizational inertia, different shapes of pain. This is the cruelty of enterprise delivery: value cannot be inherited from the previous ten clients; it can only be re-validated on this one.

The MVD has three articles of war.

- **Article one: real data, no exceptions.** Validating with the client's "desensitized (sensitive information removed) sample data" or with self-constructed demo data is the first brick of the proof-of-concept graveyard. Real data hides every devil: field meanings that contradict the documentation, 30% empty values, encoding rules from three years ago, and most deadly of all — data that itself records the wrong process. There is an even more insidious devil: data that simultaneously holds two mutually contradictory, each "correct" answers. Salesforce used its own customer-service agent as its first customer for a year, and the biggest pitfall it fell into was exactly this — when the agent hit two conflicting answers it would try to reconcile them, even fabricate, and a single outdated, unlinked old page was enough to poison the response. This forced them to go back and consolidate the company's six hundred-plus data flows into a single authoritative data source, with only one authoritative answer per question.

  - **The only hard rule for execution: the client must bring their own real business data.** Palantir's Bootcamp writes this into its rules; the John Deere project put "reviewing hundreds of real operational cases" ahead of modeling. OpenAI internally drew the line between two roles along exactly this: a solutions architect may use anonymized sample data for demos and validation, but the FDE must write production code on the client's infrastructure, with the client's real data. A solution that holds up on fake data will meet fields that exist in no document on launch day — by which point the real price has already been paid.

- **Article two: shrink the scope, not the value.** The common error is to understand the MVD as a "castrated big solution" — cut 70% of the features and end up a mutt. The correct approach cuts neither the solution's depth nor its coverage breadth in a way that flattens it: don't pursue "smart customer service covering the whole company," but rather "cover only the returns-and-exchanges ticket category, yet end-to-end and with zero human intervention"; don't pursue "group-wide supply-chain optimization," but rather "do only this one production line's scheduling conflicts, yet genuinely save 20 person-hours every week." The cut is small enough that value density is high enough — high enough that the business unit sees it with the naked eye and spreads the word on its own. Legal-AI company Harvey's expansion path is the textbook of this playbook: not a firm-wide rollout, but first penetrate one global practice group, turn the first partners into believers, then expand horizontally after six months of real combat.

- **Article three: fix the deadline to force trade-offs.** The MVD validation cycle should be counted in *weeks*, not *months*. Palantir's Bootcamp is one to five days; Sierra's publicly reported fastest go-live was four weeks; Decagon's typical deployment is four to eight weeks. The point of the deadline is not speed but forcing both sides into honest trade-offs: anything that can't demonstrate value within those few weeks is not yet core value. A six-month "minimum validation" will almost certainly grow back into a want-everything big project — another groundbreaking on the proof-of-concept graveyard.

How much is this speed worth in the client's eyes? Scott Arnold, Chief Digital and Innovation Officer at Tampa General Hospital in the U.S., put it bluntly at an industry conference: "We can solve problems in hours and days, not months and years." When blood supplier OneBlood suffered a cyberattack, this hospital used Palantir's platform to stand up a blood-inventory allocation app within hours, then handed it to the state of Florida for other hospitals to reuse. He also conceded Palantir's price carries a premium, "but the premium is worth it" — a weekly cadence buys never just speed, but the certainty of having the tool in hand on the night something goes wrong.

### The Bootcamp: Industrializing the MVD

Palantir's AIP Bootcamp, launched in 2023, is the only MVD pipeline that has been validated at scale to date.

First the data: starting from fewer than a hundred pilots in 2022, the number of sessions has doubled year over year; media tracking shows the cumulative completed sessions long ago passed a thousand, with nearly 6 per day at the 2025 peak; the traditional enterprise-software sales cycle (nine to twelve months) was compressed to a few weeks; U.S. commercial revenue grew 137% year-over-year in Q4 2025, a growth the company publicly attributed almost entirely to this. (Source: Appendix C)

Now the process — it breaks the MVD into five standardized moves. Day 0, prep: both sides lock an extremely focused core battlefield — "optimize a certain production line's scheduling," "reduce inventory-turnover days" — refusing all grand narratives. Day 1, connect: link up the client's existing systems, extract the isolated data, and build a preliminary ontology model.

Days 2–3, build: the FDE and the client's technical staff write code and configure rules back-to-back, wire the LLM into the business flow, and produce an automated workflow that executes real actions. Days 4–5, demo and decision: what's produced is not a report but a living software interface that business executives click with their own hands, watching the AI give recommendations based on their own company's data — and after the awe, straight into commercial negotiation.

The Bootcamp's brilliance is that it simultaneously solves the MVD's three classic problems: the real-data problem (the client brings it), the deadline problem (capped at five days), and the referee problem (executives use it hands-on). It also handily solves a deeper problem — trust. Let the decision-maker operate a system based on their own data with their own hands, and you can skip most of the feasibility report.

How fast does the contract come after the Bootcamp? Palantir has disclosed a real cadence on earnings calls, fast enough that peers might not believe it: a large healthcare company attended the Bootcamp in December and, five weeks later, signed a five-year agreement with $26 million ACV (Annual Contract Value); a global bank, after a one-month pilot, first signed a $2 million initial contract, then four months later expanded to a three-year, $19 million ACV agreement; pharmacy chain Walgreens first piloted in 10 stores, lifted in-store operational efficiency by 30%, then rolled out to 4,000 stores within eight months, with AI-driven end-to-end workflows automatically handling roughly 384 billion decisions per day that would otherwise have required human action. (Source: Appendix C) This set of numbers answers "what happens after the MVD": projects that pass validation don't grow slowly — they scale by leaps. The client has already seen the value with their own eyes in five days; what remains is just the commercial process.

This "first ten, then four thousand" cadence maps in the Chinese-enterprise context to: first win one business unit, one plant, or one regional company, then use the usage data to knock on the group's door.

Of course, replicating this model has a threshold: behind it must sit a mature platform foundation, or five days won't even get the environment standing. For teams without a platform, the executable simplified version is the "two-week sprint validation": week one, go on-site, connect data, set metrics; week two, build a prototype that solves only a single-point problem but can run real business, and demonstrate to the business side on the weekend with an on-the-spot go/no-go decision. The form can be tailored; the articles of war cannot.

The two-week schedule can be broken down concretely. Week one: Day 1, on-site alignment — with the client, write the "single-point problem" as one sentence and the acceptance metric as one number; Days 2–3, connect data — only the minimal dataset this problem needs, with permissions, desensitization, and export method locked down on the spot; Days 4–5, build the skeleton that can query data and answer.

Week two: Days 6–8, wire the prototype into the real business flow and let one or two real users start using it; Day 9, collect usage traces and a problem list; Day 10, demo — not to IT demonstrating features, but to the business side demonstrating "your problem, now it's like this" — then decide on the spot: scale up, adjust, or part ways.

Without a platform foundation, cobble the toolchain from what's at hand: call a commercial API for the model, or take an open-source model for private deployment; use an open-source vector database for knowledge retrieval; use an open-source framework for workflow orchestration; use the lightest frontend template for the interface. This "frankenstack" is enough to survive one single-point validation. The only thing to watch is turning the sprint into a technology-selection conference — the sole criterion for selection during validation is speed; whether it's reusable or extensible is a question worthy of consideration only after validation passes.

The client side also has three cooperation requirements: 1) a business-side owner who can make decisions must be present; 2) an internal data liaison who understands the data must accompany throughout; 3) access to real data must be in place on Day 1, not "currently going through process." Miss any one of the three and the two-week sprint will most likely slide back into a traditional proof of concept.

## 2.6 Should You Early-On Accommodate the Client's Existing Environment?

The MVD phase hits a disagreement almost every project runs into: our solution should accommodate the client's existing technical environment to what degree — that pile of legacy systems running for twenty years, the department-built small tools, and the strict security-compliance boundaries?

Both sides have a point. The "accommodate" camp says: validating within the client's real constraints is the only real validation. The "rebuild" camp says: deeply adapting to an environment about to be replaced wastes precious validation time on engineering that's doomed to be thrown away.

FDE practice offers a middle path: be data-compatible with the old system, but never architecturally accommodate it — what I call "read old, write new."

At the data layer, deeply compatible with the old environment. Wherever the client's data lives, read from there — even if it's in a legacy mainframe, in a shared-drive spreadsheet, in some ancient system's private interface. The old mainframes of finance and the heterogeneous systems of hundreds of clinics in healthcare have always been the core battlefield of deployment work. There's no shortcut to read-data compatibility, because data is the prerequisite for validating value, and data will never move house to accommodate your architecture.

The good news is that this layer of work is being changed by AI itself: the field mapping, cross-system data shuttling, and data extraction from interfaceless legacy systems that once required manual interpretation can now largely be handed to agents — for example, using a browser agent to simulate manual operations and extract data from legacy systems with no interface. Integration cost is dropping by orders of magnitude. (Source: Appendix C)

At the architecture layer, refuse absolutely to become a parasite on the old environment. The validation-phase system should run within its own controllable boundary, interacting with the old system through interfaces, rather than writing code into the old system. Three reasons: 1) the validation-phase solution itself has better than a 50% chance of being overturned and rewritten, and the deeper the parasitism the greater the waste; 2) writing into the old system means going through the client's change-management process, measured in months, which fundamentally conflicts with the MVD's weekly cadence; 3) maintaining an "evacuable" posture is itself a negotiating chip and an honest stance — the FDE leaves when done, but a parasite can never leave.

At the process layer, yield to people's habits, not the system's habits. This is the one technical teams most easily get backwards. The technical environment can be hard-nosed, but people's habits must be yielded to.

If the business user's core actions happen in spreadsheets and email, the MVD's interface should appear in the spreadsheet plugin and email, not demand that the user log into a brand-new portal. OpenAI's deployment at Spain's BBVA entered through the ChatGPT interface already used by its 120,000 employees, rather than building from scratch — a model of yielding to habit. The cause of death from section 2.1 still holds here: employees' unwillingness to adopt new tools ranks first among the five obstacles. What a new system really has to contend with is the user's old habits.

## 2.7 "Action Over Words" User Research

Finally, pull the camera back to the source of the methodology and talk about the divide between FDE-style user research and traditional research.

The creed of traditional research is "ask": surveys, interviews, focus groups. The FDE creed is "watch" and "do" — action over words. There are three reasons, layered and progressive.

Layer one: the client doesn't know what they want. This is a cognitive law. Faced with an entirely new category — intelligence-analysis software in 2004, AI agents in 2025 — users have no frame of reference to describe their needs.

The reason Palantir's demo loop works is precisely that it doesn't ask "what do you want" but says "here's what I built, tell me where it's wrong." A person's judgment of "where it's wrong" is far stronger than their imagination of "what they want."

Layer two: what the client says and what they do are two different things. The lawyer-group example from section 2.1 is the best proof: a survey asking "are you willing to use professional legal AI," procurement would tell you the willingness is strong — after all, they just spent $50,000 on the tool. But observe the lawyers' actual behavior and they're drafting contracts with ChatGPT.

In the enterprise context, "saying" is polluted by too many factors: political correctness, politeness toward the vendor, protecting one's own role. Only behavior doesn't lie. The shadowing work method observes behavior; the MVD measures behavior — both built on the foundation that "doing is truer than saying."

Layer three: the highest-quality research happens in shared labor. In an interview, the client is a "subject being studied," guarded and performing; working shoulder to shoulder, the client is a colleague, relaxed and real. The two or three days in the Bootcamp when the FDE and the client's technical staff write code back-to-back exchange more information density than any formal research — the client will casually mention in the gaps of debugging, "actually we never trusted this field," "this process looks like it goes through the system, but it's actually still a phone call."

These words would never appear in a formal interview, because they look "unofficial." Yet they are precisely the critical intelligence for deployment success or failure.

The interview itself is being transformed by AI. Ding Xindong, CTO of marketing-tech company Tezign, shared a practice of no longer sending structured questionnaires but using an agent to conduct autonomous interviews across the entire company — differentiated communication based on different scenarios and different people's actual pain points, finally aggregating into a global diagnostic map of "what stage each product line is at, what the pain point is, what approach suits advancing it." AI has driven down the cost of this company-wide deep conversation. (Source: Appendix C)

At this point, the right problem is locked and value is preliminarily validated. The next battlefield is turning the validated single-point value into a real contract and a relationship that truly begins — how to win the client.
