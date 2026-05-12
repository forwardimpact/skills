# Forward Impact Skills

Agent skills for the [Forward Impact](https://forwardimpact.team)
engineering standard.

## Install

With [npx skills](https://github.com/vercel-labs/skills):

```bash
npx skills add forwardimpact/fit-skills
```

With [APM](https://microsoft.github.io/apm/), add to your `apm.yml`:

```yaml
dependencies:
  apm:
    - forwardimpact/fit-skills
```

Then `apm install` deploys the skills to your active client
(Claude Code, Copilot, Cursor, OpenCode, Codex, or Gemini). To pull a
single skill, reference it by path:

```yaml
dependencies:
  apm:
    - forwardimpact/fit-skills/skills/fit-doc
```

## Available Skills

| Skill | Description |
| --- | --- |
| **fit-benchmark** | Run coding-agent task families across multiple runs, grade with hidden tests the agent cannot see, and aggregate pass@k across skill-set versions. Use when proving whether a skill-pack change improved coding outcomes. |
| **fit-doc** | Build static documentation sites from markdown with the fit-doc CLI. Use when building, previewing, or configuring a fit-doc site — covers commands, front matter, auto-generated outputs, and the pre-build hook. |
| **fit-eval** | Drive a single agent, run a supervisor–agent relay, or facilitate a multi-agent session — and capture every turn as an NDJSON trace. Use for agent evaluations (pass/fail verdicts) or agent collaboration (specialists coordinating in one session). Pair with `fit-trace` for analysis. |
| **fit-guide** | Find growth areas and verify agent work, both grounded in your organization's engineering standard. Use when a promotion conversation ended without specifics and you need evidence of what to improve, when reviewing agent output and you want a second opinion against the standard, or when asking about skills, levels, and career expectations. Also covers setting up the Guide service stack and ingesting knowledge content. |
| **fit-landmark** | Demonstrate engineering progress without making individuals feel surveilled, and find growth areas backed by evidence. Use when the quarterly review has only ticket counts and you need system-level trends, when checking promotion readiness, when assessing whether culture investments are working, or when exploring GetDX snapshot trends, marker evidence, engineer voice, and growth timelines. |
| **fit-map** | Define what good engineering means so roles have clear, defensible expectations. Use when managers disagree on what a level requires and you need a written standard, when defining or updating skills, capabilities, behaviours, disciplines, tracks, levels, and questions, or when pushing people rosters, syncing GetDX snapshots, ingesting GitHub artifacts, and verifying the activity database. |
| **fit-outpost** | Keep track of people, projects, and threads without depending on memory. Use when context is scattered across email, calendar, and notes and you need a daily briefing, when managing email drafts, or when scheduling background AI tasks, maintaining a personal knowledge base, checking agent status, and waking agents on demand. |
| **fit-pathway** | See what's expected at your level, configure agents to meet your organization's engineering standard, and make staffing decisions you can defend. Use when expectations are unclear and you need role definitions by discipline, track, and level, when agents follow generic practices instead of your standard, when analyzing career progression gaps, or when generating job definitions, interview questions, or a published engineering standard site. |
| **fit-summit** | Make staffing decisions you can defend by modeling team capability as a system. Use when a post-mortem surfaces the same skill gap again, when evaluating whether a hire, transfer, or promotion strengthens the team, when detecting structural risks like single points of failure, or when simulating what-if scenarios, aligning growth with team gaps, comparing teams, and tracking capability trajectory over time. |
| **fit-terrain** | Generate synthetic data for development, testing, and demos. Use when creating example agent-aligned engineering standard definitions, organizational documents, activity records, or knowledge base content from a terrain DSL file, or when testing pipeline changes end-to-end with synthetic datasets. |
| **fit-trace** | Download, query, and analyze agent execution traces. Use when investigating agent behavior, debugging workflow failures, or studying how agents use tools — covers CLI commands, analysis method, and worked examples. |
| **fit-wiki** | Manage the Kata agent team wiki: send cross-team memos, refresh storyboard XmR charts, bootstrap and sync the wiki. Use when an agent needs to communicate with teammates, update storyboard metrics, or sync wiki state. |
| **fit-xmr** | Analyze time-series CSV metrics with Wheeler/Vacanti XmR control charts to distinguish stable processes from special causes. Renders the canonical 14-line X+mR chart and applies the three Wheeler detection rules. Use when a metric is being tracked over time and the question is whether it has changed — covers signal rules, the chart layout, and how to read the report. |
