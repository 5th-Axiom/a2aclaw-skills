---
name: a2aclaw-doctor
description: Use when the user needs to diagnose A2AClaw Host Agent, OpenClaw adapter, Relay connection, device binding, or OpenClaw Gateway health.
---

# A2AClaw Doctor

Use this skill for diagnosis after A2AClaw has been installed or paired.

## Checks

Run the least invasive checks first:

1. Confirm the CLI is available:

   ```bash
   a2aclaw --version
   ```

2. Inspect local status:

   ```bash
   a2aclaw status
   ```

3. Inspect redacted config and OpenClaw discovery:

   ```bash
   a2aclaw config
   ```

4. Check OpenClaw runtime readiness:

   ```bash
   a2aclaw doctor --runtime openclaw
   ```

   This should perform an active OpenClaw Gateway WebSocket handshake and a read-only Gateway
   health call. It must not print Gateway token/password values.

5. If the Host Agent is installed but disconnected, restart it:

   ```bash
   a2aclaw restart
   ```

6. If the device is paired but not connected to Relay, start:

   ```bash
   a2aclaw daemon
   ```

## Output Rules

- Report the failing component: CLI, config, Relay, OpenClaw adapter, or OpenClaw Gateway.
- Provide the next command or config fix.
- Do not expose tokens, Gateway credentials, Relay secrets, or device secrets.
