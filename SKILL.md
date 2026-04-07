---
name: superpowers-streamer-cli
description: Install, log into, run, and troubleshoot the published SuperPowers desktop streamer npm package. Use when a user wants to set up `superpowers-ai` from npm, sign in or create an account with email or phone, start the streamer, open the printed control link, stop it later, or recover from common npm or runtime issues without needing source-code access.
---

# SuperPowers Streamer CLI

Assume the skill does not have repo or source-code access. Work only from the published npm package and the user's terminal environment.

## Use This Skill For

- Installing the published `superpowers-ai` npm package
- Helping a user log in or create an account with email or phone verification
- Starting the local streamer and using the printed control link
- Stopping the streamer later
- Troubleshooting npm install problems, login problems, or package runtime issues

## Core Rules

- Do not assume any local source tree or machine-specific filesystem layout.
- Do not tell the agent to edit repo files unless the user explicitly says they have the source code and wants development help.
- Prefer the published package workflow first.
- Keep commands customer-facing and simple.

## Standard Flow

1. Check that Node and npm exist.

```bash
node -v
npm -v
```

2. Install the package.

```bash
npm install -g superpowers-ai
```

If the user's npm cache is broken or permission-denied, retry with a clean temp cache:

```bash
mkdir -p /tmp/superpowers-npm-cache
npm_config_cache=/tmp/superpowers-npm-cache npm install -g superpowers-ai
```

3. Log in or create the account.

```bash
superpowers login
```

This should prompt for:
- email or phone
- verification code

4. Tell the user that the package should start the streamer and print a control link automatically after login.

5. If needed, start again manually.

```bash
superpowers start
```

6. To stop the local streamer later:

```bash
superpowers stop
```

7. Helpful account commands:

```bash
superpowers whoami
superpowers logout
```

## Customer Guidance

- Install package: `npm install -g superpowers-ai`
- Start login: `superpowers login`
- Start again manually: `superpowers start`
- Stop streamer: `superpowers stop`
- Open the printed `/general` control link in the browser to control the stream

## macOS Notes

On macOS, the user may need to allow:
- Screen Recording
- Accessibility

If macOS prompts for permissions, tell the user to approve them and then rerun:

```bash
superpowers start
```

## Troubleshooting

Read `references/install.md` for install and usage wording.
Read `references/troubleshooting.md` for common npm, login, and streaming failures.
