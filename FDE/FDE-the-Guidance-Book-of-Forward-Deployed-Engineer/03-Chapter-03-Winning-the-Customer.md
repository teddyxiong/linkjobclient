---
title: "Chapter 3 · Winning the Customer"
original_title: "第 3 章 赢得客户"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "https://fde4.ai/book/03-%E7%AC%AC3%E7%AB%A0-%E8%B5%A2%E5%BE%97%E5%AE%A2%E6%88%B7"
source_file: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer/blob/main/03-%E7%AC%AC3%E7%AB%A0-%E8%B5%A2%E5%BE%97%E5%AE%A2%E6%88%B7.md"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [第 3 章 赢得客户](https://fde4.ai/book/03-%E7%AC%AC3%E7%AB%A0-%E8%B5%A2%E5%BE%97%E5%AE%A2%E6%88%B7)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

# Chapter 3 · Winning the Customer

> "Enterprises buying AI is like your grandmother getting an iPhone — she wants to use it, but she needs you to set it up for her."
> — a16z (Andreessen Horowitz)

## 3.1 Screen for Your Lighthouse Customers

The first lesson of user acquisition for internet products is screening seed users: 100 users who love you beat 10,000 users who think you're merely okay. The equivalent in the FDE world is the lighthouse customer — a customer that gives you not just revenue, but a signal that broadcasts to the entire industry.

The strategic value of a lighthouse is multiplied under the FDE model, for three reasons.

First, the lighthouse is the strongest sales asset. Enterprise customers have long decision chains and a high aversion to risk, so peer endorsement is the shortest path to persuasion.

The origin story of legal-AI company Harvey is textbook: the first major customer it announced, in February 2023, was Linklaters, a top-tier global law firm with 3,500 lawyers across 43 offices. Once that lighthouse lit up, big clients like PwC and Cleary Gottlieb followed in quick succession — the legal industry cares most about pedigree, and landing Linklaters was the equivalent of getting a pass to the entire top-tier law-firm market. Palantir's early history mirrors this: the CIA was its most demanding and most valuable endorser, and the intelligence community's trust later became the key that opened the doors to Wall Street, manufacturing, and government markets.

The process by which Harvey lit this lighthouse was itself an FDE lesson.

In November 2022, Linklaters formed a dedicated group — the Market Innovation Group, led by partner David Wakeling — to quietly trial the product of what was then an obscure startup. They didn't watch your demo; they put it straight to work across the whole firm. By the end of the pilot, 3,500 lawyers had posed some 40,000 real-work questions to the system, spanning 250 practice areas and 50 languages. Wakeling's verdict became the line quoted repeatedly across the legal world: "I've spent 15 years in legal tech, and I've never seen anything that could be this game-changing." Another partner demonstrated a concrete scenario to the press: asking the system to prepare a ten-page package for a US client on "how to open a bank in Luxembourg" — "and it actually did it." (Source: Appendix C)

Second, the lighthouse determines your product's DNA. Under the FDE model, on-site learning flows back into the product — meaning your first ten customers are, in effect, helping shape your product. Pick the wrong lighthouse and your product gets steered toward a direction with no generalizability. a16z's first piece of advice to startups — "sell smart" — is exactly about this: a young company can't serve everyone, so choose an Ideal Customer Profile (ICP) that at least shares common ground in system environment and use cases, so that the learning from every deployment compounds instead of canceling out.

Third, the quality of a lighthouse matters an order of magnitude more than its quantity. Your capacity is naturally scarce — an elite team can deeply serve only a single-digit number of customers at the same time, and one wrong pick costs you not "a missed deal" but a top-tier team bogged down in a quagmire for half a year. So the three high-risk signals from Chapter 2 (no business owner accountable, refusal to provide real data, cosmic-scale demands) must still be checked here, plus one lighthouse-specific test: from the very start of the collaboration, agree on whether — once successful — they are willing to step forward: co-publish a case study, appear and testify at industry conferences, host visits from your prospects. A lighthouse unwilling to speak publicly on your behalf is worth at least half as much.

### Beware the "Requirement Locust"

