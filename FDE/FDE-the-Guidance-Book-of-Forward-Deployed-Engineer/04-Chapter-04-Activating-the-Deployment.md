---
title: "Chapter 4 · Activating the Deployment"
original_title: "第 4 章 激活部署"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "https://fde4.ai/book/04-%E7%AC%AC4%E7%AB%A0-%E6%BF%80%E6%B4%BB%E9%83%A8%E7%BD%B2"
source_file: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer/blob/main/04-%E7%AC%AC4%E7%AB%A0-%E6%BF%80%E6%B4%BB%E9%83%A8%E7%BD%B2.md"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [第 4 章 激活部署](https://fde4.ai/book/04-%E7%AC%AC4%E7%AB%A0-%E6%BF%80%E6%B4%BB%E9%83%A8%E7%BD%B2)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

# Chapter 4 · Activating the Deployment

> "The model is usually the cleanest part. The hard part is finding the workflow nobody wrote down."
> — A frontline FDE
>
> "No matter how technology evolves, the human nature and power-and-accountability games inside an organization remain a harder problem than the technology itself."
> — Shen Yue, frontline FDE practitioner

## 4.1 Going Live Is Not Activation: The "First-Day Curse" of Enterprise Deployment

In consumer internet, "activation" means a new user completes a key action and experiences the product's "aha moment" (the instant a user first perceives the product's value). In enterprise deployment, activation means **the target user group forms a stable habit of using the system in their daily work** — not applause at the demo, but continued high-frequency use three months later even when no one is pushing them.

In other words: an enterprise software "launch" only completes the administrative process of procurement and acceptance; "activation" happens in the user's behavior. The launch day is worth celebrating, but whether a project ultimately succeeds still depends on whether anyone is still using it three months on.

