# CJIT ATC — v3.1.9 Cloudflare production snapshot

Snapshot date: 2026-11-10 UTC. These are preserved **deployed Worker source snapshots**; they are not the original complete application build repository.

## Files

- `deploy/frontend-worker.js` — generated frontend Worker that serves the ATC v3.1.9 controller UI and its packaged assets. Includes the production hotfix that **decompresses stored gzip assets before sending HTML, JavaScript and CSS**, avoiding binary page corruption.
- `deploy/radio-ai-worker.js` — active ATC backend Worker, including AI radio and voice endpoints.

## Verified deployment

- Production controller: `https://atc.cjitnetworks.com`, verified HTML title **CJIT ATC Command Center v3.1.9**, and controller login interface.
- Administration: `https://admin.atc.cjitnetworks.com`, served through the shared 911/ATC administrative Worker (tracked separately in `Developer-CJ/CJIT-911-SIM`), verified as **ATC Simulator Administration v3.1.9**.
- AI gateway: `https://server1.atc.cjitnetworks.com`; route maps to `cjit-atc-sim-radio-ai`.
- Radio gateway: `https://atc.radio.cjitnetworks.com`; served by a separate realtime gateway.
- Radar: `https://radar.atc.cjitnetworks.com` (external hosting).
- Overhead panel: `https://ohp.atc.cjitnetworks.com` (external hosting).

## Required backend Cloudflare bindings

- `AI`: Workers AI
- `CFG`: shared D1 configuration database
- `DB`: ATC simulator D1 database
- `AUDIO`: R2 asset bucket

The frontend Worker is a generated build, not a safe editable original. Rebuilding and deploying it requires the original build pipeline and an audited asset manifest. Preserve existing Cloudflare domains, resource bindings, and routes. Credentials and PINs that exist in client-served resources must **not be treated as server-side secrets**; use server-validated authentication for production access. This public repository must not contain private tokens, passwords, customer data, or internal network bootstrap instructions.

## Outstanding verification

- End-to-end Workers AI voice generation and browser audio playback with all fallback levels
- Actual microphone PTT transcription and controller/pilot reply sequences
- Session persistence and synchronized pop-out consoles
- Aircraft/radar data integrity and performance
- Authenticated operator/admin role permission tests

Do not use this simulator for real-world air traffic control or emergency dispatch.