When building internet products you must beware the "product locust" — early users who swarm in, use you up, leave, and mislead your product direction. The corresponding species in the FDE world is the "requirement locust": clients with ample budget and ravenous demand who drain your team without producing any compound return. Three identifying traits:

1. Their needs clearly diverge from your company's strategic direction, so even if you build them, no reusable capability gets accumulated;
2. They treat the FDE as cheap outsourcing, assigning work by headcount rather than aligning on outcomes;
3. Internal politics consume enormous energy, and your main job becomes helping one department prove another department wrong.

Saying no to requirement locusts is hard — their contract value is often tempting. But Barry's calculus is this: a wrong pilot burns not just the immediate cost, but your team's time, morale, and the product compound interest that could have grown on the right customer.

## 3.2 Start with the Dumbest Thing

The famed incubator YC has an old adage: "Do things that don't scale." For example, the founders of the home-sharing platform Airbnb once went door to door photographing hosts' homes, and the founders of the online-payments company Stripe personally helped users install their own software.

When McGrew was asked on the Lightcone podcast about the relationship between FDE and this old adage, he gave a precise formulation: the FDE model is doing things that don't scale, at scale.

This line lays bare the philosophical undercurrent of FDE customer acquisition: in the enterprise market, there is no scalable shortcut to earning trust — only the dumb way. Three layers, each building on the last.

Layer one: show up in person. On a16z's checklist of advice for forward-deployed teams, the last item is just four words: be there in person. The reason: "cliché, but clichés become clichés because they're true" — being there improves not just sales but, when mapping a customer's internal power structure and driving adoption of new tools, multiplies the odds of success.

Enterprise customers' trust is priced by "number of meetings" and "shared experiences." Remote meetings can get you a familiar face, but trust only grows after you've weathered things together.

Layer two: get your hands dirty. OpenAI's FDEs went into Iowa farm fields alongside agronomists; Palantir's engineers lived for weeks at a time on oil-drilling platforms and aircraft final-assembly lines; Harvey's FDEs ran adoption demos partner by partner inside law firms. None of these scenes is "efficient," yet each produces something remote communication never can: a felt sense of the customer's situation. That firsthand feel translates directly into solution quality — only after you've stepped in the mud of a farm field do you understand why that seemingly perfect phone interface is unusable in harsh outdoor light.

Layer three: be a servant first, a mentor later. The most common early mistake an FDE makes walking in is the posture of "we're here to save you." Get the posture wrong and every intelligence channel slams shut.

The right order is to do the most inconspicuous service first: fix a data problem for the client's analyst, fill in an interface document for the IT department, automate a weekly report for the business team. These "dumb tasks" buy three strategic assets: a true map of the organization's interior (who calls the shots, who is trusted, who is the hidden key node), the truth about the data environment (which data is trusted, which is decoration), and — most important — the identity credential of "this outsider is one of us." Only after that identity is established does what you say start to carry weight.

The end of the dumb way is not staying dumb forever. Chapter 7 will cover how to distill these dumb efforts into a repeatable playbook — but before scaling, you must first wade through the mud to blaze the path worth replicating.

## 3.3 The Trust Dividend: the Endorsement Lode of flagship Customers

Enterprise procurement is a market of "extreme information asymmetry and extreme cost of failure," where decision-makers rank their trust in information in a clear hierarchy: the vendor's own marketing ranks below analyst reports; analyst reports rank below peers' public case studies; peers' public case studies rank below peers' private recommendations. The last tier — "someone I know used it and says it really works" — crushes every other channel in conversion efficiency. And the FDE model happens to be the best machine for producing "private-recommendation material": what you deliver is not a software license but a sentence from the client executive at a peers' dinner — "they really know this stuff."

Mining this lode takes action at three levels.

Layer one: make the delivery a "story worth telling." The precondition for a client executive to vouch for you is that your delivery can be told as a story that makes him look good in front of peers. This requires the delivery to carry three narrative elements: a concrete number ("chemical usage down 70%," "anti-money-laundering investigation from hours to minutes"), a concrete person ("our agronomist worked in the field with their team"), and a concrete contrast ("what used to take three months took five days this time").

When the delivery ends, proactively help the client's internal champion assemble this narrative — one page, three diagrams, a version that can be told in 30 seconds. How finely the material is made determines whether others retell it faithfully.

