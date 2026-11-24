# Known gaps

- Request body for `POST /campaigns/recipients` is not specified in the source.
- Response `response` object fields per endpoint are not specified.
- Create-campaign body: only `name` and `message_content` appear in the official example. Other fields (scheduling, media) are not documented here.
- Rate limits and monthly quotas per plan: see https://whats360.live/#pricing.
- The page https://whats360.live/developers is the dashboard sign-in, not public documentation. This repository is the public reference.
- No live production calls were made to produce this documentation.


## Update
The campaign create body and recipients body are now documented in [campaigns.md](campaigns.md) from the dashboard developer portal. Responses and errors remain undocumented.
