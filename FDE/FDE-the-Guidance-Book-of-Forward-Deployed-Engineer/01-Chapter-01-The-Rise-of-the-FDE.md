---
title: "Chapter 1 · The Rise of the FDE"
original_title: "第 1 章 FDE 的崛起"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "https://fde4.ai/book/01-%E7%AC%AC1%E7%AB%A0-FDE%E7%9A%84%E5%B4%9B%E8%B5%B7"
source_file: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer/blob/main/01-%E7%AC%AC1%E7%AB%A0-FDE%E7%9A%84%E5%B4%9B%E8%B5%B7.md"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [第 1 章 FDE 的崛起](https://fde4.ai/book/01-%E7%AC%AC1%E7%AB%A0-FDE%E7%9A%84%E5%B4%9B%E8%B5%B7)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

# Chapter 1 · The Rise of the FDE

> "One challenge of building software for spies is: I don't know any spies."
> — Bob McGrew, early Palantir executive and former Chief Research Officer of OpenAI

## 1.1 Let's Start with a Dead Multi-Million-Dollar Project

The beginning of every story is the same. In the conference room of a large enterprise, the vendor's demo has just ended. The large language model answers fluently, the data dashboard shimmers with light, and even the most demanding executive can find no fault. The CEO decides on the spot: sign. The contract is worth several million dollars; both sides shake hands, pose for photos, and issue a press release.

Nine months later, the project is dead.

Not dead in a blaze of glory, but dead in silence. The system is still running, the servers are still on, only no business unit is actually using it. The vendor delivered every function in the contract; the enterprise paid every penny in the contract. The only thing that never arrived was "value."

If you think this is just bad luck, the report *The GenAI Divide* released by MIT's NANDA Lab in 2025 will tell you: this is the norm. They interviewed 52 organizations, collected 153 executive questionnaires, and reviewed more than 300 public enterprise AI projects. The conclusion is a single sentence: of the $30–40 billion burned in, **95% produced no measurable financial return whatsoever**.

Before citing that 95%, we have to state its scope. After the report was published, doubts converged on three points:

1. It defined "failure" as no measurable financial-statement impact within six months — by that standard, the early investments in the internet and cloud computing were almost all "failures";
2. Its measurement of value only counts profit, cost, and revenue; leading indicators like process speed-ups and employee adoption don't count;
3. The sample is dominated by large enterprises, and the failure data comes only from the project-sponsor side. Commentators also flagged a conflict of interest: the NANDA lab itself studies the Internet of Agents, and the report's proposed solution happens to point right back at its own turf. (Source: Appendix C)

All these doubts hold, yet none overturned the directional judgment: enterprise-grade AI projects fall short of expectations across the board — independent research from RAND Corporation, S&P Global, and others points to the same picture. So when this book cites 95%, it takes the direction, not the precise value; a failure rate precise to the single digit is itself a false precision.

More interesting is the *way* it fails. The report specifically wrote: the problem is not the model. Those models that dazzled in the demo remain smart in production — they just "don't remember feedback, don't store context, don't enter the workflow" — they look like a product but use like an exhibit.

Stanford's same-year macro data bears witness from the sidelines: 88% of organizations are using AI, yet the share of agent applications that actually reach production is only single-digit percent. McKinsey delivered the final cut: only 6% of enterprises can say AI contributes more than 5% to profit.

In the days *Fortune* covered this report, a manufacturing COO's gripe circulated through the industry: "Online they say everything has changed. Back in our workshop, nothing has moved." (Source: Appendix C) That line cuts deeper than any data — his company lacks neither budget nor tools; what it lacks is someone to shove the tools into the workshop's real processes.

The report also contains a quieter contrast that directly votes for this book's theme: systems enterprises build behind closed doors succeed at only about one-third the rate of buying a mature off-the-shelf solution. The report's lead author said that nearly every enterprise they visited was trying to build its own tools — and building in-house is precisely the path that dies the most.

He also told a contrasting-pair story. Some startup companies run by nineteen- and twenty-year-olds used generative AI to reach $20 million in revenue in a single year. Their playbook is the exact opposite of the old-guard enterprises: pick just one pain point and hammer through it, and tightly bind themselves to customers who actually use their product. Older companies always want to swallow the whole elephant in one bite; the young ones take only a small bite, chew through it, then take the next. (Source: Appendix C)

In truth, this chasm was not dug in the AI era. China's enterprise-software industry has been lying in that ditch for over a decade: big companies demand customization, vendors lose money on every deal, and once delivered the code is abandoned, until collectively they degrade into "the client's outsourcing company." A veteran of enterprise software on the *Hardcore Hacker* (Yingdi Haike) podcast put it bluntly: "Customization is the nemesis of SaaS; this curse can only dissolve naturally when the market matures." The American side is more presentable, but the script is much the same: sales closes the deal, implementation comes on-site, half a year later delivers a "fully featured but nobody-loves-it" system, followed by endless bickering.

At root it is the same wall: the place where software is built and the place where value is created are not the same place. On this side of the wall, requirements are relayed through tickets, minutes, and weekly reports, distorted one layer with each relay; on the other side, the client's real workflow hides in spreadsheets nobody wrote down, in conventions passed by word of mouth, in the tacit knowledge of "ask Old Wang about that." The software industry invented countless ladders to scale the wall — requirements documents, user research, implementation methodologies, customer-success systems — but the wall has always remained.

Until one company decided: stop climbing the wall, send a person over.

