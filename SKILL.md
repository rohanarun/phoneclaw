---
name: superpowers-streamer-cli
description: Build, debug, test, and publish the SuperPowers npm CLI streamer. Use when working on the SuperPowers command-line installer/launcher, magic-code login, backend session token flow, headless macOS streamer runtime, room targeting, `/general` control links, or npm publishing as `superpowers-ai`.
---

# SuperPowers Streamer CLI

Follow this workflow:

1. Inspect the CLI package and backend auth/session endpoints first.
2. Keep the npm package name as `superpowers-ai` unless the user explicitly asks otherwise.
3. Keep the CLI commands as `superpowers` and `supers`.
4. Preserve backward compatibility for existing web and iOS auth flows.
5. When changing room selection, keep the CLI launcher, control link, and streamer runtime aligned on the same `room_id`.
6. For macOS headless mode, ensure the runtime keeps retrying the chosen room and logs useful startup/debug output.
7. Before publishing, run local packaging checks and a local install test.
8. Prefer fixing the package, launcher, and runtime together when the bug crosses those boundaries.

## Key Files

Read these first when relevant:

- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers/package.json`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers/src/commands/login.js`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers/src/commands/start.js`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers/src/platform.js`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers/src/download.js`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/live_server.py`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/server/index.html`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/macos/Sources/MacAppState.swift`
- `/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/macos/Sources/MacConfig.swift`

## Local Validation

Run these as appropriate:

```bash
node --check "/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers/src/commands/start.js"
node --check "/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers/src/platform.js"
swift build --package-path "/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/macos"
cd "/Users/rohanarun/Documents/New project/SuperPowersAR 5/SuperPowersAR/SuperPowersAR/npm/SuperPowers" && npm_config_cache=/tmp/superpowers-npm-cache npm pack --dry-run
