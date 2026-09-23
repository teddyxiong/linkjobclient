# Now That You Have Jev — What Next? What Can Jev Actually Do: A Real Landed-List After Stripping Away the Hype

**Source:** [@servasyy_ai (huangserva)](https://x.com/servasyy_ai/status/2101132667056185544)

## Why I Wrote This

Less than a week after Jev's release, the internet is already full of "200× faster," "never wrong," and "LLMs will be replaced." I went through a lot of posts and also ran a batch of test cases. My impression: not many people have actually built things — most of it is reposts, opinions, and "I'm planning to build a...".

This article does only three things: clarify what Jev is and isn't; categorize the genuinely working cases by use; and explain where the hype is.

## What Jev Is: an AI That Only Does Multiple-Choice

TypeSafe AI released Jev on September 15, 2026. Its founder, Diogo Almeida, came from OpenAI.

**One-sentence understanding: ChatGPT and Claude are "AIs that can write essays"; Jev is an "AI that only does multiple-choice." You give it a piece of information and a few questions whose options are predefined, and it returns all the answers at once — each answer with a "how confident I am."**

It can only answer three types of questions:

- **Single choice (Choice):** pick one from up to 255 options;
- **Scoring (Score):** give a score on a scale;
- **Yes/no (Noul):** give the probability of "yes."

Why is it fast and cheap? A normal large model writes character by character, but Jev's answer range is fixed in advance — it just computes the probability of each option. Official numbers: 0.07 to 0.5 seconds response, $0.042 per million input tokens, output free. Its training objective is also different: it doesn't pursue "pretty answers," it pursues "accurate probabilities" — when it says 70% confidence, roughly 70% should be correct.

It can't chat, can't write code, can't write copy, and can't see images.

### How to Get Jev

Today there are two paths. One is official: go to the TypeSafe site and join the waiting list; once approved you'll receive an "You're in!" email, and clicking through to register gives you an API key. I waited a few days; below is that email.

**The other is OpenRouter:** no waiting — register and call the `typesafe/jev` model directly, billed per use. If you want to get started immediately, take this one. The two rounds of testing below were run from OpenRouter.

### Official Numbers, and Where to Discount Them

The official comparison (all self-reported):

TypeSafe didn't run public benchmarks but built its own suite: have each model make decisions in the same program, using the average answer of the two strongest models as the ground truth. On this suite, Jev's accuracy is about 68% — close to mid-tier large models — but 40–400× cheaper and 20–200× faster.

Three criticisms on Hacker News worth remembering:

1. **"Never hallucinates" means "won't give an answer outside the options,"** but picking the wrong option is entirely possible. TypeSafe's CEO himself admitted this.
2. **The term "frontier model" borrows a bit of borrowed glory.** A more honest phrasing: on **"doing multiple-choice"** specifically, it pushes speed and cost to a new level.
3. **The speed comparison isn't entirely fair.** It compares against the time a large model takes to write out a full answer, not against a large model that also only answers one letter.
4. **The viral Doom demo feeds it enemy coordinates, not the screen.** The model effectively has wallhack — what that shows is fast reactions, not the ability to play games.

My take: these criticisms don't overturn its value, but they show **"Jev replaces LLMs" is a false premise.** The sensible usage: LLMs help you think through the judgment rules, and Jev executes high-frequency, low-cost in production. What it competes for isn't LLM work, but those small judgments that previously "weren't worth putting AI on."

## Scenarios That Have Genuinely Worked

Each item below has accessible code, a demo, or a product entry. Numbers are mostly self-reported and not independently verified.

### 1. As a "Decision-Maker" for AI Assistants

The largest and highest-quality category. At every step an AI assistant has to pick one action from a finite set — which is exactly a multiple-choice, and it has to be fast.

The benchmark is Browser Use's open-source Jev Ultrafast: instead of screenshotting every step for a vision model, it breaks the webpage into a numbered list of elements and has Jev choose "what to do, on which one." In a real test, searching for a flight went from 9.5 seconds to 7.1 seconds; the project ships measurement scripts and is the most complete-evidence case I've seen.

Other projects with the same idea: (references)

### 2. Classifying Massive Data Item by Item

This is where Jev saves the most money. Output is free and input is extremely cheap, which means asking "does this one need an alert" or "is this email a scam" over millions of records is economically viable. Doing this with LLMs was always too expensive and too slow.

Text-classification tests: (references)

### 3. "Auto-Pass When Confident, Ask the Big Model When Not"

In my view this is the most worth-studying use, because it uses Jev's most unique thing: that "how confident" number.

This approach has a prerequisite — the probability must be accurate. If Jev says 90% confidence but is only right 70% of the time, the whole pipeline leaks. This is what I focused on verifying in my second round of testing, below.

### 4. Real-Time Response and "Predicting What You Want" Interfaces

(references)

### 5. Simulation and Control Experiments

A reminder: these are all simulated data. Jev can't see images, and the online "autonomous driving" claims have already been debunked by engineers. Treat it as exploring shapes.

## Already Integrated Into Products

This is the signal I care about most: someone is bearing the consequences of Jev being wrong inside a real, paid product.

(references)

## What I Didn't Count

OpenJev, Kev, Nimble and similar imitation substitutes aren't counted — they aren't Jev applications. Pure opinions, tutorials, launch announcements, and ideas with no running evidence were also excluded — that part outnumbers the real cases several times over.

## My Own Testing: Four Failures, Two Rounds That Worked

The cases above were all run by others; the following I ran myself. Failures first, then the ones that worked.

### First, Four Failures: Shoehorning Jev Into My Own Tools Got Stuck Everywhere

The first week I had Jev, I didn't rush to run benchmarks — I directly stuffed it into the tools I use daily, to see if it could speed me up. Four attempts, all failed. To be clear first: the failures weren't in the model itself — Jev's API returned normally every time, and its Chinese judgments were accurate. Rather, the moment it was squeezed into real applications, it hit a wall.

The four failures trace to three root causes:

**1. It can't see the content.** The compression plugin and disk cleanup both died here. To squeeze into the 32K limit you have to cut content first, and once cut it can't judge. "Fast AND accurate" — only the first half holds: to be accurate you must show it the content, and showing it the content blows the limit. It's not that it's imprecise; it's that you never showed it the content.

**2. Subscription pricing kills its economics.** Its selling point is "hundreds of times cheaper than calling an LLM," but the Codex and Claude Code I use are subscriptions — the judging is already bundled into the monthly fee, at zero marginal cost. Inserting a Jev layer only adds a layer, a second, and more failure modes. As for "routing to a cheap model to save quota" — switching to a cheap model isn't "saving," it's "buying less."

**3. It can only "judge," not "do work."** Once it needs to plug into a real workflow, you have to rely on third-party plugins or proxies to move the data around, and most of those projects were written by an individual in two or three days. The failure usually isn't Jev's fault — it's the shell around it.

The lesson these four gave me isn't "Jev is useless," but: **people who want to use it to speed themselves up won't get far; people who build it into products as a component might.** So I changed direction, did two proper rounds of tests, and answered two questions:

One, out of these 60 cases, how many are actually usable today? Two, is Jev's "how confident" number accurate? If not, that third use case ("route by confidence") is empty talk.

So I ran two rounds: Round one, have Jev score 217 Jev projects itself, judge "usable or not," answer the first question, and incidentally verify the "massive classification" use. Round two, generate 100 Chinese news items, pre-label the answers, have Jev make 300 judgments, see whether its "confidence" matches actual accuracy, incidentally test real domestic speed, and bring in a cheap LLM as a control. This was also the only one of my five attempts that truly worked.

### Round One: Having Jev Score 217 Projects Itself

Take the 60 cases plus 167 Jev projects on GitHub — 217 public introductions in total — feed them to Jev, and have it judge each one: "can you get it and use it today?"

1. **Genuinely "ready to use" ones are few, and almost all are interfaces, not applications.** Of the 217, only 15 were judged "usable now" with sufficient evidence, and 14 of them are Jev integrations inside mainstream dev frameworks like pydantic-ai, LangChain, and Vercel AI SDK. The only application is jev-ultrafast — consistent with my labeling it the benchmark.
2. **Demos on X are mostly "the author got it running, but you can't get it."** The buzz is real; the downloadable ones are few.
3. **On the "already integrated into products" five, Jev is more conservative than I am.** It only recognizes SPIRITT and ReqLLM as reachable today.

Limitation: Jev only looked at the text I fed it — no opening links, no running code. It judged "is the public evidence sufficient," not "is the project good." Whether its "confidence" is accurate can't be verified in this round, because I have no ground truth for the 217 items.

### Round Two: Is Its "Confidence" Accurate, and How Fast Is It in China?

100 Chinese tech news items, answers pre-labeled, three questions each, 300 judgments total. The control group is the cheap Qwen 3.8 Flash. Called serially, one by one, from Shanghai.

1. **Every one it said it was "90%+ confident" in was correct.** Of the 300 judgments, 255 were in this tier, all correct. Set 80% as the auto-pass line and you can auto-pass 89% of requests with only 1 error. The "auto-pass when confident" approach, at least on simple tasks, holds.
2. **Shanghai real test was about 0.7 seconds — slower than official, but extremely stable.** The slowest single call was 1.5 seconds; the Qwen Flash control had a similar median, but its slowest was 32 seconds. Jev doesn't win on "fast" — it wins on "no long tail."
3. **Accuracy and cost both break even with a cheap LLM.** 94.7% vs. 93.0%, and each cost $0.003. The official "40–400× cheaper" compares against frontier LLMs; against lightweight models Jev has no edge.

Limitation: the 100 items were made from 25 templates each varied 4 times, so tasks are on the simple side, and "all high-confidence correct" isn't surprising. The 80%–90% tier has only 11 samples, so nothing can be concluded there. The 12 items where Jev and Qwen disagreed were almost all label-boundary issues like "does a cloud database count as application or other" — conclusions depend on how you define labels. To draw production conclusions you need blind tests on real data.

## Overall Judgment

After two rounds of testing, plus the earlier four failures, my view is clear.

**1. Jev is real, but it isn't "a cheaper LLM" — it's a different thing.** Against a lightweight model like Qwen Flash, accuracy ties and cost ties; the only things it adds are stable response time and a confidence number on each answer that you can use for routing. Whoever chooses it for "cheap" chose wrong. It isn't smarter — it turned "judgment" from "writing essays" into "filling in answer sheets," at the cost of only being able to fill answer sheets.

**2. The Jev usable today is an interface inside frameworks, not an application.** 217 projects filtered down to 15 truly usable, 14 of them integration layers in pydantic-ai, LangChain, and Vercel AI SDK. On my own, four times I stuffed it into daily tools and all failed. The demos on X — just watch them, don't expect to use them. **Jev is a part for people building products, not an efficiency booster for people using tools.**

**3. Its only truly valuable use is one: routing by confidence.** High confidence auto-pass, low confidence ask the LLM. In my test, 255 judgments at 90%+ confidence had zero errors. This isn't "replacing LLMs" — it's adding a fast, stable gate in front of the LLM that blocks 80–90% of requests.

**4. But don't go to production today.** Both rounds have samples on the simple side; the 80%–90% tier has only 11 samples. The official account still has a waiting list; OpenRouter works immediately, but that's a third-party channel, not the official service commitment.

**My plan, three steps:**

1. List the places in your business where you currently use a big model but actually only make it return one option. If there are none, don't chase this hype.
2. If there are, pick one, use real historical data with answers pre-labeled by hand, run a blind test, and focus on the real accuracy of the 70%–90% tier.
3. If it passes, add a Jev gate in front of the LLM, start from a 90% threshold, and gradually lower it while watching the data.