# Whats360 Developer Resource Center (preliminary - unverified notes)

Status: preliminary. This page indexes user-supplied technical notes about whats360.live. The notes were compiled from the platform's developer materials, but the original materials have not been re-inspected and nothing on this page has been independently verified against the live dashboard or the production API (the dashboard was unreachable at publication, and no live API call has ever been made). Treat every endpoint, parameter, auth detail, error code and response shape linked from this page as unverified until you confirm it in your own dashboard Developers page. This is not an official or complete API reference.

Labels used throughout: **unverified** (user-supplied technical notes, not independently verified), **illustrative** (example code not executed), **tested-locally** (syntax check or unit test with fake fetch, never against the real API).

Verified from the platform's own public page (https://whats360.live/llms.txt, fetched Nov 25, 2026): the service connects WhatsApp numbers by QR code and is not the official WhatsApp Business API, and it offers a free trial with no card required.

Questions about integrating: chat with the team on WhatsApp (https://wa.me/201030741766) - it is the first contact channel - or email info@whats360.live.

## 1. Start here

1. [Quick start](https://github.com/whats360-api/whats360-api-docs/blob/main/quick-start.md) (**unverified**): the notes describe getting a token and device ID from the dashboard Developers (API) page, connecting a test device, and sending a first message. Confirm each step in your own dashboard before following it.
2. [API reference](https://github.com/whats360-api/whats360-api-docs/blob/main/api-reference.md) (**unverified**): the notes' endpoint and parameter list. Not confirmed complete, correct or current; not an official reference.
3. [OpenAPI draft](https://github.com/whats360-api/whats360-api-docs/blob/main/openapi.yaml) (**unverified**): machine-readable draft of the same unverified notes.
4. [Postman collection](https://github.com/whats360-api/whats360-postman-collection) (**unverified**): import and fill in your credentials; the requests reflect the unverified notes.

## 2. Authentication and request management

- The notes describe WhatsApp API calls taking `token` (and usually `instance_id`) as query parameters, and the VCash and Email APIs using `Authorization: Bearer`, with the Email flow starting at a login call. None of this is verified. Check the auth section of your own dashboard Developers page before writing code against any of it.
- General good practice regardless of provider: tokens in URLs can end up in logs, so call any API from your server, never from client-side code, and keep secrets in environment variables (`.env.example` in the examples repo).
- The notes say media send endpoints take media by URL and that the URLs must be direct, publicly reachable links - unverified; confirm the exact hosting requirements in the dashboard before relying on this.

## 3. Sending messages

- Endpoint list in the notes: [API reference](https://github.com/whats360-api/whats360-api-docs/blob/main/api-reference.md) (**unverified**) - send-text, send-image, send-video, send-audio, send-doc as written there.
- Runnable-shaped examples in cURL, PHP, Node.js, Python: [code-examples.md](https://github.com/whats360-api/whats360-api-docs/blob/main/code-examples.md) (**illustrative**, PHP not run) and [whats360-developer-examples](https://github.com/whats360-api/whats360-developer-examples) (send-message, send-media, send-bulk with dry-run default; **tested-locally** where marked). These are built from the unverified notes - expect to adjust them against your dashboard.

## 4. Campaigns (bulk messaging)

- The notes describe a create -> add recipients -> start -> monitor flow, with a field table in [campaigns.md](https://github.com/whats360-api/whats360-api-docs/blob/main/campaigns.md) (**unverified**).
- Consent and safety: campaigns send real messages. Test on numbers you own; send only to people who agreed to receive messages. No delivery or restriction-avoidance guarantee exists.

## 5. Webhooks

- [Webhooks guide](https://github.com/whats360-api/whats360-webhooks/blob/main/webhooks-guide.md) (**unverified**): the notes describe outgoing event types, payload fields, incoming webhooks with field mapping, Shopify and WooCommerce setup, n8n, and a dashboard template list. The event list differs between versions of the notes and is not verified - confirm the events your account actually receives before building on them.
- Receiver code: [node-webhook-receiver.js](https://github.com/whats360-api/whats360-webhooks) (logs the fields from the unverified notes, returns 200) and Flask/Express/PHP/Laravel receivers in [developer-examples](https://github.com/whats360-api/whats360-developer-examples) (Flask and Express **tested-locally**; PHP and Laravel not executed).

## 6. Integration scenarios (stores, CRM, automation)

- [Integration examples](https://github.com/whats360-api/whats360-integration-examples): WooCommerce order confirmation without code (incoming webhook) and as a plugin snippet, OTP message (Node.js), payment notification (provider-agnostic; verify payment with your own provider first), CRM forward of incoming messages, plus a workflow diagram. Test labels per file; none live-tested; all built on the unverified notes.
- [crm/README.md](https://github.com/whats360-api/whats360-integration-examples) (**unverified**): user-supplied descriptions of dashboard CRM pages (bots, Persona, external data sources, embedding, CRM statuses). These describe dashboard pages; they are not confirmed API endpoints.

## 7. Error handling

- [errors.md](https://github.com/whats360-api/whats360-api-docs/blob/main/errors.md) (**unverified**): the notes list HTTP-style error codes (400, 401, 403, 404, 463, 500) with suggested meanings. The suggested handling in the notes has not been verified and is not repeated here; in particular, no suggested workaround for code 463 is published because it is unverified and could conflict with recipient-consent requirements. If you hit an error, check the dashboard docs or contact support.
- [error-handling example](https://github.com/whats360-api/whats360-developer-examples) (**tested-locally**, 3 unit tests): maps the unverified codes to actions; treat it as a starting skeleton only, not as confirmed behavior.

## 8. Other APIs

- [VCash](https://github.com/whats360-api/whats360-vcash-api) (**unverified**): the notes describe SMS, USSD and balance operations through a connected phone. USSD runs on a real SIM and can move money: documentation only, never run from an example.
- [Email send](https://github.com/whats360-api/whats360-email-api) (**unverified**): the notes describe a login -> token -> send flow, plus DNS records the notes say the dashboard recommends.

## 9. Test data

Use placeholders only: `YOUR_TOKEN`, `DEVICE_ID`, numbers like `201234567890`, `abc123`. The notes mention a `&sandbox=true` test mode - **unverified**, confirm in your dashboard before relying on it.

## 10. FAQ

- **Is this the official WhatsApp Business API?** No. Whats360 links numbers by QR code. It is not the Meta Cloud API and not a Meta partner (per the platform's public llms.txt).
- **My send returned an error (for example 463).** The notes list 463 as a recipient-related error, but the suggested fix in the notes is unverified and is not repeated here. Do not message numbers to work around sending errors; send only to people who agreed to receive messages. Check the dashboard docs or contact support.
- **What does a success response contain?** Not verified. The notes show a JSON envelope with a success flag, a message and a response object, but the envelope itself is unconfirmed and the fields inside `response` per endpoint are not documented. Code defensively and log raw responses while testing.
- **How many recipients per request?** Not documented in the notes.
- **Is there a sandbox?** The notes mention `&sandbox=true`; unverified.
- **Rate limits and quotas?** Not documented in the notes. The public pricing page (https://whats360.live/#pricing) lists plans, but whether API quotas apply per plan is unconfirmed - check your dashboard.
- **Can I trust the examples to work unchanged?** No. They are built from unverified notes with placeholders. Fill in your credentials, confirm each endpoint against your dashboard, and test on your own numbers first.

## 11. How this center is maintained

This page indexes user-supplied technical notes compiled from the platform's developer materials in Nov 2026. The original materials have not been re-inspected and the live dashboard was unreachable when this page was published, so each resource is labeled with its verification status instead of being presented as confirmed documentation. When the dashboard becomes reachable, each note will be checked against it and the labels updated. Gaps stay listed in [known-gaps.md](https://github.com/whats360-api/whats360-api-docs/blob/main/known-gaps.md) instead of being filled by imagination. Found an error? Open an issue on the relevant repo.
