---
name: "Vue Vben Admin Contributor Guide"
description: "Development workflow and contribution rules for the Vue Vben Admin monorepo"
lastUpdated: "2025-06-11"
---

# Contributor Guide

## Directory Overview
- `apps` – application source including `web-antd`, `web-ele`, `web-naive` and `backend-mock`.
- `packages` – shared packages such as `@core`, `effects`, `stores`, and more.
- `internal` – lint, tsconfig and vite configuration helpers.
- `docs` – documentation site source.
- `scripts` – CLI helpers and turbo run scripts.
- `playground` – small demo projects.

For a complete tree see [docs/src/guide/project/dir.md](docs/src/guide/project/dir.md).

## Quick Start
1. Ensure **Node.js 20.15+** and **Git** are installed. Check versions with `node -v` and `git -v`.
2. Clone the repository:
   ```bash
   git clone https://github.com/vbenjs/vue-vben-admin.git
   ```
   Gitee mirrors are available but may lag behind.
3. Keep the project path free of spaces or non‑Latin characters or the dev server will fail.
4. Install dependencies using the bundled pnpm via Corepack:
   ```bash
   npm i -g corepack
   pnpm install
   ```
   If npm registry access is blocked, set `COREPACK_NPM_REGISTRY=https://registry.npmmirror.com`.
5. Start a project with `pnpm dev` and choose an app from the list, or run `pnpm run dev:antd`, `pnpm run dev:ele`, `pnpm run dev:naive`, `pnpm run dev:docs`, or `pnpm run dev:play` directly.

## Dev Environment Tips
- Use **pnpm** with Node.js 22.1.0 (at least 20.10.0). The exact version is in `.node-version`.
- After cloning the repo run `corepack enable` and then `pnpm install` to install dependencies.
- Start all packages with `pnpm dev`, or use `pnpm dev:antd`, `pnpm dev:naive`, `pnpm dev:ele`, or `pnpm dev:docs` for a specific app.
- To preview documentation only run `pnpm run docs:dev`.
- Build the project with `pnpm build` or use the `build:<app>` scripts under `package.json`.
- Use the internal CLI tools located in `scripts/`:
  - `pnpm vsh lint` – lint the repo, `pnpm format` – format files.
  - `pnpm check` – run circular dependency, dependency, type and spelling checks.
  - `pnpm vsh code-workspace --auto-commit` – update VSCode workspace file (run automatically on commit).
- If dependency installation fails, run `pnpm reinstall` to clean and reinstall all packages.
- `pnpm turbo-run <command>` provides interactive helpers for common scripts.
- Changesets are managed with `pnpm run changeset` and versioning with `pnpm run version`.

## Testing Instructions
- Run unit tests with `pnpm test:unit`.
- Run `pnpm lint` to ensure ESLint, Stylelint and Prettier rules pass.
- Type check with `pnpm check:type`; you can run all checks with `pnpm check`.

## Git & Commit Guidelines
- Commit messages follow the conventional commit standard. Allowed types include `feat`, `fix`, `perf`, `style`, `docs`, `test`, `refactor`, `build`, `ci`, `chore`, `revert`, `types`, and `release`.
- Use `pnpm commit` to generate commit messages that satisfy [CommitLint](internal/lint-configs/commitlint-config/README.md).
- Pre‑commit hooks run via lefthook to format and lint staged files automatically.

## Pull Request Instructions
- Create a topic branch from `main` and open your PR against `main`.
- Explain the reason for new features or provide details when fixing a bug.
- Run tests and lint checks before submitting.
- Keep your PR focused; multiple small commits are acceptable as GitHub can squash them on merge.
- Title your PR in the form `[<project_name>] <Title>` so changelogs generate correctly.
- Avoid modifying `pnpm-lock.yaml` unless you add or update dependencies.

See the `docs/` directory or <https://doc.vben.pro/guide/introduction/vben.html> for detailed documentation.
The quick-start guide is available in [docs/src/guide/introduction/quick-start.md](docs/src/guide/introduction/quick-start.md).