Layer two: turn the client's success into the client's social currency. Pharmacy chain Walgreens is the sample: after deploying to 4,000 stores in eight months via the Bootcamp model, it became a star at industry conferences; market-research firm J.D. Power went further — after attending Palantir's Bootcamp as a customer, it began running Bootcamps for its own customers. (Source: Appendix C) This is the ideal state: the customer shows off your methodology as its own industry leadership. The endorsement upgrades from "thank you" to "proud to use you."

Layer three: beware the endorsement's "backlash mechanism." The enterprise market holds grudges. One high-profile customer's failed delivery spreads far faster than ten successes — because failure stories go down better with drinks. This is exactly why the "rejection mechanism" of Chapter 2 and the "activation discipline" of Chapter 4 matter so much: the Achilles' heel of lighthouse strategy is not failing to find a lighthouse, but letting the lighthouse go dark in your hands.

## 3.4 Map the Customer's True Net Worth with Data

Before and after an FDE walks in, there is a move called "onboarding due diligence" (hereafter "due diligence"): before writing the first line of code, use a structured method to find out the customer's entire net worth. A complete due-diligence checklist contains five maps.

- **Data map:** what data sources the customer has, who owns each, what quality they are, who controls permissions, and whether there is dark data you could never imagine — a spreadsheet an old employee hoards privately, a report that only circulates in email, a paper ledger. The point is not "what exists" but "which is trusted." In almost every organization, the official data source and the data source employees actually trust are not the same; the latter is what you must connect to.

- **Process map:** the real operating picture of the target business process — not the version in the process documents, but the version observed through shadowing (following the user like a shadow to observe their real work), including all the steps, exceptions, and workarounds that never made it into the docs. Specially mark three points: the step that consumes the most time, the step whose failure costs the most, and the step charged with the most emotion. These three points are usually the richest vein of value.

- **Organization map:** who initiates, who pays, who uses, who can veto, who is the uncrowned king. The most common cause of death for enterprise projects is not technical — it's miscalculating the organizational account: your internal champion is too junior, or too senior (senior enough to have no time for you), or the right person wasn't brought in. Especially find the kind of "knowledge hub": low rank, but everyone goes to them when they hit a real problem. They are both your best source of requirements and the seed nodes for later rollout.

- **System map:** the true face of the technical environment — the list of systems to integrate with and their interface status, security and compliance boundaries, change-management process. The system map decides your deployment architecture and schedule. Many projects' timelines are bankrupt on day one because no one asked clearly: on the client side, releasing a version takes a six-week process.

The last map is the most sensitive and the most critical: the political map. It answers three further questions: whose cheese does this project move, is the process targeted for automation a source of power for some department, and whose job will look redundant after the solution lands. Imagine a concrete scene: on the day of the go-live demo, the business department that cooperated throughout is applauding, while in the corner a manager from another department says nothing — the process he is responsible for maintaining is exactly the one you automated away. *The GenAI Divide* report lists "employees unwilling to adopt new tools" as the number-one roadblock, and the root of the resistance is mostly not laziness but fear — fear of being replaced, fear of being proven incompetent, fear of losing the meaning of one's existence.

The function of the political map is to identify the carriers of these fears in advance and design them a "new path" in the solution, not a "dead end." The renewal topic of Chapter 5 will return to this: the person you designed as a "victim" becomes the most determined opponent at renewal time.

Only when all five maps are complete have you truly "walked in." This due diligence usually takes one to two weeks, conducted separately by "Echo" (the business team responsible for user research) and "Delta" (the on-site engineer team), reconciling daily. It looks like pure cost, but the account is reckoned this way: the two weeks of due diligence save three months of mad sprinting on the wrong battlefield.

## 3.5 Technical Content Marketing: Build a Trust Engine That Outputs Continuously

Content marketing is the classic weapon for internet companies' customer acquisition. The customer-acquisition logic of an FDE company dictates a unique positioning for its content marketing: not chasing traffic, but pursuing "pre-sale of professional trust."

