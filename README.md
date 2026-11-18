# Plain Business Writing

An agent skill that makes AI write and edit business text the way a person would. It removes the patterns that make drafts read as machine written and keeps the facts, numbers and voice of the original.

It works on proposals, emails, summaries, slide copy and similar business writing. It can edit a draft, audit one without rewriting it, or write from your notes.

## What it does

The skill gives the agent three modes.

- **Edit** makes the smallest change that fixes the problem and returns the text with a short note on what changed. This is the default.
- **Detect** quotes each problem line, names the pattern and suggests a fix without rewriting anything.
- **Draft** writes new text from facts you supply, using the same rules.

It checks for 19 patterns, ranked by how strongly they signal machine writing. A few examples:

| Pattern | Before | After |
| --- | --- | --- |
| Staccato stack | A proposal and a working concept. The name is a placeholder. We want you to pick it apart. | This is a working proposal, and the name is still a placeholder. We'd like you to pick it apart. |
| Not X but Y | It's not that the overlay route is broken, it's that we don't know yet whether it holds up. | We don't yet know whether the overlay route holds up. |
| Dash as connector | The rollout, which began in May, is on track. | The rollout began in May and is on track. |

The full list, along with banned words, dash and comma rules, and title rules, is in [SKILL.md](SKILL.md).

## Guardrails

- It never invents numbers, quotes, customers or results. Where a fact is missing it writes a plainer sentence or leaves a placeholder.
- It checks that names, numbers, dates and quotes survive the edit unchanged.
- Meaning, voice and naturalness outrank pattern removal. An edit that would change what the author said, or read worse, does not happen.
- It leaves quotations, proper names, code, paths and links alone.
- A line with no real problem stays as written. If nothing needs changing, it says so.
- A writing sample from you overrides the rules, including the dash rule.
- In file edits it changes prose only and reports which lines it touched.

## Install

### Claude Code

Copy the skill into your skills folder.

```bash
mkdir -p ~/.claude/skills/plain-business-writing
cp SKILL.md ~/.claude/skills/plain-business-writing/SKILL.md
```

For a single project, use `.claude/skills/plain-business-writing/` inside that project instead.

### Claude.ai

Zip the folder containing `SKILL.md` and upload it under Settings, Capabilities, Skills.

### Other agents

Any agent that reads a markdown instruction file can use `SKILL.md` as is. The front matter holds the name and a description of when to apply it.

## Usage

Ask in plain language. The skill applies when you request writing or editing of business text, or ask to remove AI slop or humanize a draft.

```text
Tighten this proposal and remove anything that sounds like AI.
```

```text
Audit this email for AI writing patterns. Don't rewrite it.
```

```text
Draft a one page summary from these notes.
```

## Limits

The skill reduces the usual signs of machine writing. It does not aim to beat AI detectors, and detectors may still flag edited text. It also works best with real source material, because the rules cannot supply specific facts that are not in the draft.

## Credits

This skill builds on two open source projects:

- [no-ai-slop](https://github.com/petergyang/no-ai-slop) by Peter Yang, for the edit and detect modes, the banned word list and the portability test.
- [humanizer](https://github.com/blader/humanizer) by blader, for the ranked pattern approach, the check and recheck process, and the writing sample override. Humanizer draws on Wikipedia's "Signs of AI writing" guide.

Both are MIT licensed.

## License

Released under the [MIT License](LICENSE).
