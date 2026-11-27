# Errors

Status: user-supplied technical notes, not independently verified against the live dashboard or API. The meanings below come from those notes; confirm each code in your own dashboard docs before building handling around it.

| Code | Meaning (from the notes, unverified) |
|---|---|
| 400 | Bad request, for example a missing parameter |
| 401 | Invalid or expired token |
| 403 | Limit reached (messages or requests) |
| 404 | Device not found |
| 463 | Recipient-related (per user-supplied notes; unverified) |
| 500 | Server error |

## Error 463
The notes describe this as a WhatsApp-side restriction related to the recipient, for example that there is no open chat with your number. This explanation is unverified - it has not been confirmed against the live dashboard or API. No workaround is published here: do not message a number to get around a send error, and only message people who agreed to receive messages from you. If you hit this error, check the dashboard docs or contact support.

Error body: `{"success": false, "error": "error message"}` (shape per user-supplied notes, unverified)
