# Design Partner for AI coding agents

A portable design system for AI coding tools that work directly in real repositories.

This project gives your coding agent two reusable skills:

- **`design`** — focused design work such as audits, accessibility, responsive layout, interaction, typography, color, motion, redesign, and finishing.
- **`design-auto`** — a hands-off design autopilot that inventories the interface, builds an evidence-backed backlog, completes several jobs sequentially, verifies each result, and reports when it is done.

The goal is practical: improve the real interface, preserve the product's intent, test what can actually be tested, and never pretend an unobserved result was verified.

## Why use it?

- Works from the codebase and its existing design language
- Covers brand sites and product interfaces
- Treats accessibility, responsive behavior, states, and recovery as core design work
- Produces structured `checkup`, `review`, and `smell` reports when requested
- Avoids generic generated-design habits and unearned visual effects
- Keeps autonomous work bounded by repository instructions and normal safety approvals
- Runs independently and never reads or writes `.commandcode/`

## Quick start: install or update

Use this same prompt for a first installation or to update a stale installation. Paste it into Codex, Claude Code, Cursor, OpenCode, or another AI coding agent with filesystem access:

```text
Install or update the two reusable design skills from this repository to its latest available commit:
https://github.com/administrakt0r/commandcode-design-skills

Do the work yourself and do not ask me routine questions. Treat the repository as the source of truth; do not recreate or summarize its skill instructions.

1. Fetch a fresh copy of the repository into a temporary directory and record the resolved commit SHA. Do not modify the repository I am currently working in.
2. Detect this AI coding tool's supported global, user-level skill or reusable-workflow directory from its local configuration or documentation. For Codex, prefer $CODEX_HOME/skills when CODEX_HOME is set, otherwise use ~/.codex/skills. For another tool, use its documented equivalent. Do not guess a project-local location if a user-level location exists.
3. Inspect the existing `design` and `design-auto` destinations if present. Compare them with the fetched commit. If both already match exactly, leave them unchanged and report that they are current.
4. Assemble clean staging directories on the same filesystem. The staged `design` skill must contain the repository's root `SKILL.md`, `references/`, and `agents/`. The staged `design-auto` skill must contain `design-auto/SKILL.md` and `design-auto/agents/`. Do not copy the nested `design-auto/` directory into the staged `design` skill.
5. Validate both staged skills before changing an installed copy. Confirm the frontmatter, referenced files, metadata, sibling dependency, and explicit-only invocation policy for `design-auto`.
6. For each stale or missing destination, create a timestamped backup if it exists, then replace that exact managed skill directory with its validated staging directory. Do not merge old files into the new package because that retains stale references. Do not modify sibling skills or delete the backup.
7. If this tool has no native skill system, install or update equivalent named reusable workflows or prompts called `design` and `design-auto`. Keep all reference files available and adapt only the invocation metadata and path resolution required by the tool; do not rewrite or summarize the design rules.
8. Verify the final installed copies against the fetched commit. Confirm every referenced file exists, `design-auto` resolves the sibling `design` skill, neither skill operationally reads or writes `.commandcode/`, and project artifacts are restricted to `.design-agent/`.
9. Report whether each skill was installed, updated, or already current; include the source commit SHA, exact installed paths, validation performed, invocation syntax, backup paths, and whether a restart or new session is required. Do not claim support you could not verify.

Do not commit, push, publish, deploy, or change system-wide configuration outside the selected user-level skill directory. Clean up only the temporary fetch and staging directories you created after successful verification.
```

For Codex, start a new session after installation and invoke:

```text
$design checkup
$design redesign the settings page
$design-auto
```

`design-auto` is explicit-only by design, so it will not silently begin an autonomous sweep during an ordinary design request.

## Ready-to-use workflows

### Thorough autonomous sweep

Use this when you want the agent to scan broadly, build its own backlog, and complete several improvements without routine interaction:

```text
Use $design-auto to thoroughly inspect this repository and improve the interface. Work through several evidence-backed jobs sequentially, verify each one, and report only when the sweep is complete.
```

### Focused implementation

Name the surface and outcome. The skill selects the appropriate design mode:

```text
Use $design to make the account settings page clearer, more responsive, and easier to complete with a keyboard. Edit the real implementation and verify the result.
```

### Audit, then repair

Run each prompt as a separate turn because audit modes intentionally create reports without changing the interface:

```text
Use $design checkup to audit the interface. Create only the required report artifacts.
```

```text
Use $design to fix the highest-impact evidence-backed findings from the latest design reports, then verify the implementation.
```

### Establish project design context

Use once when a repository needs durable product, audience, voice, and visual-direction context:

```text
Use $design setup to inspect this repository and create or update its design brief.
```

### Create a new interface

Give the agent a concrete product, audience, and primary task instead of asking for a generic page:

```text
Use $design create to build a responsive appointment-booking interface for a neighborhood clinic. Patients must be able to choose a service, practitioner, date, and available time, then review their selection before confirming.
```

### Pre-release finish

Use after functionality is complete:

```text
Use $design finish to inspect the completed interface, correct safe release-blocking design issues, and verify accessibility, responsive behavior, states, and visual consistency without changing product scope.
```

## Independent runtime

These skills do not require Command Code and do not use its project files. They ignore `.commandcode/` completely, even when that directory already exists.

Their own optional project memory and audit artifacts live only under `.design-agent/`:

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

## What `design` can do

The skill routes natural-language requests or named modes including:

`checkup`, `smell`, `review`, `deslop`, `typeset`, `recolor`, `motion`, `interaction`, `a11y`, `relayout`, `responsive`, `redesign`, `tokenize`, `setup`, `finish`, `refine`, `voice`, `surface`, and `create`.

Audit modes report only. Implementation modes change real files and verify the result as far as the available tools allow.

## How `design-auto` works

On each invocation it:

1. Inventories representative routes, templates, states, viewports, and input modes.
2. Establishes or refreshes design audit evidence without treating reports as implementation work.
3. Builds and ranks a concrete backlog before choosing the first easy fix.
4. Runs one design mode at a time and verifies each user-visible job.
5. Completes at least 3 jobs in a normal run, targets 5, and caps the run at 8.
6. Returns one concise completion report with coverage, completed jobs, verification, and remaining work.

It does not invent work merely to reach a count, and it does not bypass credentials, approvals, destructive-action safeguards, production boundaries, or missing product decisions. An unusually clean or blocked project may finish below 3 jobs only after the full coverage matrix is inspected and the reason is reported.

## Repository layout

```text
.
├── SKILL.md                 # design skill entrypoint
├── agents/openai.yaml       # Codex-facing metadata
├── references/              # mode-specific design guidance
├── design-auto/
│   ├── SKILL.md             # autonomous orchestrator
│   └── agents/openai.yaml   # explicit-only invocation metadata
└── PROMPT.md                # portable fallback for tools without skills
```

The diagnostic report HTML template is only for generated audit reports. It is not a product UI starter or visual style recommendation.

## Portable fallback

If an agent cannot install skills, use [PROMPT.md](PROMPT.md) as a turn-level instruction and keep it beside `SKILL.md` and `references/`. The fallback contains no machine-specific absolute path.

## Repository

Published at [administrakt0r/commandcode-design-skills](https://github.com/administrakt0r/commandcode-design-skills).
