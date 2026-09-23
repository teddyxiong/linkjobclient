# Jev Into Claude Code & Codex — a Step-by-Step Tutorial: Turbo-Charge Your Coding Agent's Decision-Making!

**Source:** [@xmglab (小码哥)](https://x.com/xmglab/status/2101932146416075073)

Hi everyone, I'm 小码哥 (Xiao Ma Ge).

Yesterday I shared how Jev beginners can quickly try it out:

Jev opened to everyone today — no more waitlist, just register and use it directly. The speed of this rollout is honestly a bit crazy.

Click in and you can start using it:

> https://console.typesafe.ai

Right now every new user gets a starting **$5** credit, which the official says covers roughly **120 million tokens**; there's no place to top up yet, but top-ups may open later.

Today I'll share **how to use Jev in Claude Code, Codex, and other Coding Agents.** If you don't have time, bookmark it.

## Get the API Key

Open the API keys page and create an API key:

> https://console.typesafe.ai/keys

After you get the API key, save it, and set a `TYPESAFE_API_KEY` environment variable locally. Later you can use it directly in AI tools without worrying about leaking it.

## Jev Model Pricing

Jev isn't a free model, but it's absurdly cheap — cost is **40–400× lower** than other models, and output is free.

## Test With a curl Request

**You can send a request directly:**

```bash
curl -X POST https://api.typesafe.ai/v1/systemone \
  -H "Authorization: Bearer $TYPESAFE_API_KEY" \
  -H "Content-Type: application/json" \
  -d @- <<'EOF'
  {
    "state": "我的 Claude 账号被封号了，一直没有解封，用不了，麻烦帮我看下",
    "model": "jev-latest",
    "questions": {
      "urgency": {
        "type": "noul",
        "instructions": "这个问题和登录有关系吗?"
      }
    }
  }
EOF
```

Test output:

### Using It in a Coding Agent

Jev provides a plug-and-play Skill:

> https://github.com/typesafe-ai/skills

It provides the complete context of the TypeSafe API:

- The three question types;
- Architecture patterns;
- Best practices for organizing evaluations.

This Skill can be used in **Claude Code, Codex, and other Coding Agent tools.**

## Using It in Claude Code

### Install the Skill

Run the following two install commands in the terminal:

```bash
claude plugin marketplace add typesafe-ai/skills
claude plugin install typesafe@typesafe-ai
```

### Use Jev

Anyone familiar with Skills knows that to use a Skill you can directly say "use the TypeSafe skill..." to trigger it, or use the `"/typesafe:typesafe-ai"` slash command to actively invoke the TypeSafe Skill.

For example:

> /typesafe:typesafe-ai Mac mini 我有必要买吗？请直接给判断

It produced a result in 12 seconds, telling me I shouldn't buy a Mac mini right now.

> /typesafe:typesafe-ai 分析下这个项目，判断有哪些可替代复杂的逻辑或弱代码。

The output has an extra "TypeSafe" column indicating which code needs deleting/keeping/extracting into a shared component — TypeSafe just gives the judgment.

### Update the Skill

This applies only to the Claude Code plugin installation:

```bash
claude plugin marketplace update typesafe-ai
claude plugin update typesafe@typesafe-ai
```

Restart Claude Code or run `/reload-plugins` to load the update.

To enable automatic updates, open `/plugin`, then choose Marketplaces → typesafe-ai → enable automatic updates.

## Using It in Codex and Other Tools

### Install the Skill

Run the following install command in the terminal:

```bash
npx skills add typesafe-ai/skills --skill typesafe-ai
```

By default it includes mainstream Coding Agents like **Codex, Cursor, Gemini CLI, and OpenCode**; below you can custom-select others, and finally press Enter to install.

### Use Jev

Same thing — in Codex you use Jev like any Skill; type "/Typesafe" and it will auto-suggest:

Here's a video demo: (see the original article)

### Update the Skill

If you installed via skills.sh, just run `npx skills update` to update.

If you copied the Skill manually, replace the entire skill directory with the latest GitHub version.

## Automatic Install via a Prompt

You can also use a prompt to install automatically:

> Install the TypeSafe skill. If you're in Claude Code, run `claude plugin marketplace add typesafe-ai/skills`, then run `claude plugin install typesafe@typesafe-ai`. If you're in another Coding Agent, run `npx skills add typesafe-ai/skills --skill typesafe-ai` and choose your Coding Agent. Use one of the two install methods. You can read the skill's documentation directly at: https://github.com/typesafe-ai/skills/blob/main/skills/typesafe-ai/SKILL.md (raw version: https://raw.githubusercontent.com/typesafe-ai/skills/main/skills/typesafe-ai/SKILL.md). Then you can use the TypeSafe skill while developing this project.

Send it to any Coding Agent that supports Skills, and it will install automatically according to the current Coding Agent.

Alright, that's it for this Jev installment.

Overall, **the most interesting thing about Jev is that it offers a completely different way of working — it doesn't generate content, but leans more toward helping you do judgment, analysis, and decision-making.**

So I think **the best way to play Jev isn't alone, but together with Coding Agents like Claude Code and Codex — Claude Code / Codex does the work, Jev does the judging.**

Plus the official Skill is already provided, so you basically don't need to wrap the API yourself — just install it and call it directly inside the Coding Agent.

Right now new users still have **$5 credit, about 120 million tokens**, and Jev's price itself is very low — perfect for heavy testing.

Today I only demoed Jev's simple application; it actually has quite a few god-tier scenarios that I'll share later. I'll also keep testing Jev's real-world effectiveness in real projects, code refactoring, and complex technical decisions.

**Follow me if it helped** — I'll keep sharing hardcore, practical content.

I'm 小码哥 (Xiao Ma Ge). See you next time.