# The Hottest AI Role Right Now: What Exactly Does an FDE Do, and How Can Ordinary People Get In?

**Source:** [@AdrianPunk115](https://x.com/AdrianPunk115/status/2083090241683128626)

In the past couple of years, the most sought-after people in the AI world have either been training models or building AI products.

By 2026, another role has suddenly burst onto the scene: **FDE**.

Its full name is Forward Deployed Engineer. Honestly, even after hearing the name, you still have no idea what it actually does.

First, look at a few numbers:

- A LinkedIn report shows that FDE-related roles grew **42×** between 2023 and 2025;
- OpenAI established its Deployment Company in May 2026, with an initial investment of over **$4 billion**, and brought in about **150** deployment engineers and experts through an acquisition;
- AWS followed with **$1 billion**, preparing to send thousands of engineers into customer teams.

The fact that big companies are suddenly scrambling for these people shows the wind has shifted. A 0.1-point difference on a model leaderboard may mean nothing to a customer; but an AI that can plug into a legacy system, run inside a workflow, and ultimately save real money is something customers are willing to keep paying for.

**The AI industry has moved from "competing on models" to "competing on implementation."**

If you've been looking at AI transitions lately, or searching for your next career direction, this article will clarify three things: what FDE is, what one does on a day-to-day basis, and how someone without a coding background can transition into it step by step.

## 1. What Exactly Is an FDE?

I'd prefer to explain it this way:

> **An FDE is someone who steps into a customer's real business and takes AI all the way from a demo to production.**

Suppose a customer says: "We want to build an AI customer service." An ordinary requirements ticket might start writing features here, but an FDE has to keep digging:

- How many tickets customer service handles per day today;
- Which questions AI can answer;
- Which replies must be manually confirmed;
- Which system customer data lives in;
- How to retract an AI reply when it's wrong;
- After launch, whether to measure response speed, resolution rate, or labor cost.

Only after these questions are clarified does the coding begin. And writing the system isn't the end either — you still have to integrate data, configure permissions, run evaluation, push to production, watch adoption, and bring the pitfalls you hit on-site back to the product team.

The whole job can be compressed into six steps (shown in the diagram in the original article):

**Requirements are only the starting point; results are the deliverable.**

So an FDE usually has to handle three things at once: business understanding, engineering delivery, and customer-facing communication.

There are plenty of people who can write code, but far fewer who are willing to go into a customer's site and untangle a mess until it can go live. That's why FDEs are hard to hire and, at the same time, increasingly expensive.

## 2. What an FDE Actually Does in a Day

Suppose a chain retail company approaches an AI vendor and says it wants an "intelligent replenishment Agent." That sentence sounds clear enough, but the moment an FDE walks in, the question marks start multiplying:

- Which stores are most prone to stockouts;
- Whether replenishment should consider sales, weather, holidays, or promotion plans;
- Whether the Agent only gives suggestions or directly generates purchase orders;
- Above what amount human approval is required;
- Whether updating inventory once a day is enough;
- Who handles overstock and loss when a recommendation is wrong.

In the first week, he may not write a single line of code. First he finds the store manager to see how replenishment is done now, confirms the rules with supply chain, looks at the interfaces with IT, then talks to security about permissions. Only after the process is fully understood does he enter the engineering phase:

- Integrate the inventory, sales, and order systems;
- Clean the historical data;
- Write the model calls and Agent workflow;
- Build a page employees are actually willing to open;
- Add login, permissions, logging, and monitoring;
- Prepare test data;
- Set up manual review and failure fallbacks.

After launch he still has to keep watching. Did the stores actually use it? What's the suggestion-adoption rate? Did the stockout rate drop? Why did employees quietly go back to Excel? All of this is part of his job.

If adoption is too low and he just walks away with "users don't know how to use it," the project is basically dead. Whichever part is unpleasant — the page, the flow, or the model output — you go back and fix it.

**What an FDE delivers is a business process that's already up and running. Making a polished demo only gets you halfway up the mountain.**

## 3. How Is It Different From a Programmer, a Product Manager, or Pre-Sales?

These roles often work together and their boundaries overlap. The simplest way to tell them apart is to look at where each person's responsibility ends.

An FDE's boundary is broader. Meeting with a customer about business in the morning, querying a database in the afternoon, and fixing an interface in the evening — all of these can happen on the same day.

But don't misunderstand one thing: **the "E" in FDE is still "Engineer."**

OpenAI's current FDE openings explicitly require candidates who can write and review production-grade front- and back-end code. Palantir's new-grad role also requires proficiency in at least one programming language. So you can transition without a computer-science background, but you can't get there by completely bypassing code.

If you prefer business and customers and don't want to write production code long-term, you can first look at Deployment Strategist, AI product manager, industry solution consultant, customer success, or AI consulting. These roles are also on the AI implementation chain, with a lighter engineering responsibility.

## 4. Why Is FDE Heating Up Right Now?

The reason is simple: AI keeps getting stronger, and the implementation problem keeps getting more obvious.

### A Demo Can Be Made in a Day — Production Isn't So Forgiving

Hook up a model API, stuff in a few documents, and build a chat page, and you can impress the boss in a day. But the moment you get ready to launch, the dirty data, messy permissions, the legacy system with no interface, model outputs that drift, the security team demanding an audit, and employees unwilling to change their habits all surface at once.

Model upgrades can't fix the chaos on the ground. A company needs someone to dive into the business and clear these out one by one.

### Agents Have Started Actually "Taking Action"

When a chatbot answers one thing wrong, the user can simply ignore it. But once an Agent can send emails, change orders, and submit approvals, an error flows directly into the business.

Identity, permissions, evaluation, logging, manual review, and exception recovery — none of these can be skipped. And every company's systems look completely different, so this work can't be handled by a one-size-fits-all manual.

### AI Companies Also Need Customers to Actually Use It

Signing the contract is just getting in the door. It's only after the model enters core processes that usage volume, renewals, and department expansion slowly start to happen.

An FDE is closest to customer outcomes, and therefore closest to an AI company's revenue. This is the commercial reason OpenAI and AWS are willing to invest heavily.

### AI Coding Multiplies the Output of Generalists

Before, building an enterprise application meant waiting for product, front-end, back-end, data, and ops to schedule together. Now a strong-engineering generalist, aided by AI coding, can finish the prototype, integration, testing, and revision much faster.

Two or three people embed in a customer team, ship the first version in a few weeks, then iterate quickly on real feedback — that economics finally adds up.

**The last phase was about whose model was stronger; this phase is about who can fit a model into the business. FDE stands right in that gap.**

## 5. Where Is the Opportunity for Ordinary People?

Reading this far, you might think: "Isn't this still only for senior programmers?"

Senior engineers do have an edge, but FDE capability comes from several directions. Ordinary people don't have to reset to zero and retrain — first look at what you already have, then fill in the missing half.

### Software Engineers: Closest to It

You already know how to write production code and why systems crash. Next, focus on filling in user interviews, business processes, requirement scope, ROI, and adoption.

The most direct practice is to proactively join customer meetings, pre-sales support, or internal AI implementation projects. Don't keep waiting for others to break requirements into Jira tasks before you start.

### Data Analysts: A Great Fit for the Transition

Data analysts usually know SQL, understand metrics, and are used to communicating with business departments. Their weak spot is usually engineering:

- How to turn a notebook into a service;
- How to integrate APIs;
- How to build login and permissions;
- How to deploy and monitor;
- How to recover after an error.

Turning an analysis that only you can run into a tool your colleagues open every day — that's already a big step toward FDE.

### Product, Consulting, and Industry Operations: Industry Experience Is Very Valuable

If you've done manufacturing, you know production scheduling and yield; if you've done finance, you know auditing and compliance; if you've done retail, you know inventory and store execution. This experience is hard to make up for with a few courses.

What you need to add is programming, databases, APIs, and deployment, and then build a runnable system with your own hands. For your first transitional role, you can look at:

- Deployment Strategist;
- AI product manager;
- AI solution consultant;
- Solutions Engineer;
- Technical implementation.

Get into the AI implementation field first, then gradually increase your engineering responsibility.

### Pre-Sales, Implementation, and Solutions Architects: You May Already Be Halfway There

You know the customer, and you know how troublesome permissions, procurement, and legacy systems inside an enterprise are. Next you need to get over the code hurdle, moving from making demos, configuring products, and drawing architecture diagrams on to development, testing, deployment, and maintenance.

This route is usually shorter than a full career change.

### Completely From Zero: First Build One Hard Skill

With no technical experience and no industry accumulation, jumping straight at FDE will be a struggle. You can first enter through data analysis, AI operations, technical support, implementation consulting, junior development, or an industry-solution assistant role.

**FDE is rarely anyone's first career stop — it's more like several streams of experience finally converging into one.**

## 6. A Six-Month Roadmap for Ordinary People

After reading the job description, the easiest thing to do is bookmark courses. Six months later, your bookmarks are overflowing but your resume is still empty.

Six months is enough to build an FDE portfolio you can actually submit. Whether you land a role still depends on your prior experience, engineering level, and the target company's requirements.

### Months 1–2: Build Up Your Engineering Foundation

First learn the most commonly used things:

- Python or TypeScript;
- SQL and databases;
- HTTP, JSON, and APIs;
- Git;
- Error handling and testing;
- Docker and basic deployment.

The acceptance standard for this phase is a single thing: **independently build a small app with a database and an API that, once deployed, other people can open and use.**

First get input, processing, saving, error reporting, and deployment working end to end. Whether the framework is the latest isn't that important for now.

### Months 3–4: Build a Complete AI Application

On top of the first version, keep adding model APIs, RAG, Tool Calling, structured output, logging, Evals, failure retry, and manual review.

Stop building "upload a PDF and then chat." Pick a concrete task:

- Help sales organize leads and give follow-up suggestions;
- Help customer service look up knowledge and draft replies;
- Help finance check expense-reimbursement materials;
- Help operations organize data and flag anomalies;
- Help a manufacturing team look up equipment faults and maintenance records.

In the second phase, focus on four metrics (shown in the diagram in the original article).

### Months 5–6: Find Real Users

Find three to five people willing to try it and have them use it continuously for two weeks. Record how long the old and new processes each take, how many times it was used in total, which suggestions were adopted, which errors needed manual handling, and why users gave up midway.

Real users will surface all the hidden problems: dirty data, insufficient permissions, a hard-to-use page, processes changing daily, and too-high model costs. Working through these at least once is what gives you a project that actually looks like an FDE's.

Finally, package it into a case study:

Don't pile up a few lines of framework names on your resume — write out three things clearly: **who used it, for how long, and how the metrics changed.**

## 7. When Job Hunting, Don't Search Only for "FDE"

The name of this role hasn't been fully standardized yet. Besides Forward Deployed Engineer, you can also search for:

- Forward Deployed AI Engineer;
- Applied AI Engineer;
- AI Deployment Engineer;
- Solutions Engineer;
- AI Solutions Architect;
- Deployment Strategist;
- AI application delivery engineer;
- AI solution engineer;
- Agent engineer.

After spotting a role, check four things first:

1. Will you have direct contact with customers and front-line users;
2. Will you write production code yourself;
3. Are you responsible from discovering the problem all the way through to launch;
4. After launch, will you track adoption and business outcomes.

If all four are covered, the work will be closer to FDE.

### How to Prepare for the Interview

FDE interviews often give you a very vague problem, like: "A hospital wants to use AI to shorten patient wait times. What would you do?"

Don't rush to pick a model. You should ask clearly where in the process patients wait, who handles queuing and triage, what the current average wait is, where the data lives, which decisions must be made by medical staff, and what metrics define project success.

Only after the questions are clear do you talk about systems, permissions, and launch scope. What the interviewer wants to see is whether you can turn a vague problem into something clearer bit by bit — memorizing ten model names won't get you through this.

## 8. Watch Out for "On-Site Delivery With a New Name"

Once FDE gets hot, more and more roles with the same name but different substance will appear. Some roles let you write critical code, drive adoption, and bring field experience back to the product; other roles are just on-site firefighting every day, where your code never enters the main repo and you're judged only on person-days and acceptance.

They're all called FDE, but their career value differs enormously. In the interview, you can ask directly:

1. Which repository will the FDE's code go into?
2. Does the team report to product, engineering, or project delivery?
3. Is the project measured by adoption and business metrics, or only by on-time acceptance?
4. How do field issues make their way into the product roadmap?
5. After the project ends, who is responsible for long-term operation?
6. What reusable components were accumulated from the last three projects?
7. How much time is spent on business travel, on-site work, and on-call respectively?

The judgment criteria are simple:

- **Real FDE**: writes production code, owns the results, and the experience flows back to the product;
- **Re-skinned on-site vendor**: billed by person-days, revolves around acceptance, and redoes everything for every project.

If a company makes you own the results but gives you no data permission, no technical decision-making power, and no product support, the job will very likely be exhausting. The title is new, but the way of working may not have changed at all.

## Finally

The explosion of FDE shows that AI has entered its next stage. Models will keep getting stronger, but the bigger gap has now appeared between models and real business.

Customers need someone to walk into the field and connect messy data, legacy systems, business rules, and real users. This job has a high bar: you have to write code, understand business, face customers, and own the results after launch.

The opportunity for ordinary people lies in the half of capability they already have. If you can code, add business and customer skills; if you know an industry, add engineering and deployment; if you've done data, pre-sales, or implementation, keep pushing the capabilities you already have forward. If you're starting completely from zero, first build one hard skill that can be verified.

If there's only one thing you do right now:

**Find a real problem, build a tool that can go live, and have three people use it continuously for two weeks.**

Complete that loop, and your work will already start to look like an FDE's. The job title can come later.

## Reference Links

- LinkedIn: Building a Future of Work That Works
- OpenAI: OpenAI launches the OpenAI Deployment Company
- AWS: Introducing Forward Deployed Engineering for Partners
- OpenAI: Forward Deployed Engineer job description
- Palantir: Forward Deployed Software Engineer, New Grad

## About the Author

**Punk｜** USTC MBA｜Chief Designer at HerName｜Executive Dean of Stanley Business School｜

｜AI prompts｜made 8 figures in 3 months｜Learn in Public｜@AdrianPunk115