# PRAXO-CORE for Go

Go is the reference implementation of PRAXO-CORE: an embeddable, MIT-licensed agent execution kernel with explicit policy controls, checkpoints, events, and tool calling. It runs in-process and does not require a hosted service.

## At a glance

| Field | Value |
| --- | --- |
| Package | `github.com/axisvela/praxo-core/v2` |
| Registry | [Go module proxy / pkg.go.dev](https://pkg.go.dev/github.com/axisvela/praxo-core/v2) |
| Install | `go get github.com/axisvela/praxo-core/v2@v2.9.0` |
| Source version | `v2.9.0` |
| Published version | `v2.9.0` |
| Source tag | `v2.9.0` |
| Tier | Core (reference) |
| Contract | `SPEC_VERSION` `0.2.0` |
| Documentation | https://axisvela.github.io/praxo-core/ |
| License | MIT |

## Highlights

- Governed agent loop with policy hooks, tool authorization, HITL, and events.
- Provider-neutral model, tool, memory, checkpoint, sandbox, and VFS seams.
- Runnable examples for live models, consumer starters, HITL, and checkpoints.
- Go is the reference implementation for the shared `spec/` contract.

## Quick start

Install the published package:

```bash
go get github.com/axisvela/praxo-core/v2@v2.9.0
```

See the [full Go README](language/go/README.md) for complete installation, build, and verification commands.

## Examples

Runnable examples live under [`examples`](examples) and [`language/go/examples`](language/go/examples).

| Example | What it shows |
| --- | --- |
| [checkpoint](examples/checkpoint) | This example shows the product-owned checkpoint boundary: |
| [echo](examples/echo) |  |
| [ecosystem](examples/ecosystem) | These adapters show how AxisVela components plug into PRAXO-CORE's interfaces. Each adapter accepts a callback, so product code can supply its own client without adding product... |
| [ecosystem-sdk](examples/ecosystem-sdk) | This is a separate example module that uses real AxisVela SDKs instead of the callback skeletons in [`../ecosystem`](../ecosystem). |
| [embedded-service](examples/embedded-service) | This example embeds PRAXO-CORE in a vendor-neutral HTTP service using the published `github.com/axisvela/praxo-core/v2` module. |
| [embedded-service-auth](examples/embedded-service-auth) | This example extends the embedded HTTP service with an application-verified bearer token and tenant-scoped policy. |
| [governed-workspace](examples/governed-workspace) | A deterministic, no-API-key demo of the governance path: read-only by default, writes require explicit human approval, denial prevents execution, and a path escape is rejected b... |
| [hitl](examples/hitl) | This example demonstrates a write tool that requires human approval: |
| [integrator](examples/integrator) |  |
| [multiagent](examples/multiagent) | This example uses `pkg/agent/delegation` to run two subagents asynchronously and aggregate their results. |
| [plugin](examples/plugin) | This example shows a minimal runtime plugin process and a host that invokes it through `pkg/plugin/host/process`. |
| [quickstart](examples/quickstart) |  |
| [recipes](examples/recipes) |  |
| [reference](examples/reference) | A small runnable example that combines the OpenAI-compatible adapter with: |
| [sandbox](examples/sandbox) | A high-risk tool pattern: authorize before execution, allow only an exact command, and run without a shell. |
| [session-checkpoint](examples/session-checkpoint) | This example shows a two-step multi-turn flow: |
| [workspace-agent](examples/workspace-agent) | This standalone Go module uses the published PRAXO-CORE package to build a read-only workspace assistant. It registers `fs.list`, `fs.read`, `fs.glob`, and `fs.grep` from `pkg/v... |
| [consumer-go](language/go/examples/consumer-go) | This module installs published Core `2.9.0`, without local replacements or optional adapters. It is the current-package starter, separate from the historical `2.5.0` compatibili... |
| [live-model](language/go/examples/live-model) | The Go project lives in [`go/`](go/). Other language projects live under `language/<lang>/examples/live-model`, so the dedicated language mirrors include them. Each example: |

## Verify

Run the module checks from the mirror root:

```bash
go test ./...
go vet ./...
go build ./...
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/go/README.md`](language/go/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

## Community

- X: <https://x.com/axisvela>
- Weibo: <https://weibo.com/u/1936025761>

## Repository layout

- `pkg/`, `adapters/`, `cmd/`, `internal/` — Go module source
- `examples/` — runnable Go and cross-language examples
- `language/go/examples/` — published-package consumer and live-model examples
- `spec/` — shared contract, vectors, and parity inventories
- `LICENSE` — MIT license

## Canonical source

- Canonical source: https://github.com/axisvela/praxo-core
- Registry introduction: `REGISTRY.md`
- Machine-readable entry: `llms.txt` and `llms.md`
- Mirror repository: https://github.com/axisvela/praxo-core-go
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical Go source. The monorepo remains the source of truth and the release workflow source.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.
