---
title: "Appendix A · Common Metrics an FDE Should Track"
original_title: "附录 A FDE 应当关注的常用指标"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "https://fde4.ai/book/10-%E9%99%84%E5%BD%95A-FDE%E5%BA%94%E5%BD%93%E5%85%B3%E6%B3%A8%E7%9A%84%E5%B8%B8%E7%94%A8%E6%8C%87%E6%A0%87"
source_file: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer/blob/main/10-%E9%99%84%E5%BD%95A-FDE%E5%BA%94%E5%BD%93%E5%85%B3%E6%B3%A8%E7%9A%84%E5%B8%B8%E7%94%A8%E6%8C%87%E6%A0%87.md"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [附录 A FDE 应当关注的常用指标](https://fde4.ai/book/10-%E9%99%84%E5%BD%95A-FDE%E5%BA%94%E5%BD%93%E5%85%B3%E6%B3%A8%E7%9A%84%E5%B8%B8%E7%94%A8%E6%8C%87%E6%A0%87)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

# Appendix A · Common Metrics an FDE Should Track

This appendix lays out a metric system spanning the entire FDE workflow, organized across four layers: delivery, customer, commercial, and organizational. When it comes to metrics, fewer and sharper beats more — tracking 3 to 5 core metrics per customer project beats a wall-to-wall dashboard.

## 〇 · Quick Glossary of High-Frequency Jargon in This Book

One plain sentence per term. If you get stuck reading the main text, flip back here.

- **FDE (Forward Deployed Engineer):** An engineer who embeds at the customer site and owns the outcome.
- **Ontology:** A semantic layer that models a company's data, logic, and actions so the model can understand them.
- **Bootcamp:** The client brings real data; in one to five days a usable prototype is built, and executives make the call on the spot.
- **Echo / Delta:** Palantir's two-person pairing — the former reads the client, the latter builds.
- **Proof-of-Concept Graveyard:** A pilot with no deadline, no metrics, and no referee that quietly dies along the way.
- **MVD (Minimum Viable Deployment):** Validate that value truly happens in a real environment with the smallest possible engineering investment.
- **Shadowing:** Sitting beside a real user and watching them get through a real day.
- **Lighthouse Customer:** A customer who sends a signal across the entire industry; the endorsement value exceeds the contract size.
- **Demand Locusts:** Customers with ample budget and ravenous demand who drain the team yet generate no compounding return.
- **NRR (Net Revenue Retention):** Whether the same cohort of existing customers paid more or less this year than last; 100% is the passing line.
- **RPO (Remaining Performance Obligations):** The contract value that has been signed but not yet recognized as revenue.
- **ARR / ACV:** Annual Recurring Revenue / Annual Contract Value.
- **Rule of 40:** Revenue growth rate plus adjusted operating margin, a software-industry health metric; 40 is the passing score.
- **Outcome-Based Pricing:** The client doesn't pay for the software; it pays for "the problem solved."
- **Per-Person-Day Billing:** Charging by engineer headcount times number of days — the old outsourcing pricing model.
- **SLA (Service Level Agreement):** A commitment on availability, latency, and error rate.
- **Health Score:** A composite "check-up" score for the customer, synthesized from four signal types: usage, value, relationship, and commercial.
- **QBR (Quarterly Business Review):** A recurring meeting where the vendor and customer align on value every quarter.
- **RAG (Retrieval-Augmented Generation):** Letting the model look up information before answering.
- **Evaluation System:** A system that builds quantifiable yardsticks for fuzzy business quality, and simultaneously the foundation for billing.
- **MCP (Model Context Protocol):** An open standard that lets models connect to external tools, led by Anthropic.
- **Customization Decline Rate:** The Nth customer's customization workload should be significantly smaller than the first's; if it doesn't decline, it's outsourcing.

## I · Delivery-Layer Metrics (Is the project being done right?)

**TTV (Time to Value):** The time from entering the field to the customer's first measurable value. The lifeblood metric of the FDE model. Reference standard: validation of a minimum viable deployment should be measured in weeks (2 to 6 weeks), and a full deployment in months (1 to 4 months). A persistently lengthening time-to-value is the first signal that something is wrong with the methodology or the platform foundation.

**Proof-of-Concept (PoC) Conversion Rate:** The proportion of validation projects that move into paid deployments. Palantir's Bootcamp took this number from an early 5% to 10% up to roughly 75% per the company's disclosed figures (other estimates put some sessions even higher) — it measures both "customer screening quality" and "delivery quality" at once. A conversion rate that's too low signals a failure in intake screening; one that's too high (close to 100%) means you should check whether you're only taking easy, unchallenging deals.

**Evaluation Pass Rate:** The proportion of AI outputs that pass the business evaluation set, and its time-series trajectory in production. The alarm bell for quality drift.

