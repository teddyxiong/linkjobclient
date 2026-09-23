---
title: "Chapter 6 · Expanding Revenue"
original_title: "第 6 章 扩大收入"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "https://fde4.ai/book/06-%E7%AC%AC6%E7%AB%A0-%E6%89%A9%E5%A4%A7%E6%94%B6%E5%85%A5"
source_file: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer/blob/main/06-%E7%AC%AC6%E7%AB%A0-%E6%89%A9%E5%A4%A7%E6%94%B6%E5%85%A5.md"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [第 6 章 扩大收入](https://fde4.ai/book/06-%E7%AC%AC6%E7%AB%A0-%E6%89%A9%E5%A4%A7%E6%94%B6%E5%85%A5)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

# Chapter 6 · Expanding Revenue

> "The hallmark of a working FDE model is this: the amount of customization required for each subsequent client keeps shrinking."
> — Bob McGrew

## 6.1 The World of Free Validation

The internet economy turned "free" from a gimmick into a strategy. The FDE trade cannot avoid the "free" hurdle either — only the hurdle looks different here: in the era of enterprise AI, the free proof of concept is the most expensive kind of free there is.

Let us look at the scale of this free economy first. Palantir's Artificial Intelligence Platform (AIP) Bootcamp essentially turned free validation into an assembly line: clients bring real data, and within one to five days produce a deployable prototype, at zero or token cost. Starting from fewer than a hundred sessions in 2022, the number of sessions doubled year after year, reaching a peak in 2025 of nearly 6 sessions a day — counting several top engineers per session working for days, this is a free investment on the order of tens of millions of dollars a year. Barry, a former Palantir engineer, recalled the earlier days even more bluntly: "We burned millions of dollars running customer pilots, and the margin on many projects was literally negative infinity, because we did them for free."

Why does free validation work? Three ledgers add up.

The first ledger is acquisition. Traditional enterprise software acquires customers through a sales army: travel, banquets, bids, endless negotiations — money spent heavily and uncontrollably. The Bootcamp changed the playbook: instead of persuading the client, let the client persuade itself — an executive clicking through a system running on their own data beats a hundred slides.

Palantir compressed its sales cycle from nine to twelve months down to a few weeks, and its U.S. commercial revenue grew 137% year over year in a single quarter; the free Bootcamp is widely recognized as the main engine. Free validation is not pure cost: it swaps sales expense for engineering expense, and engineering expense compounds into product.

The second ledger: the power of risk pricing. McGrew's advice is that early-stage startups should proactively take on risk: "Pay us once it works." The confidence comes from faith in the product's strength, and also from a cool calculation — an enterprise client's biggest doubt about a new vendor is "can you actually deliver," and free validation is the solvent for that doubt. Once the doubt dissolves, the pricing power later actually returns to your hands: what the client buys is no longer "a gamble" but "a certainty already verified with their own eyes," and certainty can command a premium.

The third ledger: even failure should be made to pay. Free validation inevitably produces failures — this is common sense in portfolio investing. The difference lies in where the failure goes: a traditional sales failure leaves behind a pile of travel receipts; an FDE-style free validation failure leaves behind an understanding of an industry, a batch of reusable components, a set of evaluation data. As long as you have built the feedback loop from Chapter 7, even failed validations are making deposits for the company.

But free validation has one fatal precondition: you must design the day of graduation (conversion to paid) in advance — an upper bound on the cycle, acceptance metrics, and an agreement on converting to paid upon expiry. Once these are missing, "free" becomes indefinite residency. This leads to the next section.

## 6.2 The End of the Free Lunch

Free is the means, paid is the purpose; the conversion design determines the destination of all the free investment that came before. In the FDE world, "validation-to-paid" is the most critical finishing kick, and also the link where industry accidents happen most often — the "POC graveyard" mentioned repeatedly in earlier chapters is mostly not due to technical failure, but to the absence of a mechanism designed to "end."

From free to paid, there are five switches that must be designed up front.

Switch one: graduation criteria before kickoff. The requirement to "design the day of graduation" must be written down in black and white when the validation project starts, not patched in afterward. Palantir's Bootcamp takes this design to the extreme: on the schedule for days 4 to 5, right after "demo" comes "decision." Conversion is not a post-hoc event; it is a slot on the schedule.

Switch two: make the boundary of free explicit. The client must clearly know: until what day is it free, what scope is covered, and how is anything beyond that priced. A fuzzy boundary of free cultivates the expectation that "free is the norm"; by the day payment is due, the other side's feeling is not "starting to pay" but "being ripped off" — the same amount of money, with a different expectation, produces a vastly different experience.

