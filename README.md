# hdub-tech-repo-template

# First time set-up

## Requirements

1. [podman] or [npx] (if using linter hook).

## Git hooks

To enable the hooks in [githooks], run the following command from `<repo-root>`:

```bash
git config core.hooksPath ./githooks
```

<details><summary><i>Hooks breakdown</i></summary>

- `post-checkout` hook:
  - `<repo-root>/,git/worktrees/<worktree-name>/gitdir` and
    `<worktree-dir>/.git` are updated to use relative paths. This helps when the
    repo might be on a shared drive attached to a VM
  - `<worktree-dir>/.claude/memory` will be aliased to
    `<repo-root>/.claude/memory`, if it exists.

</details>

<!-- Links -->
[githooks]: ./githooks
[npx]:      https://docs.npmjs.com/downloading-and-installing-node-js-and-npm/
[podman]:   https://podman.io/docs/installation