**Discipline on the Definitions of Resolution Rate and Deflection Rate:** The resolution rate (the share of conversations closed without human intervention) and deflection rate (deflection — the share of users intercepted by self-service and never entering the human channel) are the core value metrics for customer-service deployments, and also the metrics with the messiest definitions across vendors. Taking ServiceNow's official definition as an example, a deflection counts only when two conditions are met simultaneously: no ticket submitted within 24 hours after the interaction, and a positive engagement signal present (e.g., the user gives positive feedback on the result). Before citing any vendor's resolution or deflection figure, first ask three things: what is the denominator, how long is the judgment window, who does the judging — an 86% on unclear definitions is worth less than a 51% on clear ones.

**Deployment Frequency and Rollback Rate:** A hard metric for iteration speed. A healthy deployment phase should maintain high-frequency, small steps (weekly or even daily), with a low and stable rollback rate.

**Defect Escape Rate:** The share of defects discovered only after launch. It measures the completeness of the testing and evaluation system, not the engineers' skill level.

## II · Customer-Layer Metrics (How is the customer faring?)

**Activation Rate:** The share of the target user base that forms a stable usage habit. Note that the denominator is the "target user base," not the "number of system accounts." Warning: a deployment with a chronically low activation rate is, nominally alive, actually dead.

**Usage Depth:** What share of users use the key features (how many scenarios are covered), the distribution of usage frequency (clock-in-style usage or workflow-embedded), and the appearance of self-directed exploration behavior (users start discovering new uses on their own — the most precious signal).

**Health Score:** Synthesized from four signal types — usage, value, relationship, and commercial (see Section 5.6). Key discipline: a full sweep every week; breaching the warning line automatically triggers the intervention process.

**Supporter Coverage:** The number and hierarchical distribution of active allies within the customer organization. A single point is high-risk; three points form a network.

**Caution in Using NPS:** The Net Promoter Score (NPS, the metric that asks "how likely are you to recommend us to others") has limited reference value in enterprise settings — small samples, politicized. A more reliable alternative is "early inquiry into renewal intent": two quarters before expiry, directly ask supporters "if you were to renew today, would you?"

## III · Commercial-Layer Metrics (Is the business worth it?)

**NRR (Net Revenue Retention):** The annual change in revenue from existing customers (including churn, downgrades, and expansion). The ultimate judge of the FDE business model. The passing line is 100%, the excellent line 120%. Companies with net revenue retention above 120% already have an endogenous growth engine.

**Delivery Gross Margin:** (Single-customer revenue minus direct delivery costs (labor, travel, cloud resources)) ÷ single-customer revenue. The passing line of the FDE model floats with the degree of platformization: in the pure-labor delivery phase it may be only 20% to 40%, and should rise toward 60%+ once platform reuse picks up. Whether the gross margin rises fast enough matters more than its absolute level for showing whether the model works — an FDE whose margin doesn't rise is a consulting firm.

**Customization Decline Rate:** McGrew's touchstone — the Nth customer's customization workload should be significantly smaller than the first's. If three consecutive customers show no decline in customization, immediately review the product-feedback mechanism.

**Sales Cycle:** The time from first contact to signing. Palantir used the Bootcamp to compress it from 9 to 12 months down to a few weeks. It's a composite reading of customer-acquisition efficiency and the thickness of trust assets.

**CAC Payback Period:** The time for the customer acquisition cost (CAC, Customer Acquisition Cost, including free-validation investment) to be recovered through contract gross margin. The FDE model generally looks ugly early on; the key is to see the trend of it shortening as cases accumulate.

**LTV/CAC:** The ratio of customer lifetime value (LTV, Lifetime Value) to customer acquisition cost. The healthy line for enterprise business is generally above 3; because the FDE model front-loads acquisition cost, it may be below 2 early on, and must be read together with net revenue retention to mean anything.

## IV · Organizational-Layer Metrics (Can the team go the distance?)

**Field-to-Product Feedback Rate:** The number of outputs per unit time that are distilled from the field into components or platform capabilities (components checked in, manuals updated, platformization proposals). This metric measures whether the "soul organ" of the FDE model is still beating.

**Delivery Asset Reuse Rate:** The proportion of an existing component, template, or checklist reused in a new project. The reuse rate is a composite reading of the three-level replication leverage (Chapter 7), and the target should rise quarter by quarter.

**FDE Revenue per Capita:** The annual revenue supported by each forward deployed engineer. It's the master account of scaling: the pure-labor model has a clear ceiling, and should keep rising after platformization.

**Team Endurance Metrics:** Travel intensity (days on the road per month), on-call load, attrition rate, and burnout warning signals. On Reddit, the biggest gripe among FDE practitioners is travel and endurance — once the team is burned out, all the metrics above are fireworks.

## Usage Recommendations

1. For each customer project, lock in 3 to 5 "core metric combinations": typically one value metric + one usage metric + one relationship metric.
2. Baseline data is collected on day one of the project launch — miss it and it's gone forever.
3. Metrics are co-built with the customer and jointly agreed; otherwise they have no force at the renewal negotiating table.
4. Every six months, service the metric system itself: delete what nobody looks at, add what gets repeatedly asked about.
