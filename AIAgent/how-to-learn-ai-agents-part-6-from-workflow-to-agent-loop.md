# How to Learn AI Agents (Part 6): From Workflow to the Agent Loop

**Source:** [@Tedli8](https://x.com/Tedli8/status/2101541356959125864)

Since ChatGPT's release, the center of gravity of LLM applications has been shifting: at first people cared about "how to make the model answer better"; later the question became "how to make the model call tools and keep finishing a task." This isn't an overnight leap from ChatBot to Agent, but a gradual progression from single-turn Q&A, to RAG, to fixed Workflows, and finally to the Agent Loop that adjusts actions based on environmental feedback.

## Stage One: Making the Model Answer Better

At the end of 2022, ChatGPT brought multi-turn conversation to the public. Users could not only ask directly, but also add context, specify roles and output formats, and even use prompts like "analyze first, then answer" to make the model invest more reasoning into complex problems.

But the early experience still centered on one or a few model calls: input a question, the model generates an answer, and the task ends. It's very good at organizing existing knowledge, but can't naturally know what happened after its training data, nor automatically access internal company materials.

RAG therefore became the key patch. The system first retrieves web pages, documents, or a knowledge base based on the user's question, then puts the relevant content into context so the model can answer with new information. Prompt engineering decides "how to ask," and context engineering decides "what to show the model"; both improve the input to each model call.

Workflow goes a step further: it strings multiple model calls and tool steps into a pre-designed process — for example, first classify the question, then retrieve materials, then generate the answer, and finally do a check. Tools like Dify and LangGraph help orchestrate this process. Its strengths are clear paths, predictable costs, and relatively stable results; its weakness is that when the situation isn't anticipated by the designer, it's hard to change course on the fly.

## Stage Two: From Answering to Completing Tasks

The key to an Agent isn't that the UI gains an "agent" button, but that control changes hands. A Workflow's path is mostly written in advance by the programmer; an Agent lets the model dynamically decide the next step — which tool to use, whether to switch approach, and when to stop — based on the current goal and environmental feedback.

A minimal Agent Loop can be written as: read the goal and context, call the model; the model chooses a tool; the system executes the tool and returns the result; the model observes the result and keeps reasoning. This process repeats until the task is done, the maximum steps are reached, or more user input is needed.

```python
while not done:
    action = model(goal, context, tools)
    result = run(action)
    context.append(result)
```

The code is short; what's genuinely hard is the engineering outside the loop: whether tool descriptions are clear, whether the model can judge success, whether errors can be recovered, how context is managed in long tasks, where sensitive operations require human confirmation, and how to prove through evaluation that it really completed the task.

## Why Coding Agents Broke Out First

Programming naturally suits agents: the goal can be decomposed into reading code, searching, modifying, running tests, and checking results; tool interfaces are relatively clear; and test/build results provide timely feedback. In February 2025, Anthropic released Claude Code as a research preview; around the same time, products like deep research and browser operation also began demonstrating the value of multi-step execution.

The improvement in model capability also doesn't only come from larger pretraining. Reinforcement learning aimed at reasoning, tool use, and real tasks lets the model practice "take action — see result — keep adjusting" in a feedback-rich environment. But a stronger model doesn't mean the Agent is automatically reliable: the longer the task, the more errors accumulate, so sandboxes, permission control, stopping conditions, logging, and human confirmation all remain important.

Mechanisms like Skills, plugins, and MCP are solving "how to reuse capability." They wrap operation instructions, tool interfaces, and domain knowledge into modules the model can discover and call. Agent Harness, which emphasizes plug-in architecture, also lowers the cost of building vertical Agents: the same loop, through assembling different tools and rules, can become a coding assistant, a research assistant, or an enterprise-process assistant.

## How to Choose Between Workflow and Agent

They aren't substitutes for each other. For fixed, repetitive, rule-clear tasks, prefer Workflow — for example generating the same-format report weekly, or reviewing forms by fixed rules. For tasks with open paths, steps that can't be enumerated in advance, and a need to change strategy based on intermediate results, the Agent is more suitable — for example fixing defects in an unfamiliar codebase, or doing deep research across multiple sources.

The most practical approach is usually hybrid: use Workflow to fix boundaries, approvals, and key nodes, and use the Agent to handle the parts that need judgment and exploration. That preserves controllability while gaining dynamic problem-solving.

When choosing, ask four questions: Can the path be fixed in advance? Can the result be verified automatically? How costly is failure? Is the extra time and tokens from more steps worth it? An Agent's value isn't in "being able to loop," but in getting real feedback from the environment each loop and getting closer to the goal as a result.

## From ChatBot to Agent: What Really Changed

ChatBots mainly output text, Workflows process tasks along a set route, and Agents choose actions in a loop. All three may share the same underlying LLM; the difference is how much context the system gives it, which tools, and how much decision-making power.

To understand Agents, you don't need to memorize all frameworks first. Grasp one core point: the model no longer just generates answers, but works in a loop of "think — act — observe — adjust." What's worth studying next is how to make this loop more reliable, cheaper, and easier for people to supervise.

## Further Reading

- OpenAI: A practical guide to building agents: https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/
- Anthropic: Building effective agents: https://www.anthropic.com/engineering/building-effective-agents
- Anthropic: Claude Code research preview: https://www.anthropic.com/news/claude-3-7-sonnet
- OpenAI: Introducing deep research: https://openai.com/index/introducing-deep-research/