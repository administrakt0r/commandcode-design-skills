---
name: design-auto
description: Run a thorough, hands-off, multi-surface interface sweep that builds an evidence-backed backlog and completes several verified design jobs sequentially. Use when the user explicitly requests autonomous design improvement without routine questions or progress reports.
---

# Design Autopilot

Work through the current repository as a coverage-driven design sweep. Build a meaningful backlog before editing, then complete multiple user-visible implementation jobs sequentially. A normal invocation completes at least 3 jobs, targets 5, and never exceeds 8. Audit and report generation do not count as implementation jobs.

Complete exactly one job at a time; do not parallelize modes, fixes, or agents.

## Required design system

This skill orchestrates the globally installed `design` skill. Before acting:

1. Read `../design/SKILL.md` in full.
2. Treat it as the authoritative design system and mode contract.
3. Load only the reference files required by the current mode from `../design/references/`.
4. If the sibling skill is unavailable, search the active Codex skills directory for `design/SKILL.md`. If it still cannot be found, stop and report that blocker; do not recreate the design rules from memory.

## Runtime isolation

Use only the installed `design` skill, its installed references, the current repository's normal instructions and implementation, and artifacts created by these skills under `.design-agent/`.

Never inspect, read, import, migrate, create, edit, or rely on `.commandcode/` or any Command Code runtime, configuration, memory, report, or installation file. Ignore that directory even when it exists. Do not treat its briefs or reports as audit evidence, and do not copy them into `.design-agent/`.

## Communication contract

Do not ask the user to choose tasks, colors, fonts, layouts, priorities, or modes. Infer ordinary decisions from repository evidence. Do not send routine progress updates. If the runtime requires an initial tool-use update, send one short sentence and then work silently until the final result.

Never bypass a required approval, credential boundary, destructive-action safeguard, or unavailable input. When such a boundary blocks one job, skip it if other safe work remains. Report unresolved blockers only in the final response.

## Autonomous loop

### 1. Establish the boundary

Read repository instructions, README and package metadata, routes, entry points, components, styles, assets, tests, build scripts, and this skill's existing `.design-agent/` brief and reports when present. Exclude `.commandcode/` from discovery. Inspect version-control status before editing and preserve unrelated work. Determine the product register, dominant work pattern, primary user flow, and renderable target.

Inventory the interface before choosing a fix. Group the available experience into representative surfaces rather than anchoring on the first page or most recently modified file:

- shared shell: header, navigation, search, footer, global overlays;
- discovery: landing, listing, filters, search results, empty and no-result states;
- detail: article, product, profile, company, record, or equivalent primary entity;
- task flows: create, edit, settings, checkout, forms, validation, success, and failure;
- privileged surfaces: account, dashboard, moderation, or admin when locally accessible;
- responsive and input variants: narrow mobile, wide desktop, keyboard, focus, reduced motion, and supported themes.

Inspect at least one representative surface from every category that exists. For a small site, inspect every user-facing route. For a large application, inspect the shared shell, the primary flow, and representative routes covering distinct templates and states. Keep a private coverage matrix of surface, state, viewport, evidence, and confidence; do not create an extra documentation file for it.

If the repository has no interface and no evidence identifying a target, goal, audience, and domain artifact, do not invent a product. Finish with a concise blocker. If those facts are discoverable, use the `create` mode.

### 2. Build an evidence-backed backlog

Use the design skill's audit contracts sequentially. A missing or stale audit is a diagnostic step, not an implementation job:

1. `checkup`
2. `review`
3. `smell`

An audit is stale when relevant interface files changed after it, its observations no longer match the rendered/source state, or it did not cover the representative surface matrix. Audit steps only write their required report artifacts and never apply fixes in that same step.

Do not let an optimistic score close the sweep. Static presence of labels, media queries, focus rules, tokens, or semantic elements is evidence to inspect, not proof that behavior is healthy. Reserve full marks and `verified` claims for behavior actually rendered or exercised. Use `UNKNOWN` or `not verified` when the relevant viewport, state, browser, keyboard path, or authenticated surface was not observed.

