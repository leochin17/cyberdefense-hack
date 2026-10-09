# SourceGate

A planned npm-compatible artifact gateway with continuous supply-chain research, Semgrep scanning, and evidence-backed installation decisions.

**Status: design stage.** This repository currently contains the build specification. It has no application implementation, working registry endpoint, validated sponsor integrations, or passing test suite yet.

## What it will do

SourceGate will watch npm releases, compare exact artifacts with recorded baselines, collect advisory evidence, and scan package contents before making a policy decision. Engineers will install approved versions through a registry endpoint and inspect the evidence behind quarantines and revocations in a dashboard.

A passed scan is not proof that a package is safe. Decisions will show their evidence, coverage, freshness, and policy revision. Unknown, failed, or incomplete assessments will not approve a download.

## Planned sponsor integrations

| Sponsor | Intended role | Current status |
| --- | --- | --- |
| [Semgrep](https://docs.semgrep.dev/running-rules) | Static analysis of package contents and suspicious install-time behavior | Not implemented |
| [ClickHouse](https://clickhouse.com/docs/) | Investigation events, audit history, and dashboard analytics | Not implemented |
| [Guild](https://docs.guild.ai/) | Recurring research agents with cited reports | Not implemented |
| [Akash](https://akash.network/docs/) | Container hosting for the gateway and workers | Not deployed |
| [Senso](https://docs.senso.ai/docs/overview) | Optional retrieval of vetted incident evidence | Optional extension |

The target is at least three demonstrated, working sponsor integrations. Configuration files or mocked responses will not count as a live integration.

## MVP scope

- npm packages containing JavaScript/TypeScript, starting with a curated watchlist and its dependency tree.
- Integrity and registry-signature verification, release comparisons, advisory evidence, and versioned Semgrep rules.
- Isolated artifact extraction and scanning without executing package lifecycle scripts.
- An npm-compatible installation endpoint, immutable artifact storage, and download-time revocation checks.
- A dashboard showing package status, findings, research history, and installation guidance.

Existing lockfiles and dependencies fetched directly from other URLs can bypass a registry change. The demo will verify its resolved URLs; organization-wide enforcement also requires CI and network controls.

## Build and validation plan

The [full specification](docs/build-plan.txt) defines the architecture, trust model, sponsor evidence, build sequence, and ten acceptance criteria.

The end-to-end demo must prove that an approved dependency tree installs, an inert suspicious fixture is quarantined by a real scan, scan failures block approval, and revocation prevents downloading previously cached artifacts. Live ClickHouse queries and Guild runs must support the dashboard and investigation workflow.

Setup commands, deployment instructions, and measured results will be added after the implementation is built and verified.

## Event

Prepared for the [Cyberdefense Hackathon](https://partiful.com/e/Np4oGraOAdod2mjcSfyN). Sponsor-prize eligibility must be checked against the organizers' requirements.
