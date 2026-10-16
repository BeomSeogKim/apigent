# Contributing to apigent

Thanks for taking the time. apigent is early — if something here is unclear,
open an issue and ask.

## Branches

- `main` is always releasable. Nothing is pushed to it directly.
- Work on a branch named `<type>/<short-description>`, e.g.
  `feat/github-org-polling`, `fix/mcp-empty-result`, `docs/readme-quickstart`.
- Open a pull request against `main`. One topic per PR.

## Commit messages

We follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

```
<type>(<optional scope>): <subject>

<optional body>

<optional trailers>
```

**type** is one of:

| type | when |
| --- | --- |
| `feat` | a new capability visible to users |
| `fix` | a bug fix |
| `docs` | documentation only |
| `refactor` | code change that neither fixes a bug nor adds a feature |
| `test` | adding or correcting tests |
| `perf` | a performance improvement |
| `build` | build system or dependencies |
| `ci` | CI configuration |
| `chore` | anything else that does not touch `src` or tests |

**scope** is optional and names the area: `engine`, `mcp`, `http`, `cli`,
`store`, `github`.

**subject**: imperative mood ("add", not "added" or "adds"), lower-case
first letter, no trailing period, at most 72 characters.

**body**: explain *why*, not what — the diff shows what. Wrap at 72.

**breaking changes**: add `!` after the type/scope (`feat(cli)!: …`) and a
`BREAKING CHANGE:` footer describing the migration.

Examples:

```
feat(github): poll organization repos on a configurable interval

fix(mcp): return an empty list instead of an error when no operation matches

docs: describe the operation data model
```

### AI assistance

apigent is developed with AI coding assistants, and contributors may use
them too. We disclose this at the project level, not per commit:

- Commits carry no AI co-author trailers or "generated with" banners. The
  person who opens the PR is the author and is accountable for every line.
- If an AI tool wrote a substantial part of a PR, say so in one line of the
  PR body ("Drafted with Claude Code; reviewed and tested by me.").
- Review AI output as you would a stranger's patch: read it, run it, test it.

## Pull requests

- Title follows the commit subject rules.
- Body: what changed and why, how you verified it, anything left open.
- Keep PRs small enough to review in one sitting. Squash-merge is the
  default; the squashed message must still follow the rules above.

## Code

- Every change that adds behavior comes with a test.
- Run the project's checks locally before pushing (see the README once
  there is code to run).

## License

By contributing you agree that your contributions are licensed under the
MIT License in [LICENSE](LICENSE).
