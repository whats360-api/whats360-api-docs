# Known gaps

Current as of November 25, 2026. Resolved items are marked instead of deleted, so the record stays honest.

- RESOLVED: request body for `POST /campaigns/recipients`. Now documented in [campaigns.md](campaigns.md) and as the `CampaignRecipients` schema in [openapi.yaml](openapi.yaml), from the dashboard developer portal. The maximum number of recipients per request is still not documented.
- RESOLVED: error codes. Documented in [errors.md](errors.md) (400, 401, 403, 404, 463, 500) and referenced from each OpenAPI operation's `default` response.
- Response `response` object fields per endpoint are not specified. The OpenAPI spec therefore models every response as a generic envelope (`Success` with a free-form `response` object) and says so in each operation.
- Create-campaign body: only `name` and `message_content` appear in the official example. The other fields in [campaigns.md](campaigns.md) come from the dashboard developer portal, not from a public example. Scheduling and media fields beyond that list are not documented.
- The exact unit of `batch_pause_min` is not documented (the dashboard labels it seconds while the field name says minutes).
- Sandbox mode: the developer portal mentions `&sandbox=true` to test the API without sending real messages. Not verified here.
- Rate limits and monthly quotas per plan: see https://whats360.live/#pricing.
- The page https://whats360.live/developers is the dashboard sign-in, not public documentation. This repository is the public reference.
- No live production calls were made to produce this documentation.
