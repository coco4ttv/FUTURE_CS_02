# Evidence Log

**Project:** Phishing Email Detection & Awareness System  
**Dataset:** [cw-l/message-corpus](https://github.com/cw-l/message-corpus)  
**Handling:** Original email files remain linked to their source and are not republished here. Recipient information and tracking identifiers must be redacted in public screenshots.

## Sample 01 — Google / Cloud Account Alert

**Source:** [Original Sample 01](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml)

| Evidence item | Current status | File / next action |
|---|---|---|
| Source and headers | Screenshot supplied | `sender_info.png`; redact any remaining identifiers before upload |
| Main email body | Not correctly captured yet | Retake; existing Body_info images show unrelated embedded message fragments |
| Primary link | Not correctly captured yet | Retake around the main Google-themed call to action; redact query/tracking values |
| Secondary/footer links | Screenshots supplied | Link_found_1/2/3; do not publish unredacted tracking identifiers |
| Google header analyser | Pending | Capture actual output or error |
| MXToolbox analyser | Pending | Capture actual output or error |

## Sample 02 — SiriusXM Payment-Failure Email

**Source:** [Original Sample 02](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml)

| Evidence item | Current status | File / next action |
|---|---|---|
| Source and headers | Awaiting screenshot | Capture sender, subject, date and available authentication headers |
| Main email body | Awaiting screenshot | Capture payment-failure wording and 24-hour suspension threat |
| Primary link | Awaiting screenshot | Capture the payment-details link and defanged destination; redact query values |
| Google header analyser | Pending | Capture actual output or error |
| MXToolbox analyser | Pending | Capture actual output or error |

## Sample 03 — Diabetes-Treatment Promotion

**Source:** [Original Sample 03](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)

| Evidence item | Current status | File / next action |
|---|---|---|
| Source and headers | Awaiting screenshot | Capture sender, subject, date and available authentication headers |
| Main email body | Awaiting screenshot | Capture the main treatment claim and call to action |
| Primary link | Awaiting screenshot | Capture the primary promotional link and defanged destination; redact query values |
| Google header analyser | Pending | Capture actual output or error |
| MXToolbox analyser | Pending | Capture actual output or error |

## Evidence and privacy rules

- Do not upload the original `.eml` messages.
- Redact recipient addresses, personal details, message-specific tracking tokens and any apparent credentials.
- Keep URLs defanged (for example, `hxxps://example[.]com`).
- Do not visit suspicious links.
- A screenshot is not a tool result unless it shows the actual output from that tool.
- Only mark an evidence item complete after the screenshot/export has been saved and checked.
