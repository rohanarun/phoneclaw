---
name: superpowers-streamer-cli
description: Build, debug, test, and publish the SuperPowers npm CLI streamer. Use when working on an npm package that installs the SuperPowers streamer, handles magic-code login or account creation, prints `/general` control links, launches a headless desktop streamer, or needs room-targeting and WebRTC fixes across the CLI, backend, web host, and runtime.
---

# SuperPowers Streamer CLI

Treat this as a cross-surface workflow: the CLI, backend auth/session routes, `/general` host page, and streamer runtime must agree on owner, token, and `room_id`.

## Find The Package

Do not assume a machine-specific path. Find the package root first.

- Search for a `package.json` whose `name` is `superpowers-ai`, or whose `bin` exposes `superpowers`.
- Search for companion files such as `src/commands/login.js`, `src/commands/start.js`, `src/platform.js`, and `README.md`.
- If the repo contains a Mac runtime, also look for `MacAppState.swift`, `MacConfig.swift`, or a `macos/Package.swift`.

## Core Invariants

- Keep the npm install name as `superpowers-ai` unless the user explicitly renames it.
- Keep the CLI command names as `superpowers` and `supers`.
- Keep login backward compatible for existing web and iOS callers when changing backend auth responses.
- Keep the CLI launcher, control link, and streamer runtime aligned on the same owner and `room_id`.
- Prefer explicit room targeting over broad fallback rotation when the CLI is launching a specific session.
- Do not assume the streamer is installed in a fixed filesystem location; reason from the package root and the user's runtime environment.

## Workflow

1. Identify the package root and the surfaces involved.
2. Inspect the login and startup flow:
   - npm CLI login or create-account flow
   - backend magic-code verify and session routes
   - control-link generation for `/general`
   - runtime launch logic for macOS, Windows, and Linux
3. When debugging "no stream" issues, separate them into:
   - auth/session failure
   - runtime launch failure
   - signaling connection failure
   - `Room full`
   - `Room not found`
   - host page not opening or not hosting the requested room
4. If the bug crosses boundaries, fix the CLI, backend, web host, and runtime together rather than patching only one layer.
5. Re-test packaging before publish.

## Portable Checks

Run checks from the package root, not from a hard-coded path.

```bash
npm pack --dry-run
node --check src/commands/login.js
node --check src/commands/start.js
node --check src/platform.js
