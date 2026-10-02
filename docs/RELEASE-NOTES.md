# DoCom — Release Notes (public summary)

The publisher keeps a private release ledger; this page is the public-facing
summary. **No binaries are published in this repository.** UI language:
Simplified Chinese.

## Lineage

| Milestone | What shipped |
|---|---|
| R1–R5 (Jul 2026) | Secure pairing (operator token), connected dashboard, thread send/receive over the local gateway, security patches (session handling, transport), deployment gate, reconnect status. |
| Release candidate 5.6 | Frozen baseline: pin read-only evidence hash, completed history threads read-only, Chinese UI label cleanup, release evidence package. |
| 0.2 enhancement (2026-07-26) | One-command startup (`docom:go`), Tailscale overlay validation, persistent gateway state, pairing diagnostics, current-device session management, Chinese troubleshooting guidance, approval-state sanitization, Android `docom` shell (reload / settings / speech capture / OCR capture / Android back), mobile speech & OCR with explicit paste/send, default-workspace fallback, multitask status clarity, one-command Android launch, desktop status check. |

## Architecture (public-level)

- Phone (Android WebView shell) → desktop gateway → Codex `app-server --stdio`.
- The phone **does not** connect to any public LLM endpoint.
- Device sessions are persisted as SHA-256 hashes; WebSocket uses a one-time
  ticket; workspace access enforced server-side by realpath allowlist.
- Deployment: Tailscale overlay (recommended), USB reverse forwarding, or
  TLS-terminated behind a trusted reverse proxy.

## Acceptance evidence

Pairing / dashboard / thread-send screenshots (in the README) are from the
release-smoke runs on a real device. Every claim in the README is what the app
actually does.

## Current limits

- Runtime state is local JSON storage, not a database.
- Codex `app-server --stdio` is experimental; real transport smoke is re-run
  after Codex CLI upgrades.
- APK is a private debug build, not a signed release package.