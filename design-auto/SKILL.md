---
name: design-auto
description: Autonomously audit and improve an existing repository's interface one evidence-backed design job at a time. Use when the user explicitly asks for a hands-off design sweep that should inspect, implement, verify, and continue without routine questions or progress reports.
---

# Design Autopilot

Work in the current repository until no safe, evidence-backed design job remains. Select and complete exactly one job at a time; do not parallelize modes, fixes, or agents.

## Required design system

This skill orchestrates the globally installed `design` skill. Before acting:

1. Read `../design/SKILL.md` in full.
2. Treat it as the authoritative design system and mode contract.
3. Load only the reference files required by the current mode from `../design/references/`.
4. If the sibling skill is unavailable, search the active Codex skills directory for `design/SKILL.md`. If it still cannot be found, stop and report that blocker; do not recreate the design rules from memory.

## Communication contract

Do not ask the user to choose tasks, colors, fonts, layouts, priorities, or modes. Infer ordinary decisions from repository evidence. Do not send routine progress updates. If the runtime requires an initial tool-use update, send one short sentence and then work silently until the final result.

Never bypass a required approval, credential boundary, destructive-action safeguard, or unavailable input. When such a boundary blocks one job, skip it if other safe work remains. Report unresolved blockers only in the final response.

## Autonomous loop

### 1. Establish the boundary

Read repository instructions, README and package metadata, routes, entry points, components, styles, assets, tests, build scripts, existing design brief, and existing design reports. Inspect version-control status before editing and preserve unrelated work. Determine the product register, dominant work pattern, primary user flow, and renderable target.

If the repository has no interface and no evidence identifying a target, goal, audience, and domain artifact, do not invent a product. Finish with a concise blocker. If those facts are discoverable, use the `create` mode.

### 2. Build an evidence-backed backlog

Use the design skill's audit contracts sequentially. A missing or stale audit is one job by itself:

1. `checkup`
2. `review`
3. `smell`

An audit is stale when relevant interface files changed after it or its observations no longer match the rendered/source state. Audit jobs only write their required report artifacts and never apply fixes in the same job.

After the baseline exists, consolidate findings by root cause. Rank work in this order:

1. HIGH accessibility, keyboard, contrast, destructive-action, reflow, or core-flow failures
2. Broken interaction, state, responsive, or recovery behavior
3. Lowest review lenses with concrete implementation evidence
4. Generated-design smells and low-severity finish work

Reject speculative preferences, broad rewrites without evidence, and work outside the visible product surface.

### 3. Execute one job

Choose the highest-ranked coherent root cause and the narrowest design mode that owns it. State the job internally as one target, one outcome, and observable completion criteria. Then load that mode's references and edit the real implementation.

Keep each job surgical. Correct or replace the responsible logic instead of layering wrappers or unrelated abstractions. Preserve product behavior unless the selected mode explicitly changes it. Do not commit, push, deploy, publish, access production, install unrequested remote services, or alter secrets.

### 4. Verify before continuing

Run the smallest relevant project checks after the job is complete. Render and exercise the actual interface whenever local tooling permits. Verify the affected flow with keyboard and responsive sizes appropriate to the change. Mark browser, screen-reader, touch, production, or authenticated behavior `not verified` when unavailable.

Compare claims with the actual diff and observed result. If verification fails, diagnose and repair within the same job. Do not repeat an unchanged failing command. After reasonable local alternatives are exhausted, mark that job blocked and continue only with independent safe work.

### 5. Reassess

Update the backlog from current evidence and select the next single job. After known findings are fixed, rerun stale audit gates sequentially. Continue while a safe actionable finding remains. Stop when:

- all verified HIGH and MEDIUM findings are resolved;
- no remaining LOW finding justifies a safe repository change;
- only blockers requiring user authority, credentials, inaccessible inputs, production access, or a scope-changing product decision remain; or
- repository instructions or platform limits require stopping.

Do not manufacture work merely to keep the loop running.

## Final response

Respond once, after the loop stops. Keep it concise and include only:

- completed jobs and their user-visible outcomes;
- affected files;
- checks and interface interactions actually run;
- remaining blockers or explicitly unverified areas.

Distinguish `implemented`, `verified`, and `not verified`. Do not include the internal backlog, rejected candidates, or a proposed plan.
