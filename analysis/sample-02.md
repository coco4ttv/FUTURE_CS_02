# Sample 02 — SiriusXM Payment-Failure Email

## 1. Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml`
- Original source: [Sample 02 — original email](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml)
- Date: Thu, 01 Oct 2026 05:10:28 +0000

## 2. Email overview
- Display name (decoded): `Payment_Declined`
- From (decoded): `ctlelqj.32.195982@btjgbfyk.aroke.hugunenav.biz`
- Recipient: Redacted in the dataset
- Subject (decoded): `Your SiriusXM Account will Be Removed Today Please Renew Now!`
- Claimed organisation: SiriusXM
- Reply-To: Not present in the supplied headers
- Sender: `wfxezkcnaxytrerlhvdbi@btjgbfyk.aroke.hugunenav.biz`

## 3. Main message and requested action
The email claims that a payment attempt failed while renewing a SiriusXM subscription. It says the subscription has expired and asks the recipient to update payment details. It threatens that services will be completely suspended within 24 hours if the recipient does not act.

The message displays “SXM” branding and a prominent “UPDATE MY PAYMENT DETAILS” call to action.

## 4. Content indicators
- **Brand impersonation:** The message claims to represent SiriusXM, but the From domain is `btjgbfyk.aroke.hugunenav.biz`, not an evident SiriusXM domain.
- **Urgency:** The subject says the account will be removed “Today”.
- **Fear/pressure:** The message threatens service suspension within 24 hours.
- **Financial lure:** The recipient is asked to update payment details after an alleged payment failure.
- **Unusual sender domain:** The From and Sender addresses use a random-looking domain/subdomain.
- **Unrelated unsubscribe identity:** The List-Unsubscribe header points to `bicobuluj.biz`, unrelated to the claimed subscription provider.

## 5. Link inspection
The main call to action is “UPDATE MY PAYMENT DETAILS”. Its destination uses the host `storage[.]googleapis[.]com` and path `/worklinks/evrtinggood[.]html`, followed by message-specific tracking fragments. The List-Unsubscribe header points to `bicobuluj[.]biz`.

Google Cloud Storage is a genuine hosting service; the hostname alone does not establish that the specific hosted content is official SiriusXM content. The hosted destination is unexpected in the context of a SiriusXM billing request. The link review was performed against the source text; the destinations were not opened.

## 6. Attachment review
No conventional named file attachment was identified in the supplied message. The source is multipart/digest and contains HTML parts.

## 7. Classification and risk
**Classification: Phishing**  
**Confidence: High**

The sender domain does not match the claimed brand, the email uses a payment-failure pretext, threatens suspension within 24 hours and directs the recipient to an unexpected hosted destination to update payment details.

**Potential impact:** A recipient could disclose payment-card or account information. No payment loss or credential compromise was observed.

**Recommended recipient action:** Do not use the email's payment link. Check subscription status by navigating independently to the genuine SiriusXM website and report the email.

## 8. Evidence captured
Sample-specific screenshots have not yet been added to the repository. The source details, content indicators, sender mismatch, primary link host and preliminary classification are documented in this analysis.

## 9. Header observations
The supplied Authentication-Results record SPF pass for envelope domain `aroke.hugunenav.biz`, with sending IP `129.121.93.85`. DKIM pass is recorded for `btjgbfyk.aroke.hugunenav.biz`. The visible From address uses that subdomain, while the SPF envelope domain is its parent domain. No DMARC result is shown. Reply-To, Return-Path and Received routing details are not present in the supplied source. The source also includes `X-Originating-IP: 129.121.93.85`.

### MXToolbox — Email Header Analyzer
The MXToolbox result was reviewed. Its Authentication-Results row shows:
- SPF: `pass`
- SPF envelope-sender domain: `aroke.hugunenav.biz`
- SPF sending IP: `129.121.93.85`
- DKIM: `pass`
- DKIM signing domain: `btjgbfyk.aroke.hugunenav.biz`
- DMARC: No result displayed

Both SPF and DKIM pass for the sending infrastructure shown. These results do not establish that the message was sent by SiriusXM.

## 10. Limitations
The recipient is redacted and complete delivery-routing details are unavailable. The destination was not opened or independently confirmed malicious through a live reputation check. A passing SPF or DKIM result authenticates the relevant sending domain/signature; it does not establish that the message genuinely comes from SiriusXM.
