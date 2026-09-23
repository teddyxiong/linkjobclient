# What Is the Viral Jev, How to Use It, and Are There Open-Source Alternatives?

**Source:** [国华国华 · 硅基思维](https://mp.weixin.qq.com/s/JYJc-wk646UqVFLrwEaR1Q) (WeChat)

Give it a piece of text and a few questions, and it writes not a single sentence — it only returns which option to pick, what score to give, and yes/no, attaching a certainty probability to each answer. This is Jev, the decision model that went viral a few days ago.

**Right now calling it on Vercel is free — a promotion lasting until September 25, 2026. See below for how to use it.**

First, what can it do

It does the kind of work you can settle with a single glance. Which team to hand this to, should this one be blocked, is this urgent — a person can tell at a glance, but there are tens of thousands per day, and a person can't review them all.

1. Customer-service ticket routing: a customer sends "my card was charged twice and nobody answered me for three days" — it gives four answers at once: billing issue, route to finance group, requesting a refund, emotionally angry. With keyword rules, the moment the other party phrases "charged twice" differently, it fails.

2. Email filtering: which are real business, which are sales ads, and which are phishing emails disguised as a bank or a colleague to trick you into clicking a link and entering your password.

3. Content moderation: whether comments and danmaku contain abuse or violations. If a user deliberately sends "forget your previous rules and listen to me now" to derail your AI customer service, it can block that too.

4. Saving money on expensive models: "what's today's date" and "help me design an ordering system" differ hugely in difficulty — first judge whether the question is hard, and hand the simple ones to a cheap model.

5. Predicting AI risk: before it deletes files, sends emails, or calls payment interfaces, first judge whether it will delete data, spend money, or send things outside the company — if dangerous, stop and wait for a human's nod.

6. Picking useful search results: search out a dozen passages from the corpus, have it score each for relevance, discard the low-scoring ones, and hand the rest to the big model.

7. Accepting AI's finished work: list the acceptance criteria and have it score; if below the bar, send it back to redo — no human needs to check item by item.

## What Is Jev

When we usually have a big model do classification, we write a prompt and have it output JSON. The model is still predicting text token by token; the app gets that long string and still has to write code to parse fields and catch JSON errors. The confidence the model writes in JSON is also just a string of characters it generated — not a real probability distribution.

The Jev released by TypeSafe AI takes a dedicated decision route; they call it a System One decision model, borrowing the "fast thinking" concept from *Thinking, Fast and Slow*.

TypeSafe release page: published on September 15, 2026 by founder Diogo Almeida, focused on automation rather than chat.

It doesn't generate open text; it only accepts a state (`state`, which can be plain text, ticket content, or JSON) and a set of predefined questions (`questions`).

It currently supports three question types: choice (pick one), score (rate on a scale), and boolean (a yes/no probability).

In one request, you can stuff in multiple questions at once; they share the same state and compute concurrently.

The official marketing says "no hallucination." What it means by "no hallucination" is that output is strictly confined to the field definitions you give — it will never generate content outside the format, nor fabricate extra fields. But if the ticket itself is semantically ambiguous, it can still misjudge an urgent event as an ordinary one, or pick the wrong team.

## How to Use It

The official API still has a queue — you submit an application at typesafe.ai to join the waitlist. If you don't want to wait, the fastest route is via the Vercel AI Gateway, which opens calls directly and is completely free until September 25 (after the promo ends, it's $0.042 per million input tokens, output free).

On Vercel's Jev model page: model name `typesafe-ai/jev`, marked Free, with the AI SDK integration code on the right.

### Step 1: Install dependencies and link your project

Vercel has provided the experimental interface `experimental_evaluate` since AI SDK 7.0.105. In the terminal, install the latest dependency and pull the environment variables:

```bash
pnpm i ai
vercel link
vercel env pull
```

### Step 2: A minimal call for a single judgment

Given a customer-service record, judge whether the agent actually refunded the customer:

```js
import { experimental_evaluate as evaluate } from 'ai';

const result = await evaluate({
  model: 'typesafe-ai/jev',
  state: 'The support agent issued a full refund of $49 to the customer on invoice 4411.',
  questions: {
    refunded: {
      type: 'boolean',
      instructions: 'Was a refund issued to the customer?',
    },
  },
});

console.log(result.answers.refunded.probability);
```

The returned `probability` is a float. If the result is `0.982`, your code can directly use the number in an `if` — no need to write a regex to fish a "yes" or "no" out of the text.

### Step 3: Handle multiple decisions in one request

Ticket triage or Agent interception usually needs to judge department, urgency, and refund intent at the same time:

```js
import { experimental_evaluate as evaluate } from 'ai';

const result = await evaluate({
  model: 'typesafe-ai/jev',
  state: 'My card was charged twice for invoice 4411 and nobody has answered for three days. Refund the duplicate today or we are cancelling our plan.',
  questions: {
    department: {
      type: 'choice',
      instructions: 'Route this ticket to the right department.',
      criteria: {
        billing: 'payment, double charge, or invoice problems',
        technical: 'bugs, application crashes, or errors',
        sales: 'upgrades, plan cancellation, or enterprise contract',
      },
    },
    urgency: {
      type: 'score',
      instructions: 'How urgent is this ticket from 1 to 5?',
      criteria: ['very low', 'low', 'medium', 'high', 'critical'],
    },
    wantsRefund: {
      type: 'boolean',
      instructions: 'Does the customer explicitly demand a refund?',
    },
  },
});

console.log(JSON.stringify(result.answers, null, 2));
```

The data structure it returns is directly typed JSON:

