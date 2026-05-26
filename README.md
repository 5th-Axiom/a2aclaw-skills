# A2AClaw Skills

A2AClaw skills for OpenClaw to install, pair, and diagnose the A2AClaw Host Agent.

Included skills:

- `a2aclaw-pair`: install or upgrade `@a2aclaw/cli`, validate OpenClaw readiness, and pair this host with A2AClaw using an App-generated token.
- `a2aclaw-doctor`: inspect Host Agent, adapter, Relay, and OpenClaw Gateway health.

After pairing, `a2aclaw daemon` keeps the host connected to the backend Relay over WebSocket and
forwards App messages into OpenClaw through the real Gateway WebSocket `chat.send` flow.