Switch three: turn the internal champion into a salesman. This switch is the most counterintuitive: after a successful validation, the person who actually knocks on the budget door is not your sales rep, but the client's internal champion who witnessed the value with their own eyes. The moment he walks into the finance chief's office, what he can produce in his hands determines whether that door opens.

The finance chief looks up and usually asks only three questions — what does this bring us right now? What would we lose if we stopped? Why should we pay more next year? How many of these your champion can answer depends on how much ammunition you stockpiled for him during the free period. A meeting he cannot answer leads, when it ends, to a single line: "let's revisit next year."

Your job is to arm him: a one-page value report (numbers, comparisons, colleague testimonials), a Q&A set for handling finance's challenges, and an opportunity-cost statement of "if we don't continue." The internal trust of an insider's selling is something an outsider can never reach.

Switch four: plant the price anchor early. Start talking about value during the free period — "this system freed up about 120 person-hours for you this month." Let the value narrative run through the free period; by the time the quote appears, the client already has an anchor in mind. If the free period only talks features and not value, the quote is a jarring shock.

Switch five: design a dignified exit for "no conversion." Not every validation should convert; a forced conversion is a poison contract. For clients that do not meet the bar or whose timing is off, offer a "pause but retain" option: keep the data and configuration, agree on restart conditions, maintain light-touch contact. The enterprise market is small; today's "next year maybe" is often the big deal the year after — provided you say goodbye professionally.

The five switches together boil down to one sentence: design "free to paid" not as a perilous leap, but as a gentle slope.

## 6.3 Pay for Outcomes: Clients Pay for What They Get

The FDE pricing principle is straightforward: you collect as much as the value the client receives.

The dominant pricing model of the SaaS (subscription online software) era is per-seat — paying for "the right to use." This logic is being eroded in the AI era: when one agent can do the work of 10 people, charging per account becomes a joke — are you going to charge for 0.1 of an account? Hence "pay for outcomes" is rising; Sierra's charging by "resolved conversations" is the most prominent example: the client does not pay for software, it pays for "problems solved."

The evolution chain of pay-for-outcomes has four tiers; the higher you go, the closer to value, and the harder to execute.

Tier one, by usage: charge by token, number of calls, or volume processed. The advantage is clarity and measurability; the drawback is that it tracks cost rather than value — high usage could mean high value, or it could mean an inefficient system. Model APIs priced by volume are the industry's common baseline, but application-layer companies rarely use it as the sole pricing model.

Tier two, by task (per-action): charge by "completing one return processing" or "generating one compliance report." A step beyond usage; the unit of pricing begins to carry business meaning.

Tier three, by outcome: charge by "successfully resolved conversation" or "a bad debt recovered." Sierra's pay-per-resolution and some risk-control firms' share of losses recovered fall in this tier. The execution difficulty is attribution — the determination of "resolved" requires a standard both sides accept (this is exactly the commercial use of the evaluation system from Chapter 4: the technical evaluation system is simultaneously billing infrastructure).

Tier four, by value share: take a cut based on the financial value created for the client — costs saved, revenue recovered, capacity released. This is the ultimate form, closest to value, and also the hardest: it requires the client to open financial data, requires cycle-resistant trust, and requires strong value-measurement capability. Currently it appears only in some deeply bound, high-ticket scenarios.

Companies that pay for outcomes must dare to make their results public. The client data Sierra itself published forms an interesting report card (all figures below are vendor self-reported): property management company Funnel Leasing, resolution rate 94%; fintech company Ramp, 90%; mattress brand Casper, 74% with customer satisfaction up by more than 20%; WeightWatchers, about 70%, satisfaction 4.6 out of 5; even the worst-performing client still had 64%.

Third-party estimated pricing also surfaced: the annual contract threshold starts at about $150,000, with first-year budgets including deployment fees commonly $200,000 to $350,000, and large clients reaching the millions-of-dollars-per-year level; reportedly, the price per successful resolution is $1 to $2. In other words, every penny of the client's maps to one "problem actually solved" — Sierra dares to charge this way because its evaluation system can prove to the client that "it is resolved." Pricing method and evaluation system are here two sides of the same coin. (Source: Appendix C)

The ceiling of pay-for-outcomes is when "outcome" itself becomes revenue. The customer-service agent of curtain brand Hunter Douglas crossed this line: according to a customer case published by Decagon, it has over $1 million in revenue coming from conversations handled entirely by AI with never a handoff to a human — the customer service department, traditionally a cost center, for the first time has its own revenue attribution. One should be cautious about the numbers on vendor case pages, but the direction of "customer service becoming revenue" is real. (Source: Appendix C)