## 1.2 Palantir's Victory

In 2003, Silicon Valley had just crawled out of the rubble of the dot-com bubble. Peter Thiel and a few Stanford-bred young people founded a company named after *The Lord of the Rings* — Palantir, the "seeing stone," a rock in legend that could see into the distance. What they set out to do sounded like science fiction: build data-analysis software for U.S. intelligence agencies, connect the fragments scattered across countless classified databases into a picture, and help analysts catch terrorists.

This business carried a premise that could make any product manager collapse on the spot. Years later, early executive Bob McGrew recounted this episode vividly on YC's Lightcone podcast:

> "Our goal when we started was to build software for the intelligence community — plainly put, software for spies. And one challenge of building software for spies is: I don't know any spies, and you probably don't either. Even if you happen to find a spy and ask, 'So how exactly do you work day to day?' they usually won't tell you."

No user interviews, no requirements documents, no usability testing. The first lesson of internet-startup methodology was void here. The workaround thought up by founder Stephen Cohen was endearingly clumsy: first build a demo, show it to the intelligence people, and ask what they thought. The other side was blunt: "This thing is terrible, it has nothing to do with what we do." Cohen didn't retreat; he pressed: "Then what would you want it to be different?" Then he pulled out a notebook, wrote it down point by point, went back, changed it, and brought it back to the door.

This clumsy loop was the embryo of the FDE. Hidden inside were two intuitions later proven worth a fortune: first, complex-domain customers don't know what they want until they see something usable; second, the fastest way to learn what the customer wants is to put the person who builds the thing next to the person who uses it.

The one who upgraded these intuitions into company strategy was employee No. 13, Shyam Sankar. As Palantir moved from its first customer to its second and third, the team discovered a counterintuitive fact: what each customer wanted differed in subtle but critical ways. The standard playbook is to extract commonalities, build a general-purpose product, and say no to differences. But Palantir's customers were the CIA, the FBI, and U.S. troops on the battlefield — to say no was to be out.

Sankar went the other way: build a flexibly customizable platform, then dispatch engineers to embed at the customer site and finish the last mile.

His most crucial move was to rewrite the accounting for this work. In the software industry's ledger, "customizing for a single customer" is called services, the enemy of margin. Sankar flipped it: the on-site customization should be booked as product discovery. Every pitfall an engineer steps into at the customer site is a signpost for the platform's next evolution.

Sankar himself was the first Forward Deployed Engineer, and his earliest embedded stint is practically the prototype scene for this role. Around 2007, the biggest source of U.S. casualties in Iraq was roadside bombs, and the Counter-IED operations center established for this allowed Sankar to bring a small team and a "still very rough" product into a classified information room for two weeks of co-working. A classified information room is a physically isolated secure space where even speakerphone calls are banned. Sankar came up with a barbaric trick: strap the phone to his head with elastic bands, freeing both hands to write code — one ear listening to analysts' feedback, the other ear listening to colleagues at Silicon Valley HQ. For two weeks he worked nineteen hours a day, demoing, ingesting data, collecting feedback, and fixing on the spot. At the end, the analysts said: this thing is useful. Sankar himself was wrecked, and called CEO Karp: "This is unsustainable, we're done." Karp's answer later became company culture: turn this "unsustainable" into an institution. (Source: Appendix C)

Years later a colleague recalled that Sankar scolded people without a trace of emotion. Once, he and colleague Mabry were chatting happily at an airport café when the other's inbox suddenly received a harshly worded criticism email from him — written and sent right there while sitting across from him. "There was no personal attack in it, only one subtext: to win, I owe you these truths." (Source: Appendix C)

This playbook soon drew blood on the battlefield. The embedded Palantir engineers discovered that soldiers didn't need any fancy intelligence charts; they just wanted a small tool that could mark "this road is suspicious" on a map — roadside bombs were the patrols' biggest killer. The engineers threw together a crude map tool on the spot; a soldier could click to mark a dangerous stretch, visible to the whole team in real time. This tool saved lives and later settled into a standard platform feature. It could not have been born in any headquarters conference room; it could only be born in the instant when an engineer and a soldier looked together at the same highway.

On the commercialization side, there was first a death. Palantir's first enterprise-facing product was called Metropolis, and the market reception was dismal — only a few financial firms barely used it. The second attempt, Foundry, finally opened the account, with the turning point at Airbus: in the Toulouse factory, an A380 fuel-pump fault recurred again and again, and Airbus's own engineers had been stuck for two years with no clue. Palantir's people came in, connected the sensor data to the platform, and cracked it in two weeks — when the plane climbed, the fuel sloshed away from the pump body. A trivial fix that, by report, protected orders worth tens of billions of dollars. Airbus's head of digitalization later remarked publicly: "For the same problem, we used to take twenty-four months." (Source: Appendix C) Airbus thus became Palantir's most loyal adherent in Europe, building its own data platform Skywise entirely on top of it, connecting tens of thousands of aircraft and more than 50,000 users. The later trajectory is even more interesting: this platform went from customer to channel, and today more than 150 airlines run on Skywise.

One more bit of gossip worth noting. It is widely rumored that Palantir's software was involved in the 2011 operation that killed Osama bin Laden. This claim has never been confirmed, nor ever denied — the journalist who wrote Palantir's biography reporting deliberately left this ambiguous footnote. But true or not, the rumor itself is Palantir's best sales weapon. (Source: Appendix C)

