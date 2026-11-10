# CJIT ATC Control Center

**Air Traffic Control Simulation Platform** — Powered by CJIT

A multi-display air traffic control simulation environment for practicing controller workflows, aircraft communications, radar operations, and scenario management. Developed by **CJIT Solutions / CJIT Networks**.

> **Project status:** Active development. This repository currently holds project documentation; deployed application source and operational integration have not been verified in this repository.

## Project links

| Component | Intended URL |
| --- | --- |
| Main controller simulator | https://atc.cjitnetworks.com |
| Administration | https://admin.atc.cjitnetworks.com |
| Radar | https://radar.atc.cjitnetworks.com |
| iPad overhead panel | https://ohp.atc.cjitnetworks.com |

URLs are project targets, **not** proof of live availability.

## Product scope

- Controller-oriented simulation, including ground, tower and approach workflows.
- Radar display with aircraft tracks, callsigns, squawk codes and traffic management concepts.
- Push-to-talk (PTT) pilot/controller radio interactions and AI-generated replies.
- Voice delivery architecture: synthesized speech first, with prerecorded voice fallback where appropriate; verify audio playback and error handling before declaring production readiness.
- Career, freeplay and sandbox modes with changing missions, incidents and alerts.
- Multi-monitor workflow: integrated main screen with optional detachable panels.
- Controller badge/PIN and pilot callsign/PIN identity concepts.
- Admin configuration, gateway health indicators and session status.
- Tablet-friendly overhead panel concept.

These are **product requirements and development targets**, not a claim that every feature has been implemented or tested.

## Proposed infrastructure

- Cloudflare Workers for API and application endpoints.
- Cloudflare Workers AI for AI dialogue and voice capabilities where supported.
- Cloudflare D1 for persistent simulation state and configuration when required.
- Cloudflare KV/R2 for suitable cache and asset storage.
- Dedicated gateway layer for simulation communications.

Actual resource bindings, model IDs, deployment commands and usage costs must be validated against source code and the Cloudflare account. Free-tier operation is a goal, not a guarantee.

## Engineering priorities

1. Confirm the deployed codebase and import it into this repository.
2. Validate end-to-end microphone/PTT capture, AI response, TTS playback and fallback audio.
3. Verify radar updates, controller actions and simulated aircraft state remain synchronized.
4. Test pop-out panels, mobile/tablet layouts, session persistence and authentication.
5. Add CI, reproducible builds, Cloudflare deployment configuration and automated smoke tests.

## Operational boundaries

This is a **simulation**. It is not a certified ATC system and must not be used to control real aircraft. Live aircraft data, if integrated, is for display/educational purposes only and must not be represented as authoritative separation guidance.

## Development

No build or deploy commands are published yet because this repository does not currently contain a verified application source tree. Add the application code, configuration template (without secrets), dependency lockfile and test instructions before enabling automated deployments.

**Branding:** Powered by CJIT  
**Principle:** Plan. Test. Deliver. Support.
