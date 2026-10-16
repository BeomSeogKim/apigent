# apigent

**API docs that AI agents can actually use.**

apigent reads every service repository in a GitHub organization, extracts the
HTTP APIs (controllers, routes) into a simple catalog, and serves that catalog
to coding agents over MCP and plain HTTP.

It exists because in a microservice org nobody has a single answer to
"which service has the endpoint that does X, and what do I send it?" — so
agents (and humans) end up reading other teams' code or asking in Slack.

## What it answers

One unit: an **operation**.

| field | what |
| --- | --- |
| `service` | which service (repo name, or module name in a monorepo) |
| `method` + `path` | `GET /coupons/{id}/applicable` |
| `request` | path / query / header parameters and body schema |
| `response` | body schema per status code |
| `summary` | one line, only if the source has one |
| `source` | repo, commit, file — so an agent can go check |

Nothing more. No business context, no call graphs, no environment hosts.

## How it works (v1)

1. Register a GitHub organization. That is the only required setting.
2. apigent polls the repos (or a CI job pings a trigger URL) and, for each
   changed file, has an LLM read the controllers and emit operations.
   It does **not** depend on springdoc / swagger / OpenAPI tooling being
   present — that is a later improvement, not a prerequisite.
3. Operations are stored as OpenAPI 3 and served through three tools:
   `search_operations`, `get_operation`, `list_services` — available as an
   MCP server and as the same three HTTP endpoints.

Optional per-repo hints (CLI): include/exclude repos, API class naming
convention, service name for monorepo modules, pull interval, push URL.

## Principles

- **Agents are the consumer.** No documentation UI for humans — Swagger UI
  and friends already do that well.
- **Zero-effort adoption.** Connect an org and it works; settings only exist
  to correct the engine.
- **Self-hosted, open source.** One container, your own LLM key
  (provider selectable). Your source code never leaves the LLM you chose.
- **Vendor-neutral.** Works for any agent that speaks MCP or HTTP.

## Status

Ideation. Nothing runs yet. v1 is done when a repo's controllers come out
complete and correct as agent-readable docs, measured against hand-counted
endpoint lists on a handful of real repos.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) — branch names, Conventional Commits,
PR expectations.

apigent is built with AI coding assistants. Every change is reviewed, tested
and owned by a human maintainer; commits carry no AI attribution, and PRs say
in one line when an AI wrote a substantial part.

## License

MIT — see [LICENSE](LICENSE).