Before 2016, Palantir's headcount of Forward Deployed Engineers at one point exceeded that of platform engineers. A software company with more than half its engineers not writing product at headquarters but scattered across customer sites worldwide. Wall Street couldn't make sense of it for years, dismissing it as "human-wave tactics," "more like a consulting firm."

Then time gave the answer. In 2023 it launched the AI Platform (AIP), paired with a playbook called "Bootcamp" (detailed in Chapter 8), compressing the enterprise-software sales cycle from nine to twelve months down to a few weeks. In Q4 2025, its "Rule of 40" — revenue growth plus adjusted operating margin (non-GAAP basis): the software-industry health metric where 40 is passing — hit 127%; in Q1 2026, 145%. Single-quarter bookings of $4.26 billion (bookings, total-contract-value basis), Net Revenue Retention (NRR; Palantir's reporting calls it NDR) of 139%, and $7.2 billion in cash on hand.

Karp said only one line on the earnings call: "We are a species unto ourselves." Market cap at one point broke through $400 billion. (Source: Appendix C)

Those who once laughed at its human-wave tactics were left speechless. Palantir spent twenty years proving one thing: that wall, ladders can't cross, but a person can. The people who crossed the wall got a formal name — Forward Deployed Engineer (FDE), or 前线部署工程师 in Chinese.

Sankar later publicly claimed the invention of this name on the *American Optimist* podcast. His definition is anything but official: a Forward Deployed Engineer is "the kind of person who eats the pain and produces the product."

Of course, there is another account of the origin. A VC firm has documented that IT service companies embedded engineers at the customer site earlier than Palantir did — we'll set this dispute aside for now and return to it with data in Chapter 7.

## 1.3 What Is an FDE

### One-Sentence Definition

The definition this book adopts comes from the best expositor of this model, Bob McGrew — who was an engineer at PayPal in his early years, later an early executive at Palantir, and then Chief Research Officer of OpenAI, with ChatGPT and GPT-4 both coming out of the teams he led:

> **A Forward Deployed Engineer is an engineer stationed at the customer site, bridging the gap between what the product can do and what the customer needs.**

"Stationed on-site" means your working context is embedded in the customer's: you join the customer's groups, read the customer's data, sit in the customer's meetings, and know the person "who knows why the workflow is this way" — not necessarily sitting in the customer's office every day. The "gap" is the reason this role exists: where the product works out-of-the-box, you are not needed; where the gap is deepest, you are most needed — intelligence, finance, manufacturing, healthcare, law.

"Engineer" is the most crucial qualifier: you write code that runs in production, not reports. When Palantir named the role it deliberately kept the words "software engineer," precisely to tell the world: this is not a consulting post. As for "Forward Deployed," it is a military term for troops deployed at the front line — placing the most combat-capable people closest to the problem.

### What It Is Not

First, what it is not.

It is not pre-sales. Pre-sales work ends before the contract is signed, the goal is to win the deal, the artifact is slides; an FDE's work enters deep water only after signing, the goal is to win the outcome, the artifact is a system running in production. Pre-sales is responsible for making the customer believe "this can be done"; the FDE is responsible for making it actually get done.

It is also not on-site outsourcing — a distinction especially important for Chinese readers, because "engineer on-site" carries in China too long, and too inglorious, a history. Qimeng Technology (启盟科技), among the first service providers in China to fly the FDE banner, drew the line between itself and on-site work in three sentences on its website:

1. On-site is billed by labor-hours; the FDE is billed by stage of delivery and accepted by results;
2. On-site writes everything from scratch; the FDE brings a product base and does engineering on top of it;
3. On-site stays longer and longer, and when the person leaves the system stops; the FDE leaves when done, with the capability left inside the system and the client's team.

Jove, the FDE lead at Silicon Valley AI-customer-service company Cresta, laid out this boundary even more finely in a video conversation. His team is expanding from 30 to 100 people this year, and his judgment is: an FDE only makes sense when bound to an AI platform — if it's just traditional data integration and system building, it's hard to distinguish from a traditional implementation engineer or from outsourcing. He also has a hard line on hiring: in the agent era, not knowing how to code is like illiteracy.

Another mechanism worth noting is the dual mandate: the FDE must not only make the deployment succeed but also carry the metric of "making the product more mature" — what is learned on-site must feed back into the platform. (Source: Appendix C)

It is not a consultant. A consultant delivers advice by project and is not responsible for execution; the FDE is responsible for the system's final operation, with the endpoint being "the client's team can use it independently." The collaboration between Anthropic and the fintech company FIS is a specimen: engineers embedded in FIS co-built an anti-money-laundering agent, compressing investigations from hours to minutes, but the stated goal of the collaboration was not to hand over a system but to "transfer knowledge so FIS can build agents itself" down the road. The consultant's business is built on the client's continued need; the FDE's standard for whether it succeeded is exactly reversed — the day the client no longer needs you is the day you've succeeded.

The buyer's side calculates the same way. A technology lead at JPMorgan Chase was blunt when discussing co-building with a platform vendor: "What we want is not more consultants, but engineers who can build things that don't yet exist."

It is also not a traditional product engineer. The product engineer faces abstract users — personas (what the user looks like), funnels (how many people go from visiting to paying), daily active users; the FDE faces concrete clients — a bank's risk-control department, a farm in Iowa, a patrol unit on the outskirts of Baghdad. In Palantir's official blog post "Dev versus Delta," there is an official split of these two roles: the platform engineer is responsible for "one capability, serving many clients," while the Forward Deployed Engineer (internal codename "Delta") is responsible for "one client, mobilizing many capabilities." The platform engineer pursues one feature usable everywhere; the FDE pursues thoroughly solving the problem of this one client in front of them first.

Nabeel Qureshi, who spent nearly eight years as a Forward Deployed Engineer at Palantir, boiled this discipline down to a crude line: "Screw generalizability" — save this client in front of you first; whether it can be reused at the next one is the platform team's job.

### How This Trend Took Off

A role invented in 2003 — why did it only become top-stream in 2025?

The most direct trigger was generative AI. Large language models created an unprecedented gap: anyone can produce a dazzling demo in five minutes, yet wiring that demo into an enterprise's real data, permissions, compliance, and workflow is an order of magnitude harder. The model companies gradually figured it out: the next winning move lies in deployment capability. The deployment lead at a logistics AI company put it even more bluntly: AI landing rarely fails at the model; it almost always fails at context.

The demand side voted just as bluntly. Goldman Sachs rolled out its self-developed AI assistant across the whole bank, covering more than 10,000 employees during internal testing; Klarna's AI customer service took on two-thirds of customer-service conversations in its first month; even universities moved — Syracuse University opened Claude to all faculty and students, and required training to be completed before an account was activated.

This wind didn't blow up in one night either. As early as July 2025, Semafor published an article asserting that this "plainly-named position" would change the AI industry.

The numbers sketch how steep the curve is: according to official statistics from the recruiting platform Indeed, in April 2025 there were only 643 jobs nationwide carrying the FDE title; a year later that became 5,330 (Indeed's job-matching basis), up 729%. Other institutions' figures are even more extreme — 800%, 1,165% — with varied methodologies but completely consistent direction. On YC's job board, more than 100 startups posted this position that barely existed three years ago.

The VC firm a16z (Andreessen Horowitz) straight-up called it "the hottest job in tech," with a vivid analogy: an enterprise buying AI is like your grandmother getting an iPhone — she wants to use it, but needs you to set it up for her.

A set of reports from the *Financial Times* in November 2025 is the best cross-section for observing this craze. OpenAI's Europe FDE lead Fournier said his team was founded only a year ago and is about to expand to 50 people, "demand exceeded our expectations"; Anthropic's applied-AI lead De Jong said something even more interesting: "The needs of a Fortune 500 bank and an AI-native startup are completely two different species" — so her team expanded fivefold in a year. Palantir's UK lead Prettejohn condensed the company creed into one line: "Software only has value when it truly means something to the end customer." Even Cohere's CEO Gomez stepped up to vouch: "We embed engineers from the very start of the contract, and pull back once the client is running smoothly." (Source: Appendix C)

The intensity of the talent grab has a string of hard metrics too. OpenAI's Forward Deployed function was officially announced on social media by Colin Jarvis in January 2025, with a one-line mission: "help clients push systems into production"; the team started from 2 people and grew to 52 in a year. Salesforce, which wrote "don't do your own implementation" into its textbook, publicly committed to hiring 1,000 FDEs; Google Cloud released 59 positions at once, with CEO Kurian personally going online to call for "builders who want to stand at the center of the agent era"; Box's CEO Levy publicly asserted that this will become one of the most sought-after positions in tech.

Databricks went even further, restructuring its entire professional-services department into an FDE organization that served more than 1,900 clients in twelve months. Even Deloitte, which sells consulting for a living, established a dedicated FDE business line in December 2025. Europe wasn't idle either — from Mistral to Lovable, the recruitment focus of star startups is shifting from research talent to deployment talent. (Source: Appendix C)

This wind even blew into the government's field of vision. At the end of 2025, Shanghai held the nation's first FDE specialized training class, jointly staged by six units including the Municipal Organization Department and the Municipal Commission of Economy and Informatization. Interestingly, the composition of the first cohort: not engineers, but the heads of municipal state-owned enterprises and key industry regulatory departments — train the demand side first, then the supply side. The goal of the supporting project is just as plain: link a hundred enterprises, build a thousand agents, and drive ten thousand developers to transform.

The official framing of this role is "special forces in the field of artificial intelligence." A role hot enough for the government to step in and run a training class is rare in the history of the software industry.

Then came the giants voting with their feet. On May 11, 2026, OpenAI announced the formation of a "Deployment Company": self-controlled, jointly with 19 top capital partners including TPG, Bain Capital, and Brookfield, with initial investment exceeding $4 billion, media disclosing a pre-money valuation of about $10 billion, and incidentally acquiring a consulting company with 150 deployment engineers. A few hours later, Anthropic was reported to be forming a matching joint venture with Blackstone. The two largest model companies, on the same day, elevated "deployment" from a cost center to a strategic asset — the capital market voted for the FDE in the most expensive way possible.

Why is the capital market willing to vote this way? The VC firm Foundation Capital ran the numbers openly: they estimate this wave is targeting a market on the order of $4.6 trillion — half being the salaries enterprises pay to sales, marketing, and engineering roles, and half being IT services and outsourcing spend. In other words, software's billing object is shifting from the "tool budget" to the "labor budget." In a16z's words: software is no longer just helping workers work; software itself is the worker.

Of course, there is also calm skepticism. The *Wall Street Journal*, in its reporting, put the question on the table: this playbook looks more like consulting than software; embedded talent is too expensive, and whether it can scale remains an open case. This is a serious question — and this book responds to it head-on in Chapter 7.

The deepest reason is still what McGrew sees through: "The AI agent is a category without a hegemon yet, so there's a massive amount of product discovery to do." What customer-management software should look like had a standard answer twenty years ago; what an agent should look like, nobody knows — including the client. The answer can only be found at the client's site. McGrew put it even more plainly on Sequoia Capital's *Training Data* podcast: the reason Palantir's AI Platform is valuable is precisely that it is not the model, but the layer "outside the model, dealing with the rest of the enterprise" — the stronger the model, the more valuable this layer becomes.

Tech analyst Ben Thompson offers a longer historical coordinate: multi-year, deeply-embedded delivery is not a Palantir quirk but a return to the software industry's norm of forty years ago — his judgment is that services and integration teams will return in full, and this generation of AI companies must learn to sell from the customer's top down.

In 2003, Palantir invented the FDE because "it didn't know how spies work"; in 2025, the entire industry embraced the FDE en masse because "it didn't know how enterprise agents should work."

## 1.4 The FDE's Responsibilities and Traits

### A Résumé Born for This Role

If you want to answer "what kind of career is an FDE," McGrew's résumé is almost the standard answer.

His first job was at PayPal, an early engineer. That batch of people was later called the "PayPal Mafia" and profoundly shaped all of Silicon Valley. After leaving, he joined Palantir in its startup phase and rose to executive, personally witnessing the entire process of the FDE evolving from an emergency measure into company strategy. When he led the product and engineering teams he offered a famous analogy: Forward Deployed Engineers at the customer site build "gravel roads" one by one leading to value, and the product team judges which gravel roads are worth widening and hardening into "highways" that serve the next ten clients. He later summed up the whole model in one line: scale the non-scalable.

Further on, he became Chief Research Officer of OpenAI, leading the development of ChatGPT, GPT-4, and the o1 reasoning model. In other words, this person has both built the platform on this side of the wall and crossed to the site on the other side, and finally personally built the very technology that piled this wall even higher.

An interesting scene played out at a 2025 YC AI conference. McGrew had expected entrepreneurs to surround him asking "how did you invent ChatGPT," but instead everyone chased after the same question: how exactly does Palantir's FDE model operate? A person who invented ChatGPT was asked most about delivery methodology.

### Three Layers of Traits

Synthesizing more than twenty job postings from various companies and the firsthand accounts of practitioners, the FDE's traits can be distilled into three layers.

The first layer: a sufficiently broad technical generalist. The FDE doesn't need to be the deepest expert in any one field, but must be able to independently solve full-stack problems on-site (from UI to database, single-handedly): write code, tune interfaces, understand data pipelines, get on the cloud, read the temperament of large language models, and also understand the enterprise environment's "utilities" — single sign-on (log in once, access everywhere), permissions, compliance certifications. The recruitment market has a clear price tag for this combination: GetPerspective's *Forward Deployed Engineer Compensation Report*, released in early 2026, shows that at top AI labs a mid-level FDE's median total compensation is about $385,000, a senior about $610,000, and a principal over $1 million — higher than most same-level pure R&D roles, because the market knows how scarce such people are. (Source: Appendix C)

The second layer: the ability to translate technology into business results. This is the watershed between the FDE and the ordinary engineer. A frontline practitioner's words are widely quoted: "The model is usually the cleanest part. The hard part is finding the workflow nobody wrote down, the data source people actually trust, and the person who knows why the process is that way." Palantir's hiring standard is even blunter: "The candidate's expressiveness, clarity, and ease in communication should make me happy to have them run a meeting with a client."

The interview also screens for this translation ability. The FDE interviews at both OpenAI and Palantir feature a signature segment called "problem decomposition": you're handed a huge, vague, real enterprise problem, and for sixty minutes you write not a single line of code — only how you probe, how you define scope, how you build order in the chaos. The interviewer's advice: understand the problem before you jump in — slow is smooth, smooth is fast. In an ordinary interview, "I optimized the query by 40%" is a perfect answer; in an FDE interview the perfect answer is: "I optimized the query by 40%, which let the client's analysts get their reports two hours earlier every day, and the team's throughput tripled." The technical achievement must be converted into the client's language.

The third layer: a sense of ownership, plus a bit of "rebelliousness." A line circulates in practitioner circles, describing precisely the accountability this role demands: "Deployment broke at 2 AM. You don't file a ticket, don't blame another team, don't go back to sleep. You fix it. Period." Palantir has a more subtle expectation for its business-side roles: both deep industry knowledge and the daring to be a "rebel" — able to see the absurdity of the client's status quo, and daring to push for a tenfold, not a ten-percent, improvement. CEO Karp's behavioral benchmark back then was the "French waiter": embedded in the service flow, sensitive to real needs, yet with enough confidence and taste to guide the client from "what they think they want" to "what is truly good for them."

### How a Day Goes

In daily terms, an FDE's time is roughly divided like this: 40–50% soaked in the client side writing code and tuning systems, 20–30% aligning direction with client management, decomposing problems, and making architecture decisions, 10–20% precipitating the patterns learned on-site back into the company's product line, and the remainder on evaluation, optimization, and knowledge sharing — writing playbooks, internal evangelism, training client teams.

Hidden in this schedule is an important piece of information: the FDE is not a "dispatched engineer" but an "engineer with a dual mission" — delivering results to the client on one end, feeding intelligence back to the company on the other. This is also the theme of the next two sections.

## 1.5 Everything Judged by Results

If you had to sum up the FDE's work creed in one sentence, it would be: everything judged by results. Palantir executive Mabry breaks it down into two plain questions: "Does it actually work? Does it actually matter?" — by his account, the FDE model is "one of the company's biggest secrets."

First, separate "data" from "results." The history of enterprise software has never lacked projects with good-looking data and terrible results: the feature checklist 100% ticked, but only 5% of people use it; system availability at four nines (online 99.99% of the time), yet the business department would rather keep using spreadsheets. Among the 95% failed projects in that MIT report, the vast majority were not short of data reports — the numbers were all there, but the value never arrived, because nobody was accountable for "that line on the financial statements."

The FDE model institutionally ensures that "results" are not diluted, specifically through three things.

- **Pricing moves toward results:** In its early government projects, Palantir already made heavy use of "pay only when it's done" arrangements. McGrew recalls it plainly: "Early on, it's reasonable for a startup to bear all the risk — you pay us once it's done." This logic evolved more finely in the AI era: Sierra charges by "resolved conversations," no resolution, no charge; many FDE service providers do stage-based delivery and acceptance by results. Once charging is tied to results, the delivery team's every behavior gets re-sorted — you won't spend three weeks polishing a feature nobody uses, because "nobody uses it" comes out of your own pocket. Platform vendors are following suit: Databricks wrote milestone- and results-aligned pricing options into its official delivery model.

- **Success metrics are set before work begins:** The first step of an FDE project is not writing code, but defining "what counts as success" together with the client. Palantir's Bootcamp requires the client to first lock an extremely focused core battlefield — "reduce a production line's scheduling conflicts by 30%," not "explore AI empowering manufacturing" — precisely to prevent the project from drifting, under the name of "exploration," toward something unverifiable. The OpenAI–John Deere collaboration is a textbook demonstration: first, together with agronomy experts, review hundreds of real operation cases, build a custom evaluation system, and only then begin iterating the model. The final figure "chemical use reduced by up to 70%" was not an after-the-fact promotional gloss but a target set before work began.

- **The ultimate judge is the client organization's behavior change:** That report contained a pungent finding: only about 40% of enterprises provide official AI-tool subscriptions to employees, while as many as 90% of employees use personal consumer-grade products daily to solve work problems. This means that many "successfully launched" projects are actually in a state of "official system idling while employees detour around it." In FDE philosophy, the milestone is not the day the system goes live, but the day the client's team changes its way of working. Sierra internally and deliberately named the role "Agent Engineer"; lead Moller, explaining the selection standard, said they only take two kinds of problems — ones that are truly hard, and ones with truly real business impact, and both must hold at once.

"Everything judged by results" sounds like common sense, but in execution it offends the entire structure of interests: 1) sales no longer dares to over-promise, because the delivery team is accountable for results; 2) the client's IT department can no longer report with a "feature checklist," because the business department's usage rate has become the acceptance standard; 3) the FDE itself can no longer disclaim with "I did it per the requirements," because the right-or-wrong of the requirements themselves is now on its account. This is where the reason this role is expensive — and worth being expensive — lies.

