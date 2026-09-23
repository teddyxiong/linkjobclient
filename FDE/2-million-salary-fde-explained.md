# A $280K Salary and 42x Demand Growth: What Exactly Is an FDE? (A Beginner's Roadmap)

> **Source:** [WeChat Official Account article](https://mp.weixin.qq.com/s/BdjxwNyUpGeZ-yn-JgRP1g)
> Translated from Chinese. Original title: 《年薪 200 万，招聘需求暴涨 42 倍！FDE 到底是什么？【附小白上车路线】》

A technology has to be born twice to change the world: once in the lab, and once in reality.

LinkedIn data shows FDE demand has grown 42x in two years, far outpacing demand for ordinary AI engineers. Overseas total compensation can reach roughly 2 million RMB (~$280K); in China, ByteDance tops out around 1.05 million RMB.

You don't need to train models, and you don't need to understand the algorithms. If you can plug AI into a customer's environment and make it produce results, you can get paid for it.

Backend engineers, implementation engineers, pre-sales, and product managers all have a way in. Here is the practical roadmap.

## Practice These Three Things First — You Can Start Tonight

Anthropic's official job description spells out, in the Responsibilities section, exactly what an FDE ships: **MCP servers, sub-agents, and agent skills**.

That hands you the target. You can practice all three on your own machine today, and what you build goes straight onto your resume.

### 1. Agent Skill — start here; lowest barrier, results in a week

- **What it is:** packaging a way of working into a skill the AI can invoke directly.
- **How to practice:** pick a process you know best (writing weekly reports, doing competitive analysis, processing expense claims). Write it as a `SKILL.md`: when it triggers, what the steps are, what each step does.
- **Output:** a skill package that works the moment it's installed, and that you can hand to a colleague.

### 2. MCP Server — practice second; one to two weeks

- **What it is:** the interface layer that lets AI call external tools and data.
- **How to practice:** write one for something you use every day (your own notes library, an internal API at your company, a website you rely on).
- **Output:** a server that runs and that someone else can install.

### 3. Sub-agent — practice last; the hard part is decomposing the work, not writing the code

- **What it is:** splitting one large task across several specialized AI agents.
- **How to practice:** take a real piece of repetitive work and split it into 3-4 roles. For example: researcher → fact-checker → first-draft writer → critic.
- **Output:** a workflow you can run repeatedly, not a one-off conversation.

### Template for your first agent skill

Replace the bracketed parts with your own:

```
Skill name: [e.g. Weekly Report Assembly]

[When to use]
Trigger when I say "[trigger phrase, e.g. put together this week's report]".

[Ask me these two things first]
1. Which days does this cover
2. Who is it for this time (manager / peer / customer)

[Steps]
1. Read the records for that period from [where the data lives,
   e.g. my log file / a specific folder]
2. Sort them into three buckets: done / in progress / blocked
3. For anything blocked, state clearly who it is blocked on and what
   is needed to unblock it
4. Output in [format, e.g. under 300 words, one line per item]

[Do not]
- Do not invent things I never recorded
- Do not use corporate filler language
```

Save this file as `SKILL.md`, drop it into Claude Code's skills directory, and it works. Write it, then iterate — that beats three days of theorizing.

**Why these three beat grinding algorithm puzzles:** the JD has two hard requirements — "production experience with LLMs" and "have actually shipped an application." These three artifacts prove both at once, and they are real things you can open up and show someone.

## Rewrite Your Resume: One Line Worth Ten

FDE job descriptions want "technical **and** customer-facing." Purely technical or purely business phrasing both get filtered out. The same experience carries completely different weight depending on how it's written:

| Weak | Strong |
| --- | --- |
| I spent five years as a developer at a bank | I know the full corporate account-opening process at a bank, and the three steps where it stalls |
| Responsible for maintaining and iterating internal systems | Cut the manual steps in process X from 6 to 2, saving X hours per quarter |
| Proficient with AI tools such as ChatGPT and Claude | Built a workflow for X with Claude; 12 people on the team use it daily |
| Strong communication and teamwork skills | Led 3 cross-team requirements alignments, turning "we want an AI assistant" into 5 concrete, acceptance-testable requirements |

The pattern: the left column says *what I did*; the right column says *what I got done, and how much*. This role is far more sensitive to outcomes than to titles.

## A Career Switch Is an Asset, Not Baggage

Many people think "I'm not from a pure engineering background, so I can't reach this." The opposite is true.

The head of FDE at OpenAI has said they deliberately mix the team: people who know the customer's industry, and people who know nothing about it at all. The reasoning is that outsiders challenge the status quo more readily and propose solutions insiders would never think of.

Anthropic's JD also explicitly lists as a plus: a background in finance, healthcare and life sciences, or another vertical industry.

### Four entry paths, each with a different gap to close

| Background | What you're missing | How to close it |
| --- | --- | --- |
| Backend / development | Customer-facing experience | Volunteer to run a requirements session with the business side, start to finish, yourself |
| Implementation / delivery | Nothing — you already have the on-site half, which is the harder half to acquire | Build the three artifacts above and you're complete |
| Pre-sales / solutions | You're the closest fit already | Move from "can present a solution" to "can build a running one myself" |
| Product manager | The technical round | Python plus the three artifacts above |

Industry experience works the same way — it's an asset, not baggage:

```
You've worked in banking / hospitals / manufacturing / government / education
→ NOT "experience unrelated to technology"
→ IT IS the vertical-industry background the JD explicitly asks for

On your resume, write it as:
"I know what people in industry X struggle with every day, and I know
why their systems are so hard to change."
```

## Interviews: Strong Engineers Often Fail the Non-Technical Round

The most counterintuitive thing about this role: plenty of technically strong people fail the round that doesn't test technology.

The non-technical round watches for three things:

1. **Requirements clarification.** The customer says "I want an AI assistant." Can you draw out what they actually want solved?
2. **Solution translation.** Can you explain a technical approach in terms the business side understands and agrees with?
3. **Closing the loop.** Do you instinctively think "once this is live, what will prove it worked"?

There's only one way to prepare: take a real project you've done and walk through it along this line.

```
What the customer / business side said at the time: ______
What I judged the real problem to be: ______ (this MUST differ from the line above)
What I did: ______
The metric I used to prove it worked: ______
If I did it again, I'd do this earlier: ______
```

The second line is the crux. If your "real problem" is identical to the customer's own words, the interviewer knows you've never done requirements clarification.

Filled in, it looks like this:

```
What the business side said: they wanted an AI support agent that could
answer user questions automatically

What I judged the real problem to be: it wasn't that questions couldn't be
answered — it was that support answered the same question 200 times a day,
and 80% of those came from three pages with unclear instructions

What I did: first rewrote the copy on those three pages, then set up
auto-replies for the remaining high-frequency questions

The metric that proved it worked: manual ticket volume down 62%, average
support response time from 4 minutes to 40 seconds

If I did it again: I'd sit with the support team's queue for two days before
writing any code
```

Note that the most valuable action in this example — rewriting the copy on three pages — isn't a technical solution at all. That is exactly what an FDE interviewer wants to see.

One more key to understanding the role, from OpenAI's head of FDE:

> An FDE's value isn't in writing code. It's in solving the problem, and making yourself no longer needed. If the same problem brings you back, it was never really solved.

Being able to articulate that in an interview is worth more than any amount of memorized tech stack.

## The Bar Is Lower Than You Think — With Two Hard Constraints

**Education: not a hard bar.** Anthropic's JD says a bachelor's degree "or equivalent combination of education, training, and experience." It closes by explicitly encouraging you to apply even if you don't meet every requirement.

**Experience: a hard bar.** Four-plus years of experience that is technical *and* customer-facing. Note the "and" — pure coding doesn't count, and pure sales doesn't count. Engineers with consulting experience and former technical founders are explicitly welcomed in the JD.

**Travel: a hard bar.** OpenAI sets expectations for new hires at roughly 50% of time on customer sites; colleagues in the UAE and Japan are around 80%. The Anthropic posting says 25%. This isn't occasional travel — it's the shape of the job. If you can't accept it, don't apply.

## Where to Apply — Search These Terms

Naming for this role isn't standardized across markets, and searching only "FDE" misses more than half the listings:

```
English keywords (overseas / remote roles)
Forward Deployed Engineer
Forward Deployed Software Engineer
Solutions Engineer + AI / LLM
Applied AI Engineer
Deployment Strategist

Chinese keywords (large Chinese tech companies / AI startups)
交付工程师 + 大模型      (delivery engineer + LLM)
解决方案工程师 + AI      (solutions engineer + AI)
AI 应用工程师            (AI application engineer)
前置交付 / 前线工程师     (forward delivery / frontline engineer)
```

Three kinds of employers are hiring:

1. **Model labs themselves** (OpenAI, Anthropic, and others).
2. **Data and platform companies.** Palantir invented the role; its published salary band is $175K–$225K.
3. **LLM divisions at large Chinese tech companies.** ByteDance's "Doubao LLM FDE" pays 35K–70K RMB per month, 15 months' pay per year.

Across all tracked openings, 71% explicitly require AI/ML capability, the salary band runs $150K–$325K, and senior total compensation exceeds $780K.

## Three Things You Can Do Today

1. **Open Anthropic's careers page and read the FDE job description end to end** — not to apply, but to use it as the most accurate gap checklist available, ticking off each line against yourself.
2. **Start writing your first agent skill tonight.** Pick the process you know best; you can have a finished artifact in a week.
3. **Rewrite the three most important lines on your resume** using the four before/after pairs above. This step costs nothing and requires no new skills, but it may have the highest return on investment of anything here.

The real barrier to this role isn't your degree. It's whether you can stand on both the engineering side and the customer side at the same time. Most people can only hold one side, which is why the role is worth what it pays.
