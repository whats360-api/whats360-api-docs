# Whats360 Developer Resource Center

One entry point for integrating with whats360.live: guides, API examples, webhook recipes, error handling and integration scenarios. Every resource links its source repo. Labels used throughout: **documented** (from the platform's developer materials, transcribed into these repos as of Nov 2026; not verified by a live API call), **illustrative** (example code not executed), **tested-locally** (syntax check or unit test with fake fetch). Nothing here has been run against the production API. Product overview and connection model (QR-based, not the official WhatsApp Business API) are also stated in the platform's public https://whats360.live/llms.txt.

Questions about integrating: chat with the team on WhatsApp (https://wa.me/201030741766) - it is the first contact channel - or email info@whats360.live.

## 1. Start here

1. [Quick start](https://github.com/whats360-api/whats360-api-docs/blob/main/quick-start.md): get your token and device ID from the dashboard Developers (API) page, connect a test device, send one text to your own number, then a small campaign to consenting numbers.
2. [API reference](https://github.com/whats360-api/whats360-api-docs/blob/main/api-reference.md) (**documented**): every endpoint and parameter.
3. [OpenAPI draft](https://github.com/whats360-api/whats360-api-docs/blob/main/openapi.yaml): machine-readable spec of the same surface.
4. [Postman collection](https://github.com/whats360-api/whats360-postman-collection): import and fill in your credentials.

## 2. Authentication and request management

- Every WhatsApp API call takes `token` as a query parameter; most also take `instance_id`. Tokens in URLs can appear in logs: call the API from your server, never from client-side code. Keep secrets in environment variables (`.env.example` in the examples repo).
- VCash and Email APIs use `Authorization: Bearer` instead; the Email flow starts with `POST /api/auth/login`. Treat tokens as expiring.
- Media send endpoints need direct, publicly reachable media URLs.

## 3. Sending messages

- Endpoint table: [API reference](https://github.com/whats360-api/whats360-api-docs/blob/main/api-reference.md) (send-text, send-image, send-video, send-audio, send-doc).
- Runnable-shaped examples in cURL, PHP, Node.js, Python: [code-examples.md](https://github.com/whats360-api/whats360-api-docs/blob/main/code-examples.md) (**illustrative**, PHP not run) and [whats360-developer-examples](https://github.com/whats360-api/whats360-developer-examples) (send-message, send-media, send-bulk with dry-run default; **tested-locally** where marked).

## 4. Campaigns (bulk messaging)

- Flow: create -> add recipients -> start -> monitor. Full field table: [campaigns.md](https://github.com/whats360-api/whats360-api-docs/blob/main/campaigns.md) (**documented** from the dashboard campaign reference).
- Consent and safety: campaigns send real messages. Test on numbers you own; send only to people who agreed to receive messages. No delivery or restriction-avoidance guarantee exists.

## 5. Webhooks

- [Webhooks guide](https://github.com/whats360-api/whats360-webhooks/blob/main/webhooks-guide.md) (**documented**): outgoing events include incoming message, outgoing message, send failure and subscription end (see the guide for the documented list), payload fields, incoming webhooks with field mapping, Shopify and WooCommerce setup, n8n, and the dashboard template list.
- Receiver code: [node-webhook-receiver.js](https://github.com/whats360-api/whats360-webhooks) (logs documented fields, returns 200) and Flask/Express/PHP/Laravel receivers in [developer-examples](https://github.com/whats360-api/whats360-developer-examples) (Flask and Express **tested-locally**; PHP and Laravel not executed).

## 6. Integration scenarios (stores, CRM, automation)

- [Integration examples](https://github.com/whats360-api/whats360-integration-examples): WooCommerce order confirmation without code (incoming webhook) and as a plugin snippet, OTP message (Node.js), payment notification (provider-agnostic; verify payment with your own provider first), CRM forward of incoming messages, plus a workflow diagram. Test labels per file; none live-tested.
- Dashboard CRM features (bots, Persona, external data sources, embedding, CRM statuses): [crm/README.md](https://github.com/whats360-api/whats360-integration-examples) - descriptions of dashboard pages, not API endpoints.

## 7. Error handling

- [errors.md](https://github.com/whats360-api/whats360-api-docs/blob/main/errors.md): 400, 401, 403, 404, 463, 500, with the 463 fix (message the number once from the phone, then retry).
- [error-handling example](https://github.com/whats360-api/whats360-developer-examples) maps documented codes to actions (**tested-locally**, 3 unit tests).

## 8. Other APIs

- [VCash](https://github.com/whats360-api/whats360-vcash-api): SMS, USSD, balance through a connected phone. USSD runs on a real SIM and can move money: documentation only, never run from an example.
- [Email send](https://github.com/whats360-api/whats360-email-api): login -> token -> send, with the DNS records the dashboard recommends.

## 9. Test data

Use placeholders only: `YOUR_TOKEN`, `DEVICE_ID`, numbers like `201234567890`, `abc123`. The dashboard mentions a `&sandbox=true` test mode - **unverified**, confirm in your dashboard before relying on it.

## 10. FAQ

- **Is this the official WhatsApp Business API?** No. Whats360 links numbers by QR code. It is not the Meta Cloud API and not a Meta partner.
- **My send returned 463.** The recipient has not opened a chat with you. Message them once from the phone, then retry. See errors.md.
- **What does a success response contain?** `{"success":true,"message":...,"response":{}}`. The fields inside `response` per endpoint are **not documented**; code defensively.
- **How many recipients per request?** Not documented.
- **Is there a sandbox?** The dashboard mentions `&sandbox=true`; unverified.
- **Rate limits and quotas?** Per plan, see https://whats360.live/#pricing.
- **Can I trust the examples to work unchanged?** They use documented endpoints and parameters with placeholders and are labeled per test status. Fill in your credentials and test on your own numbers first.

## 11. How this center is maintained

Sources are the whats360.live dashboard developer pages, transcribed into the github.com/whats360-api repos with capture dates in each repo. When the dashboard changes, the repos are updated and the change is marked with its date. Gaps stay listed in [known-gaps.md](https://github.com/whats360-api/whats360-api-docs/blob/main/known-gaps.md) instead of being filled by imagination. Found an error? Open an issue on the relevant repo.