## 1.6 The FDE's Four Faces in the Team

A single FDE lives simultaneously in four worlds; he is the connector of those four worlds.

- **To the client, he is an "embedded product manager + full-stack engineer":** Like an anthropologist he observes the client's real work — the most valuable discoveries often come from "watching," not "asking" — and like an entrepreneur he directly builds on the spot where he observes. Palantir institutionalized this two-person combination: the Deployment Strategist (internal codename "Echo") is responsible for understanding the client's mission, stakeholders, and adoption path, while the Forward Deployed Engineer (internal codename "Delta") is responsible for technical implementation. The two form a team — one diagnoses, one builds; neither can be missing.

- **To the company's product line, he is a "forward scout and intelligence officer":** This is the most essential difference between the FDE and traditional delivery teams. The cost of traditional implementation is cost of goods sold; every person-day (billed by head and by day) must be earned back from the contract; a healthy FDE organization treats on-site work as R&D — when three clients hit the same integration gap, that is not three troubles but one piece of product intelligence; when five deployments need the same workflow, that should be abstracted into the platform's next standard capability. Former Palantir engineer Barry recalls that Foundry's key components were born in client sites scattered across Zurich, Houston, São Paulo, Toulouse, and elsewhere, growing bottom-up and finally feeding back into a product with annual revenue in the billions. (Source: Appendix C)

