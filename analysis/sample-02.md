# Sample 02 — SiriusXM Payment-Failure Email

## 1. Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml`
- Original source: [Sample 02 — original email](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml)
- Date: Thu, 01 Oct 2026 05:10:28 +0000

## 2. Email overview
- Decoded display name: `Payment_Declined` (the encoded header contains replacement characters)
- From: `ctlelqj.32.195982@btjgbfyk.aroke.hugunenav.biz`
- To: Redacted by the dataset
- Decoded subject: `Your SiriusXM Account will Be Removed Today Please Renew Now!` (the encoded header contains replacement characters)
- Claimed organisation: SiriusXM
- Reply-To: Not present in the supplied headers
- Sender: `wfxezkcnaxytrerlhvdbi@btjgbfyk.aroke.hugunenav.biz`

## 3. Main message and requested action
The message states that the recipient's monthly payment has failed and that the subscription has consequently been cancelled. It invites the recipient to renew the subscription using the link in the email.

A separate section presents account-style information, including a customer ID, email address, status and expiry date. The displayed recipient email is redacted in the supplied source. The account details are part of the email's own claims and have not been independently verified.

The message also contains a prominent payment update instruction and warns that services will be completely suspended within 24 hours if the recipient does not act.

## 4. Content indicators
- **Brand impersonation:** The message presents SiriusXM / SXM branding, while the sender address uses `btjgbfyk.aroke.hugunenav.biz`, not an evident SiriusXM domain.
- **Urgency:** The subject says the account will be removed “Today”.
- **Threat of service loss:** The body threatens complete suspension within 24 hours.
- **Financial pretext:** The message claims a monthly payment failed and asks the recipient to renew or update payment details.
- **Unusual sender domain:** The sender uses a random-looking subdomain under `hugunenav.biz`.
- **Unrelated unsubscribe identity:** The List-Unsubscribe header points to `bicobuluj.biz`, which does not match the claimed subscription provider.
- **Encoded header artefacts:** The MIME-encoded From display name and subject contain replacement characters when decoded. This is a formatting/data-quality anomaly; the classification is based on the combined sender, content and link indicators rather than encoding artefacts alone.

## 5. Link inspection
The primary call to action is “UPDATE MY PAYMENT DETAILS”. Its destination uses the host `storage[.]googleapis[.]com` and path `/worklinks/evrtinggood[.]html`. The supplied URL also contains message-specific tracking and query values, which are not reproduced in this analysis.

The email uses a Google Cloud Storage hostname for a payment action that claims to belong to SiriusXM. Google Cloud Storage is a genuine hosting service, but the hostname does not establish that the specific hosted page is an official SiriusXM billing page. The destination is inconsistent with the claimed billing context.

The link was inspected in the source text and recorded in defanged form. It was not opened.

## 6. Attachment review
No conventional named file attachment was identified in the supplied message. The source is multipart/digest and contains HTML parts. The multipart format itself does not establish that a separate file attachment is present.

## 7. MXToolbox header analysis

The message headers were analysed using [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx).

| Header check | Result | Observed detail |
|---|---|---|
| SPF | **Pass** | Envelope domain: `aroke.hugunenav.biz` |
| SPF sending IP | — | `129.121.93.85` |
| DKIM | **Pass** | Signing domain: `btjgbfyk.aroke.hugunenav.biz` |
| DMARC | Not displayed | No DMARC outcome is available in the captured result |
| Return-Path | Not present in supplied corpus | The corpus removes routing headers |
| Received route | Not present in supplied corpus | MXToolbox does not show a hop-by-hop delivery route |
| Received delay shown by MXToolbox | 0 seconds | This is the analyser's displayed value; without the Received chain it should not be interpreted as proof of instantaneous delivery |

Both SPF and DKIM pass for the sending infrastructure shown. These results authenticate the relevant sending domain/signature; they do not establish that the email was sent by SiriusXM. The visible From domain is `btjgbfyk.aroke.hugunenav.biz`, while the SPF envelope domain is `aroke.hugunenav.biz`. No DMARC result is shown, so a DMARC outcome cannot be inferred from the screenshot.

The source also contains an ARC set signed with `d=google.com`. This identifies the domain shown in the ARC signature; it does not mean Google authored the original message or endorses the sender.

## 8. Classification and risk
**Classification: Phishing**  
**Confidence: High**

The message impersonates a subscription provider, uses a failed-payment pretext, threatens service suspension within 24 hours and asks the recipient to update payment details through an unexpected hosted destination. The sender domain does not match the claimed brand. These combined indicators support a phishing classification.

**Potential impact:** A recipient could disclose payment-card or account information. No payment loss or credential compromise was observed during this analysis.

**Recommended recipient action:** Do not use the payment link or reply to the message. Check subscription status by navigating independently to the genuine SiriusXM website and report the email through the organisation's security process.

## 9. Evidence captured

The Sample 02 evidence folder contains the following investigation captures:

| Evidence file | What it records |
|---|---|
| `from and to.png` | Original From and To header fields |
| `Decoding subject line.png` | CyberChef decoding of the MIME-encoded subject |
| `Decoding of the from email_03.png` | Base64 decoding of the MIME-encoded From field |
| `Body.png` | Message text referring to the failed monthly payment and cancelled subscription |
| `information on reciepiants account.png` | Account-style details displayed in the email, with recipient information redacted |
| `urgency message and link.png` | 24-hour suspension warning and payment-update call to action |
| `Link.png` | Defanged primary link destination |
| `MX Toolbox output.png` | Parsed message headers and SPF/DKIM authentication results |
| `MX Toolbox output2.png` | MXToolbox header summary and relay information |
| `Decoding of the from email.png` | CyberChef inspection of the encoded From header |
| `Decoding of the from email_02.png` | Search result used during the sender-string investigation; not treated as an independent technical verdict |
| `assesment of link.png` | Supplementary automated interpretation of the link; not treated as a URL reputation scan or independent confirmation |

## 10. Limitations
The dataset redacts the recipient and removes routing headers such as `Received` and `Return-Path`, preventing a complete hop-by-hop delivery analysis. The MXToolbox output shows SPF and DKIM passing but does not display a DMARC result. The hosted destination was not opened or independently confirmed malicious through a live reputation service. The account-style details in the email were not independently verified.
