# Whats360 API Reference

Base URL: `https://whats360.live/api/v1`

## Authentication
Every request needs a `token` query parameter. An invalid or expired token returns `401`. Most requests also need `instance_id`, the ID of the connected WhatsApp number (device) that performs the action.

```
GET https://whats360.live/api/v1/send-text?token=YOUR_TOKEN&instance_id=DEVICE_ID&jid=201234567890@s.whatsapp.net&msg=Hello
```

`jid` is the WhatsApp chat ID. For a normal number: `<international number>@s.whatsapp.net`.

Keep the token secret. Tokens in URLs can appear in logs, so call the API from your server only.

## Send messages
All send endpoints use GET. A trailing `?` marks an optional parameter.

| Function | Method and path | Parameters |
|---|---|---|
| Send text | GET /send-text | token, instance_id, jid, msg |
| Send image | GET /send-image | token, instance_id, jid, imageurl, caption? |
| Send video | GET /send-video | token, instance_id, jid, videourl, caption? |
| Send audio | GET /send-audio | token, instance_id, jid, audiourl |
| Send document | GET /send-doc | token, instance_id, jid, docurl, caption? |

Media URLs must be direct, publicly reachable links. For error `463`, see [errors](errors.md).

## Manage devices
A device is a WhatsApp number linked to your account.

| Function | Method and path | Parameters |
|---|---|---|
| List devices | GET /instances | token |
| Create device | GET /instances/create | token, id, name? |
| Start / connect | GET /instances/connect | token, instance_id |
| Stop | GET /instances/disconnect | token, instance_id |
| Status | GET /instances/status | token, instance_id |
| QR code (JSON) | GET /instances/qr | token, instance_id |
| Interactive QR page (open in browser) | GET /instances/qr-page | token, instance_id |
| Delete device | GET /instances/delete | token, instance_id |

`delete` and `disconnect` really change device state. Try them only on a test device.

## Campaigns (bulk messaging)
Create a campaign with a JSON body, add recipients, then start it. You can pause, resume, stop and read stats.

| Function | Method and path | Parameters |
|---|---|---|
| List campaigns | GET /campaigns | token, instance_id |
| Create | POST /campaigns/create | token, instance_id + JSON body |
| Add recipients | POST /campaigns/recipients | token, instance_id, campaign_id + JSON body |
| Start | POST /campaigns/start | token, instance_id, campaign_id |
| Pause | POST /campaigns/pause | token, instance_id, campaign_id |
| Resume | POST /campaigns/resume | token, instance_id, campaign_id |
| Stop / cancel | POST /campaigns/stop | token, instance_id, campaign_id |
| Status and stats | GET /campaigns/status | token, instance_id, campaign_id |
| Delete | POST /campaigns/delete | token, instance_id, campaign_id |

The official create example sends a name and message text and accepts a variable such as `{{name}}`:
```json
{"name":"test","message_content":"Hello {{name}}"}
```
The recipients body is not specified in the source. Check the dashboard Developers page before using it.

## Response format
Success:
```json
{"success": true, "message": "...", "response": { }}
```
Error:
```json
{"success": false, "error": "error message"}
```

## curl examples
```bash
# Send text
curl "https://whats360.live/api/v1/send-text?token=YOUR_TOKEN&instance_id=DEVICE_ID&jid=201234567890@s.whatsapp.net&msg=Hello"
# List devices
curl "https://whats360.live/api/v1/instances?token=YOUR_TOKEN"
# Create device
curl "https://whats360.live/api/v1/instances/create?token=YOUR_TOKEN&id=new-device&name=New+Device"
# Create campaign
curl -X POST "https://whats360.live/api/v1/campaigns/create?token=YOUR_TOKEN&instance_id=DEVICE_ID" \
  -H "Content-Type: application/json" -d '{"name":"test","message_content":"Hello {{name}}"}'
# Start campaign
curl -X POST "https://whats360.live/api/v1/campaigns/start?token=YOUR_TOKEN&instance_id=DEVICE_ID&campaign_id=CAMPAIGN_ID"
```

Monthly API limits depend on your plan: https://whats360.live/#pricing