- **To sales:** Enterprise clients have been let down too many times and are immune to all slides. The FDE rebuilds trust with two moves: one, act — on the client's own data, in the client's own environment, produce something runnable on the spot; two, be honest — dare to say no to the client's false premises. Palantir's Bootcamp turned this trust-production process into a procedure: the client brings real data, and within one to five days a deployable prototype is built that executives click through with their own hands. The early Bootcamp's paid conversion rate was only 5% to 10%, while the company has disclosed a later conversion rate approaching 75%. (Source: Appendix C)

- **To the organization itself:** Palantir has produced a strikingly dense cohort of entrepreneurs — an interview on Lenny's Podcast gave a number: nearly a third of its product managers started their own companies after leaving. This is not surprising — the FDE's daily training is, in a resource-constrained, vaguely-demanded, complexly-related environment, to end-to-end make something valuable and get people to use it, which is almost a complete rehearsal for founder training. Srinivas, who later founded Decagon, Moller, who built Sierra's agent-engineering team, and several authors who wrote the most-circulated methodology articles in this industry — all walked out of Palantir's Forward Deployed post. One company's talent spillover became an entire industry's talent infrastructure. (Source: Appendix C)

These four identities together amount to one thing: the organization's way of understanding the client has changed — from relayed second-hand information to the first-hand experience an engineer touches on-site.

