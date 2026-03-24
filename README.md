# sage

> Built on [gstack](https://github.com/garrytan/gstack) by [Garry Tan](https://x.com/garrytan). Extended with deep research, iterative improvement loops, and custom workflows.

sage is an AI-powered engineering team in your terminal. It turns Claude Code into twenty specialists — a CEO who rethinks the product, an eng manager who locks architecture, a designer who catches AI slop, a researcher who crawls the web in parallel, a reviewer who finds production bugs, a QA lead who opens a real browser, a security officer who runs OWASP + STRIDE audits, and a release engineer who ships the PR. All slash commands, all Markdown, all free.

## Quick start

1. Install sage (30 seconds — see below)
2. Run `/office-hours` — describe what you're building
3. Run `/plan-ceo-review` on any feature idea
4. Run `/review` on any branch with changes
5. Run `/qa` on your staging URL

## See it work

```
You:    I want to build a daily briefing app for my calendar.
You:    /office-hours
Claude: [asks about the pain — specific examples, not hypotheticals]

You:    Multiple Google calendars, events with stale info, wrong locations.
        Prep takes forever and the results aren't good enough...

Claude: I'm going to push back on the framing. You said "daily briefing
        app." But what you actually described is a personal chief of
        staff AI.
        [extracts 5 capabilities you didn't realize you were describing]
        [challenges 4 premises — you agree, disagree, or adjust]
        [generates 3 implementation approaches with effort estimates]
        [writes design doc → feeds into downstream skills automatically]

You:    /research calendar APIs and briefing UX patterns
Claude: [launches 20+ parallel web crawlers across 5 waves]
        [builds persistent knowledge base with source quality scoring]
        [compresses findings 5:1 between waves — surfaces what matters]

You:    /plan-ceo-review → /plan-eng-review → approve → build
        [writes 2,400 lines across 11 files in ~8 minutes]

You:    /review
        [AUTO-FIXED] 2 issues. [ASK] Race condition → you approve fix.

You:    /qa https://staging.myapp.com
        [opens real browser, clicks through flows, finds and fixes a bug]

You:    /ship
        Tests: 42 → 51 (+9 new). PR: github.com/you/app/pull/42
```

Eight commands, end to end. That is not a copilot. That is a team.

## Install — 30 seconds

**Requirements:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (Windows only)

### Step 1: Install on your machine

Open Claude Code and paste this. Claude does the rest.

> Install sage: run **`git clone https://github.com/hussainarslan/sage.git ~/.claude/skills/sage && cd ~/.claude/skills/sage && ./setup`** then add a "sage" section to CLAUDE.md that says to use the /browse skill from sage for all web browsing, never use mcp\_\_claude-in-chrome\_\_\* tools, and lists the available skills: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /autoplan, /research, /ralph, /careful, /freeze, /guard, /unfreeze, /sage-upgrade. Then ask the user if they also want to add sage to the current project so teammates get it.

### Step 2: Add to your repo so teammates get it (optional)

> Add sage to this project: run **`cp -Rf ~/.claude/skills/sage .claude/skills/sage && rm -rf .claude/skills/sage/.git && cd .claude/skills/sage && ./setup`** then add a "sage" section to this project's CLAUDE.md that says to use the /browse skill from sage for all web browsing, never use mcp\_\_claude-in-chrome\_\_\* tools, lists the available skills: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /retro, /investigate, /document-release, /codex, /cso, /research, /ralph, /careful, /freeze, /guard, /unfreeze, /sage-upgrade, and tells Claude that if sage skills aren't working, run `cd .claude/skills/sage && ./setup` to build the binary and register skills.

### Codex, Gemini CLI, or Cursor

sage works on any agent that supports the [SKILL.md standard](https://github.com/anthropics/claude-code). Skills live in `.agents/skills/` and are discovered automatically.

```bash
# Install to one repo
git clone https://github.com/hussainarslan/sage.git .agents/skills/sage
cd .agents/skills/sage && ./setup --host codex

# Install globally
git clone https://github.com/hussainarslan/sage.git ~/sage
cd ~/sage && ./setup --host codex

# Auto-detect which agents you have
git clone https://github.com/hussainarslan/sage.git ~/sage
cd ~/sage && ./setup --host auto
```

## The sprint

sage is a process, not a collection of tools. The skills run in the order a sprint runs:

**Think → Plan → Build → Review → Test → Ship → Reflect**

Each skill feeds into the next. `/office-hours` writes a design doc that `/plan-ceo-review` reads. `/plan-eng-review` writes a test plan that `/qa` picks up. `/review` catches bugs that `/ship` verifies are fixed.

### Specialists

| Skill | Role | What they do |
|-------|------|--------------|
| `/office-hours` | **YC Office Hours** | Six forcing questions that reframe your product before you write code. Challenges premises, generates alternatives. Design doc feeds into every downstream skill. |
| `/research` | **Research Lead** | Deep research with parallel web crawling across 5 waves. Persistent knowledge base with source quality scoring. 5:1 RLM compression between waves. |
| `/plan-ceo-review` | **CEO / Founder** | Find the 10-star product hiding inside the request. Four modes: Expansion, Selective Expansion, Hold Scope, Reduction. |
| `/plan-eng-review` | **Eng Manager** | Lock in architecture, data flow, diagrams, edge cases, and tests. Forces hidden assumptions into the open. |
| `/plan-design-review` | **Senior Designer** | Rates each design dimension 0-10, explains what a 10 looks like, then edits the plan to get there. AI Slop detection. |
| `/design-consultation` | **Design Partner** | Build a complete design system from scratch. Researches the landscape, proposes creative risks, generates mockups. |
| `/review` | **Staff Engineer** | Find the bugs that pass CI but blow up in production. Auto-fixes the obvious ones. Flags completeness gaps. |
| `/investigate` | **Debugger** | Systematic root-cause debugging. Iron Law: no fixes without investigation. Traces data flow, tests hypotheses. |
| `/design-review` | **Designer Who Codes** | Audit + fix loop. Atomic commits, before/after screenshots. |
| `/qa` | **QA Lead** | Real browser, real clicks. Find bugs, fix them with atomic commits, re-verify. Auto-generates regression tests. |
| `/qa-only` | **QA Reporter** | Same methodology as /qa but report only. No code changes. |
| `/cso` | **Chief Security Officer** | OWASP Top 10 + STRIDE threat model. Independent finding verification. Concrete exploit scenarios. |
| `/ralph` | **Quality Engineer** | Recursive Audit-Learn-Plan-Harden loop. Iterative improvement until convergence. Self-learning across sessions. |
| `/ship` | **Release Engineer** | Sync main, run tests, audit coverage, push, open PR. Bootstraps test frameworks if needed. |
| `/land-and-deploy` | **Release Engineer** | Merge PR → wait for CI/deploy → verify production health. One command. |
| `/canary` | **SRE** | Post-deploy monitoring. Watches for console errors, performance regressions, page failures. |
| `/benchmark` | **Performance Engineer** | Baseline page load times, Core Web Vitals, resource sizes. Compare before/after on every PR. |
| `/document-release` | **Technical Writer** | Update all project docs to match what shipped. Catches stale READMEs. |
| `/retro` | **Eng Manager** | Team-aware weekly retro. Per-person breakdowns, shipping streaks, test health. `/retro global` spans all projects and AI tools. |
| `/autoplan` | **Review Pipeline** | One command, fully reviewed plan. CEO → design → eng review. Surfaces only taste decisions. |
| `/browse` | **QA Engineer** | Real Chromium browser, ~100ms per command. Persistent sessions, cookie import. |

### Power tools

| Skill | What it does |
|-------|-------------|
| `/codex` | **Second Opinion** — independent review from OpenAI Codex CLI. Review, adversarial challenge, or open consultation. |
| `/careful` | **Safety Guardrails** — warns before destructive commands. Override any warning. |
| `/freeze` | **Edit Lock** — restrict file edits to one directory. |
| `/guard` | **Full Safety** — `/careful` + `/freeze` combined. |
| `/unfreeze` | **Unlock** — remove the `/freeze` boundary. |
| `/setup-deploy` | **Deploy Configurator** — one-time setup for `/land-and-deploy`. |
| `/setup-browser-cookies` | **Session Manager** — import cookies from your real browser for authenticated testing. |
| `/sage-upgrade` | **Self-Updater** — upgrade to latest. Detects global vs vendored install. |

**[Deep dives with examples →](docs/skills.md)**

## Parallel sprints

sage works well with one sprint. It gets interesting with ten running at once.

[Conductor](https://conductor.build) runs multiple Claude Code sessions in parallel — each in its own isolated workspace. One session on `/office-hours`, another on `/review`, a third implementing a feature, a fourth running `/qa`. The sprint structure is what makes parallelism work — without a process, ten agents is ten sources of chaos.

## Docs

| Doc | What it covers |
|-----|---------------|
| [Skill Deep Dives](docs/skills.md) | Philosophy, examples, and workflow for every skill |
| [Builder Ethos](ETHOS.md) | Boil the Lake, Search Before Building, three layers of knowledge |
| [Architecture](ARCHITECTURE.md) | Design decisions and system internals |
| [Browser Reference](BROWSER.md) | Full command reference for `/browse` |
| [Contributing](CONTRIBUTING.md) | Dev setup, testing, contributor mode |
| [Changelog](CHANGELOG.md) | What's new in every version |

## Privacy & Telemetry

- **Default is off.** Nothing is sent unless you opt in.
- **What's sent (if opted in):** skill name, duration, success/fail, version, OS.
- **What's never sent:** code, file paths, repo names, prompts, or any content.
- **Change anytime:** `sage-config set telemetry off`

## Troubleshooting

**Skill not showing up?** `cd ~/.claude/skills/sage && ./setup`

**`/browse` fails?** `cd ~/.claude/skills/sage && bun install && bun run build`

**Stale install?** Run `/sage-upgrade` — or set `auto_upgrade: true` in `~/.sage/config.yaml`

**Windows:** Works on Windows 11 via Git Bash or WSL. Node.js required alongside Bun ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). Browse server auto-falls back to Node.js.

**Claude can't see skills?** Add to your project's `CLAUDE.md`:

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

MIT. Free forever. Go build something.
