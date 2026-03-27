# Skills

Agent skills for [OpenCode](https://opencode.ai). Install with [`npx skills`](https://skills.sh) or clone directly.

## Available Skills

| Skill | Description |
|---|---|
| [design-exploration](design-exploration/) | Generates multiple design variants with different visual directions, then implements the chosen one |
| [opencode-memory](opencode-memory/) | Read-only access to local OpenCode history — sessions, plans, conversations, and project context |

---

<details>
<summary><h2>design-exploration</h2></summary>

Generates multiple distinct design variants of a component or page, each with a completely different visual direction, then implements the chosen one.

### Install

```bash
npx skills add carson2222/skills --skill design-exploration -g -y
```

Or browse on [skills.sh](https://skills.sh/carson2222/skills/design-exploration).

### What it does

Give it a component, page, or section and it produces N variants (default 5), each taking a fundamentally different visual direction. You compare them in the browser, pick one, and it implements the final version with real data.

Works in two modes:
- **New project** — no design system yet, variants define one. Each gets its own fonts, colors, layout philosophy.
- **Existing app** — design system already exists. Variants explore different layouts and compositions while staying consistent with your tokens and patterns.

### What models work best

**Claude Opus 4.6** with high thinking budget covers ~95% of runs. Gemini can produce solid UI too. Open source models (GLM5, MiniMax, Kimi K2.5) sometimes surprise you but are less predictable. Codex is not recommended for frontend design.

### How to get good results

This is not a "run it and pray" skill. Output quality scales directly with context. Before running:
- What matters to you? Professional? Playful? Dark and moody?
- Who is this for? What vibe are you going for?
- Drop assets (images, logos, icons) in the project folder with descriptive filenames.

Talk to it like you'd talk to a designer. The more you give it, the better it gets.

</details>

<details>
<summary><h2>opencode-memory</h2></summary>

Lightweight, read-only access to your local OpenCode history. No injection, no bloat — the agent can look things up when it would help.

### Install

```bash
npx skills add carson2222/skills --skill opencode-memory -g -y
```

Or browse on [skills.sh](https://skills.sh/carson2222/skills/opencode-memory).

### The problem

Every "memory" plugin out there injects context everywhere, bloating every request. Most of the time you don't need history. But when you do — resuming a project, referencing a past decision, debugging something that came up before — the agent should be able to check on its own without you having to explain where OpenCode stores things.

Without this skill, getting the agent to browse local OpenCode data requires precise wording and a lot of luck. It tries Claude, Codex, random paths, and gives up. This skill solves that by teaching the agent exactly where to look and how to query it.

### What it covers

- **Sessions** — list, filter by project, search by title
- **Messages** — read full conversations from any session
- **Search** — full-text search across all past conversations
- **Plans** — list and read saved plans
- **Projects** — see all tracked projects with session counts
- **Prompt history** — recent prompts you've typed

### How it works

The skill teaches the agent the OpenCode storage model and provides ready-to-use `sqlite3` queries. No scripts, no external tools — just `sqlite3` (available on every Mac/Linux) and bash. The SKILL.md contains the database paths, schema, and copy-paste query templates for every common operation.

The agent will auto-trigger when:
- You reference something done before ("last time", "that plan we made")
- You're resuming work on a project
- You ask about history, plans, or past sessions
- It suspects prior context would help

### Requirements

- `sqlite3` CLI (pre-installed on macOS and most Linux)
- OpenCode must have been used at least once (creates the database)
- macOS/Linux (reads `~/.local/share/opencode/`, respects `XDG_DATA_HOME`)

</details>

---

## License

Apache 2.0. See [LICENSE](LICENSE).
