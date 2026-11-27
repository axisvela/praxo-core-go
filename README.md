# PRAXO-CORE for Go

Go is the reference implementation of PRAXO-CORE: an embeddable, MIT-licensed agent execution kernel with explicit policy controls, checkpoints, events, and tool calling. It runs in-process and does not require a hosted service.

## At a glance

| Field | Value |
| --- | --- |
| Package | `github.com/axisvela/praxo-core/v2` |
| Registry | [Go module proxy / pkg.go.dev](https://pkg.go.dev/github.com/axisvela/praxo-core/v2) |
| Install | `go get github.com/axisvela/praxo-core/v2@v2.11.3` |
| Source version | `v2.11.3` |
| Published version | `v2.11.3` |
| Publication status | published |
| Canonical source tag | [`v2.11.3`](https://github.com/axisvela/praxo-core/tree/v2.11.3) |
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
go get github.com/axisvela/praxo-core/v2@v2.11.3
```

See the [full Go README](language/go/README.md) for complete installation, build, and verification commands.

## What's included

| Capability | Status | Detail |
| --- | --- | --- |
| Agent loop | native | Policy hooks, final-argument authorization, HITL, and typed events |
| Tools | native | Registry, gateway, JSON Schema, retries, and bounded parallel calls |
| Context | native | Memory, context budgets, middleware, checkpoints, and streaming |
| Providers | native | OpenAI-compatible, Anthropic, and Gemini adapters with SSE |
| Integrations | seams | MCP, OpenTelemetry, workspace/VFS, and process/WASM plugin hosts |
| Retrieval and delegation | native | Retriever seam and local subagent delegation |
| Conformance | native | Shared spec vectors and checked-in API snapshots |

## Examples

Runnable examples live under [`language/go/examples`](language/go/examples).

| Example | What it shows |
| --- | --- |
| [checkpoint](language/go/examples/checkpoint) | This example shows the product-owned checkpoint boundary: |
| [consumer-go](language/go/examples/consumer-go) | This module installs published Core `2.11.3`, without local replacements or optional adapters. It is the current-package starter, separate from the historical `2.5.0` compatibil... |
| [echo](language/go/examples/echo) |  |
| [ecosystem](language/go/examples/ecosystem) | These adapters show how AxisVela components plug into PRAXO-CORE's interfaces. Each adapter accepts a callback, so product code can supply its own client without adding product dependencies to the framework. These skeletons intentionally do not import ecosystem SDKs. For a real Core-backed adapter, see [`../ecosystem-sdk`](https://github.com/axisvela/praxo-core/blob/main/language/go/examples/ecosystem-sdk) (NOETIVELA). |
| [ecosystem-sdk](language/go/examples/ecosystem-sdk) | This is a separate example module that uses real AxisVela SDKs instead of the callback skeletons in [`../ecosystem`](https://github.com/axisvela/praxo-core/blob/main/language/go/examples/ecosystem). |
| [embedded-service](language/go/examples/embedded-service) | This example embeds PRAXO-CORE in a vendor-neutral HTTP service using the published `github.com/axisvela/praxo-core/v2` module. |
| [embedded-service-auth](language/go/examples/embedded-service-auth) | This example extends the embedded HTTP service with an application-verified bearer token and tenant-scoped policy. |
| [governed-workspace](language/go/examples/governed-workspace) | A deterministic, no-API-key demo of the governance path: read-only by default, writes require explicit human approval, denial prevents execution, and a path escape is rejected b... |
| [hitl](language/go/examples/hitl) | This example demonstrates a write tool that requires human approval: |
| [integrator](language/go/examples/integrator) |  |
| [live-model](language/go/examples/live-model) | The Go project lives in [`go/`](https://github.com/axisvela/praxo-core/blob/main/language/go/examples/live-model/go/). Other language projects live under `language/<lang>/examples/live-model`, so the dedicated language mirrors include them. Each example: |
| [multiagent](language/go/examples/multiagent) | This example uses `pkg/agent/delegation` to run two subagents asynchronously and aggregate their results. |
| [plugin](language/go/examples/plugin) | This example shows a minimal runtime plugin process and a host that invokes it through `pkg/plugin/host/process`. |
| [quickstart](language/go/examples/quickstart) |  |
| [recipes](language/go/examples/recipes) |  |
| [reference](language/go/examples/reference) | A small runnable example that combines the OpenAI-compatible adapter with: |
| [representative-chain](language/go/examples/representative-chain) | This example runs one representative governed chain in Go: |
| [sandbox](language/go/examples/sandbox) | A high-risk tool pattern: authorize before execution, allow only an exact command, and run without a shell. |
| [session-checkpoint](language/go/examples/session-checkpoint) | This example shows a two-step multi-turn flow: |
| [workspace-agent](language/go/examples/workspace-agent) | This standalone Go module uses the published PRAXO-CORE package to build a read-only workspace assistant. It registers `fs.list`, `fs.read`, `fs.glob`, and `fs.grep` from `pkg/v... |

## Scenario Tutorials

Scenario-oriented tutorials live under `language/go/Tutorial`. Planning context: [Tutorial Plan](https://axisvela.github.io/praxo-core/getting-started/tutorial-plan/), [100 candidate agent scenarios](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), and [Tutorial Catalog](https://axisvela.github.io/praxo-core/getting-started/tutorial-catalog/).

| Path | What it shows |
| --- | --- |
| [Tutorial](language/go/Tutorial) | Bounded Go examples built on the native Core. Each tutorial is a small, runnable slice with explicit non-goals and an application-owned boundary; none is a complete industry pro... |
| [customs-reroute](language/go/Tutorial/customs-reroute) | A scoped customs tutorial over the Go reference Core. It validates fixed document fields for one shipment, compares two routes and drafts a review-only reroute. The source and m... |
| [emergency-route-plan](language/go/Tutorial/emergency-route-plan) | A scoped emergency-planning tutorial over the Go reference Core. It reads fixed road closures for one event through an application-owned `RoadSource`, drafts a review-only relie... |
| [evidence-vault](language/go/Tutorial/evidence-vault) | A scoped security-operations tutorial over the Go reference Core. It reads one allowlisted evidence file from a local `vfs/localfs` backend confined to a vault root, then drafts... |
| [fullstack-workspace](language/go/Tutorial/fullstack-workspace) | A scoped full-stack-planning tutorial over the Go reference Core. It reads a fixed allowlisted workspace, applies one bounded edit to `app.go` and inspects synthetic diagnostics... |
| [incident-coordination](language/go/Tutorial/incident-coordination) | A scoped operations tutorial over the Go reference Core. It reads one fixed `incident-100` snapshot through an application-owned `IncidentSource` interface, drafts an operator u... |
| [litigation-timeline](language/go/Tutorial/litigation-timeline) | A scoped litigation-support tutorial over the Go reference Core. It builds a cited timeline from fixed synthetic documents, flags one contradiction and drafts a review-only evid... |
| [logistics-checkpoint](language/go/Tutorial/logistics-checkpoint) | A scoped logistics tutorial over the Go reference Core that shows a two-run workflow across a checkpoint. The first run assesses a fixed `shipment-100` and saves a `checkpoint.C... |
| [pentest-lab-review](language/go/Tutorial/pentest-lab-review) | A scoped penetration-testing tutorial over the Go reference Core. It inventories one fixed allowlisted loopback lab host through an application-owned `LabSource`, reports two se... |
| [soc-alert-triage](language/go/Tutorial/soc-alert-triage) | A scoped security-operations tutorial over the Go reference Core. It reads one fixed `alert-100` snapshot through an application-owned `AlertSource`, redacts personal data with... |
| [zero-trust-review](language/go/Tutorial/zero-trust-review) | A bounded first slice of [CY-05](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), not a live policy engine. It reads fixed access events for one tenant, identifies over-granted permissions, and drafts a review-only narrowing. It does not change live grants, authenticate principals or call a live model. |

## Reference Applications

Reference application sources live under `language/go/application`. See each README for implementation scope and validation status.

| Path | What it shows |
| --- | --- |
| [application](language/go/application) | A Go HTTP service and CLI where the agent drives the primary incident workflow: an operator submits an incident intent, the agent searches application-owned telemetry, diagnoses... |

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
- LinkedIn: <https://www.linkedin.com/company/axisvela/>
- Facebook: <https://www.facebook.com/profile.php?id=61596905732406>
- YouTube: <https://www.youtube.com/@axisvela>
- Discord: <https://discord.com/channels/1575163993767809064/1575164343148875977>
- GitHub Discussions: <https://github.com/axisvela/praxo-core/discussions>
- GitHub Issues: <https://github.com/axisvela/praxo-core/issues>
- Documentation: <https://axisvela.github.io/praxo-core/>
- Architect: <https://axisvela.architect.pub>

## Repository layout

- `pkg/`, `adapters/`, `cmd/`, `internal/` — Go module source
- `language/go/examples/` — runnable Go and cross-language examples
- `language/go/Tutorial/` — scenario-oriented tutorials
- `language/go/application/` — AI-native reference application
- `spec/` — shared contract, vectors, and parity inventories
- `LICENSE` — MIT license

## Canonical source

- Canonical source: https://github.com/axisvela/praxo-core
- Registry introduction: `REGISTRY.md`
- Machine-readable entry: `llms.txt` and `llms.md`
- Mirror repository: https://github.com/axisvela/praxo-core-go
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical Go source. The monorepo remains the source of truth and the release workflow source. The mirror's `main` branch tracks current source, not a release snapshot. Source tags refer to the canonical monorepo and are not necessarily present in this mirror; syncing the branch does not publish mirror tags or registry packages.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.
