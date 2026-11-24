# Campaigns: create, add recipients, start, track

Source: the developer portal pages of the whats360.live dashboard (campaign reference and example block). Not tested against the live API by the author of this repository. All values below are placeholders.

Base URL: `https://whats360.live/api/v1` · every call takes `token` and `instance_id` as query parameters.

## Flow
1. `POST /campaigns/create` with a JSON body
2. `POST /campaigns/recipients` (also needs `campaign_id`) with a JSON body
3. `POST /campaigns/start` (needs `campaign_id`)
4. `GET /campaigns/status` (needs `campaign_id`)

## Create body fields
| Field | Required | Meaning |
|---|---|---|
| name | yes | Campaign name |
| message_content | yes | Message text. Supports variables such as `{{name}}` |
| daily_limit | no | Daily cap. Max 1000, default 500 |
| min_delay_ms | no | Minimum delay between messages in ms. Default 3000 |
| max_delay_ms | no | Maximum delay in ms. Default 7000 |
| batch_size | no | Batch size, 1 to 50. Default 20 |
| batch_pause_min | no | Minimum rest between batches (the dashboard labels it seconds) |
| send_hour_start | no | Start hour 0 to 23. Default 8 |
| send_hour_end | no | End hour 0 to 23. Default 22 |
| variables | no | Global variables as JSON |
| campaign_type | no | `promotional` or `transactional` |

## Recipients body
```json
{ "recipients": [
  {"phone": "201000000001", "name": "Ahmed"},
  {"phone": "201000000002", "name": "Sara", "variables": {"name": "Sara"}}
] }
```

## Example (placeholders)
```bash
curl -X POST "https://whats360.live/api/v1/campaigns/create?token=YOUR_TOKEN&instance_id=DEVICE_ID" \
  -H "Content-Type: application/json" \
  -d '{"name":"Marketing Campaign","message_content":"Hello {{name}}! We have a special offer for you","daily_limit":500,"min_delay_ms":3000,"max_delay_ms":7000,"batch_size":20,"send_hour_start":8,"send_hour_end":22}'

curl -X POST "https://whats360.live/api/v1/campaigns/recipients?token=YOUR_TOKEN&instance_id=DEVICE_ID&campaign_id=CAMPAIGN_ID" \
  -H "Content-Type: application/json" \
  -d '{"recipients":[{"phone":"201000000001","name":"Ahmed"}]}'

curl -X POST "https://whats360.live/api/v1/campaigns/start?token=YOUR_TOKEN&instance_id=DEVICE_ID&campaign_id=CAMPAIGN_ID"
curl "https://whats360.live/api/v1/campaigns/status?token=YOUR_TOKEN&instance_id=DEVICE_ID&campaign_id=CAMPAIGN_ID"
```

Starting a campaign sends real messages. Test with numbers you own. Use recipients who agreed to receive messages. The platform and this documentation do not guarantee delivery or protect against account restrictions.

## Still undocumented
Response fields of each call, error codes, maximum recipients per request, how `batch_pause_min` is measured exactly.

## Sandbox mode
The developer portal says: add `&sandbox=true` to any API request to test the API without sending real messages. Not verified here.
