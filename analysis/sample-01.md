# Sample 01 — Google / Cloud Account Alert

## 1. Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml`
- Original source: [Sample 01 — original email](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml)
- Date header: `03-31-2026` (as written in the source)

## 2. Email overview
- Display name: `Payment-Service-Alert`
- From: `nooreply@csl.yusoilxyhryni.us`
- Recipient: Redacted in the dataset
- Subject: MIME-encoded. The encoded subject appears to refer to urgent cloud-account access suspension due to a storage limit.
- Claimed identity in the main HTML section: Google Support Team
- Reply-To: Not present in the supplied headers
- Sender field: Random-looking token rather than a conventional email address

## 3. Main message and requested action
The first main HTML section displays Google-style branding and a “Support Team” heading. It claims that a threat has been detected on the recipient's device and warns that the SIM card, data, photos and contacts could be compromised unless action is taken. The same message then presents a subscription-closure warning and urges the recipient to renew within 48 hours to avoid account closure.

The content combines a cloud-storage/account warning, a device-virus warning and a subscription/membership renewal. The unrelated pretexts weaken the credibility of the message and are a significant social-engineering indicator.

## 4. Content indicators
- **Brand impersonation:** Google-style logo and “Support Team” branding appear in the message, while the From domain is `csl.yusoilxyhryni.us`, not an evident Google sender domain.
- **Urgency and fear:** The message warns of device compromise and uses a 48-hour renewal deadline.
- **Contradictory pretext:** Storage limit, device threat and subscription renewal are combined in one message.
- **Payment/renewal pressure:** The recipient is directed to renew a membership.
- **Unrelated unsubscribe identity:** The List-Unsubscribe address uses `fanatics.com`, which does not match the claimed Google identity.

## 5. Link inspection
The main HTML section contains a subscription-closure link and a separate call to action asking the recipient to secure the device. The observed destination host is `storage[.]googleapis[.]com`, with the path `/whilewait/comessuccess[.]html`.

Google Cloud Storage is a genuine hosting service; its hostname alone does not establish that the specific hosted content is an official Google page. The destination is unexpected in the context of a Google account/device-security alert. Long, message-specific query and tracking values are omitted from the published evidence.

The supplied source also contains secondary footer and unsubscribe links. These were not treated as the principal call to action. The link review was performed against the source text; the destinations were not opened.

## 6. Attachment review
No conventional named file attachment was identified in the inspected main message section. The message is multipart/digest and contains HTML content. Multipart formatting alone does not establish the presence of a file attachment.

## 7. Additional MIME content
Later portions of the supplied multipart/HTML source contain unrelated message fragments, including Enterprise Plus and Event Temple text, alongside random-looking account strings and credential-like fields. These fragments do not match the main Google-themed alert and are treated as anomalous concatenated content in the supplied sample. They are not attributed to the organisations named in those fragments and are not reproduced in the published evidence.

## 8. Classification and risk
**Classification: Phishing**  
**Confidence: High**

The message uses Google-style branding with a sender domain unrelated to Google, combines inconsistent security and subscription claims, applies fear and time pressure, and directs the recipient to an unexpected hosted destination. Taken together, these indicators support a phishing classification.

**Potential impact:** A recipient could be persuaded to disclose account or payment details or interact with deceptive content. No actual credential theft, payment loss or malware execution was observed.

**Recommended recipient action:** Do not follow the links or reply. Check any account alert by navigating independently to the genuine service and report the email through the organisation's security process.

## 9. Evidence captured
- [`sender_info.png`](../evidence/sample-01/sender_info.png) — sender and available header information.
- [`main_body_and_link.png`](../evidence/sample-01/main_body_and_link.png) — main Google-style message content and primary device-security link, with message-specific query values obscured.

## 10. Header analysis — MXToolbox

I reviewed the headers using [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx). The result shows:

| Header check | Result | Observed detail |
|---|---|---|
| SPF | **Pass** | Envelope-sender domain: `pispszltq.voaxodovlpu.synrg.co.za` |
| SPF sending IP | — | `95.173.180.123` |
| DKIM | No pass result displayed | The captured Authentication-Results row does not show a DKIM pass |
| DMARC | No result displayed | No DMARC outcome can be concluded from this output |
| Relay delay | 0 seconds displayed | The source corpus does not preserve the Received chain, so this display does not establish a complete delivery timeline |

The SPF pass means the sending IP was permitted by the envelope-sender domain shown. It does not authenticate the visible From address, `nooreply@csl.yusoilxyhryni.us`, as Google. No DKIM pass or DMARC result is displayed in the captured output.

### ARC header interpretation

The header table also contains an ARC set with `d=google.com` in the ARC-Seal and ARC-Message-Signature, alongside an ARC-Authentication-Results entry recording the SPF pass. This indicates that a Google mail system added an authenticated-received-chain record while handling the message. The Google domain in the ARC signature identifies the signer of that ARC record; it does **not** mean Google authored the original email or that the visible From address belongs to Google.

The SPF result preserved in the ARC record still relates to the envelope-sender domain `pispszltq.voaxodovlpu.synrg.co.za` and sending IP `95.173.180.123`.

## 11. Limitations
The recipient is redacted, complete delivery-routing details are unavailable, and the supplied message contains unrelated concatenated MIME content. The destination was not opened or independently confirmed malicious through a live reputation check. Missing authentication fields are recorded as unavailable rather than failed.
