# Forward Impact Skills

Agent skills for the [Forward Impact](https://forwardimpact.team)
engineering standard.

## Install

With [APM](https://microsoft.github.io/apm/):

```bash
apm install forwardimpact/fit-skills
```

With [npx skills](https://github.com/vercel-labs/skills):

```bash
npx skills add forwardimpact/fit-skills
```

## Available Skills

| Skill | Description |
| --- | --- |
| **fit-benchmark** | Prove whether a skill-pack change made agents better at writing code. Use when a single passing eval doesn't prove anything and you need multi-run pass@k evidence, when grading coding tasks with hidden tests the agent cannot see, or when comparing outcomes across skill-set versions. |
| **fit-doc** | Ship a documentation site that agents and humans can both navigate. Use when building a static site from markdown, when previewing with live reload, or when configuring front matter, templates, llms.txt augmentation, content partials, or the pre-build hook. |
| **fit-eval** | Prove whether agent changes improved outcomes with reproducible evidence. Use when an eval passes locally but fails in CI and the only output is 'assertion failed', when you need a pass/fail verdict from a judge agent, or when coordinating multiple specialist agents in one session. Pair with `fit-trace` for trace analysis. |
| **fit-guide** | Find growth areas and verify agent work, both grounded in your organization's engineering standard. Use when a promotion conversation ended without specifics and you need evidence of what to improve, when reviewing agent output and you want a second opinion against the standard, or when asking about skills, levels, and career expectations. Also covers setting up the Guide service stack and ingesting knowledge content. |
| **fit-landmark** | Demonstrate engineering progress without making individuals feel surveilled, and find growth areas backed by evidence. Use when the quarterly review has only ticket counts and you need system-level trends, when checking promotion readiness, when assessing whether culture investments are working, or when exploring GetDX snapshot trends, marker evidence, engineer voice, and growth timelines. |
| **fit-map** | Define what good engineering means so roles have clear, defensible expectations. Use when managers disagree on what a level requires and you need a written standard, when defining or updating skills, capabilities, behaviours, disciplines, tracks, levels, and questions, or when pushing people rosters, syncing GetDX snapshots, ingesting GitHub artifacts, and verifying the activity database. |
| **fit-outpost** | Keep track of people, projects, and threads without depending on memory. Use when context is scattered across email, calendar, and notes and you need a daily briefing, when managing email drafts, or when scheduling background AI tasks, maintaining a personal knowledge base, checking agent status, and waking agents on demand. |
| **fit-pathway** | See what's expected at your level, configure agents to meet your organization's engineering standard, and make staffing decisions you can defend. Use when expectations are unclear and you need role definitions by discipline, track, and level, when agents follow generic practices instead of your standard, when analyzing career progression gaps, or when generating job definitions, interview questions, or a published engineering standard site. |
| **fit-summit** | Make staffing decisions you can defend by modeling team capability as a system. Use when a post-mortem surfaces the same skill gap again, when evaluating whether a hire, transfer, or promotion strengthens the team, when detecting structural risks like single points of failure, or when simulating what-if scenarios, aligning growth with team gaps, comparing teams, and tracking capability trajectory over time. |
| **fit-terrain** | Produce a complete eval dataset from a single DSL file so you can prove agent changes with reproducible evidence. Use when setting up an eval and you need to coordinate generation, rendering, and validation, when bootstrapping a realistic environment for demos or testing, or when regenerating a dataset after a schema change. |
| **fit-trace** | See exactly what an agent did and whether a change improved outcomes. Use when an agent workflow failed and you need to understand why, when you want to measure token usage, cost, and efficiency across runs, or when studying agent behavior patterns from NDJSON traces. |
| **fit-wiki** | Give agent teams stable memory that persists across sessions. Use when an agent finishes a session and its findings would vanish without shared memory, when sending a memo to a teammate, when refreshing storyboard XmR charts, or when bootstrapping and syncing a wiki. |
| **fit-xmr** | Distinguish signal from noise so the team acts on real changes, not fluctuations. Use when a metric changes and the team debates whether it is a real shift or just noise, when you need a compact status chart for a wiki, PR, or report, or when recording and analyzing time-series metrics with Wheeler/Vacanti XmR control charts. |