When choosing a pricing tier, there is a plain principle of judgment: the closer the pricing unit is to client value, the higher your pricing ceiling, but the higher your measurement and trust costs.

There is another consequence few calculate carefully: what the pricing tier does to your financial statements. Per-seat subscription gives stable, predictable revenue, and capital markets assign it a software valuation; pay-for-outcomes makes revenue fluctuate with the client's resolution volume, and collections rise and fall with the acceptance rhythm — the timing of revenue recognition, the days of accounts receivable, the predictability of cash flow, all get worse. Sierra's model effectively takes onto its own shoulders the usage risk that the client originally bore: if the client uses little, your revenue is little, while your engineering costs do not drop a cent per day. This is not an argument against pay-for-outcomes — its value to the client relationship was discussed earlier — but a reminder: companies choosing high-tier pricing must have cash reserves and a cost structure that can withstand revenue fluctuation. Pricing room is bought with volatility; first confirm you can afford the trade.

What does "writing value metrics into acceptance criteria" look like when it lands in a contract? An executable clause spells out at least five things:

- **Metric definition:** "Resolved" means the end user accepted the answer and did not escalate to a human within 24 hours.
- **Baseline and measurement window:** use the 8-week average before launch as the baseline, measured quarterly.
- **Determining party and data source:** based on a dashboard mutually recognized by both sides, not the vendor's unilateral report.
- **Dispute arbitration:** when data diverges, use third-party audit or joint review, not renegotiation.
- **Abort clause:** when the client's data foundation falls short and metrics cannot be measured, how costs and responsibilities are shared.

The most often omitted of the five is the last, and the most damaging when something goes wrong is also it. Missing any one of these, the "pay-for-outcomes" on the acceptance table degrades into "pay-for-relationship."

For readers in the China market, one more realistic footnote: domestic enterprise clients' acceptance of "subscription" remains limited to this day; "perpetual license plus implementation" and "pay by project acceptance" are still the mainstream. The pricing for the FDE model's landing in China often has to blend East and West: deliver and accept by stage (suiting project-based habits) + write value metrics into acceptance criteria (injecting the pay-for-outcomes gene). Pure subscription is the ideal here, while hybrid is the way to survive.

## 6.4 Deep Cultivation of the Installed Base: From One Department to a Whole Web

The enterprise market has an iron law: the biggest revenue growth is not in new clients, but inside old ones. The industry measures this with Net Revenue Retention (NRR, see Chapter 5); excellent FDE-driven companies keep their NRR above 120% year after year — even without signing any new deals, the installed-base revenue naturally grows by 20%. Palantir's commercial story is essentially a story of deep cultivation of the installed base: from one intelligence cell to the whole institution, from one factory to the whole group, from government departments to a commercial empire.

The playbook for deep cultivation has a vivid industry phrase: "land and expand." Landing relies on the previous five chapters; expansion has three directions.

- **Horizontal: from one team to adjacent teams.** You built an intelligent ticketing system for customer service; the after-sales department and technical support department next door are then your easiest next clients. In horizontal expansion, the most persuasive evidence is inside the client: same company, same data environment, a colleague from the next department testifying in person — this is the expansion with the least sales resistance, requiring almost no re-establishment of trust. Harvey's expansion in law firms follows this rhythm: enter through a single practice group, validate over six months in the field, expand horizontally to the whole firm.

- **Vertical: from the execution layer to the decision layer.** The initial project usually serves front-line executors; vertical expansion transmits the value chain upward: build analysis and early-warning for mid-level managers, build decision dashboards for executives. The significance of vertical expansion is not just revenue, but also safety — Chapter 5 said that a system loved only by the grassroots has no defender in budget season; a system that enters the executive's field of view enters the ranks of the organization's "fixed assets."

- **Depth: from auxiliary tool to core process.** The deepest expansion is to turn the system from a "helpful tool" into an "indispensable process" — from "giving advice" to "executing business actions," from "optional" to "part of the standard operating procedure." Every step of depth expansion comes with greater responsibility and a higher trust threshold, but it also builds the deepest moat: replacing a tool only takes swapping software, while replacing a system embedded in a process is like performing an operation.