The way an enterprise customer finds you is not by seeing your ad, but: hitting a hard problem, searching and asking around, discovering that some company has published an extremely professional public treatment of this problem, and concluding — "they get it, go to them." Content here plays the role of "qualification screening" at the very front of the customer's decision chain. Palantir publishes scenario-based technical articles year-round; OpenAI and Anthropic turn enterprise customer cases into detailed technical narratives; a16z's *Trading Margin for Moat* set the tone for the entire field — none of these are brand promotion, they are carefully cultivated trust assets.

FDE companies' content marketing has three articles of war that distinguish it from conventional enterprise content.

- **Article one: write from the "trench perspective," not the "booth perspective."** Conventional enterprise content talks about how strong the product is and how big the vision; FDE content talks about how hard the problem was and how we waded through it. Why did former Palantir engineer Barry's *Understanding Forward Deployed Engineering* go viral in the industry? Because it wrote only about what you can't see from the booth: the waste of reinventing wheels, the negative-margin pilots, the burned-out engineers — and this "airing our dirty laundry" piece became the best sermon for the Palantir model. The truth from the trenches carries inherent force, because readers can tell apart: who is reciting marketing scripts, and who is describing the reality they live in every day.

- **Article two: open-source your methodology to manufacture "the qualification to be cited."** Publishing how you do discovery, validation, and delivery — in the short term you teach competitors, but in the long term you define the industry standard. When the entire industry's customers start asking questions in your framework ("how do you build your evaluation system?" "what does your deployment checklist look like?"), you move from supplier to examiner. In 2026, practitioner open-source communities like OpenFDE emerged and rapidly aggregated attention, exactly showing that this industry's hunger for knowledge is far from satisfied; whoever systematically satisfies it first seizes the definitional power. The writing of this book is, in a sense, also a practice of the same logic.

- **Article three: make the client's internal champion the hero of the content.** The byline logic of case articles is subtle: the protagonist should be the visionary manager on the client side, while your team is the "partner who helped him succeed." Giving the champion a stage is handing an "invitation to become him" to the counterpart role in the next potential customer.

Beyond content, two other kinds of assets can "go to work" long-term on the desks of the customer's engineers.

One kind is open-source tools and components. The initiator of enterprise procurement is the executive, but the technical veto power sits with the engineers. Open-sourcing the general-purpose modules distilled from delivery — evaluation frameworks, connectors, deployment templates — is planting trust votes on the technical end of the decision chain. Anthropic turned the Model Context Protocol (MCP, an open standard letting models connect to external tools) into a public spec, and FDE delivery at the customer site is built on this protocol — the first lesson the customer's engineers learn is Anthropic's tech stack. Lean teams have a lighter version too: a quick-start kit that lets a customer engineer connect sample data and get it running in an afternoon is the best sales engineer.

The other kind is presence in the engineer community. In the target industry's technical communities, your engineers show up consistently — answering questions, sharing hard-won lessons, submitting code. The conversion path of this presence is long, but it reaches exactly the people who hold the technical veto. For an FDE company, hiring and customer acquisition are one and the same act here: the best candidate pool and the best customer leads often come from the same community.

## 3.6 Clearing Procurement, Legal, and Security Review

The "gates" of the enterprise market are the procurement department, the legal department, and the security review committee. A large number of technically successful FDE projects die inside these three gates — and die without any technical dignity: the contract terms fall apart, the data-processing agreement stalls, the security questionnaire drags into its fourth month.

The key to clearing them is how you view these three gates: treat them as obstacles and you crash in the last mile; treat them as part of delivery and you gain an edge instead — most tech companies answer the security questionnaire into its fourth month, but if you submit in two weeks, you win.

