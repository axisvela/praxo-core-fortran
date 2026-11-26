# PRAXO-CORE for Fortran

PRAXO-CORE is an embeddable, MIT-licensed agent framework. This package is its native Fortran 2008 Core: an in-process agent loop with tools, policy, middleware, events, checkpoints, and human-in-the-loop decisions, implemented in Fortran rather than bridged to another runtime.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxo-core-fortran` |
| Registry | Source / CMake |
| Build | Source build (see README) |
| Source version | `0.12.0` |
| Published version | not published |
| Source tag | `fortran/v0.12.0` |
| Tier | Core |
| Contract | `SPEC_VERSION` `0.2.0` |
| Documentation | https://axisvela.github.io/praxo-core/languages/fortran/ |
| License | MIT |

## Highlights

- OpenAI-compatible model: native (transport seam)
- Anthropic model: native (transport seam)
- Gemini model: native (transport seam)
- MCP client: native (transport seam)
- Harmovela sink: native (transport seam)
- OpenTelemetry sink: native (transport seam)
- Subagent delegation: native (synchronous seam)
- Retriever: native

## Quick start

This implementation is source-only. Follow the build instructions in [`language/fortran/README.md`](language/fortran/README.md).

## What's included

| Capability | Status | Detail |
| --- | --- | --- |
| OpenAI-compatible model | native (transport seam) | `openai_compatible`; caller supplies HTTP transport; `generate_stream` reassembles SSE content, tool calls, usage, and finish reason |
| Anthropic model | native (transport seam) | `anthropic_compatible`; caller supplies HTTP transport; `generate_stream` reassembles Anthropic SSE |
| Gemini model | native (transport seam) | `gemini_compatible`; caller supplies HTTP transport; `generate_stream` reassembles Gemini SSE |
| MCP client | native (transport seam) | `mcp_client`; caller supplies transport |
| Harmovela sink | native (transport seam) | `harmovela`; caller supplies HTTP transport |
| OpenTelemetry sink | native (transport seam) | `otel_sink`; caller supplies transport |
| Subagent delegation | native (synchronous seam) | `subagent_run`; no asynchronous manager |
| Retriever | native | `document`, `retriever`, `retrieve_documents` |

## Examples

Runnable examples live under [`language/fortran/examples`](language/fortran/examples).

| Example | What it shows |
| --- | --- |
| [checkpoint](language/fortran/examples/checkpoint) | This example uses the Fortran Core checkpoint allowlist to encode and decode only registered payload types. |
| [consumer](language/fortran/examples/consumer) | This example runs a deterministic model against the Fortran Core, registers one `record(target)` tool, applies an explicit tool scope plus policy, and checks that an allowed cal... |
| [event-sink](language/fortran/examples/event-sink) | This example uses the Fortran Core sink composition to fan out lifecycle and tool events and filter the tool-only stream. |
| [hitl](language/fortran/examples/hitl) | This example demonstrates a write tool that requires human approval: |
| [identity-policy](language/fortran/examples/identity-policy) | This example binds a trusted principal to policy decisions and rejects missing, inactive, role-mismatched, and tenant-mismatched actions. |
| [live-model](language/fortran/examples/live-model) | This example connects the Fortran Core to an OpenAI-compatible endpoint through the existing `praxo_openai` adapter and registers one low-risk `get_time(zone)` tool. The model m... |
| [mcp](language/fortran/examples/mcp) | This example uses a caller-owned in-process transport with the Fortran MCP client. It covers initialize, `tools/list`, and `tools/call` without a server process. |
| [provider-fallback](language/fortran/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [retry](language/fortran/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](language/fortran/examples/service) | This example defines a transport-neutral request handler boundary with health, principal, and run cases. Wire it into any Fortran HTTP server. |
| [session-checkpoint](language/fortran/examples/session-checkpoint) | This example saves and restores a conversation history across two agent turns. It uses the Core allowlist for payload encoding and a teaching in-memory payload. |
| [streaming](language/fortran/examples/streaming) | This example collects agent stream parts from the Fortran Core and checks the `values` and `messages` lifecycle. |
| [structured-output](language/fortran/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Scenario Tutorials

Scenario-oriented tutorials live under `language/fortran/Tutorial`. Planning context: [Tutorial Plan](https://axisvela.github.io/praxo-core/getting-started/tutorial-plan/), [100 candidate agent scenarios](https://axisvela.github.io/praxo-core/getting-started/agent-scenarios/), and [Tutorial Catalog](https://axisvela.github.io/praxo-core/getting-started/tutorial-catalog/).

| Path | What it shows |
| --- | --- |
| [Tutorial](language/fortran/Tutorial) | Bounded Fortran examples built on the native Core. Each tutorial is a small, runnable slice with explicit non-goals and an application-owned boundary; none is a complete industr... |
| [dispatch-review](language/fortran/Tutorial/dispatch-review) | Simulates a fixed charge/discharge schedule and checks limits outside the agent. No grid command. |
| [eda-placement](language/fortran/Tutorial/eda-placement) | Explores a fixed placement grid and reports stated proxy values. No foundry-valid layout or proven PPA optimization. |
| [fire-spread](language/fortran/Tutorial/fire-spread) | Replays fixed fuel/weather cells and reports a modeled spread. No operational warning or firebreak dispatch. |
| [leak-localization](language/fortran/Tutorial/leak-localization) | Ranks fixed pressure drops and drafts a review-only inspection. No valve isolation or field dispatch. |
| [mesh-review](language/fortran/Tutorial/mesh-review) | Compares a fixed mesh descriptor against stated constraints and drafts an assessment. No manufacturability or mechanical certification. |
| [mining-slope](language/fortran/Tutorial/mining-slope) | Computes fixed displacement indicators and drafts a review alert. No collapse prediction or vehicle dispatch. |
| [ocean-routing](language/fortran/Tutorial/ocean-routing) | Compares fixed route and weather costs and drafts a route. No navigation, fuel-savings or CII compliance claim. |
| [pollution-tracing](language/fortran/Tutorial/pollution-tracing) | Compares fixed sensor readings and drafts two investigation hypotheses. No causal or enforcement finding. |
| [simulation-metrics](language/fortran/Tutorial/simulation-metrics) | A scoped numerical tutorial over the native MIT Fortran Core. It computes fixed simulation metrics through a native tool, then lets a deterministic model package the computed nu... |
| [weather-anomaly](language/fortran/Tutorial/weather-anomaly) | Computes fixed temperature anomalies and drafts a review-only notice. No operational forecast or warning dispatch. |

No accepted end-to-end reference application is recorded for this language yet. Candidate goals are tracked in the [Reference Application Portfolio](https://axisvela.github.io/praxo-core/project/roadmap/#reference-application-portfolio).

## Verify

Run the checks from `language/fortran`:

```sh
python language/fortran/run-tests.py
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/fortran/README.md`](language/fortran/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

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

- `language/fortran/` — implementation source, tests, API snapshot, and examples
- `spec/` — shared contract, vectors, and parity inventories
- `LICENSE` — MIT license

## Canonical source

- Canonical source: https://github.com/axisvela/praxo-core/tree/main/language/fortran
- Registry introduction: `language/fortran/REGISTRY.md`
- Machine-readable entry: `language/fortran/llms.txt` and `language/fortran/llms.md`
- Mirror repository: https://github.com/axisvela/praxo-core-fortran
- Release index: https://axisvela.github.io/praxo-core/languages/registry-status/

This repository is a discovery mirror of the canonical Fortran source. The monorepo remains the source of truth and the release workflow source.

PRAXO-CORE is not a hosted model, workflow engine, identity provider, or safety controller. Do not infer exactly-once execution, complete sandbox isolation, production security certification, live-provider behavior, or physical safety from this package.

MIT licensed.
