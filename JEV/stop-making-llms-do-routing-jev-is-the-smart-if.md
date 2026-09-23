# Stop Making LLMs Do Routing — Jev Is the Smart `if`

**Source:** [@sven_ai (毅行出海)](https://x.com/sven_ai/status/2101495236325425333)

Customer ticket routing — many teams are still using GPT to "read it once and output JSON." The problem: what you actually need isn't a piece of text, but a judgment that can go into an if/else.

Jev's positioning is exactly the opposite: it's not a chat model, and it doesn't generate replies; it turns unstructured state into a typed, probability-carrying decision result.

Official entries:

- Announcement: https://typesafe.ai/blog/introducing-system-one-models-and-jev
- Quickstart: https://docs.typesafe.ai/introduction/quickstart
- API endpoint: https://api.typesafe.ai/v1/systemone
- Model route: `jev-latest`
- Python SDK: `typesafe-sdk`
- JS SDK: `@typesafe-ai/sdk`

## 1. Ticket Routing Is Fundamentally "Judgment," Not "Generation"

Look at a customer ticket:

> "I've been waiting 5 days for my refund, and the bill still shows a charge. If this isn't handled I'll file a complaint. Order number 1842."

The traditional LLM approach is usually:

1. Assemble the prompt;
2. Require the model to output JSON;
3. Parse the JSON;
4. Validate fields;
5. Handle format errors, hallucinated fields, and explanatory filler;
6. Then connect to business branches.

This is awkward.

Because what a routing system really needs is just a few judgments:

- Should it go to billing, technical, or support?
- Is it urgent?
- Is there refund intent?
- How frustrated is the user?
- Is confidence high enough for automatic handling?

Jev's core value is right here: turning "fuzzy judgment" into a smart `if` in ordinary code.

It provides three primitives:

- Choice: pick one of many, e.g. route to which department;
- Noul: a soft boolean from 0 to 1, e.g. is it urgent, is there refund intent;
- Score: continuous rating, e.g. anger level, risk level, lead quality.

Note: Jev doesn't generate customer replies, nor will it check order status for you. It only judges the current state. Querying the database, refunding, and sending messages are still your own business code's responsibility.

## 2. One Call Returns Multiple Decisions

First install the SDK:

```bash
pip install typesafe-sdk
```

Set the environment variable:

```bash
export TYPESAFE_API_KEY="your API Key"
```

Below is a minimal runnable Python example. The client reads `TYPESAFE_API_KEY` by default and calls `jev-latest`.

```python
from typesafe_sdk import Choice, Noul, Score, TypeSafeClient

client = TypeSafeClient()

ticket = """
客户ID: u_9281
订单号: 1842
内容: 我已经等退款 5 天了，账单还显示扣款。
再不处理我就投诉。你们客服每次都让我等，太离谱了。
"""

response = client.system_one(
    state=ticket,
    questions={
        "department": Choice(
            instructions="这个工单应该由哪个团队优先处理？",
            criteria={
                "billing": "扣款、发票、订阅、退款、账单相关问题",
                "technical": "登录、集成、报错、系统不可用等技术问题",
                "support": "一般咨询、账号信息、使用帮助",
                "legal": "投诉、合规、法律威胁或监管相关风险",
            },
        ),
        "is_urgent": Noul(
            instructions="客户是否表达了明显的紧急性或升级风险？"
        ),
        "refund_intent": Noul(
            instructions="客户是否明确想要退款或追踪退款状态？"
        ),
        "frustration": Score(
            instructions="客户当前挫败或愤怒程度",
            criteria=[
                "平静，只是在陈述事实",
                "不满但仍然克制",
                "明显愤怒，出现投诉、威胁、强烈负面表达",
            ],
        ),
    },
)

answers = response.answers

department = answers["department"].choice
department_conf = answers["department"].confidence
urgent = answers["is_urgent"].noul
refund = answers["refund_intent"].noul
frustration = answers["frustration"].score
frustration_conf = answers["frustration"].confidence

print("department:", department, department_conf)
print("urgent:", urgent)
print("refund_intent:", refund)
print("frustration:", frustration, frustration_conf)
```

The key point of this code isn't "it can classify," but that the four judgments are done in one request.

This is a completely different cost model from calling an LLM 4 times in a row. The Quickstart in the official docs shows the same pattern: one state, multiple groups of Choice / Score / Noul questions, all answers returned at once.

The official announcement also gives current pricing: Jev input tokens at $0.042 / MTok, output free; claimed latency in the 70ms–500ms range. The more aggressive "193.6× faster / 444.6× cheaper" comes from the official workflow eval — self-tested in nature, with no sufficient third-party reproduction. You can reference it for engineering, but don't treat it as a procurement conclusion.

## 3. Wire Confidence Into if/else

The most natural way to land Jev isn't to "trust the model," but to "let the model provide probabilities for the branches."

For example, a customer-service system can be wired like this:

```python
if department_conf < 0.55:
    queue = "human_triage"
    reason = "部门判断置信度不足，交给人工分诊"

elif urgent > 0.8 and frustration >= 1.5:
    queue = "priority_billing_escalation"
    reason = "高紧急度 + 高挫败，进入账单升级队列"

elif department == "billing" and refund > 0.7:
    queue = "refund_billing"
    reason = "明确退款意图，进入退款账单队列"

elif department == "legal":
    queue = "risk_review"
    reason = "存在投诉或合规风险"

else:
    queue = department
    reason = "自动分流"

print(queue, reason)
```

This is the so-called "smart if."

A traditional `if "refund" in user.text` is too brittle. Full LLM decision-making is too slow, too expensive, and too hard to control. Jev sits in the middle: natural-language understanding goes to the model, final control stays in the code.

I suggest treating thresholds as product parameters rather than hard-coded truth:

- confidence < 0.5: manual review;
- 0.5–0.75: low-risk automation, keep logs;
- > 0.75: enter the automatic branch;
- High-value customers, legal risk, overly large refunds: force manual regardless of score.

This is also the biggest difference between Jev and chat models: its output is naturally suited to being observed, logged, tuned, and replayed.

## 4. When Not to Use Jev

Jev is not a replacement for GPT.

It's not suited for:

- Generating customer-service replies;
- Summarizing long documents;
- Querying a knowledge base;
- Writing SQL;
- Reasoning through complex business processes;
- Questions that require external fact retrieval.

It's suited for:

- Classification;
- Routing;
- Scoring;
- Judging whether conditions are met;
- Extracting simple structured signals;
- Adding guardrails to an Agent or LLM;
- Pre-gating in front of expensive models.

In customer-service scenarios, a more sensible architecture is:

1. Jev judges department, urgency, refund intent, and risk score;
2. Ordinary code checks orders, subscriptions, and SLA;
3. Low-risk requests flow automatically;
4. High-risk requests go to a human or a stronger LLM;
5. When a reply is needed, then call GPT / Claude.

So the point isn't that "Jev is smarter than GPT." That's inaccurate.

A more accurate way to put it is:

> GPT is the brain that can talk; Jev is a judgment function you can stuff into a code branch.

If your system has a pile of slow, expensive, hard-to-control classification prompts, don't rush to fine-tune, and don't rush to a bigger model. Take 100 real tickets, break them into one Jev call using the Choice / Noul / Score above, and record the results, confidence, and human labels.

If you can get this step working, you'll quickly see clearly: which places need an LLM, and which actually just need a smarter if.