The MIT NANDA Lab report *The GenAI Divide* contains a telling set of numbers: only about 40% of companies provide official AI tool subscriptions to their employees, yet as many as 90% of employees use personal, consumer-grade AI tools for daily work. This means the real state of many companies is a "two-track system": the official system idles while shadow AI (the phenomenon of employees bypassing the company's official systems and working with personal tools) runs rampant. The system went live, but activation never happened.

Why do enterprise deployments universally die at the activation stage? Because they must clear three gates that are nothing like those of a consumer internet product (a to-C product aimed at individual users). Consumer internet products die from being "not fun," while enterprise deployments die in the users' hands — users find them awkward: one extra step versus the old habit, and no one uses it; users find them untrustworthy: one mistake and trust drops to zero; users find them irrelevant: and then even fewer will touch it.

None of these three gates can be cleared at headquarters; you can only clear them in the client's meeting rooms, workshops, and workstations. That is why activation is the FDE's home turf, and also what most differentiates it from traditional "deliver-and-leave" implementation: traditional implementation treats the acceptance form as the finish line, while the FDE treats a change in the client's behavior as the finish line.

## 4.2 Fast Iteration: The "Hotfix" Culture of the Deployment Phase

Internet products iterate through A/B testing (grouped comparison experiments), inching toward the optimum with small, fast steps. But strict A/B testing is impossible in enterprise deployment scenarios — the sample is too small and the interference too great. Yet its spirit — fast, incremental, evidence-based iteration — becomes a way of working during deployment: respond to every minor complaint from users as if repairing an online incident. I call this the "hotfix."

The iteration rhythm of consumer internet products is measured in "releases" — weekly or biweekly. The FDE's deployment-phase rhythm is measured in "days" or even "hours": a business user says in the morning "this output is missing the supplier code field," and the field is added by the afternoon; a workshop foreman says today "the buttons on this interface are hard to hit with gloves on," and the buttons are doubled in size tomorrow. The significance of this response speed to users far exceeds the feature itself — a problem raised in the morning fixed by the afternoon builds more trust than any promise. In the first month, users form their judgment: "this team is for real," or "another one that delivers and leaves."

This rhythm is not a slogan.

Skai, a brand-performance marketing company, once took on just such an urgent request: thousands of products needed unified categorization across multiple e-commerce platforms. In the past, this would have required pulling in the data science team and scheduling it — "they had the tools, but limited capacity, and getting onto the roadmap would take a long time." This time, a small squad doing custom work for the client called the model directly on the data platform: on day one they wrote the prompt and got it running on the client's product catalog; on day two it was released to production — the same job would have taken at least a month by traditional methods. The vice president who led the effort summed it up afterward: "I don't need to become a prompt engineer, and I don't need to become an LLM expert." The confidence behind the hotfix is that the toolchain has already been laid right next to the problem. (Source: Appendix C)

The hotfix culture has three execution points.

First, feedback must reach the person writing the code directly, with no telephone game in between. Previously, user feedback had to pass through customer success, product managers, and scheduling before finally reaching the engineer — each hand-off lost half the context, and by the time it was scheduled, a week had passed and the user's heart had gone cold. In the FDE model, feedback reaches the person writing the code directly; ideally, the person writing the code sits right next to the user — this is not rhetoric: Prabhu Narsina, the vice president in charge of data and AI at First American, recalling collaboration with the platform's engineers, said verbatim that "they met with us and wrote code and debugged with us almost every day." Palantir is precisely what shortens this loop: the forward deployed engineer can build, test, learn, and feed back on site, without waiting for a formal product requirement to wind through the process.

Second, iteration priority is ranked by "usage-blocking severity," not by "feature importance." The trade-off logic of the deployment phase is the reverse of the product phase. The product phase ranks requirements by strategic value, while the deployment phase asks "what is blocking tomorrow's usage" — a color-scheme issue, if it makes workshop workers feel "this was built for office white-collar workers," is the highest priority; a powerful forecasting feature, if users can't use it right now, is deferred until after activation. During deployment, get the usage rate up first and push feature depth back.

Third, ask one question at the end of every day: which moment of the user's tomorrow did today's change make smoother? Iterating this way is not merely "serving every request" — every fix is a conscious act of activation design: you are dismantling the friction points between the user and the system, one by one. The list of friction points is hidden in the process map from the onboarding due diligence and in everyday observation.

OpenAI's FDE methodology has a corresponding rhythm breakdown: early co-creation (on-site whiteboard alignment), validation (building the evaluation system, i.e. evals), and delivery (multi-day on-site building). Note that the delivery phase still takes "multi-day on-site" as its unit — the ability to fix this fast relies on a person standing guard next to the problem.

## 4.3 Iterating Inside the Client's Environment: Evaluation-Driven Quality Improvement

Speed is solved, but the question of direction remains: where to change, and what counts as "better"? In AI deployment, the vehicle for answering this question is a practice that only went mainstream after 2024: the **evaluation system** — using a batch of standard cases to continuously score the system's output.

Traditional software quality has only two states: functionally right or wrong, tested or not. AI system quality, by contrast, is continuous, probabilistic, and context-dependent — the same answer that dazzles in a demo can be a disaster in a specific business context. Worse still, the definition of "good" belongs to the business side, not the engineering side: an answer the model considers perfect, a domain expert may see at a glance as amateurish. Without this yardstick of evaluation, iterating on an AI deployment is blind running: after half a month of tuning, no one can say whether quality went up or down.

The engineering practice of evaluation systems has, in leading teams, solidified into three steps.

Step one: Grow it from real cases. The evaluation set cannot be invented by engineers; it must come from the client's real business material. The essence of this step is to make the domain expert's tacit judgment explicit as an executable yardstick.

Step two: Let the business side be the judge. The evaluation system is not a toy for engineers to amuse themselves with; the reviewers must include the business side. The best approach is to shape evaluation into a form business experts can participate in: side-by-side output comparisons, simple good/bad annotations, regular review meetings.

This process yields double returns: the evaluation set gets more accurate, and the business side's understanding of the system deepens — as they watch the system answer better and better on their own cases, the accumulation of trust is seen with their own eyes, not reported to them. The Morgan Stanley case written in Chapter 2 did exactly this: the ones scoring the system were not engineers but the financial advisors who use it every day.

Step three: Connect the evaluation system to the production loop. Going live is not the finish line of evaluation. Continuously collect real inputs and outputs in production, sample and evaluate periodically, and alert immediately if the score slips — this turns "quality" from a one-time pre-launch acceptance into continuous care throughout the lifecycle. After all, what users are most sensitive to is not average quality but the stability of quality: the trust collapse caused by a single system error takes ten correct responses to refill.

What does evaluation-driven quality improvement look like on a curve? The public case from Intercom, a customer-service software company, offers a rare complete upward curve: its AI customer-service product could initially resolve on average only 23% of conversations, rose to 51% after swapping in a new underlying model, and reached as high as 86% after deep customization for specific clients; Anthropic itself used it for customer service and, tuning it continuously since its 2024 launch, raised the resolution rate (the share of conversations resolved without human intervention; see Appendix A for the discipline on definitions) to 79%, resolving roughly 560,000 conversations per month. Salesforce walked the same climb: it spent a full year tuning its own customer-service agent before the "can't answer" rate dropped from a third to under a tenth (Chapter 2 expanded on the other side of its self-use pitfalls).

The score on launch day is only the starting point of the curve, and quality iteration during activation is measured in quarters. (Source: Appendix C)

John Deere's collaboration is the most complete public example of "evaluation system first." What this company needed to solve was herbicide waste: traditional sprayers cover the whole field, while its "See & Spray" technology uses 36 cameras plus machine vision to spray only weeds while traveling at 12 to 15 miles per hour — covering the area of three soccer fields per minute. The precision-agriculture ideal is grand: the U.S. plants 12 trillion corn and soybean plants a year, the best farmland yields 200 bushels per acre, and top growers hit 600 — "if every single plant could be cared for individually, yields could be transformed." That is the verbatim account of Justin Rose, a John Deere technology executive.

But what farmers want is not technology but trustworthy advice. OpenAI's forward deployed engineers flew to Iowa, went into the fields with agronomists, first reviewed hundreds of real operation cases together with the experts and built a custom evaluation system, then iterated the model rapidly — and they had to catch the farming season, because missing the planting window means missing a year.

The final result: chemical usage reduced by up to 70%, and farmer interaction frequency increased sixfold. Only with the "good" defined first by the evaluation system did these two numbers follow. (Source: Appendix C)

The deeper significance of the evaluation system is that it turns the veteran's mental "what counts as good" into a scoring standard the system executes automatically every day. This is precisely the microcosm of the FDE model — the client's knowledge is no longer just text in a requirements document, but a yardstick alive inside the system.

## 4.4 Finding Another Way In: Lowering the Barrier to Use

Getting the user to reach value with the fewest possible actions is product-design common sense. But the barrier to using an enterprise system is often an obstacle outside the system. Four "barrier-lowering" techniques have been repeatedly validated in deployment practice.

Technique one: Parasitize the interface the user already has. Wherever the user's main battlefield is, that is where your system should appear: if they work in spreadsheets, make a spreadsheet plugin; if they approve in email, let the approval happen in email; if they work in a ticketing system, embed the AI suggestion into the ticket card. Asking them to log into a new system is like building a wall between you and them that must be climbed every single day.

OpenAI entered through BBVA's existing ChatGPT interface used by 120,000 employees, and Anthropic used the Model Context Protocol (MCP) to bring the model into clients' existing workflow tools — same logic.

Lowe's, a home-improvement retailer, took the same logic onto the sales floor: its in-store AI assistant was not built as a new system but installed directly into the handheld terminals employees already carried, letting them ask about products and inventory by voice. This assistant rolled out to over 1,700 stores and answered more than 5 million employee questions cumulatively. The project lead's verbatim words: "If you haven't spent time on the sales floor, you can't design for the store team." (Source: Appendix C)

BBVA is the best example of "entering the organization along old habits." It began working with OpenAI in May 2024, and the first step was simply issuing 3,300 ChatGPT Enterprise accounts — no company-wide campaign, just letting seed users play on their own. Employees quickly created over 20,000 custom assistants (GPTs, employee-built dedicated AI apps) on their own, of which about 4,000 were used at high frequency; rather than banning "shadow AI," management did the opposite: "we gave everyone a safe platform to experiment on with confidence." Alongside this came structured training: 250 executives (including the chairman himself) took the course first, and the bank built an "AI Pioneer Network," cultivating a group of power users internally called "AI geeks." The data a little over a year later: employees saved about 3 hours per week on average, 83% used it actively every week, and accounts had expanded to 11,000. In December 2025, the two sides officially announced a bank-wide rollout: 25 countries, 120,000 employees, and the launch of an end-to-end transformation roadmap called "The Eight Things." From 3,300 to 11,000 to 120,000, every expansion step happened only after the usage data of the previous step was published — this is activation that "lets the habit walk on its own." (Source: Appendix C)

The local version of this playbook has one key difference: Chinese companies rarely have the soil for "employees choosing their own tools," so the seed is not "issue accounts and let employees play," but first securing a dedicated budget for one business unit or one line of business — the first batch of accounts allocated by the organization is itself legitimacy.

Technique two: The activation rate is hidden in the default values. A new user's first reaction to a blank system is "now what," and most drop-off happens in those three seconds. The FDE's solution is to pre-install the "first use": preset templates, pre-filled examples (based on the client's own data), preset guidance (when first opened, there is already a to-do list that belongs to them). On day one, the system should understand what the user might want to do better than the user does — this is where the observations gathered from the first few days of on-site watching come in handy.

Technique three: Translate "ask the AI" into "click a button." Enterprise users' fluency with "talking to AI" is far more uneven than imagined. So letting users compose their own questions is offloading the engineering burden onto the people least equipped to bear it.

The mature approach is to wrap high-frequency scenarios into one-click actions: "generate last week's anomaly report," "reconcile this batch of invoices," "draft this customer letter" — behind the button sits a complete, evaluation-tuned prompt and workflow. Conversational interaction is left for exploration; button interaction is left for daily use.

The most aggressive practitioner of Technique three is the vendor sharpening its own knife first. Salesforce's own help center had accumulated over 740,000 knowledge articles, and in the past customers had to search for answers themselves; they wrapped a Q&A agent directly into the help center, going live in two months with low-code (low-code, drag-and-drop no-programming development) tools — today 76% of inquiries are resolved without human intervention (accessed August 2026). ServiceNow did the same by turning the knife on itself first: by its own disclosure, its own assistant generated about $10 million in annualized benefit within 120 days of going live.

Activating yourself first is both the best test bed and the most persuasive sales material. (Source: Appendix C)

Technique four: Be a "copilot" first, talk about "autopilot" later. Facing high-risk, high-resistance processes, do not push automation in one step. Let the system exist first as an "advisor" — AI drafts, humans confirm; AI flags, humans adjudicate. Through each confirmation, users build a trust calibration toward the system's judgment; only when the confirmation pass rate reaches a certain level does automation come onto the agenda.

John Deere's solution still preserves the agronomist's final decision authority; agent designs in financial-compliance scenarios generally retain human gatekeeping; medical scenarios all the more so — at Tampa General Hospital, the sepsis (a potentially fatal body-wide infection response) warning remains a system prompt with a physician's adjudication (Chapter 8 will expand on this case that saved hundreds of lives). Copilot first, automation later, is the steady path that trades a little activation rate for controllable risk.

But "human confirmation" has a counterintuitive failure mode: too many confirmations and people stop looking. Anthropic's engineering team published a set of telemetry data (usage data auto-reported by the system): users approve about 93% of permission requests — the more they see, the less carefully they look, and approval fatigue makes oversight a formality; in one internal exercise, a phishing email saying "run this for me" succeeded 24 out of 25 attempts.

Their solution was to move the boundary from "hoping people carefully allow each time" down into the system's foundation: deny by default, so that even if something goes wrong it cannot breach the wall. For high-risk content scenarios, this boundary is pushed to before launch: TIME, for its Person of the Year interactive AI experience, had a red team (red team, a team that simulates attackers to do security testing) simulate thousands of attack methods before clearance. A copilot must be paired not just with a "confirm button" but with a boundary that does not depend on human attention. (Source: Appendix C)

## 4.5 The Long, Drawn-Out Integration War

Every FDE veteran carries a set of scars, all from the same war: the integration war with the client's "legacy systems" — those old systems that have run for years inside the enterprise and no one dares touch.

The brutality of this war exceeds the imagination of everyone who has not served on the front line. a16z's description in *Trading Margin for Moat* hits the nail on the head: the context AI applications need — history, business logic, permission systems — is all locked inside the enterprise's internal databases, interfaces, and workflows, and connecting them is "never a choice but a required course." A financial firm's legacy mainframes, a hospital's hundreds of heterogeneous clinic systems, a manufacturer's dozens of siloed shop-floor systems — the common trait of these environments is: outdated documentation, incomplete interfaces, and half the people who understood them already retired.

This war has four strategic points.

- **First, fight integration as a campaign, not as a chore.** Integration work is written in most project plans as a single line — "system integration: 2 weeks" — and then balloons to four months in execution. The root error is treating integration as a technical chore — when in fact it is at once technical archaeology, organizational politics, and data governance, an out-and-out hard battle. The correct posture: draw the system map during onboarding due diligence, grade and schedule integration risks, and gnaw the hardest bone earliest — integration has the greatest uncertainty, and every day its start is delayed, the entire project's schedule is left exposed.

- **Second, solve data problems before model problems.** That report contains a widely quoted insight: the underlying cause of many failed AI projects is "garbage in, garbage out" — AI plugged into ungoverned data sources, where the same document's ten versions are hit at random, making the output naturally untrustworthy. Palantir's solution is the ontology: first model the enterprise's data assets into a layer with business semantics, clarifying "which field is authoritative, which version is valid, who is allowed to see what," and AI runs on top of this foundation. The universal lesson of this path is: data governance cannot be done once and for all before starting, but runs through the entire project — many AI projects, by the end, consist essentially of governance. Even Palantir itself stumbled on this: an internal system was blown up by 2.3 million data entries, and the first sentence of the post-mortem was "we had never seen the data this system actually had to process."

The U.S. Navy's "shipbuilding operating system" is the most spectacular footnote to this lesson. In December 2025, the Secretary of the Navy and Palantir's CEO jointly announced a $448 million contract: first covering two large shipyards, three naval dry docks, and one hundred suppliers. The shipbuilding industry's data environment is a textbook disaster: ERP systems, decades-old databases, and paper blueprints coexist. Yet two numbers from the pilot phase silenced everyone: at General Dynamics Electric Boat, the nuclear-submarine manufacturer, **submarine scheduling was compressed from 160 manual hours to under 10 minutes**; at Portsmouth Naval Shipyard, **materials review time was compressed from weeks to under an hour**.

The Secretary of the Navy specifically emphasized: "This is not a concept, not a pilot, not research — this is already happening." (Source: Appendix C)

Only by first spending great effort to bring the data into a unified semantic layer can an efficiency miracle occur — not the other way around.

The same logic replays across three completely different industries. Wendy's, the fast-food chain: syrup-stockout scheduling across all 6,450 North American stores used to take 15 employees a full day to check; after connecting to the data platform, a plan comes out in five minutes. Fannie Mae, the mortgage giant: used AI to detect mortgage fraud with a detection rate over 99%, far exceeding the old rules-based system. Citibank: customer credit approval compressed from hours to minutes — AI reads in one breath the credit history, transaction habits, industry risk, and affiliated companies.

Three industries, one common premise: first organize the scattered data into a semantic layer machines can understand, and intelligence has somewhere to land. (Source: Appendix C)

- **Third, use AI to fight the AI integration war.** An important variable after 2025: the integration work itself is beginning to be automated by AI. The scenario a16z anticipated has partly become reality — for old systems with no interface, a browser agent simulates a human to fetch data; field mapping, format conversion, and interface-document interpretation are largely handed to models. The self-imposed standard of leading teams is: "automate the integration process as much as possible — process mining, data pipelines, system integration, interface-document sorting — this speed advantage compounds." Using AI to do the work of AI deployment — this may be the most delightful part of the role.

- **Fourth, know when to go around rather than conquer.** Not every legacy system is worth a frontal integration: some systems' correct solution is "shadow reading" — read-only snapshots, overnight sync; some are "manual ferrying" — keep a human step during the transition; some simply "declare isolation" — explicitly tell the client that this process's data is out of scope for the project. An engineer's pride always wants to conquer every fortress, but the FDE's judgment precisely shows in choosing the battlefield — the project wants client results, not total technical victory.

## 4.6 Change Management: Getting the Client Organization to Stand Behind You

The biggest soft resistance to activation is not in technology but in the organization. Among the report's five major roadblocks, "employee resistance" and "change management" together account for nearly half. Getting the system running takes only engineers; but changing people's behavior takes mobilizing the whole organization.

In the FDE context, change management centers on cultivating three groups of people.

- **Sponsors: your internal allies.** Behind every successful deployment stands a sponsor inside the client: someone who genuinely believes in the cause and is willing to stake their own reputation to clear the path. David Wakeling of law firm Linklaters is a classic example — as the firm's head of market innovation, he was Harvey's counterpart, advocate, and protective umbrella inside the firm. Points for cultivating a sponsor: give them material they can present (stories they can tell outward), give them battle honors (turn their vision into a highlight of their career), give them a sense of safety (you take the front when things fail). One well-treated sponsor beats ten product presentations. Lowe's simply turned this into policy: every AI project must fall into one of three categories — "how customers buy, how stores sell, how employees work" — and must have backing from a senior-vice-president-level business owner — "if they don't get in the game, we don't do it."

- **Influencers: the informal opinion leaders.** Every organization has a group of uncrowned kings: the senior analyst, the workshop veteran, the person everyone says "just ask him." They hold no power, but they hold trust. Their one line "this thing actually works" outweighs three all-hands emails from management; their one line "doesn't work" and the next day no one in the workshop opens it. So during activation, deliberately cultivate these people: let them be the first to trial, take every one of their complaints seriously, make adopting their suggestions visible — "this field was added per Master Wang's suggestion." Making influencers co-authors is the shortest path to cracking the "I won't use what I didn't make" mindset. Device-management company Jamf is an extreme case: after rolling out across all 16 departments, the biggest surprise was that "the broadest adoption was not driven by engineers" — the performance-review conversation tool was built by a business colleague in under 45 minutes, whereas similar past projects took a team three months. When the barrier to building drops to this level, influencers are no longer just word-of-mouth nodes but direct builders.

- **Losers: the interest groups your solution displaces.** Automation inevitably redistributes work, and redistributing work inevitably creates losers: the approver whose sense of presence was compressed, the department whose information barrier was pierced, the veteran whose "proprietary craft" was replaced. If ignored, they become the system's most stubborn underground resistance — passive non-cooperation, spreading accident stories, voting against at acceptance. Mature change management designs the "losers' way out" in advance: redirect the freed labor to higher-value work (and publicly commit to no layoffs), transform "gatekeepers" into "coaches" (the veteran's experience is used to train the system), and let the losers see their place in the future. This is both humane and purely utilitarian — the cost of resistance far exceeds the cost of reassurance.

The collaboration between ticketing platform Vivid Seats and Sierra shows what "full client-side mobilization" looks like during activation. After deciding to introduce an agent, the company's product, customer-experience, and engineering teams all piled in — "once we made the decision, we went all in, all-hands testing." The result: from kickoff to launch in under four weeks, a 40% lift in post-launch resolution rate, and a 35% lift in customer satisfaction (CSAT).

But the more valuable change came afterward: once routine questions were absorbed by the agent, the customer-experience team shifted from "queuing up to fight fires" to root-causing process problems, even finding bandwidth for service beyond customer expectations; and the agent conversation data began feeding back into the product — "if ten thousand people ask about the same feature in a month, we can immediately put it on the priority list. The best moment is: a pattern-driven product improvement means users don't even need to ask for help anymore." (Source: Appendix C) Taken to the extreme, activation means users need to ask for help less and less — this case also previews "feeding the product back from the field" in Chapter 7.

The structure of mobilization can also be designed in reverse: it is not only the client mobilizing, the vendor embeds resources into the client organization too. Lyft's collaboration with Anthropic is a three-piece set: co-building the product, Lyft getting early-test access to new capabilities first, and Anthropic training Lyft's engineers — the result was an 87% drop in average customer-service resolution time, with thousands of requests resolved directly by agents every day. Of the three pieces, the third is the cheapest and the easiest to cut, yet it is often exactly what determines whether the mobilization takes root in the client organization. (Source: Appendix C)

Corresponding examples are emerging in Chinese companies too. Ren Xiliang, head of efficiency engineering at e-commerce company DeWu (Poizon), breaks the AI transformation of a ten-thousand-person company into three steps: step one, reach consensus with everyone and lower the tool barrier so everyone uses it first; step two, divide enterprise scenarios into quadrants by error-tolerance space, and hand the high-error-tolerance scenarios (such as business analysis) to AI first; step three, set up a dedicated knowledge-operations group that dives into business teams and moves experts' tacit experience from individual heads into a space AI can see. Consensus, scenarios, knowledge — the order cannot be reversed: first have people willing to use it, then pick the right place to use it, and finally give AI rice to cook with. (Source: Appendix C)

The ultimate test of change management has only one criterion: after your team withdraws, is the system still being used? If it was bustling while you were there and cooled rapidly after you left, that is not activation, it is accompaniment. A truly activated organization walks forward on its own.

## 4.7 I, Robot — Automating the Delivery Work Itself

Delivering automation to the client is the product itself; automating your own delivery work is efficiency. The latter is the FDE team's first lever to escape "revenue scaling linearly with headcount."

Astonishingly large portions of an FDE's daily work are template-able, repetitive labor: new-client deployment-environment initialization, standard pipelines for data ingestion, security-review questionnaire responses, pre-launch checklists, and periodic client-report formats. Every action done a second time should trigger one question: "can this become a script, a template, or a checklist?"

Leading teams have already distilled their practice into four categories of assets.

- **Deployment templates:** package environment setup, permission configuration, and monitoring integration into one-click infrastructure-as-code (IaC). When a new client comes on board, a standardized environment can be spun up in their cloud environment on day one, rather than configured from scratch over a week. Decagon can compress simple-scenario deployment to 15 days, behind which lies a highly templated integration layer. (Source: Appendix C)

- **Integration component library:** connectors for mainstream enterprise systems (pre-built integration parts), written once and reused everywhere. Palantir's ontology model essentially takes this logic to its extreme: the product of data ingestion is not a one-time pipeline but a reusable, business-meaning-bearing data asset.

- **Checklist culture:** security-review checklists, launch-readiness checklists, handover checklists. The moment this set of checklists proves most valuable is the day before withdrawal: the on-site engineer and the client's successor sit down and tick off the handover checklist item by item, and only when every box is ticked does the person withdraw. The checklist turns "depending on individual experience" into "depending on organizational memory."

- **Automated reporting:** weekly reports to the client and field intelligence to the company should both be semi-automatically generated. An FDE's hourly rate is too high to spend on copy-paste — and even less should "forgetting to report" sever the loop between field and product discussed in Chapter 7.

Automation has one more easily overlooked use: hand quality checks to machines too. DoorDash is typical: its AI customer-service system handles hundreds of thousands of incoming calls a day, behind which automated test capacity increased 50-fold — without such test capacity, day-scale iteration would never dare run on traffic this large. This is also one source of DoorDash's confidence in completing, with an external expert team, the journey from design to deployment in eight weeks. (Source: Appendix C)

How considerable the compounding of automation is can be seen from one angle: a16z lists "building or buying tools to automate service delivery" as a key recommendation for forming a forward deployed team, and judges this to be the key variable letting this generation of AI companies run faster and with a lower per-deal threshold than the previous generation of enterprise-software companies. Sierra's published client data also confirms this: from kickoff to launch, the fastest was under two weeks and the slowest six weeks, with one client resolving over half its inquiries on launch day; Palantir compressed its sales cycle from nine months to weeks — none of this relied on engineers working overtime, but on turning yesterday's delivery into today's scaffolding.

Former Palantir engineer Barry put this logic even more plainly: the company burned millions of dollars on client pilots, and many pilots' profit margins were "literally negative infinity," but management booked it as R&D, not cost — every implementation is first an opportunity to build and learn, and only second a business. "Ninety-nine percent of founders and investors can't swallow that." Only by admitting delivery is an investment does it get to compound. (Source: Appendix C)

"The FDE is just a human-wave tactic, isn't it" — the most common doubt, by now, also has its answer. The problem with a human wave is not the number of people, but that everyone is doing non-reusable, one-time labor. Every delivery builds the road for the next delivery — this way, the same team keeps getting faster round after round.

The system is running, and people are using it. But the cruelty of enterprise business is this: activation only lets a project survive its first year; whether it survives long-term still depends on the renewal. Next chapter: holding the renewal.
