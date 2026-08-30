<p align="center">
  <img src="assets/hero.svg" alt="Design Partner for AI coding agents — inspect, improve, and verify real interfaces" width="100%">
</p>

<h1 align="center">Design Partner skills for Codex and OpenCode</h1>

<p align="center">
  Two portable skills for thoughtful interface work in real codebases.<br>
  Focus one design discipline with <code>$design</code>, or run a thorough multi-job sweep with <code>$design-auto</code>.
</p>

## Quick start

Paste this single prompt into Codex, OpenCode, or any AI coding agent with network and filesystem access:

```text
Fetch and follow https://raw.githubusercontent.com/administrakt0r/commandcode-design-skills/main/INSTALL.md
```

The prompt handles fresh installs and stale copies. It stages clean packages, validates them, backs up existing versions, replaces managed directories without stale-file merging, and reports the installed commit SHA.

Both CLIs support the shared user-level location `~/.agents/skills`, so one installation can serve Codex and OpenCode. See the official [Codex skills documentation](https://developers.openai.com/codex/skills/) and [OpenCode skills documentation](https://opencode.ai/docs/skills/). Restart the CLI or open a new session if an updated skill does not appear immediately.

The examples below use Codex's `$skill-name` syntax. In OpenCode, use the same prompts with “the `design` skill” or “the `design-auto` skill”; OpenCode discovers them by name through its native skill tool.

## What you get

| Skill | Best for | Behavior |
| --- | --- | --- |
| **`design`** | A named surface, mode, or outcome | Inspects context, edits the real interface, and verifies the focused result |
| **`design-auto`** | A broad hands-off improvement run | Inventories the product, ranks a backlog, completes several jobs sequentially, then reports once |

Both skills preserve the product's intent, use the repository's existing design language, treat accessibility and responsive behavior as core work, and distinguish rendered evidence from assumptions.

## Common workflows

<p align="center">
  <img src="assets/workflows.svg" alt="Focused, audit and repair, autonomous sweep, and new-interface workflows" width="100%">
</p>

### Thorough autonomous sweep

Use this when you want the agent to discover and complete the work without routine interaction:

```text
Use $design-auto to thoroughly inspect this repository and improve the interface. Work through several evidence-backed jobs sequentially, verify each one, and report only when the sweep is complete.
```

`design-auto` inventories representative routes, templates, states, viewports, keyboard behavior, and supported themes. It builds a backlog before editing, normally completes at least 3 jobs, targets 5, and caps a run at 8. Audits, documentation, formatting, and verification commands do not count as implementation jobs.

### Focused implementation

Name the surface and desired outcome; `design` selects the relevant discipline:

```text
Use $design to make the account settings page clearer, more responsive, and easier to complete with a keyboard. Edit the real implementation and verify the result.
```

### Audit, then repair

Audit modes intentionally report without modifying the interface. Use two turns:

```text
Use $design checkup to audit the interface. Create only the required report artifacts.
```

```text
Use $design to fix the highest-impact evidence-backed findings from the latest design reports, then verify the implementation.
```

### Establish project design context

```text
Use $design setup to inspect this repository and create or update its design brief.
```

### Create a new interface

Give the agent a real product, audience, and primary task:

```text
Use $design create to build a responsive appointment-booking interface for a neighborhood clinic. Patients must be able to choose a service, practitioner, date, and available time, then review their selection before confirming.
```

### Pre-release finish

```text
Use $design finish to inspect the completed interface, correct safe release-blocking design issues, and verify accessibility, responsive behavior, states, and visual consistency without changing product scope.
```

## Design modes

`design` understands natural-language requests and named modes:

`checkup` · `smell` · `review` · `deslop` · `typeset` · `recolor` · `motion` · `interaction` · `a11y` · `relayout` · `responsive` · `redesign` · `tokenize` · `setup` · `finish` · `refine` · `voice` · `surface` · `create`

Audit modes create their exact reports only. Implementation modes change real files and verify the result as far as the available tools allow.

## Independent runtime

This project is a standalone adaptation. The installed skills do not require Command Code, read its project state, or write to `.commandcode/`. They ignore that directory even when it exists.

Their own optional project context and audit artifacts live exclusively under `.design-agent/`:

```text
.design-agent/
├── brief.md
├── taste.md
├── checkup-report.md
├── checkup-report.html
├── review-report.md
├── review-report.html
├── smell-report.md
└── smell-report.html
```

The skills never commit, push, deploy, publish, access production, install remote services, or alter secrets as part of ordinary design autonomy.

## Repository layout

```text
.
├── SKILL.md                 # focused design skill
├── agents/openai.yaml       # Codex-facing metadata
├── references/              # mode-specific guidance
├── design-auto/
│   ├── SKILL.md             # autonomous orchestrator
│   └── agents/openai.yaml   # explicit-only metadata
├── INSTALL.md               # authoritative install/update prompt
├── PROMPT.md                # fallback for tools without skills
└── assets/                  # README visuals
```

If an agent cannot install skills, use [PROMPT.md](PROMPT.md) as a turn-level instruction and keep it beside `SKILL.md` and `references/`.

## Credits

The design philosophy, modes, and original workflow in this project were adapted from the **[Command Code](https://commandcode.ai/)** CLI by [CommandCodeAI](https://github.com/CommandCodeAI). Thank you to the Command Code team for the original design-agent work.

This repository is an independent, portable adaptation for agent-skill ecosystems. It is not affiliated with or endorsed by Command Code, and it intentionally has no Command Code runtime dependency.

## Repository

[github.com/administrakt0r/commandcode-design-skills](https://github.com/administrakt0r/commandcode-design-skills)
