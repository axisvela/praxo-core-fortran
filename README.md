# PRAXO-CORE for Fortran

A native Fortran 2008 agent implementation with source tag `fortran/v0.9.0`. Version `0.6.0` adds cancellation, stream callbacks, a native SSE parser, and caller-provided batch tool dispatch. Version `0.4.0` replaced the bounded ASCII matcher with upstream RE2 through a small C ABI library. The agent loop, JSON, policy, middleware, and human-in-the-loop interrupt decisions remain Fortran, not a bridge to another agent runtime. All 63 normative vectors across eleven groups and native regressions pass locally. Source tags do not imply package-registry publication.

## At a glance

| Field | Value |
| --- | --- |
| Package | `praxo-core-fortran` |
| Registry | Source / CMake |
| Build | Source build (see README) |
| Source version | `0.9.0` |
| Published version | not published |
| Source tag | `fortran/v0.9.0` |
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
| OpenAI-compatible model | native (transport seam) | `openai_compatible`; caller supplies HTTP transport |
| Anthropic model | native (transport seam) | `anthropic_compatible`; caller supplies HTTP transport |
| Gemini model | native (transport seam) | `gemini_compatible`; caller supplies HTTP transport |
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
| [event-sink](language/fortran/examples/event-sink) | This example uses the Fortran Core sink composition to fan out lifecycle and tool events and filter the tool-only stream. |
| [identity-policy](language/fortran/examples/identity-policy) | This example binds a trusted principal to policy decisions and rejects missing, inactive, role-mismatched, and tenant-mismatched actions. |
| [mcp](language/fortran/examples/mcp) | This example uses a caller-owned in-process transport with the Fortran MCP client. It covers initialize, `tools/list`, and `tools/call` without a server process. |
| [provider-fallback](language/fortran/examples/provider-fallback) | This example calls a fallback only after the primary fails and preserves the primary failure when both fail. |
| [retry](language/fortran/examples/retry) | This example retries a transient failure with a bounded attempt count and keeps the exhausted failure state. |
| [service](language/fortran/examples/service) | This example defines a transport-neutral request handler boundary with health, principal, and run cases. Wire it into any Fortran HTTP server. |
| [streaming](language/fortran/examples/streaming) | This example collects agent stream parts from the Fortran Core and checks the `values` and `messages` lifecycle. |
| [structured-output](language/fortran/examples/structured-output) | This example validates a final JSON answer against a schema and rejects invalid output. |

## Verify

Run the checks from `language/fortran`:

```sh
python language/fortran/run-tests.py
```

This mirror contains the language source and the shared `spec/` vectors, so the implementation can be built and tested here. See [`language/fortran/README.md`](language/fortran/README.md) for the exact commands. The monorepo CI runs conformance, API snapshot, and native tests for this implementation.

## Community

- X: <https://x.com/axisvela>
- Weibo: <https://weibo.com/u/1936025761>

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
