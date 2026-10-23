# Journal Insight Companion｜日记洞察伙伴

[简体中文](README.md) | [English](README.en.md)

A Chinese-first [Agent Skills](https://agentskills.io/)-style Skill that supports journaling across multiple messages and provides in-depth reflection only when explicitly requested. Once triggered, it outputs **Deep Insights → Takeaways suitable for saving in notes → A diary summary within 500 Chinese characters**, in that order, by default.

## Core Design

| Principle | Behavior |
| --- | --- |
| **Listen first, reflect later** | Recording mode is the default; in-depth analysis begins only after an explicit instruction such as “开始洞察” (“Start reflecting”). |
| **Depth over breadth** | Select 1–2 suitable perspectives per session rather than mechanically applying psychological terminology. |
| **Value evidence and counterexamples** | Distinguish facts, interpretations, and hypotheses; avoid uncritical agreement or attributing environmental problems solely to the individual. |
| **Preserve useful outputs** | After “开始洞察,” provide all three parts by default; omit a part only when the user explicitly requests it. |
| **Compare across dates** | Compare entries from different dates when context is available; do not assume the model can automatically access every past conversation. |

## Repository Structure

```text
journal-insight-companion/
├── SKILL.md                    # Skill entry point and workflow rules
├── README.md                   # Chinese project guide, installation and usage
├── README.en.md                # English project guide, installation and usage
├── LICENSE                     # MIT license
├── .gitignore
├── examples/
│   └── conversations.md        # Trigger examples
└── references/
    └── evaluation-checklist.md # Manual testing checklist
```

## Installation

This is a **prompt-based Skill** and requires no Python or other dependencies. Clone or download this repository, then follow your AI Agent client's documentation to place the directory containing `SKILL.md` in its Skills search path. Paths, discovery mechanisms, and permission requirements vary by client; consult the client's official instructions.

```bash
git clone https://github.com/<YOUR_USERNAME>/journal-insight-companion.git
```

> Replace `<YOUR_USERNAME>` with your GitHub username. This URL is an example only; it does not imply that the repository has already been created.

If your client does not support Agent Skills, you can use the contents of `SKILL.md` directly as custom instructions. Automatic triggering and state retention depend on the client.

## Usage

| Stage | Example user message | Assistant behavior |
| --- | --- | --- |
| Start recording | “开启日记模式” (“Start diary mode”) | Enter multi-message recording mode. |
| Continue recording | Send more diary content | Respond briefly without starting in-depth analysis early. |
| Trigger reflection | “开始洞察” (“Start reflecting”) | Output the three parts below in order. |
| Explicitly omit a part | “开始洞察，但不用整理日记” (“Start reflecting, but skip the diary summary”) | Provide insights and Takeaways, omitting the diary summary. |
| Request one output | “整理成500字以内日记” (“Summarize as a diary entry within 500 Chinese characters”) | Produce only the diary summary. |

Default output order:

1. **Deep Insights**
2. **Takeaways suitable for saving in notes**
3. **A diary summary within 500 Chinese characters**

See [`examples/conversations.md`](examples/conversations.md).

## Design Boundaries

| Area | Description |
| --- | --- |
| Mental health | Not a psychotherapy or clinical diagnosis tool. |
| Data retention | Does not save diary entries by default; continuity across sessions depends on the host product's memory, files, or context capabilities. |
| Privacy | Does not upload diary content to third-party services; this repository contains no personal diary data. |
| Platform compatibility | Does not guarantee that every AI platform will automatically recognize or strictly follow the Skill. |


## License

MIT; see [LICENSE](LICENSE).