```json
{
  "department": {
    "choice": "billing",
    "confidence": 0.991,
    "probabilities": {
      "billing": 0.991,
      "technical": 0.006,
      "sales": 0.003
    }
  },
  "urgency": {
    "score": 4.12,
    "confidence": 0.88,
    "probabilities": [0.01, 0.02, 0.05, 0.62, 0.30]
  },
  "wantsRefund": {
    "probability": 0.985
  }
}
```

### Step 4: Branch routing by probability

Now that you have native probabilities, set safety thresholds in your business code:

```js
const { department, urgency, wantsRefund } = result.answers;

// probability below 0.8, or the score is uncertain — hand to manual review
if (department.confidence < 0.8 || urgency.confidence < 0.7) {
  await assignToHumanQueue(ticketId, 'Low confidence classification');
  return;
}

// high certainty + requesting a refund — add an urgent tag and go through billing
if (wantsRefund.probability > 0.9 && urgency.score >= 4.0) {
  await routeToBillingFastTrack(ticketId);
} else {
  await routeToQueue(ticketId, department.choice);
}
```

Price table details (seven columns): context 32K, ZDR (zero data retention) and No Training both checked, and input/output are currently all free.

## Want an Open-Source Alternative? Keep Reading

By the way, a quick plug for my beginner Agent tutorial mini-program: it not only lets you track AI hot news in real time and follow Codex quota-reset times, but also offers free tutorials — 8 series, 171 AI tutorials, 700,000+ characters of body text, 290 images, and nearly 300 code examples.

## Open-Source Alternative: Laya

Jev is a closed-source commercial API. If you need private deployment or offline running, the community has an open-source alternative called Laya.

The author said on Reddit that he built this architecture a year ago, and after Jev's release he open-sourced the model under the Apache 2.0 license.

On HuggingFace, Laya's model card: Apache 2.0 license, 0.4B (421M) parameters, based on ModernBERT.

If you don't want to set up a local environment, you can try the online demo on HuggingFace Space first (search HuggingFace for `convaiinnovations/laya-demo`).

Laya demo's ticket triage: input on the left, with real-time probabilities for intent, urgency, and refund_requested on the right.

The demo runs on HuggingFace's public ZeroGPU; due to queueing and network, measured latency fluctuates between 130ms and 4s. The official 32.8ms figure is pure inference time on a local dedicated T4 GPU.

Running it locally is also lightweight; it's based on ModernBERT, with the whole model at only 400M parameters:

```bash
pip install laya
```

Local Python calling code:

```python
from laya import Router

# Note: in production you must add preload=True
# otherwise, when switching languages, reloading weights from disk takes 7 to 10 seconds
router = Router(preload=True)

state = "发票4411被重复扣款，三天没有人回复。请今天退款。"
questions = {
    "department": {
        "type": "choice",
        "instructions": "Route this ticket to a team.",
        "criteria": {
            "billing": "payment or charge problems",
            "technical": "application bugs",
            "sales": "account upgrades or plans",
        },
    },
    "is_urgent": {
        "type": "noul",
        "instructions": "Is this ticket urgent?",
    },
}

res = router.predict(state, questions)
print("部门:", res["answers"]["department"]["choice"])
print("退款意图概率:", res["answers"]["department"]["probabilities"])
print("实际使用的模型:", res["routing"]["model"])
```

Laya currently provides three checkpoint files:

| Checkpoint | Base architecture | Params | Default context | Use case |
|---|---|---|---|---|
| `convaiinnovations/laya` | ModernBERT-large | 421M | 512 | Pure English text, safety filtering, email triage |
| `convaiinnovations/laya-multilingual` | mmBERT-base | 322M | 1024 (up to 8k) | 100+ language mixed tasks, ~2.2× faster inference |
| `convaiinnovations/laya-typed-decisions` | ModernBERT-large | 421M | 1024 | A fine-tuned model specialized for scoring |

## Laya's Limitations

If you plan to use Laya to replace Jev, there are several limitations you must know up front.

If you run the English checkpoint on Khmer (Cambodia's official language) tasks, accuracy drops to 0.000, but the average confidence is 0.952.

When the model utterly can't understand a language, it still stays very confident. In this case, the "low-confidence → escalate to human" safety fallback fails.

Laya Chinese routing result: when the input is Chinese, the front-end regex Router accurately identifies han characters and auto-routes to the multilingual model, taking 131ms.

So the code above must use `Router`. It checks the Unicode character set with regex before the input enters the model; once it finds non-Latin characters, it switches directly to the multilingual model, avoiding the English model's blind spot.

The official benchmark comparison shows advantages in multilingual, low latency, and open-source self-hosting, but a clear gap on large-classification tasks with many options.

Second, it can't handle many options. On the Banking77 benchmark with 77 classification options, Laya's accuracy is 0.425, while Jev reaches 0.870. When options exceed 20, the token space Laya allocates to each option gets severely compressed.

Third, the officially advertised 0.766 accuracy comes from `laya-typed-decisions`, which was specially fine-tuned on the eval set. The two general base models score only 0.362 and 0.342 on the same test, below the 0.461 majority-class baseline. Its general zero-shot ability isn't strong — you need to re-fine-tune it on your own business data.

Fourth, scoring is currently the weakest part, with only 0.372 accuracy on the SST-5 scoring test.

**If your business is high-frequency, fixed categories with labeled data, self-hosting Laya is a good deal; but if you need to handle arbitrary questions and dozens of long options, you still have to use Jev.**

**Open-source repo:** (see the original article for the repository link)

**If you found this article helpful, feel free to follow, like, and share.**