## 1.7 How to Recruit an FDE

First, a splash of cold water: the FDE is one of the hardest roles to hire in the software industry, because it demands that one person be excellent simultaneously in two dimensions that usually trade off against each other.

Former Palantir engineer Barry laid this bare in a memoir essay: Palantir's standard for hiring FDEs was "engineers who could get into Google or Facebook" — because they go to the client site to build systems, not to tune parameters; but technical skill alone is far from enough; the forward-deployed also need creativity, judgment, and client-facing charm. He added a stinging line: this is far more expensive and difficult than hiring a traditional pre-sales team.

Decomposing the practices of the recruitment market, FDE hiring has three key stages.

- **Candidate profile:** Hire "curious bulldozers," not "refined craftsmen." a16z's advice to startups used the phrase "curious doers": strong agency, little respect for the status quo, hungry for the client's problems. McGrew is more specific: an FDE team wants two kinds of people — "domain rebels": know the industry but don't worship its conventions; "prototype speedsters": speed over perfection, accepting that the first version will be thrown away and rewritten. Conversely, two types favored in traditional engineering culture are danger signals for the FDE role: the "craftsman" who puts code elegance above client results, and the "loyal executor" who treats every word from the client as gospel. Palantir in its early days simply installed the filter at the very outside of the funnel: openly embrace the defense business, pay below market, and demand scary-long hours — Qureshi calls this the "bat signal," effective only on its own kind.

