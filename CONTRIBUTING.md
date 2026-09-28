# Contributing and Development

This file documents how to run, maintain, and deploy the ACCL website.

## AI-Assisted Development

This website was created and refined with assistance from Google AI Studio and Codex. Human review remains required for content accuracy, scientific claims, deployment settings, and final publishing decisions.

## Tech Stack

- React 19
- Vite 6
- TypeScript
- Tailwind CSS
- React Router
- Motion
- Lucide React

## Branch Naming

Use a personal fork as `origin` and the main repository as `upstream`. Start each new task from the latest `upstream/main`:

```bash
git fetch upstream main
git switch -c <type>/<scope>-<summary> upstream/main
```

Branch names use lowercase kebab case. Choose a type from `feat`, `fix`, `docs`, `refactor`, or `chore`; use the affected area as the scope; and describe one reviewable change in the summary. Do not use a date unless the change belongs to a dated release.

Examples:

```text
feat/group-add-member
fix/publications-author-marker
docs/repo-contribution-guidelines
```

Keep unrelated work on separate branches and in separate pull requests. Do not reuse a branch after its pull request is merged.

## Local Development

Prerequisite: Node.js

Install dependencies from the lockfile:

```bash
npm ci
```

Run the development server:

```bash
npm run dev
```

By default the app is served at:

```text
http://localhost:3000/
```

Build for production:

```bash
npm run build
```

Type-check:

```bash
npm run lint
```

Before committing, check the affected page and assets locally. Run `npm run lint`, `npm run build`, and `git diff --check`. Review `git status` and the staged diff so that generated `dist/` files, temporary files, private source documents, and credentials are not committed.

## Commits and Pull Requests

Use one logical change per commit. Write commit subjects in English as `<type>(<scope>): <imperative summary>`, using the same types and scopes as branch names. Keep the subject specific and avoid a trailing period.

Examples:

```text
feat(group): add Xingwei Zhong
fix(publications): mark corresponding author
docs(repo): define contribution workflow
```

Stage the intended files explicitly and inspect `git diff --cached` before committing. Push the branch to `origin`, then open a pull request against `upstream/main`. The pull request should summarize the change and list the checks performed; include a screenshot when the page layout changes. Do not push directly to `upstream/main`.

For AI-assisted changes, present the exact diff and validation results to Carlz for human review before opening or reopening each pull request. Wait for explicit approval for that specific pull request; approval of earlier work does not apply to later changes.

## Deployment

This repository is deployed with GitHub Pages through GitHub Actions. Pushes to `main` trigger:

```text
.github/workflows/deploy.yml
```

The workflow builds the Vite app, uploads the `dist/` artifact, and deploys it to GitHub Pages. A `404.html` fallback is generated for client-side routing.

Primary domain:

```text
https://ruijun-dang.github.io/
```

The legacy domain `www.ruijundang.pro` should be used as a redirect to the primary site. Do not configure it as the GitHub Pages custom domain if `ruijun-dang.github.io` should remain canonical.

## Content Updates

Most site content is maintained in:

```text
src/data.ts
```

Main pages are in:

```text
src/pages/
```

Assets served from the site root are in `public/`. Assets imported by components or data files are in `src/assets/`:

```text
public/
src/assets/
```

Important sharing and SEO assets:

```text
public/home_banner.png
public/wechat-share.png
index.html
public/sitemap.xml
public/robots.txt
```