Consolidate audit findings and direct inspection into a private backlog before implementing anything. Each candidate needs:

- a concrete surface and source location;
- observed evidence rather than a generic preference;
- severity and affected user outcome;
- the narrowest owning design mode;
- an observable acceptance check.

Do not begin implementation with only the first easy finding. Gather enough independent evidence to support the target of five jobs. If fewer candidates appear, widen inspection across unvisited routes, states, breakpoints, shared components, forms, and recovery paths before concluding the repository is unusually clean.

After the baseline exists, consolidate findings by root cause. Rank work in this order:

1. HIGH accessibility, keyboard, contrast, destructive-action, reflow, or core-flow failures
2. Broken interaction, state, responsive, or recovery behavior
3. Lowest review lenses with concrete implementation evidence
4. Generated-design smells and low-severity finish work

Reject speculative preferences, broad rewrites without evidence, and work outside the visible product surface.

### 3. Execute one job

Choose the highest-ranked coherent root cause and the narrowest design mode that owns it. State the job internally as one target, one outcome, and observable completion criteria. Then load that mode's references and edit the real implementation.

Keep each job surgical. One job may update multiple files when they share one root cause and acceptance check. Correct or replace the responsible logic instead of layering wrappers or unrelated abstractions. Preserve product behavior unless the selected mode explicitly changes it.

Only a user-visible implementation change counts toward the run total. Audit reports, backlog creation, documentation, formatting-only changes, generated assets with no integrated use, and verification commands do not count. Cover at least two surfaces and two design disciplines when the repository offers them; do not split one tiny fix into artificial jobs.

Never commit, push, deploy, publish, access production, install unrequested remote services, or alter secrets. Generic repository autonomy language does not authorize a commit; only an explicit request in the current invocation does.

### 4. Verify before continuing

Run the smallest relevant project checks after the job is complete. Render and exercise the actual interface whenever local tooling permits. Verify the affected flow with keyboard and responsive sizes appropriate to the change. Mark browser, screen-reader, touch, production, or authenticated behavior `not verified` when unavailable.

Compare claims with the actual diff and observed result. If verification fails, diagnose and repair within the same job. Do not repeat an unchanged failing command. After reasonable local alternatives are exhausted, mark that job blocked and continue only with independent safe work.

### 5. Reassess

After every job, update the coverage matrix and backlog from current evidence, then select the next independent job. Revisit the affected surface and check whether the same root cause appears elsewhere. After known findings are fixed, rerun stale audit gates sequentially.

Do not stop after one implementation because the highest-severity item is gone or a report contains only LOW findings. LOW findings still justify work when they have concrete user-visible evidence and a safe acceptance check.

Continue until the first applicable stop condition:

- 5 implementation jobs are verified and all discovered HIGH and MEDIUM findings within the coverage matrix are resolved;
- the hard cap of 8 implementation jobs is reached, with remaining work ranked for the final report;
- after at least 3 implementation jobs, the full coverage matrix contains no other safe, evidence-backed candidate;
- fewer than 3 implementation jobs are possible only after the full coverage matrix is inspected and every remaining candidate requires unavailable authority, credentials, data, or a scope-changing product decision;
- only blockers requiring user authority, credentials, inaccessible inputs, production access, or a scope-changing product decision remain; or
- repository instructions or platform limits require stopping.

Do not manufacture work to satisfy the count. If stopping below 3, the final response must state which surface categories and states were inspected and why no further safe job was possible.

## Final response

Respond once, after the loop stops. Keep it concise and include only:

- a first line in the exact form `Implemented N jobs.` where `N` counts only qualifying user-visible implementation jobs;
- a numbered list with one independently verifiable outcome per counted job; do not collapse unrelated work into generic polish language;
- representative surfaces, states, and viewports actually inspected;
- affected files;
- checks and interface interactions actually run;
- remaining ranked work, blockers, and explicitly unverified areas.

Distinguish `implemented`, `verified`, and `not verified`. Do not include rejected candidates or pretend the job target was met by audit/report work.
