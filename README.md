# Design Partner for AI coding agents

A portable design system for AI coding tools that work directly in real repositories.

This project gives your coding agent two reusable skills:

- **`design`** — focused design work such as audits, accessibility, responsive layout, interaction, typography, color, motion, redesign, and finishing.
- **`design-auto`** — a hands-off design autopilot that inspects a repository, completes one evidence-backed job at a time, verifies the result, and reports when it is done.

The goal is practical: improve the real interface, preserve the product's intent, test what can actually be tested, and never pretend an unobserved result was verified.

## Why use it?

- Works from the codebase and its existing design language
- Covers brand sites and product interfaces
- Treats accessibility, responsive behavior, states, and recovery as core design work
- Produces structured `checkup`, `review`, and `smell` reports when requested
- Avoids generic generated-design habits and unearned visual effects
- Keeps autonomous work bounded by repository instructions and normal safety approvals

## Quick start

Paste the whole prompt below into Codex, Claude Code, Cursor, OpenCode, or another AI coding agent with filesystem access:

```text
Install the two reusable design skills from this repository:
https://github.com/administrakt0r/commandcode-design-skills

Do the installation yourself and do not ask me routine questions.

1. Fetch the repository into a temporary directory. Do not modify the repository I am currently working in.
2. Detect this AI coding tool's supported global, user-level skill or reusable-workflow directory from its local configuration or documentation. For Codex, prefer $CODEX_HOME/skills when CODEX_HOME is set, otherwise use ~/.codex/skills. For another tool, use its documented equivalent. Do not guess a project-local location if a user-level location exists.
3. Install the repository root as a skill named `design`, preserving `SKILL.md`, `references/`, and `agents/` when that metadata format is supported.
4. Install the repository's `design-auto/` directory as a sibling skill named `design-auto`. Its `../design/` dependency must resolve after installation.
5. If either destination already exists, inspect it first and create a timestamped backup before replacing or merging anything. Preserve unrelated user files and invocation policy unless the repository explicitly defines that policy.
6. If this tool has no native skill system, install equivalent named reusable workflows or prompts called `design` and `design-auto`. Keep all reference files available and adapt only the invocation metadata and path resolution required by the tool; do not rewrite or summarize the design rules.
7. Validate both installed entrypoints, confirm every referenced file exists, and verify that `design-auto` can resolve the sibling `design` skill.
8. Report the exact installed paths, validation performed, and the invocation syntax for this tool. Mention if a restart or new session is required. Do not claim support you could not verify.

Do not commit, push, publish, deploy, or change system-wide configuration outside the selected user-level skill directory.
```

For Codex, start a new session after installation and invoke:

```text
$design checkup
$design redesign the settings page
$design-auto
```

`design-auto` is explicit-only by design, so it will not silently begin an autonomous sweep during an ordinary design request.

## What `design` can do

The skill routes natural-language requests or named modes including:

`checkup`, `smell`, `review`, `deslop`, `typeset`, `recolor`, `motion`, `interaction`, `a11y`, `relayout`, `responsive`, `redesign`, `tokenize`, `setup`, `finish`, `refine`, `voice`, `surface`, and `create`.

Audit modes report only. Implementation modes change real files and verify the result as far as the available tools allow.

## How `design-auto` works

On each invocation it:

1. Reads the repository and its instructions.
2. Establishes or refreshes design audit evidence.
3. Selects the highest-value coherent job.
4. Runs one design mode and verifies that job.
5. Repeats until no safe, evidence-backed work remains.
6. Returns one concise completion report.

It does not bypass credentials, approvals, destructive-action safeguards, production boundaries, or missing product decisions. A blocked action is reported honestly instead of being guessed through.

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

## Publishing note

This directory contains the publishable files but was not initialized, committed, pushed, or published by the preparation process. Add the public repository URL to the Quick start prompt after creating the GitHub repository.
