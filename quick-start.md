# Quick start

1. Sign in to the whats360.live dashboard and open the Developers (API) page for your token and device ID.
2. Connect a test device with `instances/connect` or from the dashboard. Check it with `instances/status`.
3. Send one text to your own number with `send-text`.
4. If you get `463`, the notes describe it as recipient-related (unverified). Do not message the number to work around the error; send only to people who agreed to receive messages, and check the dashboard docs or support.
5. After that works, create a small campaign and test it on numbers that agreed to receive messages before any large send.

Use environment variables for secrets:
```bash
export WHATS360_TOKEN=...
export WHATS360_INSTANCE_ID=...
curl "https://whats360.live/api/v1/instances/status?token=$WHATS360_TOKEN&instance_id=$WHATS360_INSTANCE_ID"
```
