# Translation Brief — 《前线部署工程师》→ English

Source: https://fde4.ai/book/ (version 1.0.24)
Author: 范冰 (Fan Bing)
Author's repository: https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer

## Task

Translate one Chinese source file into natural, publication-quality **English**, and write the
result to the assigned output path. Do not summarize, shorten, skip, or "improve" the content.
The English edition must be a complete, faithful rendering of the Chinese original —
every paragraph, every bullet, every table row, every figure and footnote marker.

## Hard rules

1. **Completeness.** Translate every section in the source file, start to finish. Long chapters
   stay long. If the source has 40 headings, the output has 40 headings.
2. **Markdown structure preserved.** Keep heading levels, blockquote (`>`) markers, numbered and
   bulleted lists, tables, bold/italic emphasis, inline code, and horizontal rules exactly as they
   map in the original. Do not renumber or merge headings.
3. **No translator's notes inside the body.** Do not insert `[TN: ...]`, explanations, or
   commentary. Translate directly. (The only exception: keep parenthetical English glosses the
   author already wrote, e.g. 「前线部署工程师（Forward Deployed Engineer，简称 FDE）」.)
4. **Names and proper nouns.** Use the entity's real English name where one exists
   (company, product, person, institution). If the source already prints the English name, reuse it
   verbatim. Do not invent names. Standard renderings:
   - 范冰 → Fan Bing
   - 鲍勃·麦格鲁 → Bob McGrew
   - 希亚姆·桑卡尔 → Shyam Sankar
   - 斯蒂芬·科恩 → Stephen Cohen
   - 彼得·蒂尔 → Peter Thiel
   - 卡普 → Karp (Alex Karp)
   - 纳比尔·库雷希 → Nabeel Qureshi
   - 麻省理工学院 NANDA 实验室 → MIT's NANDA Lab (write it plainly, e.g. "the NANDA Lab at MIT" — do NOT write "MIT NANDA (the NANDA lab at MIT)")
   - 《生成式人工智能的鸿沟》 → *The GenAI Divide*
   - 《指环王》 → *The Lord of the Rings*
   - 《美国乐观主义者》 → *American Optimist*
   - 《硬地骇客》 → *Hardcore Hacker* (Yingdi Haike podcast)
   - 《财富》 → *Fortune*
   - 兰德公司 → RAND Corporation
   - 标普全球 → S&P Global
   - 麦肯锡 → McKinsey
   - 黑石集团 → Blackstone
5. **Terminology — use this glossary consistently.**
   | 中文 | English |
   |---|---|
   | 前线部署工程师 / FDE | Forward Deployed Engineer / FDE |
   | 平台工程师 | platform engineer |
   | 三角洲（内部代号） | Delta (internal codename) |
   | 部署 | deployment / deploy |
   | 交付 | delivery / deliver |
   | 客户现场 / 驻场 | customer site / on-site, embedded |
   | 续约 | renewal |
   | 客户成功 | customer success |
   | 售前 | pre-sales |
   | 售前工程师 | solutions engineer |
   | 实施工程师 | implementation engineer |
   | 咨询顾问 | consultant |
   | 甲方 | the client side |
   | 外包 | outsourcing |
   | 项目制 | project-based (business model) |
   | 通用产品 / 可泛化性 | general-purpose product / generalizability |
   | 需求文档 | requirements document |
   | 用户调研 | user research |
   | 痛点 | pain point |
   | 工作流 | workflow |
   | 智能体 | agent (AI agent) |
   | 大模型 | large language model (LLM) |
   | 上下文 | context |
   | 生产环境 | production |
   | 开箱即用 | out-of-the-box |
   | 4 0 法则 / 40 法则 | Rule of 40 |
   | 净收入留存（NRR/NDR） | Net Revenue Retention (NRR / NDR) |
   | 训练营 | Bootcamp |
   | 签约额（bookings） | bookings |
   | 调整后经营利润率 | adjusted operating margin |
   | 非通用会计准则 | non-GAAP |
   | 财年/季度 | fiscal year / quarter |
   | 市销率 | price-to-sales (P/S) |
   | 附录 | Appendix |
   | 后记 | Afterword |
   | 自序 | Preface |
   | 出处见附录 C | (Source: Appendix C) |
   | 详见 | see |
6. **Numbers, dates, money.** Keep every figure identical to the source. Convert Chinese number
   conventions to natural English (95% → 95%; 三四百亿美元 → $30–40 billion; 4000 亿美元 →
   $400 billion; 42.6 亿美元 → $4.26 billion; 两千万美元 → $20 million; 十九个小时 → 19 hours).
   Keep years as-is (2003, 2025, 2026).
7. **Tone.** The original is vivid, confident, journalistic business writing with a narrative
   pulse. Match it in English — plain, punchy, concrete. Avoid stiff literal translation and avoid
   adding flourish the author did not write. Quotes should read like real speech.
8. **Tables and lists** must stay tables and lists, with all cells translated.
9. **Do not add a title, subtitle, or byline that is not in the source.** The document header
   (below) is the only addition.

## Required document header

Every translated file MUST begin with exactly this block, with the placeholders filled in
(do not alter the wording, keys, or order):

```
---
title: "<ENGLISH TITLE>"
original_title: "<CHINESE TITLE, e.g. 第 1 章 FDE 的崛起>"
book: "The Guidance Book of Forward Deployed Engineer"
author: "Fan Bing (范冰)"
source_url: "<FDE4 URL>"
source_file: "<GITHUB BLOB URL>"
repository: "https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer"
edition: "v1.0.24"
language: "en"
note: "English translation of the Chinese original"
---

> **Original text (Chinese):** [<CHINESE TITLE>](<FDE4 URL>)
> **Author's repository:** [github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer](https://github.com/xdash/FDE-the-Guidance-Book-of-Forward-Deployed-Engineer)

---

```

Then the translated body starts with the H1 heading (e.g. `# Chapter 1 · The Rise of the FDE`).

## Output

Write the finished file with the Write tool at the exact path you were given. Then reply with a
2-line confirmation: output path + source word/heading count sanity check.
