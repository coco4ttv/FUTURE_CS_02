# Sample 01 — Google / Cloud Account Alert

## Stage 2 — Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml`
- Original source: [Open Sample 01](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml)
- Date header: `03-31-2026` (as written in the source)

## Stage 3 — Email content investigation

### 1. Email overview
- Display name: `Payment-Service-Alert`
- From: `nooreply@csl.yusoilxyhryni.us`
- To: Redacted in the dataset
- Subject: MIME-encoded. Decoded text appears to refer to an urgent cloud-account access suspension due to a storage limit; preserve the raw subject in evidence if the decoded display differs.
- Claimed identity in the main HTML section: Google Support Team
- Reply-To: Not present in supplied headers
- Sender field: Random-looking token; not a normal email address

### 2. Main message and requested action
The first main HTML section displays Google-style branding and a “Support Team” heading. It claims that a threat has been detected on the recipient's device and warns that the SIM card, data, photos and contacts could be compromised unless action is taken. It then presents a subscription-closure warning and urges the recipient to renew within 48 hours to avoid account closure.

The message mixes a cloud-storage/account warning, a device-virus warning and a subscription/membership renewal. This inconsistent story is a significant content indicator.

### 3. Content indicators
- **Brand impersonation:** Google-style logo and “Support Team” branding, while the From domain is `csl.yusoilxyhryni.us`, not an evident Google sender domain.
- **Urgency and fear:** Device-compromise language and a 48-hour renewal deadline.
- **Contradictory pretext:** Storage limit, device threat and subscription renewal are combined in one message.
- **Payment/renewal pressure:** The recipient is directed to renew a membership.
- **Unrelated unsubscribe identity:** The List-Unsubscribe address uses `fanatics.com`, which does not match the claimed Google identity.

### 4. Link inspection (static only)
- Primary visible link text includes a subscription-closure notice and a request to secure the device.
- Defanged host observed: `storage[.]googleapis[.]com`
- Main path observed: `/whilewait/comessuccess[.]html`
- The source contains long query strings and tracking-style values. Do not publish those unique values.
- **Interpretation:** Google Cloud Storage is a genuine hosting service, but the hostname alone does not prove that the specific hosted content is official Google content. The destination is unexpected in the context of a Google account-security alert.
- Other footer/unsubscribe links also point to Google Cloud Storage paths. These should be documented separately from the primary call-to-action.
- URLs were inspected in the source only. No destination was visited.

### 5. Attachment check
No conventional named file attachment was identified in the inspected main message section. The message is multipart/digest and contains HTML. Multipart formatting alone does not prove that a file attachment exists.

### 6. Additional content anomaly
Later portions of the supplied multipart/HTML source contain unrelated message fragments (for example, Enterprise Plus and Event Temple text), random-looking account strings and other content that does not fit the main Google-themed alert. Treat these as anomalous embedded/concatenated content in the supplied sample, not as proof that those organisations sent the alert. Do not reproduce any apparent usernames, passwords or recipient identifiers in the public repository.

### 7. Preliminary classification
**Classification: Phishing**

**Confidence: High**

**Rationale:** The main message uses Google-style branding with a sender domain unrelated to Google, mixes inconsistent security and subscription claims, applies fear and time pressure, and directs the recipient to an unexpected hosted destination. Together these indicators support a phishing classification.

**Potential impact:** A recipient could be persuaded to disclose account or payment details or interact with deceptive content. No actual credential theft, payment loss or malware execution was observed.

**Recommended recipient action:** Do not follow the links or reply. Check any account alert by navigating independently to the genuine service and report the email through the organisation's security process.

## Stage 3 — Evidence status
- `sender_info.png`: supplied screenshot of the message headers; useful after checking/redacting identifiers.
- `Body_info_1.png` and `Body_info_2.png`: these show unrelated Enterprise Plus/Event Temple and other embedded message fragments, not the main Google-themed alert. **Do not use these as the main email-body evidence or upload them publicly**, because they contain unrelated account-like strings and apparent credentials.
- `Link_found_1.png`, `Link_found_2.png` and `Link_found_3.png`: show footer/secondary links and tracking-style values. They do not clearly capture the primary call-to-action near the beginning of the main HTML body. Recapture the primary link and redact its query string before publication.
- Still needed: one screenshot of the main Google-themed body and one screenshot of the primary link around the start of the HTML body.

## Stage 4 — Header analysis (not yet completed)
Google Admin Toolbox and MXToolbox results have not yet been added. Record their actual output in Stage 4; do not assume a missing field is a failed authentication result.

## Limitations
- Recipient information is redacted by the source.
- Full delivery-routing information is not present in the supplied source.
- The email contains unusual unrelated embedded/concatenated content.
- Link destinations were not visited or independently confirmed malicious.