Two "land and expand" report cards are worth reading side by side. Harvey started from a single law firm, Linklaters, and by 2026 its users exceed 100,000 lawyers and 1,300 organizations, covering most of the top 100 U.S. law firms, over 500 in-house legal teams and 50 asset management firms, across 60 countries; its Annual Recurring Revenue (ARR) rose from about $100 million in August 2025 to about $190 million in January 2026 — nearly doubling in five months. Industry surveys show 68% of responding law firms already use Harvey's agents in production, and heavy users save an average of 11 hours per week. Its valuation jumped four times within a year accordingly: $3 billion, $5 billion, $8 billion, $11 billion. (Source: Appendix C) And Palantir's NRR report card of 139% was already covered in section 5.1 — the two tables together illustrate the logic of deep cultivation: new contracts are driven by marketing, but revenue growth mainly grows from inside old clients.

There is also a quieter form of expansion: eating other line items off the client's budget sheet. According to a customer case published by Decagon, after ClassPass's intelligent customer service went live, the actual auto-deflected consultation volume was 10 times the expectation; then something small happened — its AI translation quality surpassed the localization vendor it had originally hired, whose contract was not renewed upon expiry. The client's budget did not grow; it just changed owners. Once depth expansion reaches a certain depth, your competitor is no longer a peer, but the other vendors on the client's budget sheet. (Source: Appendix C)

These expansions share the same rhythm discipline: expansion must be pulled by value, not by sales quotas. The health-score system from Chapter 5 has an offensive use here: departments with high usage depth and clear value are the next targets for expansion; and the moment in the client organization when "people see others using it well and come asking" is the golden window for expansion — at that point you are not selling, you are responding to demand.

## 6.5 How Anthropic and FIS Played the Financial Services Hand

The most instructive partnership in the 2026 enterprise AI market is worth seeing in full — Anthropic and fintech giant FIS jointly built a financial-crime agent.

FIS is a giant of global financial technology infrastructure, serving the core systems of banks worldwide. In May 2026, FIS launched its financial-crime detection agent, with the Bank of Montreal and Amalgamated Bank as first clients. What this agent does: compress anti-money-laundering investigations from hours to minutes — automatically assemble evidence across bank core systems, present to investigators ranked by risk, fully auditable and traceable throughout.

In approach, four moves lock together.

Move one, embed rather than deliver. Anthropic dispatched its applied AI team and Forward Deployed Engineers to embed directly inside FIS, co-designing with FIS's experts. Note: FIS is not the end client, but a channel-level partner — Anthropic's agent will enter the hundreds of banks behind it through FIS's products. This is one deal, and also the entry to a hundred deals.

Move two, knowledge transfer as a selling point. The official statement specifically wrote: the goal of embedding includes "transferring knowledge so FIS can independently build and scale more agents in the future." Writing "teaching the client" into the contract — this is both a preventive response to the worry of "vendor lock-in" (echoing the "vendor withdrawal reaction" of 5.1), and also an advanced form of binding: when the client's tech stack grows on your methodology, the cost of separation only rises.

Move three, auditability as a product feature. In financial compliance scenarios, regulators require every decision to be replayable. Anthropic made "fully auditable, traceable" a core selling point of the agent, not an add-on feature — this gives all regulated industries a template: what others see as compliance cost can be your reason to charge a premium.

Move four, ecosystem amplification. On the same day the FIS case was published, Anthropic also announced connectors and "ready-to-use" templates for financial services, plus a dozen similar partnerships — a single case is immediately abstracted into replicable product assets. Around the same time, word also spread in the market that it was forming an enterprise AI services company with Blackstone, reportedly around $1.5 billion in scale, going head-to-head with OpenAI's deployment company. (Sources above: Appendix C)

This hand has one more hidden thread — the vigilance of the CIOs. CIO.com, a tech media outlet for CIOs, quoted in its reporting the warning of Mahapatra, a strategy officer at a consulting firm: "The most structural problem in this model is who actually pays for the cost of forward deployment — a question CIOs should ask but mostly don't." Gartner analyst Alex Coqueiro predicted that before 2028, 70% of enterprises will be forced to abandon such solutions due to vendor cost and skill hollowing-out. This reminds us: in the revenue design of the FDE model, there is a long-term balance hidden — the value you create must continuously exceed the cost and dependency brought by your mere presence. Making money from "creating value" sustains a business; making money from "the client can't live without you" will eventually be settled by the client.

## 6.6 Turning Punishment into Reward: The Pricing Psychology of Usage and Scale-Up

Good mechanism design can turn punishment into reward. In the FDE business model, this wisdom applies to a subtle scenario: what to do when client usage exceeds expectations.

