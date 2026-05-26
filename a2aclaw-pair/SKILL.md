---
name: a2aclaw-pair
description: Use when the user wants to install or upgrade A2AClaw, verify OpenClaw readiness, and bind the current OpenClaw host to the A2A App with an App-generated one-time token.
---

# A2AClaw Pair

Use this skill for first-time A2AClaw setup and OpenClaw pairing.

## Required Workflow

Follow this order exactly. Do not skip checks.

1. Install or upgrade the CLI:

   ```bash
   npm install -g @a2aclaw/cli@latest
   ```

2. Install or update the local Host Agent, OpenClaw adapter, and platform background service:

   ```bash
   a2aclaw install
   ```

   Service managers are platform-specific:

   - macOS: launchd
   - Linux: pm2
   - Windows: node-windows

3. Verify OpenClaw readiness before pairing:

   - OpenClaw config can be found.
   - Gateway URL is discovered or derived from `gateway.port`.
   - Gateway auth is usable without printing token/password.
   - Local OpenClaw Gateway is reachable through the WebSocket protocol.

4. Only after readiness checks pass, pair with the token supplied by the A2A App:

   ```bash
   a2aclaw pair --runtime openclaw --token <token>
   ```

5. After pairing succeeds, confirm that the background Relay service is running:

   ```bash
   a2aclaw status
   ```

   `a2aclaw pair` starts or restarts the platform service automatically. If the status/check output
   shows that Relay is not running, run `a2aclaw restart` first. For foreground debugging only, run
   `a2aclaw daemon`.

## Output Rules

- If pairing succeeds, say that A2AClaw binding is complete.
- If daemon starts successfully, say that A2AClaw Relay is connected.
- If pairing fails, name the failed step and provide the next command or config fix.
- If Gateway readiness fails, report only the failing check and the next command/config fix.

## Do Not

- Do not use `npx` for background-service installation.
- Do not skip OpenClaw Gateway readiness checks.
- Do not print local OpenClaw Gateway credentials or A2AClaw device secrets.
- Do not invent unsupported `a2aclaw` flags.