- **Interview:** Replace rote questions with "problem decomposition." As mentioned earlier, this segment is the soul of the FDE interview: hand the candidate a vague, enormous, real-business problem with rough edges — "a bank's compliance team manually checks 30,000 transaction alerts a day, 90% false alarms, what do you do" — then observe for sixty minutes. What's examined is not the answer but the process: did they ask about constraints before acting, distinguish root cause from symptom, remember that a real user sits at the other end of the system, and clearly explain the tradeoffs. Palantir also embeds about twenty minutes of behavioral questions in each technical round, and explicitly rejects candidates who are technically strong but culturally mismatched — the most important item in the culture checklist being a sense of order amid ambiguity.

- **Compensation structure:** Accept a hybrid structure of "engineer compensation + floating bonus tied to the company's operating metrics." Early-2026 market data can serve as an anchor: Palantir Forward Deployed Engineers' median total compensation is about $215,000; at top AI labs a mid-level FDE is about $385,000 and a senior about $610,000; Anthropic's roles have base salaries between $200,000 and $300,000. Another detail worth noting is bonus design: Palantir's bonuses are often tied to operating metrics such as client expansion, sitting between engineering bonuses and sales commissions; a16z's advice is to align incentives with the account manager but not let the FDE carry hard sales quotas — that would steer behavior toward signing, not toward results. An author who dug through fifty job postings offers a simpler litmus test: check whether the role's compensation package contains a sales commission — a high commission share likely means pre-sales with a trendy new title. Compensation structure is also part of the role's definition: how you pay affects how people behave. (Source: Appendix C)

## 1.8 How to Become an FDE

Switching perspective: if you are an engineer, product manager, or consultant wanting to enter this high-growth market, what path do you take?

First, a self-test: the glamour and the cost of this role are two sides of the same coin. In forum practitioner communities, the discussion of the FDE has a rare honesty. The positive part: the best combination of technical depth and brand endorsement, one of the few roles that simultaneously accumulates technical, business, and client resources. The cost part: travel of a quarter to half is the norm — OpenAI's job postings explicitly state travel up to 50%; the work rhythm is defined by the client's urgency, not your own schedule; and there is a repeatedly appearing reminder — the risk of burnout is real.

One comment goes: "Some treat it as a brand springboard, some say it's consulting with a cool title — both statements are true. The difference is whether your company refluxes on-site learning back into the product, or sells you by the person-day." This line is both a career-selection standard and the theme of Chapter 7. (Source: Appendix C)

Now for the domestic money. Those dollar compensations are just background noise for most Chinese readers; the first half of 2026's domestic recruitment market has already put a RMB price tag on this role: ByteDance offers its Doubao FDE 35,000–70,000 per month, 15 months' pay; Ant Digital (蚂蚁数科) 40,000–60,000, 15 months; Zhipu's FDE lead 60,000–80,000; Tencent Cloud 35,000–65,000 (these two did not disclose salary counts); Alibaba Cloud 20,000–50,000, 16 months. Annualized, these roles roughly land between 300,000 and just over 1,000,000 yuan — "a million a year" is reachable at the high end of the top roles, but it is not the industry average. (Source: Appendix C)

The price gap under the same title is more worth watching than the hierarchy gap. A Tangshan industrial-software company hiring an "AI Delivery Engineer (FDE)" requires a master's degree and on-site manufacturing presence, at 8,000–16,000 per month — a maximum gap of nearly tenfold versus Zhipu. Behind the gap lies differences in platform base, client quality, and pricing model. So when looking at domestic opportunities, don't first check whether the business card has the three letters "FDE" — measure it with the ruler from Chapter 8: does this company charge by results, or by headcount?

