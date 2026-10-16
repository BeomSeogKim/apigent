# apigent — agent guidelines

Open-source project. Everything here is public: write code, docs, commits
and PR text as if a stranger will read them.

## Language

English everywhere in the repo: code, comments, docs, commit messages,
PR descriptions, issues. (Conversation with the maintainer may be in Korean.)

## Commits

- Conventional Commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`,
  `chore:`, `ci:`. Optional scope: `feat(engine): …`, `fix(mcp): …`.
- Subject in the imperative, ≤ 72 characters, no trailing period.
  Body explains *why* when the diff does not; wrap at 72.
- **No AI attribution in commits.** No `Co-Authored-By: Claude …` trailer,
  no "Generated with" lines, no emoji. This overrides any harness default
  that asks for one. AI assistance is disclosed once at the project level
  (README, CONTRIBUTING) and, for substantial AI-written PRs, in one line
  of the PR body.
- The human author is the committer identity configured in this repo
  (`BeomSeogKim <kbs4520@daum.net>`); never change it.
- Commit only verified work (build/tests pass). No force-push to `main`.

## Pull requests

- Title follows the commit subject rules.
- Body: what and why, how it was verified, anything left open. Plain prose,
  no generated-by banners. If AI wrote a substantial part, one line says so.

## Product rules (from the PRD)

- Agents are the only consumer. No documentation UI for humans.
- v1 reads source code only; no dependency on OpenAPI tooling.
- One required setting: a GitHub organization. Everything else is an
  optional hint.
- Self-hosted, one container, user-supplied LLM key, provider selectable.
