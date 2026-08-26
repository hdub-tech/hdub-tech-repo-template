# hdub-tech-repo-template

## First time set-up

### Requirements

1. [podman], [docker] or [npx] (if using linter hook).

### Git hooks

To enable the hooks in [githooks], run the following command from `<repo-root>`:

```bash
git config core.hooksPath ./githooks
```

<details><summary><i>Hooks breakdown</i></summary>

- `post-checkout` hook:
  - `<worktree-dir>/.git` is updated to use a relative path. This helps when the
    repo might be on a shared drive attached to a VM
  - `<worktree-dir>/.claude` will be sym linked to `<repo-root>/.claude`, if
    it exists.
- `commit-msg` hook: lints the message against [commitlint-config] using a
  pinned commitlint — podman or docker if available, else npx.

</details>

### Linting

#### Markdown

Markdown is linted against [markdownlint-config]. Run from `<repo-root>`:

```bash
podman run --rm -v .:/workdir:z,ro docker.io/davidanson/markdownlint-cli2:v0.22.1
```

> [!NOTE]
> _Drop `,ro` if using `markdownlint --fix`, so the volume is writeable._

#### Node (ESLint)

First time set-up:

```bash
nvm use
npm install
```

General use:

```bash
npx eslint FILE_OR_DIR
```

<!-- Links -->
[commitlint-config]:   ./commitlint.config.mjs
[githooks]:            ./githooks
[markdownlint-config]: ./.markdownlint.yaml
[docker]:   https://www.docker.com/get-started/
[npx]:      https://docs.npmjs.com/downloading-and-installing-node-js-and-npm/
[podman]:   https://podman.io/docs/installation
