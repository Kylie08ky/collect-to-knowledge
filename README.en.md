# Collect to Knowledge · 收藏转知识

[简体中文](README.md) · **English**

Turn “saved for later” into something you understand and can use.

A reusable AI skill that turns social posts, podcasts, videos, articles, and
personal excerpts into actionable knowledge cards—with sources, everyday
applications, and a clear next step. Optionally file them by topic in **your own Notion**.

> This is an agent workflow, not a standalone application. It uses your AI host's
> reading, file, image-generation, and Notion capabilities. Media transcription
> is an optional, separately installed dependency.

## What it does

| Input / request | Result |
| --- | --- |
| Accessible articles, posts, pasted text, screenshots | Key ideas, conditions, limitations, and provenance |
| Podcasts/videos with captions or successful transcription | Knowledge notes based on actual content, with coverage disclosed |
| “How can I use this?” | Everyday applications, labeled hypothetical examples, a minimum next action |
| “Give me an execution plan” | Checklists and, where appropriate, a 3–7 day experiment |
| “Make a visual card” | A visual knowledge card plus editable text; requires image generation |
| “Save and classify in Notion” | Deduplication, primary category, tags, sources, and images in the same note |
| New material for an existing source | Updates that preserve user annotations and action states |

**Source → read/transcribe → extract knowledge → apply → plan → optional image → optional Notion filing**

## Quick start

### 1. Install

Send this to Codex:

```text
Use skill-installer to install https://github.com/Kylie08ky/collect-to-knowledge.
SKILL.md is at the repository root; name the skill folder collect-to-knowledge.
If already installed, inspect the existing version and preserve my local
configuration instead of overwriting it.
```

Alternatively, download the repository, name the folder `collect-to-knowledge`,
and place it in your AI host's supported skills directory. Codex's installer uses
`$CODEX_HOME/skills`, falling back to `~/.codex/skills`.
Use it on your next turn; start a new chat if it is not recognized.

Other agents that read `SKILL.md` may adapt this workflow. Installation paths,
tools, and permissions vary by host. Primary testing was in Codex; compatibility
with every other host is not guaranteed.

### 2. Configure your own Notion destination

Connect Notion in your AI host and give that connection access to your target,
then send:

```text
Use $collect-to-knowledge to complete first-time setup.

My Notion destination is: [paste your own page link].
Create a topic-based knowledge database inside that page.
Categories: Psychology, Philosophy, Economics & finance, Health,
Learning & growth, Technology & tools, Lifestyle, Unsorted.
For content I give this skill, automatically create English text knowledge
cards and one visual card, with everyday applications and an action plan.
Save them under the appropriate topic.
Store my target and preferences in local config.local.json, never on GitHub.
```

The agent reads and verifies the destination. An existing suitable database can
be reused. **If no target is configured, the skill asks which page to use first.**

You can instead choose:
- **Preview before saving**: “Show the finished notes first; save only after I confirm.”
- **No Notion**: “Only deliver in chat or local files.”
- **Text only**: “Do not generate images by default.”

The public repository contains only an unconfigured `config.example.json`.
Your page URL, database IDs, and preferences belong in `config.local.json`
beside the installed SKILL.md. That file is gitignored.
Credentials belong to your host's Notion integration, never this file or chat.

### 3. Use it

```text
$collect-to-knowledge
Process this source: [link]
Extract the key ideas, everyday applications, and an action plan.
Save according to my configured preferences.
```

Or use natural language:

> Turn this into knowledge cards, including an image, and file it by topic in Notion: [link]

## Example requests

```text
Turn this podcast into knowledge cards. Include timestamps for important ideas.
[link]

Process this Xiaohongshu video and design a plan for someone with 15 minutes a day.
[link]

File this article under Philosophy. Keep the reasoning and limitations.
[link]

Process these three links separately, deduplicate them, and file by topic.
[links]

Show me a draft from this excerpt. Do not save to Notion yet.
[text]
```

You do not need to invoke the transcriber separately for each item.
Current instructions such as “don't save” or “text only” override saved preferences.

## Optional podcast and video transcription

Install [hotcatty/media-transcriber](https://github.com/hotcatty/media-transcriber)
separately, following its current requirements for Python, FFmpeg, and local
speech models. Its listed platforms include Xiaoyuzhou, Bilibili, Xiaohongshu
video, YouTube, Apple Podcasts, and local media files.

```text
Follow the current instructions at https://github.com/hotcatty/media-transcriber
to install local transcription and connect it to collect-to-knowledge.
Inspect my operating system and dependencies first, use an isolated environment,
and keep speech recognition local.
```

- Local ASR needs no DashScope key. Models and dependencies are downloaded separately.
- Windows paths and GPU libraries need machine-specific setup; Unix virtualenv paths do not work as PowerShell paths.
- Xiaohongshu image/text posts need text/image reading, not speech recognition.
- Authentication, removed links, platform restrictions, and downloader changes can prevent extraction.
- One Xiaoyuzhou episode and one Xiaohongshu video were tested during development; this does not establish universal platform support.
- Automatic transcripts can contain name, number, and wording errors.
- Optional Xiaoyuzhou helper: [weisi-gu/xiaoyuzhou-podcast-notes](https://github.com/weisi-gu/xiaoyuzhou-podcast-notes).
  Its cloud routes require separate setup and authorization; this skill does not silently switch to paid services.

See [media handling](references/media.md).

## Notion organization

When requested, a categorized database can use:
**Name, Category, Tags, Source type, Source URL, Processed date**,
with a topic board and filtered category views.

One source normally becomes one page containing text cards, images, and actions.
Secondary topics become tags rather than duplicate pages. Existing databases use
their actual schema; fixed Chinese field names are not required.

## Privacy and boundaries

- **No author's personal Notion destination is included.** Each user selects their own.
- Saving defaults to asking first. Automatic saving requires explicit opt-in.
- It processes supplied items, not every saved item in your accounts or a background feed.
- Local ASR does not make the entire workflow offline: your AI host processes content,
  and authorized summaries/images are sent to Notion.
- Do not commit source media, cookies, secrets, private transcripts, or local configuration.
- Descriptions are never presented as full transcripts; assistant-designed examples are labeled.
- Third-party copyrighted sources are synthesized with brief necessary quotations,
  not redistributed as full transcripts.
- Missing image, transcription, or Notion capabilities are reported honestly.
- AI hosting, image generation, and optional cloud services follow their own pricing.

## Repository layout

```text
collect-to-knowledge/
├── SKILL.md
├── README.md
├── README.en.md
├── config.example.json
├── agents/openai.yaml
├── references/
│   ├── setup.md
│   ├── notion.md
│   ├── media.md
│   └── visual-cards.md
├── examples/knowledge-card.md
├── .gitignore
└── LICENSE
```

[View the synthetic output example](examples/knowledge-card.md) · [Setup details](references/setup.md)

## Credits and license

This repository provides the knowledge-processing workflow; it does not bundle
third-party code, models, or installers.
Thanks to [media-transcriber](https://github.com/hotcatty/media-transcriber) and
[xiaoyuzhou-podcast-notes](https://github.com/weisi-gu/xiaoyuzhou-podcast-notes)
for optional media capabilities. Those projects retain their own licenses.

This project uses the [MIT License](LICENSE). Use, modify, and share it.
Remove private URLs, tokens, cookies, and local configuration from issue reports.
