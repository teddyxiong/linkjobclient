# Jev Model From 0 to 1: A Beginner's Tutorial

**Source:** [@ai_xiaomu (黄小木)](https://x.com/ai_xiaomu/status/2101135680168771979)

You've probably seen the "Jev model" in your feed recently — what is it?

It fundamentally can't talk. It can't chat with you, won't write documents, won't write code.

But this strange thing has broken out in the AI world in the last couple of days, raising a $40 million seed round, with a pile of people queuing to apply for trials.

So what is Jev?

## The Birth of Jev

Jev comes from a San Francisco company called TypeSafe AI, released just on September 15, 2026.

Its founder Diogo Almeida is a former OpenAI researcher and one of the co-inventors of RLHF.

It was precisely this method that turned cold language models into the articulate, empathetic ChatGPT back then.

In other words, he's one of the people who trained AI to be so good at chatting.

And now, the person who taught AI to talk has personally built an AI that pointedly doesn't talk.

The motivation, stated plainly, is also quite simple.

He said a question has bothered him for the past four years: models long ago surpassed humans at conversation, so why is real automation still so scarce? We've poured in trillions of dollars, but ordinary people's daily lives haven't really changed, and the vast majority of software hasn't become truly intelligent.

## What Is Jev?

Models like ChatGPT can be understood as an articulate consultant.

Ask it anything and it answers, can cite references and chat for ages, emotionally intelligent, and can take on any topic.

Jev is another species.

It's like that focused quality inspector next to the assembly line: you hand over a material, and he doesn't explain, doesn't make small talk, doesn't share opinions — he just gives you a crisp verdict.

The models we touch daily, like Doubao, are characterized by slow, effortful reasoning — like helping you solve a complex math problem.

Jev's characteristic is intuitive judgment — like the instant you see a face you know whether the other person is angry.

Simply put: "one glance, result out."

## Why a Chatty Chatbot Is Actually the Bottleneck

Suppose you run an online store and hundreds of customer-service messages come in each day; you want AI to automatically route them to different teams: billing to billing, logistics to logistics, technical issues to technical.

Sounds like a simple requirement.

If you do it with a normal LLM, the actual process goes like this:

Step one: you write a long prompt, earnestly begging it, "Please determine which department this message belongs to. Note, just reply with the department name, don't say anything else."

Step two: sometimes it obediently replies "billing department," and you're happy.

But other times it can't help itself and replies with a whole paragraph: "This message appears to be mainly about a billing issue; I'd suggest you first verify the charge records, and then…". It's too eager to help and can't control its mouth.

Step three: to extract the word "billing," your program has to write a bunch of extra logic to fish the keyword out of that verbose reply. This process is messy and error-prone.

Step four — and the most deadly — it occasionally glitches.

You clearly only set three departments, but it returns a fourth, or simply invents a non-existent department name. This is what people call "hallucination."

Where's the root of the problem? It's that text is simply too free.

Freedom is the virtue of chatting. Precisely because it can generate any text, an LLM can chat with you, write poems, and make up stories. But the moment you want to use it for automation, that freedom instantly becomes a nightmare. You can never 100% guarantee it won't suddenly veer off next time. Even if the probability of going off-rails is only one in ten thousand, you daren't bury it in an unsupervised system and let it run on its own.

If AI is unreliable, uncontrollable, and unpredictable, it can't be trusted — and therefore can't be built into real software at scale.

## Jev's Breakthrough: Turn "Q&A" Into "Filling a Form"

Jev's idea is to completely change the interaction model.

You don't need to converse with it.

You hand it a form with a fixed structure, and it only needs to check the boxes you've drawn.

Each call, you give it two things.

The first is called "state" — the material to be judged.

It can be as simple as one sentence, like "my card was charged twice." Or as complex as an entire ticket record, a complete customer-service conversation, or structured data with order info and refund policy.

You lay all the needed background before it at once — like spreading all the materials on the table before asking a panel of experts to judge.

The second is called "questions" — what you want it to judge.

What it returns is always a well-behaved, fixed-format answer. Your program can use it directly — no parsing, no cleaning, no guessing.

More crucially, the official hard guarantee: it's mathematically impossible for it to fill the format wrong, or to give an answer outside the form.

Because all possible answers are locked down by you in advance. It can only choose within the options you gave, and can't step out of bounds.

So whatever type of answer you ask for, it will return exactly that type — which provides the foundation for stable operation.

## Jev's Features

### The First: Multiple-Choice

A customer message comes in: "My running shoes came in the wrong size — can I exchange for size 10?" You ask it "which team should this be assigned to?" with three options: returns/exchanges, logistics, billing.

It will decisively reply "returns/exchanges." And it doesn't just give one answer — it also tells you how confident it is in each option. This message is clear, so it's almost 100% sure it's returns/exchanges, with the other two nearly zero.

If the message becomes "the shoe size is wrong, and my credit card somehow got an extra charge — what are you going to do about it?", this one isn't so clean.

It might tell you: 60% looks like returns/exchanges, 40% looks like billing. Jev doesn't pretend to be certain — it honestly lays out the dilemma for you to see.

### The Second: Rating

A bug report comes in; you give it a three-notch ruler: score 0 is just a cosmetic flaw that doesn't affect use; score 1 is a broken function, but there's a workaround; score 2 is completely stuck, totally unusable.

It might reply "1.3".

A score of 1.3 means the bug mainly belongs to the "broken but with a workaround" tier, but leans slightly toward "completely stuck." This is far more precise than forcing an all-or-nothing choice between 1 and 2, and closer to reality.

When you describe each tier, describe the specific situation rather than the degree. For example, writing "broken but with a workaround" is good — it can compare that phrase against the material.

But if you only write "moderately severe," it's lost, because "moderate" is an empty word with no reference point.

Likewise, it can't actually see the number before each tier. Just writing 0, 1, 2 and expecting it to figure out which is more severe is useless — you have to spell out in detail, as an SOP, what situation each tier actually is.

### The Third: True/False

It only answers yes or no, giving you a number for "how likely is it a yes," from 0 to 1.

For example, ask it "is this customer asking for a refund?" It replies 0.99, meaning almost certainly yes.

So in the same call you can simultaneously ask: which team to assign this to (choice), how angry the customer is (score), whether they're asking for a refund (true/false), whether the tone is already furious (true/false), and whether it mentions an unshipped order (true/false).

These questions are answered simultaneously, in parallel, each independently. So asking a few more questions barely lengthens its response time.

This leads to a very unusual programming habit: the official guidance encourages you to ask as much as possible. Ask every judgment your program might use on this message all at once — even if some answers aren't used this time, it barely costs extra money or time.

This is the complete opposite of the "ask as little as possible to save tokens" mindset when using normal LLMs.

### Jev Can Judge Itself

Normal LLMs have an incurable flaw: whether or not they understand, they answer with extreme confidence — like Doubao.

Used in automation, this flaw is fatal.

For example: suppose an AI can do something right 95% of the time — sounds okay, right? But if you don't know what causes the wrong 5%, you fundamentally can't hand that thing to it to run automatically.

Jev attaches a "confidence" to every answer — officially called confidence — and you can use this value to judge whether the model actually understands.

With this confidence, you can design very human-like handling logic, usually in three tiers:

High confidence: process automatically, no human needed, let it run with confidence.

Moderate confidence: be cautious — have a human confirm first, or go fetch more information and re-judge.

Very low confidence: don't force it — escalate to a human, or hand it to a more expensive, stronger reasoning model. It's explicitly telling you: this is beyond my ability, don't push me.

This mechanism of "act only when confident, honestly call for help when unsure" is the prerequisite for genuinely trusting an automation system.

An AI that can say "I don't know" is far more reliable than one that's perpetually confident.

### Jev Is Cheap Enough

Jev is about 200× faster and about 400× cheaper than big models of the same tier.

A single response takes only 70–500 milliseconds, faster than your blink.

How is it so absurdly fast? One sentence: because Jev doesn't need to talk.

This pricing strategy opens up a whole range of uses we previously wouldn't dare imagine.

You can use it to sift through a massive database record by record and tag each one — doing that with LLMs used to cost so much no one would touch it.

You can also embed it in an interface for real-time reactions, because it's fast enough that users feel no latency.

## How You Should Use Jev

### Define the Question

Don't ask big, vague questions — break them down into many small, concrete sub-questions, then combine the small answers in your program.

For example.

You want it to judge whether an email is spam. The laziest way is to directly ask: "Is this email spam?"

That's a big, ambiguous question.

Behind it actually hide many judgments, all crushed into one vague answer — you can't see why it judged that way, nor adjust it.

What you should do is break the big judgment "is it spam" into several small, clear sub-judgments, and ask each separately:

Is this email asking for login credentials like a password? Is it claiming you won a grand prize you never entered? Is it creating a "act now or miss out" sense of urgency? Does the organization the sender claims to be match the email's domain? Is the landing URL of the link in the email the same as the text it displays?

Each sub-question is extremely specific, so specific there's almost no room for ambiguity. Then in your program, weight and combine these small answers by importance to compute a final spam-risk score.

What Jev wants to do is give you a new building block with some common-sense judgment — not an uncontrollable black box.

## Define the Scenario

The scenarios where it can land are actually very down-to-earth — many are the grinding, laborious tasks that could only be hard-reviewed by humans before.

Customer service is the most typical.

Auto-routing tickets, identifying whether a customer is asking for a refund, judging which customer is about to blow up and needs priority calming, and extracting the customer's needs and follow-up items from call records.

All of this used to require a person to review one by one.

Content moderation is another big area. Automatically pick out spam ads, abuse, fraud, and privacy-leaking content, and grade by severity — warn lightly, ban outright for serious ones. This work exhausts and demoralizes people, so it's perfect to hand to it.

Hiring and lead-finding also work. Score resumes against your hard criteria, judge whether a candidate's experience fits the role, or judge whether a potential customer is worth a salesperson following up.

Another clever use is being a quality inspector for other AIs. Use Jev to check another LLM's output: did it go off-track, was it jailbroken by someone's phrasing into saying what it shouldn't, is the information it cited fabricated, and are the parameters it passed to tools correct.

Because Jev is fast and cheap, using it as a gate costs only a fraction of the big model itself — like adding a quality check to expensive AI for small money.

Finally, big-data cleaning. Quickly tag, classify, and find the small part you actually need within massive documents, comments, and chat logs. The scale of this work is often so large that only Jev-level cost makes it playable.

## A Final Word

If you still don't get it after reading this far, just remember this line:

Jev is cheap, fast, and can't talk — but it can help you make judgments.

Every time the cost of intelligence drops by an order of magnitude, the scenarios that use it explode exponentially — and that's your opportunity too.

**黄小木 (Huang Xiaomu)｜T11 engineer｜This article was created by opus5.0; please point out any infringement｜Continuously sharing AI news, side-income ideas, and thoughts on programmers transitioning to OPC｜X: @ai_xiaomu**