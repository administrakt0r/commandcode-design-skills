# Install or update Design Partner skills

Install or update both skills from the latest commit of:

`https://github.com/administrakt0r/commandcode-design-skills`

Work autonomously and ask only for a platform-mandated approval needed for network access or writing to the user skill directory. Do not ask routine questions. The fetched repository is authoritative; never recreate, shorten, or paraphrase its skill instructions.

## Target

Install the skills globally for the current user so they are available in every codebase:

- `design`
- `design-auto`

For Codex CLI and OpenCode CLI, use the shared agent-skills location `$HOME/.agents/skills`. Both CLIs discover skills there. If the active CLI has an explicitly configured, documented user-level skill directory that supersedes this location, use that directory and report it. Never install into the current project merely because it is writable.

## Procedure

1. Fetch a fresh copy of the source repository into a temporary directory without modifying the current project. Resolve and record the fetched commit SHA. Prefer `git`; if it is unavailable, download the GitHub archive for the default branch.
2. Resolve the selected user-level skills root and the exact destinations `<skills-root>/design` and `<skills-root>/design-auto`. Inspect existing destinations when present. Also inspect only the exact legacy user-level destinations for these two skills when they exist, including `${CODEX_HOME:-$HOME/.codex}/skills/{design,design-auto}` and `$HOME/.config/opencode/skills/{design,design-auto}`; never touch other skills.
3. Assemble clean staging directories on the same filesystem as the destination:
   - `design` contains only the source repository's root `SKILL.md`, `references/`, and `agents/`.
   - `design-auto` contains only `design-auto/SKILL.md` and `design-auto/agents/`.
   - Do not nest the source `design-auto/` directory inside the staged `design` skill.
4. Validate both staged packages before changing installed files. Confirm valid `name` and `description` frontmatter, all referenced files, metadata, the sibling `design` dependency, and `design-auto`'s explicit-only policy. When Codex's `quick_validate.py` is available, run it against both staged directories; otherwise perform equivalent structural checks.
5. Compare staged packages with installed packages. If both are identical, make no changes and report that they are already current at the fetched SHA.
6. For every stale destination, move the existing directory to a timestamped backup outside the discoverable `skills/*/SKILL.md` path, then move the validated staged directory into its exact destination. Replace the managed directory as a unit; never merge into it because merging preserves stale files. Do not alter sibling skills or delete backups.
7. Verify the installed copies against staging. Confirm that every required reference exists, `design-auto` resolves the sibling `design` skill, neither package operationally reads or writes `.commandcode/`, and its project artifacts are restricted to `.design-agent/`.
8. After the shared installation verifies successfully, prevent version ambiguity: move any legacy active copies of these exact two skills to the timestamped backup area outside every discoverable skills path. Do not delete them, and do not move or modify any other skill. If an active duplicate cannot be moved safely, leave it untouched and report the exact conflict instead of claiming the update is complete.
9. Remove only the temporary fetch and unused staging directories created by this operation after verification succeeds.

Do not commit, push, publish, deploy, install unrelated dependencies, or change system-wide configuration. Do not edit the current project.

Finish with one concise report containing:

- `design`: installed, updated, or already current;
- `design-auto`: installed, updated, or already current;
- fetched commit SHA and exact installed paths;
- validation performed and any backup paths;
- any migrated legacy copies or unresolved duplicate conflicts;
- invocation syntax for the active CLI;
- whether Codex or OpenCode must be restarted or opened in a new session.
