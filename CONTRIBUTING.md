# Contributing

Thanks for contributing to Council of High Intelligence.

## Development flow

1. Sync main:
   - `git checkout main`
   - `git pull origin main`
2. Create a feature branch:
   - `git checkout -b feat/your-change`
3. Make changes and validate:
   - `claude plugin validate .` (manifests, skill, and agent frontmatter as the plugin loader sees them)
   - `./scripts/validate-roster.py` (coordinator prose vs agent frontmatter)
   - `./scripts/council-simulation-checklist.sh`
   - `shellcheck install.sh` (for installer changes)
   - `./install.sh --dry-run`
4. Try the plugin layout in a throwaway session before opening a PR: `claude --plugin-dir .` and run `/council --dry-route --triad decision <question>`.
5. Commit with a clear message and open a PR to `main`.

## Branch cleanup after merge

If a merged branch still appears in your local remote-tracking list, prune stale refs:

- `git fetch origin --prune`

To remove a merged local branch:

- `git branch -d feat/your-change`

## Style notes

- Keep docs and installer behavior in sync.
- `skills/council/SKILL.md` is the one coordinator file Claude Code loads. Keep it a regular file: the plugin loader does not follow symlinks on every install path, and Windows checkouts turn them into one-line text files.
- Address council assets in prompts through `${CLAUDE_PLUGIN_ROOT}/...` (see the Asset Resolution section), never through bare `~/.claude/...` paths.
- Prefer explicit error handling and clear user-facing output in scripts.
- Avoid hardcoded counts when files can be discovered dynamically.
- Keep `demos/session-pack.md` aligned with active profiles and triads.
