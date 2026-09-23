# How to Learn AI Agents (Part 2): From File Servers to Search Engines

**Source:** [@Tedli8](https://x.com/Tedli8/status/2100079128431259676)

Every technology carries its own derived scenarios. Before we get deeper into the current Agent systems, let's follow the thread of the symbolist school and trace the journey of information — from being acquired human-centrically in the past, to being acquired model-centrically today.

## From File Servers to Search Engines

In the 1980s, as personal computers spread, information saw a small-scale explosion. The birth of the internet made communication easier, and many problems emerged along with it. Initially the problem was simple: how do I get a file?

In 1990, McGill University student Alan Emtage developed Archie to search for files on FTP servers. It is generally considered the prototype of the modern search engine.

One might ask: why doesn't this count as a search engine in today's sense? Because back then the internet had no unified Web text standard. It was only when HTML unified content format, HTTP unified the transport protocol, and URL unified resource addresses that crawlers had a unified object to parse. Without unified standards, it was hard to industrialize fast data acquisition, and impossible to support a modern search engine.

Still, before entering the search-engine era, the internet first went through the explosion of portal sites. As standards like HTTP, HTML, and URL matured and the number of sites grew, people naturally needed an entry point to digest the information on the network — much like today's various AI navigation sites.

In 1994, Jerry Yang and David Filo created "Jerry's Guide to the World Wide Web," originally a human-curated directory. In 1995 they founded Yahoo; in 1996 Yahoo went public with a 154% first-day gain and a market cap of $850 million. By January 2000, Yahoo's market cap once reached $125 billion. Given the scale of capital markets at the time, that fervor was no less than today's market pursuit of AI foundation-model companies.

Regrettably, Yahoo did not rise on algorithms, but climbed to the throne of portal king on human-edited directories. Yet as information grew exponentially, human editing had its limit; and once an organization takes shape, it also moves along its own inertia. Even when automated algorithms arrived later, existing departments and interest structures could still hinder innovation.

In 1998, Larry Page and Sergey Brin's BackRub, developed at Stanford, gradually evolved into Google. There are several key techniques in search engines. The first is the inverted index, which looks up documents reversely by keyword: a user enters a keyword, and the engine instantly locates documents containing those words. The second is TF-IDF, used to measure keyword importance. TF is the frequency of a word in a document; IDF is higher when a word appears in fewer documents and lower when it appears in more.

For example, the Chinese particle "的" appears at high frequency in many documents — its TF may be high, but because it's almost everywhere its IDF is low, so its final weight isn't high, and searching it carries little meaning.

Beyond these, there's the famous PageRank. It uses the link relationships among web pages to estimate page authority: a page cited by more high-quality pages generally gets a higher ranking weight. Around the same time, Robin Li's RankDex also explored ranking pages via link relationships, and later became the early foundation of Baidu's search technology.

Many people today scoff at Baidu, but back then it genuinely was a major internet company — especially before Google exited China and Baidu came to dominate the domestic search market.

A company often forms various interest departments along the inertia of its past organization, and a new business unit, worn down layer by layer, can very easily distort what were originally sensible market moves.

## From Search Engines to Recommendation Algorithms and RAG

The term "information cocoon" was once very popular. It describes the phenomenon where recommendation algorithms keep showing people what they want to see, so that over time people become trapped in familiar information and find it harder and harder to see outside viewpoints.

When people think of recommendation algorithms, many think of video-feed and text-feed recommendations. In fact, an early industrial form was the CTR (click-through-rate) model in search advertising — predicting a user's click probability. This was also the field where feature engineering shone before deep learning became widespread.

Before deep learning became mainstream, a common CTR prediction approach was GBDT + LR: first use gradient boosting decision trees to extract and combine user features, then use logistic regression to predict click-through rate.

Google proposed Wide & Deep in 2016, splitting the model into two parts, each doing a different job.

The Wide part is a linear model responsible for "memorization." It remembers high-frequency feature combinations — historical patterns like "beer + diapers."

The Deep part is a deep neural network responsible for "generalization." Through embeddings it maps sparse features into low-dimensional vectors, mining combinations that never explicitly appeared in history but might be latently related. The outputs of the two parts are added and trained jointly: one remembers the past, the other extrapolates the future — that's the core idea of Wide & Deep.

Of course, Wide & Deep has its shortcomings: many of its cross features still require manual design. Huawei's Noah's Ark Lab proposed DeepFM in 2017, combining factorization machines with deep neural networks so the model could learn both low-order and high-order feature interactions simultaneously, reducing reliance on manual feature engineering.

In e-commerce recommendation, collaborative filtering has long been an important route. Its idea is simple: why should a particular product be recommended to a particular user?

The answer often lies not only in the product itself, but also in people. User-based collaborative filtering doesn't rush to analyze a product's attributes; instead it looks at what people similar to you bought and liked. If a group of people overlaps heavily with your taste, the items they bought that you haven't probably suit you too, so the system recommends them.

Another common method is item-based collaborative filtering. It changes the angle: instead of finding similar people, find similar items. If people who like item A tend to also like item B, then A and B are similar. When you add A to your cart, the system conveniently recommends B. In scenarios where item relationships are relatively stable, this method is usually easier to maintain and reuse.

The benefit of these methods is that you don't need to understand what a product actually is — as long as you have enough user-behavior data, recommendation relationships grow on their own. But the shortcoming is also clear: at cold start, with no behavioral data, recommendation is hard; and the more a user uses it, the more easily they may be pushed toward their familiar circle — what later came to be called the information cocoon.

Later, ByteDance and others applied similar ideas at scale to text-feed and video-feed recommendation. The specific models have kept evolving, but the basic goal — learning preferences from user behavior and predicting the next interaction — hasn't changed.

At this point, we've actually arrived at a key crossroads.

Whether collaborative filtering or CTR models like DeepFM, recommendation systems on the surface make all kinds of predictions — computing similarity or estimating click rate — but behind them lies one important action: mapping discrete, sparse, semantically meaningful objects into low-dimensional dense vectors. A user's age, a product's category, every video you've clicked, can all end up as a string of vectors waiting for the model to compute and compare.

This action is something recommendation systems have done for many years, accumulating mature industrial experience. It later provided an important engineering foundation for vector retrieval and RAG.

The objects of the two differ: recommendation systems vectorize "people and things," computing "what you might like"; RAG vectorizes "knowledge and questions," seeking "which passage is most relevant to your query." The goals differ, but both can use embedding vectors to compute similarity in vector space.

Thus, when LLMs needed an external "memory store," this retrieval capability — repeatedly validated in search and recommendation systems — was naturally ported over. Only this time, the knowledge vectors are stored separately in a vector database for the model to retrieve when answering.

## From ChatBot to Agent

ChatBot is actually nothing new. As early as 1966, MIT's Joseph Weizenbaum wrote ELIZA — a program that relied on pattern matching to act as a psychotherapist. It could make you feel you were talking to a machine, but underneath it was only looking for preset phrases among keywords. In the decades since, from A.L.I.C.E. to various rule-based customer-service bots, ChatBots have been stuck on the same thing: they can only respond, never act.

The real turning point came from LLMs.

At the end of 2022, ChatGPT let a machine speak coherently, appropriately, and with context for the first time. It no longer relied only on keyword matching, but on the language ability learned from massive corpora. Overnight, ChatBot went from "artificial idiot" to "can talk about anything."

But no matter how well it talks, it's still just talking. Many enterprises used the aforementioned RAG to build corporate knowledge Q&A assistants — an extension of search capability, and a reflection of the model's capability boundary at the time.

In March 2025, Manus was officially released, positioning itself as a "general Agent." It wasn't just a chat assistant; it could use LLMs to break down tasks and call tools. After its demo video was released it went viral, and invitation codes were once bid up to high prices.

Still, some in the tech community disliked this marketing approach. Open-source projects like OpenManus appeared, letting more people see the basic prototype of an Agent at the time: calling the LLM in a multi-turn loop to select and use tools to complete tasks. Limited by the model capability and engineering polish of the time, OpenManus's real-world results still trailed commercial products.

On February 24, 2025, Claude Code was released together with Claude 3.7 Sonnet, initially as a research preview. It was one of the earlier agentic coding tools to adopt a terminal form, and it made the value of vertical Agents more concrete.

By the second half of 2025, Claude Code had spread rapidly among programmers and kept fueling a new round of AI-coding narratives. Cursor, which had long plowed the coding track, quickly followed. Today, Cursor and Anthropic (behind Claude) are both interdependent and competitive.

In early 2026, OpenClaw (previously named Clawdbot, then Moltbot) quickly went viral. It brought little fundamental innovation, but cleverly integrated terminal-style interactive apps like Telegram and Slack, letting more people intuitively feel a resident personal Agent for the first time. Yet its setup and security configuration still pose a barrier for non-developers, so many vendors began offering packaged installation and hosted solutions.

Since then, OpenClaw has also faced skepticism over engineering maturity and security boundaries; meanwhile, other open-source projects like Hermes Agent continue to evolve. On the commercial side, we've seen tools like Codex and Claude's desktop app; domestic tech giants have generally bet on the AI office track, with products like WorkBuddy, Qwen (千问), and Doubao all exploring how Agents can boost work efficiency.

## Summary

This installment reviewed the evolution of symbolism-related technology and products without going into specific technical details. Later I may first cover a few domestic vendors, before truly getting into the technical details.

Regarding AI Agents, I think there's no need to be overly anxious. Agents can indeed raise production efficiency, but a barrel's capacity is determined by its shortest stave. AI can lift the production side — but how do we lift the consumption side? It's like a message queue: overproduction only makes messages pile up, while consumption capacity is always limited.

Inside enterprises, the existing organizational structure also slows AI adoption. The overall efficiency of a process is often determined by its slowest link. So it's best to take it in stride.