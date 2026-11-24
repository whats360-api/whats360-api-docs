# Errors

| Code | Meaning |
|---|---|
| 400 | Bad request, for example a missing parameter |
| 401 | Invalid or expired token |
| 403 | Limit reached (messages or requests) |
| 404 | Device not found |
| 463 | Number not open for chat (a WhatsApp restriction) |
| 500 | Server error |

## Error 463
This comes from WhatsApp itself. The recipient has not opened a chat window with you yet, or encryption is not set up. It usually appears with new numbers or numbers you never messaged. Fix per the official reference: send one message from the phone directly to that number, then retry from the CRM or API.

Error body: `{"success": false, "error": "error message"}`
