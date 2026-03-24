# sage

> An AI-powered engineering team in your terminal. Twenty specialists, eight power tools, all slash commands.

sage turns Claude Code into a virtual engineering team — a CEO who rethinks the product, an eng manager who locks architecture, a designer who catches AI slop, a reviewer who finds production bugs, a QA lead who opens a real browser, a security officer who runs OWASP + STRIDE audits, and a release engineer who ships the PR.

**Built on [gstack](https://github.com/garrytan/gstack)** by [Garry Tan](https://x.com/garrytan) — the original open-source software factory. sage is a fork that adds deep research, iterative improvement loops, and custom workflows on top of gstack's battle-tested foundation.

## What sage adds

Everything in [gstack](https://github.com/garrytan/gstack), plus:

- **`/research`** — Deep research agent with parallel web crawling, persistent knowledge base, and cross-session learning. Uses agent swarms for massive parallel gathering with 5:1 RLM compression between waves.
- **`/ralph`** — Recursive Audit-Learn-Plan-Harden loop. Convergence-based iterative improvement that audits, researches, implements, optimizes, tests, and learns from outcomes. Self-learning across sessions.
- Custom workflows and integrations built on top of gstack's skill system.

## Quick start

1. Install sage (30 seconds — see below)
2. Run `/office-hours` — describe what you're building
3. Run `/plan-ceo-review` on any feature idea
4. Run `/review` on any branch with changes
5. Run `/qa` on your staging URL
6. Stop there. You'll know if this is for you.

## Install — 30 seconds

**Requirements:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (Windows only)

### Step 1: Install on your machine

Open Claude Code and paste this. Claude does the rest.

> Install sage: run **`git clone https://github.com/hussainarslan/gstack.git ~/.claude/skills/sage && cd ~/.claude/skills/sage && ./setup`** then add a "sage" section to CLAUDE.md that says to use the /browse skill from sage for all web browsing, never use mcp\_\_claude-in-chrome\_\_\* tools, and lists the available skills: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /research, /ralph, /careful, /freeze, /guard, /unfreeze, /sage-upgrade. Then ask the user if they also want to add sage to the current project so teammates get it.

### Step 2: Add to your repo so teammates get it (optional)

> Add sage to this project: run **`cp -Rf ~/.claude/skills/sage .claude/skills/sage && rm -rf .claude/skills/sage/.git && cd .claude/skills/sage && ./setup`** then add a "sage" section to this project's CLAUDE.md that says to use the /browse skill from sage for all web browsing, never use mcp\_\_claude-in-chrome\_\_\* tools, lists the available skills: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /research, /ralph, /careful, /freeze, /guard, /unfreeze, /sage-upgrade, and tells Claude that if sage skills aren't working, run `cd .claude/skills/sage && ./setup` to build the binary and register skills.

### Codex, Gemini CLI, or Cursor

sage works on any agent that supports the [SKILL.md standard](https://github.com/anthropics/claude-code). Skills live in `.agents/skills/` and are discovered automatically.

```bash
# Install to one repo
git clone https://github.com/hussainarslan/gstack.git .agents/skills/sage
cd .agents/skills/sage && ./setup --host codex

# Install globally
git clone https://github.com/hussainarslan/gstack.git ~/sage
cd ~/sage && ./setup --host codex

# Auto-detect which agents you have
git clone https://github.com/hussainarslan/gstack.git ~/sage
cd ~/sage && ./setup --host auto
```

## The sprint

sage is a process, not a collection of tools. The skills run in the order a sprint runs:

**Think → Plan → Build → Review → Test → Ship → Reflect**

Each skill feeds into the next. `/office-hours` writes a design doc that `/plan-ceo-review` reads. `/plan-eng-review` writes a test plan that `/qa` picks up. `/review` catches bugs that `/ship` verifies are fixed. Nothing falls through the cracks because every step knows what came before it.

| Skill | Your specialist | What they do |
|-------|----------------|--------------|
| `/office-hours` | **YC Office Hours** | Start here. Six forcing questions that reframe your product before you write code. Pushes back on your framing, challenges premises, generates implementation alternatives. |
| `/plan-ceo-review` | **CEO / Founder** | Rethink the problem. Find the 10-star product hiding inside the request. Four modes: Expansion, Selective Expansion, Hold Scope, Reduction. |
| `/plan-eng-review` | **Eng Manager** | Lock in architecture, data flow, diagrams, edge cases, and tests. Forces hidden assumptions into the open. |
| `/plan-design-review` | **Senior Designer** | Rates each design dimension 0-10, explains what a 10 looks like, then edits the plan to get there. AI Slop detection. |
| `/design-consultation` | **Design Partner** | Build a complete design system from scratch. Researches the landscape, proposes creative risks, generates realistic product mockups. |
| `/review` | **Staff Engineer** | Find the bugs that pass CI but blow up in production. Auto-fixes the obvious ones. Flags completeness gaps. |
| `/investigate` | **Debugger** | Systematic root-cause debugging. Iron Law: no fixes without investigation. Traces data flow, tests hypotheses. |
| `/design-review` | **Designer Who Codes** | Same audit as /plan-design-review, then fixes what it finds. Atomic commits, before/after screenshots. |
| `/qa` | **QA Lead** | Test your app in a real browser, find bugs, fix them with atomic commits, re-verify. Auto-generates regression tests. |
| `/qa-only` | **QA Reporter** | Same methodology as /qa but report only. Pure bug report without code changes. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + STRIDE threat model. Zero-noise: independent finding verification. Each finding includes a concrete exploit scenario. |
| `/research` | **Research Lead** | Deep research with parallel web crawling, persistent knowledge base, and cross-session learning. Agent swarm with 5:1 compression. |
| `/ralph` | **Quality Engineer** | Recursive Audit-Learn-Plan-Harden loop. Iterative improvement until convergence. Self-learning across sessions. |
| `/ship` | **Release Engineer** | Sync main, run tests, audit coverage, push, open PR. Bootstraps test frameworks if you don't have one. |
| `/land-and-deploy` | **Release Engineer** | Merge the PR, wait for CI and deploy, verify production health. One command from "approved" to "verified in production." |
| `/canary` | **SRE** | Post-deploy monitoring loop. Watches for console errors, performance regressions, and page failures. |
| `/benchmark` | **Performance Engineer** | Baseline page load times, Core Web Vitals, and resource sizes. Compare before/after on every PR. |
| `/document-release` | **Technical Writer** | Update all project docs to match what you just shipped. Catches stale READMEs automatically. |
| `/retro` | **Eng Manager** | Team-aware weekly retro. Per-person breakdowns, shipping streaks, test health trends. `/retro global` runs across all your projects and AI tools. |
| `/autoplan` | **Review Pipeline** | One command, fully reviewed plan. Runs CEO → design → eng review automatically. Surfaces only taste decisions for your approval. |
| `/browse` | **QA Engineer** | Real Chromium browser, real clicks, real screenshots. ~100ms per command. |
| `/setup-browser-cookies` | **Session Manager** | Import cookies from your real browser (Chrome, Arc, Brave, Edge) into the headless session. Test authenticated pages. |

### Power tools

| Skill | What it does |
|-------|-------------|
| `/codex` | **Second Opinion** — independent code review from OpenAI Codex CLI. Three modes: review (pass/fail gate), adversarial challenge, and open consultation. |
| `/careful` | **Safety Guardrails** — warns before destructive commands (rm -rf, DROP TABLE, force-push). Override any warning. |
| `/freeze` | **Edit Lock** — restrict file edits to one directory. Prevents accidental changes outside scope. |
| `/guard` | **Full Safety** — `/careful` + `/freeze` in one command. Maximum safety for prod work. |
| `/unfreeze` | **Unlock** — remove the `/freeze` boundary. |
| `/setup-deploy` | **Deploy Configurator** — one-time setup for `/land-and-deploy`. Detects your platform, production URL, and deploy commands. |
| `/sage-upgrade` | **Self-Updater** — upgrade sage to latest. Detects global vs vendored install, syncs both, shows what changed. |

**[Deep dives with examples and philosophy for every skill →](docs/skills.md)**

## Parallel sprints

sage works well with one sprint. It gets interesting with ten running at once.

[Conductor](https://conductor.build) runs multiple Claude Code sessions in parallel — each in its own isolated workspace. One session on `/office-hours`, another on `/review`, a third implementing a feature, a fourth running `/qa`. All at the same time. The sprint structure is what makes parallelism work — without a process, ten agents is ten sources of chaos.

## Credits

sage is built on top of [gstack](https://github.com/garrytan/gstack) by [Garry Tan](https://x.com/garrytan), President & CEO of [Y Combinator](https://www.ycombinator.com/). gstack is the original open-source software factory — twenty specialists and eight power tools that turn Claude Code into a virtual engineering team.

The core architecture, skill system, headless browser, template engine, and sprint workflow are all gstack. sage extends it with deep research capabilities, iterative improvement loops, and custom workflows.

Thank you to Garry and the gstack community for building this in the open. MIT license, free forever.

---

Free, MIT licensed, open source. Fork it. Improve it. Make it yours.

## Docs

| Doc | What it covers |
|-----|---------------|
| [Skill Deep Dives](docs/skills.md) | Philosophy, examples, and workflow for every skill |
| [Builder Ethos](ETHOS.md) | Builder philosophy: Boil the Lake, Search Before Building, three layers of knowledge |
| [Architecture](ARCHITECTURE.md) | Design decisions and system internals |
| [Browser Reference](BROWSER.md) | Full command reference for `/browse` |
| [Contributing](CONTRIBUTING.md) | Dev setup, testing, contributor mode, and dev mode |
| [Changelog](CHANGELOG.md) | What's new in every version |

## Privacy & Telemetry

sage includes **opt-in** usage telemetry to help improve the project. Here's exactly what happens:

- **Default is off.** Nothing is sent anywhere unless you explicitly say yes.
- **On first run,** sage asks if you want to share anonymous usage data. You can say no.
- **What's sent (if you opt in):** skill name, duration, success/fail, sage version, OS. That's it.
- **What's never sent:** code, file paths, repo names, branch names, prompts, or any user-generated content.
- **Change anytime:** `sage-config set telemetry off` disables everything instantly.

## Troubleshooting

**Skill not showing up?** `cd ~/.claude/skills/sage && ./setup`

**`/browse` fails?** `cd ~/.claude/skills/sage && bun install && bun run build`

**Stale install?** Run `/sage-upgrade` — or set `auto_upgrade: true` in `~/.sage/config.yaml`

**Windows users:** sage works on Windows 11 via Git Bash or WSL. Node.js is required in addition to Bun — Bun has a known bug with Playwright's pipe transport on Windows ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). The browse server automatically falls back to Node.js.

**Claude says it can't see the skills?** Make sure your project's `CLAUDE.md` has a sage section. Add this:

```
## sage
Use /browse from sage for all web browsing. Never use mcp__claude-in-chrome__* tools.
Available skills: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review,
/design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse,
/qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro,
/investigate, /document-release, /codex, /cso, /autoplan, /research, /ralph,
/careful, /freeze, /guard, /unfreeze, /sage-upgrade.
```

## License

MIT. Free forever. Built on [gstack](https://github.com/garrytan/gstack). Go build something.