The crude approach is "punitive overage": once in-contract usage is used up, overage is billed at punitive high rates, or the system simply throttles and slows down. This was common in the early days of cloud computing, with disastrous results — clients actively suppress usage to avoid overage, usage drops, value shrinks, and at renewal it is a lose-lose. What you punish is exactly what you most want: deep usage.

The "turn punishment into reward" design redefines "overage" as "a badge of growth." Three specific techniques.

Technique one: tiered pricing, cheaper the more you use. The larger the usage, the lower the unit price — when the client goes over, what they receive is not a penalty but a discount. This is the same principle as tiered mobile-data pricing, but must be expressed clearly in the contract: what the client sees is not "use more and pay more" but "use more and the unit price is lower, we both win." Same bill, different narrative, different relationship trajectory.

Technique two: overage warning + proactive upgrade. When the system detects the client is about to exceed, it does not quietly bill, but proactively reaches out: "Your usage is growing fast; at this trend, moving up one tier would save you 15%." Turn the billing event into an advisory sales opportunity — the client feels cared for, not calculated against. This move has one hidden benefit: it forces your team to continuously watch the client's usage health score, naturally converging with the health-score system of Chapter 5.

Technique three: give the credit for "savings" back to the client. When usage optimization (model tiering, caching, batching) lowers costs, proactively compute this account for the client: "This quarter, through architecture optimization, we saved you about ¥X (in ten-thousand-yuan terms)." In the eyes of the client's finance chief, a vendor that helps you save money and a vendor that waits for you to go over are two completely different kinds of supplier — a vendor that proactively helps the client save money harvests, at renewal, a trust premium far exceeding that fee.

At the bottom of pricing psychology is a plain truth: the pricing structure tells the client every day "what kind of relationship we are." A punitive structure says "we're watching you"; a rewarding structure says "we grow together with you."

## 6.7 Build a Value-Measurement System to Punch Above Your Weight

There is one more infrastructure project that cannot be avoided: building a value-measurement system that runs through all client deliveries — turning "how much value we created for the client" from an impression into data, and from data into an asset.

This system gathers the scattered components from before into one place: the "economic test" is its input (the value hypothesis at project initiation), the evaluation system is its micro foundation (quality data), the health score is its operational interface (client relationship data), and pricing and scale-up are its commercial outlet (revenue data). Put together, it helps you do four things.

For the client, it is the evidence base at renewal and scale-up: every quarterly review, every renewal negotiation, every upgrade suggestion is backed by the value report this system outputs — hours saved, error rate down, throughput up, and the corresponding financial figures. Chapter 5 said value needs to be constantly re-proven; this system is the assembly line of "proving"; a renewal negotiation with data in hand, versus one based on feeling, closes at a noticeably higher rate.

For the company, it is the physical exam of delivery quality: aggregating value data across clients, you can answer questions vital to the model's survival — which scenarios have the highest value density (where should sales firepower be directed)? Which clients have the highest delivery cost (should pricing or approach be adjusted)? Which deployments are creating value and which are spinning empty (should resources be reallocated)? Without this system, your answers to these questions are all guesses.

For the product, it is the amplifier of feedback intelligence: value data combined with usage data is the hardest basis for product decisions — which feature yields the highest value (invest more), which feature nobody uses (cut it decisively), which scenario is repeatedly customized (a signal for platformization). This connects to the theme of Chapter 7: the value-measurement system is essentially the dashboard of the "field-to-product" feedback pipeline.

The fourth thing is for the market. The first time a potential client remembers you is often not meeting your sales, but bumping into a number — "chemical usage reduced by up to 70%," "investigation time from hours to minutes." These numbers that make the whole industry remember you all come from the accumulation of the value-measurement system. The most effective case marketing is not telling stories but showing data; and data does not appear out of thin air at the negotiation table — it must start being collected on day one of delivery.

Building this system, three practical suggestions for you. First, collect the baseline from day one — without pre-transformation data there is no post-transformation value proof, and the baseline exists only at the moment the project starts, gone forever if missed. Second, metrics must be co-built with the client — a metric he does not accept, however beautifully computed, has no negotiating force; the moment it is agreed at the kickoff meeting, the metric becomes your shared language. Third, restrain the number of metrics — three to five core metrics per client is enough; too many metrics equals no metrics.

The revenue chapter ends here, with one landing point: the revenue of the FDE model is, in the final analysis, the result of value creation.

The next chapter is the "last mile" of the whole book: how to make all this not depend on heroic individuals, but settle into replicable organizational capability — scaled replication.
