---
title: "Afterword · The Professional Ethics of the FDE"
original_title: "后记 FDE 的职业道德"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "https://fde4.ai/book/09-%E5%90%8E%E8%AE%B0-FDE%E7%9A%84%E8%81%8C%E4%B8%9A%E9%81%93%E5%BE%B7"
source_file: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer/blob/main/09-%E5%90%8E%E8%AE%B0-FDE%E7%9A%84%E8%81%8C%E4%B8%9A%E9%81%93%E5%BE%B7.md"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [后记 FDE 的职业道德](https://fde4.ai/book/09-%E5%90%8E%E8%AE%B0-FDE%E7%9A%84%E8%81%8C%E4%B8%9A%E9%81%93%E5%BE%B7)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

# Afterword · The Professional Ethics of the FDE

Every book that teaches methodology must, at its end, confront one question: once you have mastered the method, where are its boundaries? The topic this book addresses is heavier than most methodology, because what the FDE holds in their hands is no ordinary technology—it is the deepest secrets of the client's organization, and a growing power to make decisions on behalf of people.

The nature of an FDE's work determines what they will see. To deliver well, you must look at the client's most authentic operational data—including the ugly parts; you must map the organization's power structure—including who is incompetent and who has fallen from favor; you must touch the core business processes—including those workarounds that skirt the gray areas. The client lays all of this open to you on the basis of a simple understanding: that you are there to help. That trust is the foundation of the FDE model, and to destroy it takes only a single overstep.

I believe the professional ethics of the FDE rest on at least six bottom lines, which I set down here to share with all who do this work.

**First, data sovereignty belongs to the client.** The data you see on the customer's site—not a single byte should appear where it does not belong—must not feed into AI training data (unless explicitly authorized by contract), must not feed into case-study material (unless the client consents in writing), and must not feed into small talk at your next job interview. The principle of least privilege is not merely a technical specification but a professional ethic: do not look at what you need not see, and anonymize whatever you can.

**Second, report results honestly, including the bad news.** In an outcome-based billing model, the greatest moral hazard is to whitewash results—to dress up "the system went live" as "value was realized," to pass off correlation as causation. The value-measurement system in Chapter 6 can be the most honest of tools or the most sophisticated lie machine; the only difference lies in the human heart. The FDE's standing rests on being "willing to be tested"—so when testing reveals a poor result, present it with the same attitude.

**Third, do not manufacture dependency, and do not sell fear.** In this industry there are two hidden practices: one is to deliberately build the system as a black box so the client can never leave you; the other is to inflate the panic of "you'll die if you don't use AI" to close deals. Gartner predicts that by 2028, 70% of enterprises will be forced to abandon forward-deployment-led solutions because of cost and the hollowing-out of skills—a warning bell for the entire industry.

And the healthy FDE model is one where delivery ends only when the client can run it themselves—transfer the knowledge to the client, and let the capability settle into the client's team.

**Fourth, take seriously the people who are replaced.** The systems an FDE delivers will, in many scenarios, genuinely displace a portion of people's work. This book covers a great deal of "change management" technique, but beyond technique lies ethics: do not celebrate efficiency in front of those displaced; do not write people into a plan merely as a "cost line" without offering a way forward; do not play dumb about whose fate you are "changing." Do not hide behind "technology is neutral"—the choices a deployer makes every day are themselves a stance.

**Fifth, say no to what the client asks for but should not have.** You will encounter requests that skirt the edge of compliance: "help us make employee behavior monitoring a little more granular," or "these data are a bit blurry on compliance, but let's connect them first and deal with it later." The "French waiter" metaphor carries its deepest meaning here—true professionalism is not satisfying every client demand, but daring to guide the client toward what is genuinely good for them and harmless to the world. The confidence to say no comes from having other clients on your books; so morality has always been bound up with the business model.

**Sixth, remember that you represent "technology" itself.** For many clients, you are the first face they meet in contact with AI. Every time you overstate, you draw down the entire industry's credibility in their eyes; every time you deliver, you make a deposit for the whole industry.

The guardrails you design also make decisions on behalf of ordinary people—Anthropic's engineering team publicly reviewed a figure: when a system pops up an approval prompt for everything, users will approve about 93% of requests, and the more they see, the less carefully they look, so "human-in-the-loop" becomes meaningless in fatigue; thus the person who designs the guardrails cannot assume the gatekeeper is always alert. As AI penetrates ever deeper into the workings of society, the deployer is the final translator between technology and human daily life—and the cost of a distorted translation is paid by everyone.

These six bottom lines are, in turn, a litmus test for choosing your employer. On the 2026 job market, roles carrying the FDE title surged within a year, yet only about one in ten engineers were willing to do this work—the gap between supply and demand is crowded with followers jumping on the bandwagon. Under the same title, a role at a frontier lab is "software engineering plus customer site," while a follower company's role may be nothing more than on-site outsourcing under a renamed label: one engineer, after joining, found the company only wanted him to do project coordination and had no intention of letting him write a single line of code, and resigned after four weeks. (Source: Appendix C)

Before entering the field, ask one more question—does this role write production code, and does on-site experience feed back into the product—far more important than salary negotiation.

Palantir itself is a company full of controversy: its history of serving intelligence and military agencies leads many to regard everything about it—including the FDE model—with wariness. My extensive citations of its methodology in this book do not amount to endorsing all of its client choices. On the contrary, precisely because the domains it serves are so sensitive, the disciplines in its engineering culture around permissions, auditing, and need-to-know are all the more worth learning from.

Nabeel Qureshi, who spent nearly eight years as an FDE at Palantir, divided the projects he handled into three categories by moral character: morally neutral, clearly for good (pandemic response, combating child exploitation), and gray-zone (military, immigration, policing). Faced with the gray zone, his answer was neither to pursue moral purity nor to turn and walk away, but to "stay in the room"—to preserve his own vote at the decision table. I cite this taxonomy because it is closer to the deployer's real situation than either "resist" or "comply": most moral dilemmas arise precisely in the gray zone, and walking out to hand the room to someone less scrupulous is not necessarily the more ethical answer.

The FDE is a young profession whose rules of conduct have yet to be written by anyone. I hope this book becomes its first boundary marker.

## Acknowledgments

I would like to thank Bob McGrew, Barry, Ted Mabry, Nabeel Qureshi, and other former Palantir employees for their public recollections and writings—you turned the methodology of a "mysterious company" into public knowledge; thanks to the hosts of podcasts such as YC Lightcone and Latent Space, whose probing questions preserved a wealth of first-hand experience; thanks to a16z, MIT's NANDA Lab, The New Stack, and CIO.com for their research and reporting; and thanks to China's pioneering FDEs for the reflections they set down on the official website—thanks to you, this conversation in the Chinese-speaking world did not have to start from zero.

Thank you to everyone who has read this far. May the roads you build be walked by others; may the road remain after you have finished walking it.
