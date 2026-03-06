# Skills

Agent Skills for AI coding agents. Compatible with Claude Code, Cursor, Copilot, Windsurf, and other [skills-compatible agents](https://agentskills.io).

## Install

Install this skill directly:

```bash
npx skills add https://github.com/carson2222/skills --skill design-exploration
```

Or browse it on [skills.sh](https://skills.sh/carson2222/skills/design-exploration).

## Available Skills

| Skill | Description |
|---|---|
| [design-exploration](design-exploration/) | Generates multiple distinct design variants with different visual directions, then implements the chosen one. |

---

## Background

I didn't write this skill today out of nowhere. The core idea has been living as a prompt in my head for months, something I kept refining every time I used it. I'd run it, notice what went wrong, adjust my approach, and over time it turned into a pretty specific workflow that consistently gave me results I was happy with.

At some point my friends and co-workers started asking me to share it because they kept seeing the output and wanted the same thing. So I finally sat down and wrapped the whole thing into a proper Agent Skill instead of just explaining it over and over.

## What models I use

I run this with **Claude Code + Opus 4.6** on highest thinking about 90% of the time. That's usually enough, and I get at least one variant I'm genuinely happy with in roughly 95% of runs.

**Gemini** can produce solid UI too. Open source models like **GLM5**, **MiniMax**, **Kimi K2.5** and others in that tier can sometimes surprise you, but they're less predictable. If you're using one of those, don't commit to a single model; swap between them and run it a few times.

I **do not recommend Codex** for this. I find it genuinely bad at frontend design work.

## How to get good results

This is not a "run it and pray" kind of skill. The output quality scales directly with how much context you give it.

Before you run it, think about:
- What matters to you? Professional and polished? Playful and friendly? Dark and moody?
- Who is this for? What's the vibe you're going for?
- What's the product? What does it do? Who uses it?

If you have assets like images, logos, or icons, drop them in the project folder where the agent can access them. **Name the files descriptively** (not `img1.png` but `hero-illustration-dark.png`). The model uses filenames to reason about what to place where.

Talk to it like you'd talk to a designer. Describe what you want, how you want it to feel, what you like, what you hate. The more you give it, the better it gets. If you give it nothing, it'll do its best, but "its best" without context is just guessing.

## License

Apache 2.0. See [LICENSE](LICENSE).
