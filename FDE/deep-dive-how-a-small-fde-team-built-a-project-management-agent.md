# Deep Dive | How a Small FDE Team Built a Project-Management Agent

**Source:** [@xiaomanhedy (Hedy Zhang)](https://x.com/xiaomanhedy/status/2095848872832622924)

As an FDE, project management is a problem you can't avoid. Recently we just got a project-management Agent workflow called "Musk" running on Feishu (Lark), so let me quickly break it down and review it with everyone ~

We built a pile of traditional project-management tools, and they all ended up dying of "maintenance costs being too high." Looking back, these 5 friction points are what really kill small teams:

1. **High entry friction:** important conversations are scattered across phone calls, WeChat, Feishu, and DingTalk; recalling them by human memory after meetings is highly error-prone. Updating status means sitting in front of a computer and opening a multi-dimensional table (database), so if you're not at your desk, it gets shelved entirely.
2. **Proper-noun recognition wrecks:** generic voice transcription frequently mistypes customer names, internal codenames, or product abbreviations that sound similar; one wrong character derails all subsequent summarization and retrieval.
3. **Multi-person conversation roles become a mystery:** the recording is fully transcribed as "Speaker 1/2," so you don't know who made which commitment or who owns which to-do; the effort of a second manual check exceeds just taking notes by hand.
4. **The project stopped, but AI keeps chasing:** with chat-only management, projects that were canceled or paused midway aren't structurally flagged, so AI lacks a unified "source of legal status" and keeps pestering you about tasks from closed projects based on old conversations.
5. **Simple operations have overly long paths:** just checking a piece of data or doing a small scrape requires "opening the computer, connecting remotely, finding the project directory" — a series of tedious steps whose prep time far exceeds the task itself.

The project-manager Agent we built is meant to automatically organize the information scattered across communications into continuously trackable project records, while also providing a unified, low-friction entry point for lightweight tasks. Whether a project should continue is still decided by humans.

Now this process can already complete a relatively complete chain:

> **Auto-record conversations → transcribe audio → correct project information → identify speakers → split into different projects → extract progress and to-dos → write into the unified Feishu multi-dimensional-table project sheet → set reminders → classify task type → dispatch to specialized Agents → collect execution results → update project status → pause or close & archive**

This article breaks this whole process down from start to finish.

## 1. Step One: Preserve the Conversation Completely

For a project-management Agent to organize projects, the premise is that it can get hold of the project communications.

Our entry point comes from **the built-in automatic call recording on Android.** (iPhone doesn't support this currently; you can consider recording cards or similar alternatives.)

Whether it's phone calls, WeChat voice, Feishu, DingTalk, or other communications, you can configure automatic recording according to what the phone supports.

After recording ends, the phone generates an audio file. The filename usually includes the date, the communication platform, and the other party's nickname, in MP3 or another common audio format.

This filename is convenient for people to search, and it also gives the Agent three important pieces of context:

- When this communication happened;
- Which platform it took place on;
- Who the other party in the conversation might be.

With this information, the Agent later has a chance to match the speaker with existing contacts. Without automatic recording, many project changes can only be recalled by people after the meeting.

A person's impression of a conversation is usually "roughly what we talked about," but project management needs more specific information: who promised what, when something will be done, which project is paused, and which material is still missing.

Once these details aren't recorded, no matter how smart the Agent is later, it can't reconstruct them.

So the first step is to fully preserve the communication that actually happened, and then auto-organize it.

## 2. The First Transcription Only Turns Sound Into Text

After the audio is generated, we send it directly to "Musk," the project-manager Agent we built on Feishu.

When the Musk Agent receives the audio, it first calls a model that supports audio processing to convert the recording into text. If there are two people in the recording, the first pass usually marks them as "Speaker 1" and "Speaker 2."

This step only completes the most basic conversion:

> Audio → time-ordered text → initial differentiation of speakers

The first-pass transcription does not directly enter the formal project record. Because although a general model can recognize most everyday language, it doesn't necessarily know the company's internal proper nouns.

Customer names, project names, product names, and internal abbreviations, if pronounced similarly, are easily transcribed into another seemingly plausible word.

If this raw transcription is handed directly to another model for summarization, the errors continue to propagate downstream.

If a customer name is wrong, the Agent may not find the corresponding contact; if a project name is wrong, progress may land in the wrong project; if a product name is wrong, subsequent retrieval loses accuracy.

Therefore, the text from the first transcription can't be used directly; it must first pass through a dedicated proper-noun correction layer before downstream summarization.

## 3. Why the Project-Manager Agent Can Correct Proper Nouns

A general speech model typed a wrong character — how can the Agent fix it? It isn't guessing blindly.

When general ASR (automatic speech recognition) encounters an unfamiliar rare word, it usually just forcibly transcribes a similar pinyin into a wrong character or an everyday word.

But the project-manager Agent's underlying correction mechanism is: **take this raw text carrying candidate wrong words, and do a context-based semantic alignment and fuzzy calibration against the "entity dictionary" (customer list, project ledger, product-line codenames) in the Feishu multi-dimensional table.**

After the first transcription is done, the Musk Agent re-examines the text with these existing project archives:

- If a word's pronunciation is extremely close to an existing contact's name, it directly does the correction-and-replacement using the other party's nickname in the filename, past relationships, and conversation context;
- If an abbreviation or wrong word sounds the same as an existing project's internal short name, it automatically falls back to the formal standard spelling in the table.

Project context plus the entity dictionary directly narrows the solution space dramatically.

The same pronunciation may have dozens of plausible Chinese-character combinations across public internet corpus; but once constrained to a specific team's business scope, it usually maps uniquely to a real, existing customer or project.

The essence of the project-manager Agent is **using a general model to "get the gist" first, then using the entity base table in the multi-dimensional table to "check against a dictionary."**

This is also why a pure transcription tool and an Agent connected to the business database differ astronomically in usability: the former only understands standard Mandarin, while the latter knows who's in your database and what's currently being pushed forward.

## 4. Speaker Identification: Use Context First, Voiceprint When Necessary

After text correction, you still need to replace "Speaker 1, Speaker 2" with real identities.

Most of our scenarios are two-person conversations.

As long as you confirm who one of them is, the other can usually be determined from the contact information in the filename.

There are currently two identification methods.

**The first is to judge by content and role.**

The project-manager Agent Musk already knows the contact's role in the project.

For example, one person mainly handles client contact and requirement communication, while the other mainly handles technical solutions. In a conversation, the side that often talks business and requirements differs noticeably in content from the side that often answers technical questions.

Combined with the contact in the filename, the Musk Agent can usually determine who the two speakers are.

This method's advantage is simplicity — no extra audio processing.

But it also has boundaries.

If the two people talk about very similar content, or the recording has more than two people, semantics alone may not distinguish them stably.

At this point you can use the second method: **comparing voice timbre ("knowing the person by voice").**

Record a designated script in advance and have the system extract the person's voiceprint features. When processing new recordings, extract voice from the different speakers' segments and match it against existing voices.

After a successful match, the system confirms which speaker is the person, and the remaining speakers are identified using the filename and project contacts.

For simple scenarios, first use the filename, contact roles, and conversation content; when content can't decide or a multi-person scenario arises, supplement with voice.

## 5. When One Call Covers Three Projects, the Agent Must Split Before Archiving

Real communication rarely follows the structure of project-management tools.

Nobody says on a call: "Now end project A; next we officially enter project B."

People might first talk about one client's materials, casually mention another project's progress, and finally assign a task related to a third project.

If the Agent just summarizes the whole conversation into one record, that record is hard to keep using.

Project A's progress, project B's risks, and project C's to-dos are stuffed into the same paragraph; afterward you can neither remind accurately nor get the complete status when viewing a single project.

So after speakers are confirmed, the project-manager Agent must also determine which projects the conversation touched.

If one communication involves multiple projects, split them by project information:

```
One complete conversation
├── Project A: new progress, to-dos
├── Project B: status change
└── Project C: materials that need supplementing
```

After splitting, write each part into its corresponding project.

This step is important.

Recordings and transcriptions are just communication records; only after splitting by project does the information truly enter the project-management system.

## 6. The Unified Project Table: the Single Authoritative Landing Point for Project Status (Including Pause and Closure)

The split-out project progress and to-dos ultimately enter a unified Feishu multi-dimensional table.

This table stores core fields like project and customer, and is the fixed, single entry point where the project-manager Agent queries and writes status.

Many teams using AI for project management only design "create task" and "remind task," but overlook a critical reality: **a project won't run on plan forever — it will pause, adjust, and even get canceled.**

We once hit an extremely typical pit: a project that was being pushed forward decided to pause midway, but that decision stayed only in some group chat or phone call and was never structurally written into the project table. A few days later, when discussing work with AI, it still treated that project as "in progress" and chased people for progress.

From human intuition, it feels like "the AI has terrible memory or is hallucinating." But from first principles, **this is a confusion between context and system state:**

- Past chats only prove "what was talked about then," and can't represent "what state it's in now";
- Chat records don't invalidate themselves; fed only old conversations, AI each time sees a historical slice full of contradictions.

Real-world project-status changes can't be solved by "adding context" to the model; there must be an authoritative landing point.

In real business, a project never has only two states — "in progress" and "completed." It may not have started, may be shelved, or may be formally terminated after review. A complete project lifecycle must leave a clear closed-loop definition in the table:

- **Explicit state transitions:** record whether a project is proceeding normally, temporarily shelved, or formally terminated;
- **Archive key information:** record the reason for pause or closure, actual start/end times, phased input/output, and a review note on unfinished items;
- **Changes take effect only in one place:** even if it's just a verbal "let's not do this for now," it must be synced to the table to fully cut off AI's follow-up questioning.

**"Chat produces information; the table confirms the present."**

This is the most core operating law of the entire system.

Before every action or answer, the Agent first reads the authoritative status in the multi-dimensional table: if it sees "paused," it stops chasing; if it sees "closed," it archives and locks.

Only when status truly closes the loop in the table does project management settle from a chaotic chat stream into a reliable, deterministic system.

## 7. The Project-Manager Agent Judges and Dispatches Tasks

Beyond progress and reminders, project communication also produces tasks that can be directly executed.

For example, a project needs to collect some materials or organize a batch of data. At this point you can send the requirement directly to the project-manager Agent.

It first writes the task into the task list, then judges how to handle the next step.

- If it's a quick, simple piece of work it can do itself, it executes directly.
- If the task needs more specialized technical capability, it dispatches to another Agent that specifically handles technical tasks.

After the technical Agent finishes, it returns the result to the project-manager Agent.

The project-manager Agent then reports the result back to the human and updates the status in the task list.

The chain is like this:

> Human proposes task → project-manager Agent registers task → classifies task type → executes it itself, or dispatches to the technical Agent → technical Agent returns result → project-manager Agent reports to human → updates task status

The benefit is that people don't need to remember which Agent to go to for each thing. They just speak through one unified entry. The project-manager Agent handles scheduling, handoff, and result retrieval — rather than people acting as "data porters."

**What this dispatch system truly lowers for the team is the human's startup cost.**

Before, handling a lightweight task meant sitting back at the computer, opening software, remotely connecting to the dev environment, and then digging up the corresponding project directory.

The actual execution may only take a few minutes, but the preparation beforehand is a hassle — startup cost is extremely high, which easily leads to procrastination or even shelving.

Now all project actions converge on the Musk Agent on Feishu.

A person sends one sentence on their phone via Feishu anytime, and the subsequent project locating, task dispatch, result retrieval, and status update are all run automatically by it. Its greatest value is compressing high-friction multi-tool switching into a single-point interaction with extremely low threshold.

## 8. Boundary Constraints: What Can Be Stably Dispatched Now Is Still Quick, Simple Tasks

Although this Agent dispatch process already works end to end, its boundaries are equally clear.

What's currently suitable to hand to the technical Agent is mainly relatively lightweight work like material collection and data organization.

They share a few common traits:

- Clear goal;
- Short execution cycle;
- No need to maintain complex context for weeks;
- Doesn't involve major business judgment;
- Result is relatively easy to check.

It still can't fully hand a long, complex development project to the Agent and wait for it to finish on its own.

Long tasks hit more problems: how to sustain context, what to do when the process changes, who checks intermediate results, and who's responsible for wrong judgments.

Unattended operation relying solely on the Agent — we haven't achieved this part yet.

The more practical value right now is shortening those simple technical tasks that originally required a person to open multiple tools into a single conversation.

## 9. The Price of Convenience Is Tokens

Actions previously done by people now require the Agent to read information, look up projects, call the model, dispatch tasks, and organize results.

These actions consume tokens.

Before, human brains remembered which software to open, which project to enter, and where to copy what information. Now these operations are transferred to the Agent — human time and attention are saved, while model-call cost rises.

**This system shifts cost from human operational friction to the running cost of the model and Agent.**

Whether it's worth it depends on whether the time saved and the risk of omission reduced exceed the token consumption.

We now mainly call the Gemini model. At this stage, model cost is far lower than the time cost of manual fiddling; an extremely low token budget is enough to support all-day high-frequency calls.

For occasional one-off tasks, manual operation may be simpler.

For communications that happen every day and need organizing across multiple projects, handing these steps to the Agent is more valuable.

When using this system, you need to get this math right.

## 10. Once There Are Many Projects, You Don't Need to Feed the Whole Table to the Model

As the project table grows larger, the Agent reading it each time may consume a lot of tokens.

Actual queries don't need to scan everything every time.

When a person asks about a project, the Agent can first locate the relevant records using keywords like the project name, customer, and contact, then read the matched content.

Its way of working is closer to:

> Search the project a user mentioned → extract project keywords → retrieve in the unified project table → find the matching project → read the latest status and related tasks → answer based on current records

Even if the project table reaches ten thousand rows, as long as project names and basic info can be retrieved, the Agent only needs to read the matched records.

## 11. A Minimum Viable Version — You Don't Need to Finish Every Feature From Day One

If building from zero now, you don't need to add voiceprints, multi-Agent, and complex closure approvals on day one.

You can first get the shortest chain working:

> Send a project recording → convert to text → manually confirm speakers → extract project progress and to-dos → manually confirm ownership → write into the unified project table → due-date reminders

As long as this chain works stably, project communication begins to move from chat into manageable records.

Then gradually add:

- Automatic correction using existing contacts and project materials;
- Identify speakers by content or voiceprint;
- Split multiple projects from one conversation;
- Dispatch simple tasks to specialized Agents;
- Automatically collect results and update status;
- Add pause, cancellation, and closure archiving.

**The build order should follow real problems.**

- If the worst pain is forgetting to-dos after meetings, first solve recording-to-to-do.
- If the worst pain is chaotic project status, first build the unified project table and closure process.
- If the worst pain is troublesome tool operation, then add task dispatch.

You don't need to pile all features on at once just to look like a complete Agent system.

## Finally: The Core of the Project-Manager Agent Is Continuously Updating Project Status

Audio transcription, proper-noun correction, voiceprint recognition, and multi-Agent dispatch solve how information enters the system and how tasks get executed.

**What truly makes it a "project manager" is that every project has a clear current status, the next step has an owner, reminders fire on time, and it can be formally ended when stopped.**

Project management needs a formal record that is continuously updated, queryable at any time, and captures each project's start and end.

The biggest taboo in building an Agent system is self-indulgent feature-piling: lower the input friction as much as possible, and pin the status uniquely in the table — only then can people truly pull away from tedious process tools and focus on the business judgment itself.