Next, practice translation: most engineers' technical foundation is good enough, but what's scarce is the craft of "translation" — specifically three kinds: translating business problems into technical problems (Chapter 2), translating technical solutions into language executives understand (Chapter 3), and translating on-site experience into knowledge the team can reuse (Chapter 7). To practice these three, class is worse than the field: shadow one pre-sales, do one on-site stint, train one real user, then see in which discomfort you grow fastest.

On interview prep, rewrite your résumé into a "client-result-oriented" form. The principle was stated earlier; to emphasize once more: every technical achievement in your résumé must complete the last mile into the client's language. "Built a RAG (retrieval-augmented generation, letting the model look up material before answering) system" is engineer language; "the RAG system I built cut customer-service first response from 4 hours to 8 minutes, and at renewal the client proactively asked to expand" is FDE language. At the same time, prepare two kinds of stories: one experience where you established order amid unclear requirements, and one honest failure — Palantir-system interviewers have an obsession with "tell a real failure," because the essence of this work is advancing amid uncertainty, and those who won't admit failure have no capacity to evolve.

When choosing a company, ask three questions in return. One: "What is your product platform?" — an FDE without a platform base is pure labor outsourcing. Two: "How does on-site learning flow back into the product?" — ask them to tell a recent instance of something precipitated from the site into a product feature; if they can't, that's a problem. Three: "Who does the FDE report to?" — reporting to the product or engineering line usually means the model is taken seriously; reporting to the sales line, beware of becoming a labor pool for pre-sales.

All the above is written for engineers. What about those who don't write code? Positions exist, and Palantir long ago reserved them: in the two-person combination of section 1.6, the Deployment Strategist with the codename "Echo" does work that is not about writing code — understanding the client's mission, stakeholders, and adoption path. Looking outward along this line, Chapter 4's change management, Chapter 5's "train the trainer" mechanism, the knowledge-operations team at Dewu (得物) that burrows into business teams to carry away tacit experience, and Chapter 3's technical content marketing — all are entry points for non-engineering backgrounds. The common requirement of these roles is exactly the old trade of those from operations, consulting, and content: straightening out human affairs.

The last question can only be answered honestly: how far can this path go? No one has finished it. The role is too new; a complete cycle has no sample yet, and only the structure is visible. The consumption end is real — the travel intensity and the rhythm defined by client urgency mentioned earlier both weigh heavier with age and family stage. The value-add end is also real — client trust, industry judgment, and cross-organizational prestige all compound precisely with years of service.

There are faintly three exits: 1) reflux into the product line — those who boiled the on-site into a platform are the natural candidates for product heads; 2) start your own company — nearly a third of Palantir's product managers started their own companies after leaving; 3) go to the client side — after reading those state-owned-enterprise stories in Chapter 8 you'll know that what the client side most lacks is precisely people who understand the vendor's playbook. Which one holds, only time five years out will tell. All that can be confirmed now is one line: this profession prices "the boiling," but on the premise that you are at a company that treats on-site learning as an asset — otherwise what boils out is merely years of service.

## 1.9 The FDE's Common Toolbox

Finally, here is the current panorama of this role's tools. Tools will become obsolete, but the capability layers behind them will not. Five layers, from the ground beneath your feet to what's behind you.

- **Platform base layer.** The premise on which the FDE model stands is "bring the platform to the site," otherwise it degrades into custom development. Palantir's Foundry and AIP have at their core what is called the "ontology" — modeling the enterprise's data, logic, and actions into a semantic layer, letting AI run on a "business-aware" foundation; OpenAI's model interfaces and agent toolchain; Sierra's agent platform. When evaluating any FDE opportunity, the thickness of this layer is the first priority.

- **AI engineering layer.** The daily craft after 2025 includes: prompt engineering and context management; retrieval-augmented generation (RAG); evaluation systems: building a quantifiable yardstick for fuzzy business quality — this is the signature skill that distinguishes the AI-era FDE from the traditional implementation engineer; agent architecture: tool calling, multi-agent collaboration, keeping a human in the loop at key points; and engineering optimization of cost and speed.

- **Data and integration layer.** Almost every FDE project spends its first week battling this layer: data pipelines, enterprise-system connectors, permissions and authentication, vector databases for AI to look things up, and data governance and desensitization (hiding sensitive information). Qureshi also has a piece of experienced advice: among enterprise data problems, 95% are access, cleaning, and association — not analysis at all; 70% of project progress gets stuck in this layer, yet it is invisible in the demos.

- **Delivery and collaboration layer.** Working within the client's security boundary means "dual adaptation": you must be able to use your own modern toolchain and also bend to the client's environment — it may be an intranet physically isolated from the internet, it may only allow deployment in the client's cloud, it may not even let you reach code-hosting sites. Containerization (the technique of packing the environment to carry it with you), infrastructure as code (managing the server environment with code), and contingency plans for "being able to get the environment running even in a disconnected meeting room" all belong to this layer.

- **Knowledge-precipitation layer.** This is the most easily overlooked layer, yet the one that decides whether the team can escape "revenue growing linearly with headcount": playbooks, component libraries, deployment checklists, and the writing habit of rewriting "one client's solution" into "one class of clients' pattern." Chapter 7 will expand on it specifically.

The five-layer toolbox together is the complete silhouette of this role: a platform as the base, engineering as the craft, accountable for the client's results, while connected to the company's product line.

In the next seven chapters we enter the heart of the methodology, beginning with the most original choice of a project — how to make sure you are solving the right problem.
