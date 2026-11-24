# Quick start

1. Sign in to the Whats360 dashboard and open the Developers (API) page for your token and device ID.
2. Connect a test device with `instances/connect` or from the dashboard. Check it with `instances/status`.
3. Send one text to your own number with `send-text`.
4. If you get `463`, message that number from your phone once, then retry.
5. After that works, create a small campaign and test it on numbers that agreed to receive messages before any large send.

Use environment variables for secrets:
```bash
export WHATS360_TOKEN=...
export WHATS360_INSTANCE_ID=...
curl "https://whats360.live/api/v1/instances/status?token=$WHATS360_TOKEN&instance_id=$WHATS360_INSTANCE_ID"
```
