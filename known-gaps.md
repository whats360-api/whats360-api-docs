# Known gaps

Current as of November 27, 2026. Resolved items are marked instead of deleted, so the record stays honest. Everything here is based on user-supplied technical notes that have not been independently verified against the live dashboard or API.

- DOCUMENTED FROM NOTES (unverified): request body for `POST /campaigns/recipients`. Written up in [campaigns.md](campaigns.md) and as the `CampaignRecipients` schema in [openapi.yaml](openapi.yaml), from the user-supplied notes. The maximum number of recipients per request is still not documented.
- DOCUMENTED FROM NOTES (unverified): error codes. Listed in [errors.md](errors.md) (400, 401, 403, 404, 463, 500) and referenced from each OpenAPI operation's `default` response. Meanings have not been confirmed against the live service.
- Response `response` object fields per endpoint are not specified. The OpenAPI spec therefore models every response as a generic envelope (`Success` with a free-form `response` object) and says so in each operation.
- Create-campaign body: only `name` and `message_content` appear in the example in the notes. The other fields in [campaigns.md](campaigns.md) are unverified. Scheduling and media fields beyond that list are not documented.
- The exact unit of `batch_pause_min` is not documented (the notes say the dashboard labels it seconds while the field name says minutes).
- Sandbox mode: the notes mention `&sandbox=true` to test the API without sending real messages. Not verified.
- Rate limits and monthly quotas per plan: not documented in the notes. The public pricing page (https://whats360.live/#pricing) lists plans only.
- The page https://whats360.live/developers is the dashboard sign-in, not public documentation. This repository is not an official reference.
- No live production calls were made to produce this documentation.
