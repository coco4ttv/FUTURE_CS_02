# Sample 02 — SiriusXM Payment-Failure Email

## Stage 2 — Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml`
- Original source: [Open Sample 02](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml)
- Date: Thu, 01 Oct 2026 05:10:28 +0000

## Stage 3 — Email content investigation

### 1. Email overview
- Display name (decoded): `Payment_Declined`
- From (decoded): `ctlelqj.32.195982@btjgbfyk.aroke.hugunenav.biz`
- To: Redacted in the dataset
- Subject (decoded): `Your SiriusXM Account will Be Removed Today Please Renew Now!`
- Claimed organisation: SiriusXM
- Reply-To: Not present in supplied headers
- Sender: `wfxezkcnaxytrerlhvdbi@btjgbfyk.aroke.hugunenav.biz`

### 2. Main message and requested action
The email claims that a payment attempt failed while renewing a SiriusXM subscription. It says the subscription has expired and asks the recipient to update payment details. It threatens that services will be completely suspended within 24 hours if the recipient does not act.

The message displays “SXM” branding and a prominent “UPDATE MY PAYMENT DETAILS” call to action.

### 3. Content indicators
- **Brand impersonation:** The message claims to represent SiriusXM, but the From domain is `btjgbfyk.aroke.hugunenav.biz`, not an evident SiriusXM domain.
- **Urgency:** The subject says the account will be removed “Today”.
- **Fear/pressure:** The message threatens service suspension within 24 hours.
- **Financial lure:** The recipient is asked to update payment details after an alleged payment failure.
- **Unusual sender domain:** The From and Sender addresses use a random-looking domain/subdomain.
- **Unrelated unsubscribe identity:** The List-Unsubscribe header points to `bicobuluj.biz`, unrelated to the claimed subscription provider.

### 4. Link inspection (static only)
- Main call-to-action text: `UPDATE MY PAYMENT DETAILS`
- Defanged host observed: `storage[.]googleapis[.]com`
- Main path observed: `/worklinks/evrtinggood[.]html`
- The links include long tracking fragments and identifiers. Do not publish the full query strings or unique values.
- List-Unsubscribe host: `bicobuluj[.]biz`
- **Interpretation:** The Google Cloud Storage hostname does not establish that the hosted content is an official SiriusXM billing page. Its use in a message claiming to update a SiriusXM payment is unexpected.
- URLs were inspected in the source only. No destination was visited.

### 5. Attachment check
No conventional named file attachment was identified in the inspected message. The source is multipart/digest and contains HTML parts.

### 6. Preliminary classification
**Classification: Phishing**

**Confidence: High**

**Rationale:** The sender domain does not match the claimed brand, the email uses a payment-failure pretext, threatens suspension within 24 hours and directs the recipient to an unexpected hosted destination to update payment details.

**Potential impact:** A recipient could disclose payment-card or account information. No payment loss or credential compromise was observed.

**Recommended recipient action:** Do not use the email's payment link. Check subscription status by navigating independently to the genuine SiriusXM website and report the email.

## Stage 3 — Evidence status
- No Sample 02 screenshots have been supplied yet.
- Capture the source/headers, main email body and primary payment link.
- Redact recipient information and remove/obscure long tracking identifiers before publishing screenshots.

## Stage 4 — Header analysis (not yet completed)
Google Admin Toolbox and MXToolbox results have not yet been added. The source includes SPF and DKIM results; record the tool's actual output separately in Stage 4.

## Limitations
- Recipient information is redacted by the source.
- Full delivery-routing information is not present in the supplied source.
- The destination URL was not visited or independently confirmed malicious.