Procurement gate: give them tools they can "report upward" with: clear phased pricing (so there's a step down on price cuts), comparable market baselines (so approval has a basis), measurable outcome commitments (so the charge of "overpaid" cannot stand). The pay-by-result model has an unexpected advantage here: what procurement finds hardest to approve is "spending you can't say what you'll get," whereas a quote like "pay $X per ticket resolved" procurement understands at a glance.

Legal gate: polish the data-processing agreement like a product. The legal focus of enterprise AI projects is highly concentrated: will the data be used to train the model? where is it stored, who can access it? who pays if there's a security incident? who's liable if the output is wrong? Smart teams productize the standard answers to these questions — preset agreement templates, model-use statements, tiered liability frameworks. Palantir's survival in the intelligence community rests on building "permissions and audit" into the product core (who viewed what data, fully traceable); Anthropic, in its work with financial clients, made "traceable, auditable" a selling point. The trust at this gate is mainly designed in advance through product and process; what you scramble for at the negotiation table is very limited.

Security review gate: use a "pre-answer whitepaper" to grab two months. The efficient team's move is to actively maintain a security whitepaper: deployment architecture diagrams, data-flow diagrams, encryption and permission schemes, compliance certifications, and the standard answers to every question ever asked in past reviews — 80% of most questionnaires can be copied straight out of it. Your response speed itself is the most direct signal of security maturity.

## 3.7 Ecosystem Bundling: Standing on the Shoulders of Channels

The ecosystem strategy of the FDE era is to borrow the shoulders of three kinds of partners.

Category one: cloud vendors and big platforms. AWS, Microsoft Azure, Google Cloud are themselves among the master entrances to enterprise AI procurement. Entering their co-sell systems is like getting a pass straight onto the enterprise procurement list. The cloud vendors' marketplaces also solve a practical pain point: customers can use their existing committed spend to buy your service, bypassing the procurement process for a new supplier.

Category two: consulting firms and system integrators. This is the most dramatic ecosystem shift of 2026. On the founding-partner list of OpenAI's newly established delivery entity "The Deployment Company" sit, side by side, Bain & Company (a company entirely separate from Bain Capital), Capgemini, and McKinsey — the world's largest consulting and integration giants turned from "potential competitors" into "equity-allied partners."

The logic is clear: model companies have the technology, consulting firms have client relationships and industry depth, integrators have the on-the-ground delivery manpower — only when the three merge can they swallow the giant "AI transformation" market whole. For a startup the lesson is two-way: beware the consulting giants eating your delivery layer under the name of ecosystem, but also see the real dividend of allying with regional and industry-specific integrators — in their hands sits client relationships you couldn't build in three years.

The same script played out in China almost simultaneously. In July 2026, Volcano Engine (under ByteDance) and EY, one of the Big Four accounting firms, signed a strategic partnership: jointly building solutions around core scenarios like data governance, financial management, and marketing growth. Most notable, the two sides plan to stand up a thousand-person-scale FDE team to "build an AI-native delivery team." Tan Dai, president of Volcano Engine, put it plainly: the FDE team must "put engineers with both technical and industry backgrounds up front at the customer site, deeply participating in the full process of solution landing." On one side, consulting giants sitting on client relationships; on the other, model platforms short on industry depth — FDE became the weld point between the two. (Source: Appendix C)

Category three: the customer's customers. The highest form of bundling is embedding into the customer's own value chain. After J.D. Power attended Palantir's Bootcamp, it began running Bootcamps for its own customers — Palantir's capability spilled outward along J.D. Power's client relationships, and the customer-acquisition cost approached zero.

When designing your delivery, you can preemptively embed this "redeployability": can this solution let the customer go serve its own customers? If yes, you've embedded yourself into the customer's business model.

## 3.8 Scheduling: Who Goes First Is Itself Strategy

Scarcity can manufacture appeal — invite-only access and waitlists are classic internet-product plays. The FDE scheduling problem is opposite in shape but identical in principle: your capacity is always smaller than demand, so "who goes first" itself becomes a strategic tool.

First, the brutal reality constraint. A qualified forward-deployed squad (one business-side plus two or three technical-side) can deliver at high quality, at the same time, usually no more than two projects. Another set of industry numbers corroborates this: one customer-success manager can handle eight to twelve customers simultaneously, while an FDE deeply embedded serves only one to three, and a single customer's deployment often means thirty to sixty days of daily on-site presence. OpenAI started with just 2 engineers in its early days, Sierra's deployment cycles are measured in months, Harvey's single-firm deployment takes six to nine months — elite delivery capacity is a naturally scarce resource.

Capacity scarcity can't be avoided; what you can manage is what price you put on that scarcity.

The first red line of pricing is contract size. Investor Tomasz Tunguz ran a blunt calculation: pairing a $200,000-a-year FDE with a $10,000 contract never adds up — this model only begins to work at roughly $100,000 per contract and above. All the scheduling calculations discussed later must first clear this floor. Translated to the China market, this red line roughly corresponds to projects in the several-hundred-thousand to million-RMB range — you can check the 10-person squad calculation in section 7.8 against your own books.

The first principle of scheduling is to rank by strategic value, not by contract amount. The decision matrix has only two dimensions: this customer's lighthouse value (strength of industry signal), and this customer's learning value (how much reusable capability can be accumulated). A customer high on both dimensions can even — should — be subsidized with resources and prioritized; Barry recalls Palantir doing free pilots in its early days and burning millions of dollars, betting exactly on this matrix. A big contract low on both dimensions is the most dangerous of all: the money looks plentiful, yet it ties up the elite team for half a year.

The second principle is to "productize the wait." If a customer waits three months to get you on-site, don't let those three months drain away: give them a data-prep checklist (speeds up on boarding), advice on organizational warm-up (which few key people to lock in first), a light remote diagnosis (keeps the temperature up, sweeps for mines early). Manage the wait well and the post-onboarding delivery cycle shrinks by a third — the queue turns from a burden on customer experience into a component of delivery quality.

The third principle is to never promise parallelism beyond capacity. Your delivery quality rests on the continuous focus of the same team — every project carries a whole context of the customer, and each switch means reloading it once; the drag of multi-project parallelism is far greater than imagined. Rather let sales sell "our schedule is booked to next quarter" as scarcity (which often even raises the price) than let the team sprint itself ragged across three customers. The better business gets, the easier it is to succumb to taking more orders. And the cost of collapsing from over-taking is usually far greater than the cost of one fewer order.

## 3.9 Writing the Proposal and the Validation Plan

The highest-priced text in the enterprise market is the proposal and the proof-of-concept (PoC) plan.

The bad news: most technical teams' proposals make the same mistake — writing all about "what we will do" instead of "what you will get." A good FDE proposal follows a strict inverted-pyramid structure.

Layer one: the business result, in one paragraph. The proposal's first paragraph must be the business result in the customer's language: "Within eight weeks, cut your anti-money-laundering investigation average handling time from 4 hours to 15 minutes, freeing investigation capacity equal to 2.5x your current team." Without this sentence, the client executive won't get past the rest of the content.

Layer two: the value-validation path, how you prove it was achieved. State the acceptance metrics, measurement method, baseline data, and the exit mechanism for each stage. The signal this layer sends is "we dare to be tested" — in an enterprise market wounded by over-promising, daring to be tested is the rarest of sincerities.

Layer three: the delivery method, how we do it. Only here does the technical plan come in, and it must be written so non-technical readers can follow: architecture diagrams with business annotations, milestones with decision points. Especially state what the customer must contribute — data access, key people's time investment. Writing clearly what the customer should do both defuses risks early and screens the customer.

Layer four: risks and countermeasures, we've thought through how we might die. Most proposals avoid risk, as if mentioning it is bad luck — yet mature buyers choosing a vendor are exactly watching whether he dares spell out the ways to die: what if data quality falls short, what if key people change, what if accuracy doesn't hit the threshold. This layer is the proposal's trust amplifier, and it is also the textual embodiment of Chapter 2's "reject the expensive PoC graveyard" idea.

The validation plan has a special feature: it is the carrier of the "graduation standard." The plan must state the time cap, acceptance metrics, and the two follow-ons of graduation versus breakup. A vaguely written validation plan is signing the construction permit for a PoC graveyard.

This "dare to be tested, write the standard dead" approach has a precedent a decade older than the AI era. Data-analytics company Looker, from 2013, did heavy pre-sales implementation within the free trial period, with one principle: the demo is the PoC — always ask the prospect for a real dataset to play with, never perform with carefully prepared sample data. At the same time they calculated to the end: about $25,000 per customer per year, two thousand customers is $100 million in annual revenue, enough to touch the IPO threshold. Its then-CEO put it plainly: if you can't say whether you need two thousand or a hundred thousand customers, you're burning venture capital's money.

How hard the validation plan dares to be written depends on how clearly the books behind it are calculated.

The buyer's side standards are also hardening in the same direction. When HR-software company Rippling selects vendors, it wrote "the vendor must invest dedicated engineering resources" into a hard requirement — the customized interface workflows they need can't be built without the vendor's engineers on the ground. Collaborative-docs company Notion is the same: itself an AI-first company, after weighing it still chose to buy rather than build, and its RFP listed five criteria, the last being: not just a vendor, but a team that can build together. Facing such buyers, a beautifully written proposal isn't enough — Chapter 2's "three gates must be passed at the customer site" begins the moment you bid.

## 3.10 From On-site to Remote: the Boundary of Hybrid Delivery

FDE delivery has undergone an important evolution in recent years: from pure on-site to a hybrid model of "remote-first plus on-site at key nodes." Palantir's official position also confirms that many projects now execute mostly remotely, with on-site concentrated at key milestones.

The rhythm design of the hybrid model is a craft. Which things must be physically present? Experience boils down to three types: 1) the early relationship-building phase (first meeting, shadowing, trust-building with executives — trust can't be built through a screen, it requires meeting); 2) high-intensity co-creation (Bootcamp-style joint building, whiteboard sprints on key architecture decisions); 3) politically sensitive periods (solution rollout, department coordination, change management — at these moments you need to read the air in the room).

Which things are actually better remote? deep coding, documentation distillation, routine iteration — work that needs uninterrupted flow.

The hybrid model has two hidden dividends. One is cost structure: on-site is among the largest variable costs in FDE delivery; a sensible hybrid ratio can open up ten points or more of delivery-margin space.

Two is talent sustainability: a team on the road half the year has significantly higher burnout; on forums, practitioners' complaints about travel top the charts. On job-review sites, Palantir's FDE role ratings write this split plainly: compensation and benefits 4.0 (out of 5), work-life balance only 2.8, with frequent complaints about a work rhythm constantly interrupted (third-party aggregated figures, not verified line by line against the original page). The hybrid model isn't laziness; it's the safeguard of organizational endurance.

But the line must be drawn: a project that never meets in person loses not just the relationship but also the first-hand knowledge of the site. Remote maintains existing trust and context, and those must first be created in the physical world.

Push the boundary one step further and you reach going overseas. American companies' globalization is demonstrated by the giants: OpenAI's FDE hiring map spreads from San Francisco and New York to London, Tokyo, Singapore, Abu Dhabi — the team's geographic distribution precisely sketches the global map of enterprises' AI paying power. The China context is a different logic: the past dilemma was "product DNA" — domestic vendors long did highly customized project-based business, mismatched with the standardized, productized demands of overseas markets. But the FDE model offers a reverse perspective — China's engineer delivery culture is precisely the closest to FDE's requirements; the real question is whether the platform foundation beneath them is thick enough.

A local reference frame has already been quietly running for a long time. From 2023, 53AI has charged by results — you pay only when the client's business genuinely improves, earlier than even its Silicon Valley peers. Tuition was paid too: early on it let prompt engineers solo the delivery, who couldn't fathom the client's business, and the founder spent half of a year and a half putting out fires everywhere; only after switching to having business experts go in first to fully absorb the business, then bringing engineers in to build, did the situation turn. The hardest evidence came from a controlled experiment: at a top online-education client, the "sales plus agent" group's output reached 3x the purely manual group. More worth recording is the client's reaction — after the per-head efficiency went up, the client didn't lay anyone off, but used the same people to grab more quality leads in the market. (Source: Appendix C)

On the specific strategy of going overseas, FDE has one innate advantage and one innate constraint. Advantage: the "lighthouse to endorsement" logic works equally in the global market, and developed-market enterprise customers' willingness to pay and contract spirit are more mature. Constraint: FDE is a heavily localized business — language, time zone, compliance, local trust networks, each demands a local team rather than remote support. This means FDE's overseas cost structure is naturally higher than SaaS going overseas, and the pace must be more restrained: first use a remotely deliverable product to gain a foothold, then in key markets assemble local delivery teams, country by country.

These ten things come down to one sentence: winning the customer is, in a market betrayed countless times, managing to make people believe. Signing the contract is only the entry ticket — next, the real hard battle begins: making the system live, making people use it.
