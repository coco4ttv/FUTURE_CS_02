# Sample 03 — Diabetes-Treatment Promotion

## Stage 2 — Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml`
- Original source: [Open Sample 03](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)
- Date: Mon, 04 May 2026 21:25:05 +0000

## Stage 3 — Email content investigation

### 1. Email overview
- Display name: `Reverse Type 2 Diabetes`
- From: `nooreplypad.32.195982@hotiaczu.courui.aventrox.my.id`
- To: Redacted in the dataset
- Subject: `See how celebrities are reversing their type 2 diabetes`
- Claimed identity: The sender promotes a diabetes-related product or treatment; no recognised healthcare organisation is established in the supplied message.
- Reply-To: Not present in supplied headers
- Sender: `coelrdvyqrvpscttzskld@hotiaczu.courui.aventrox.my.id`

### 2. Main message and requested action
The email promotes a “natural” home remedy. It claims that people are reversing Type 2 diabetes and that A1C can be lowered in three hours. It references fear of complications, including nerve damage, blindness and amputations, and invites the recipient to click a link to learn about the advertised protocol.

These are claims made by the email, not medical facts validated by this investigation.

### 3. Content indicators
- **Sensational health claims:** The subject refers to celebrities reversing Type 2 diabetes; the body claims an at-home remedy can lower A1C in three hours.
- **Fear-based wording:** It references serious complications to increase emotional pressure.
- **Unclear sender identity:** The From domain is `hotiaczu.courui.aventrox.my.id` and does not identify a recognised healthcare provider in the supplied message.
- **Promotional/tracking links:** The body contains repeated links and tracking references.
- **Unrelated unsubscribe identity:** The List-Unsubscribe header points to `consigntix.com`.

### 4. Link inspection (static only)
- Main defanged host observed: `storage[.]googleapis[.]com`
- Main path observed: `/lithesome/reachflow[.]html`
- Image host observed: `i[.]imgur[.]com`
- Tracking host observed: `tinyurl[.]com` with a tracking path.
- **Interpretation:** These are promotional/tracking destinations. Their presence alone does not establish credential theft or malware delivery. The main destination is not presented as an official healthcare-provider domain.
- URLs were inspected in the source only. No destination was visited.

### 5. Attachment check
No conventional named file attachment was identified in the inspected main message section. The message contains HTML and remote image references.

### 6. Preliminary classification
**Classification: Suspicious**

**Confidence: Medium**

**Rationale:** The message is unsolicited promotional content with sensational health claims, fear-based wording, an unfamiliar sender domain and multiple tracking destinations. However, the supplied message does not by itself establish credential harvesting, payment diversion or malware delivery. “Suspicious” is therefore more defensible than asserting confirmed phishing on the current evidence.

**Potential impact:** Recipients could be misled into engaging with an untrustworthy health promotion, disclosing information through a landing page or making decisions based on unsupported claims. This investigation does not assess the medical validity of the claims.

**Recommended recipient action:** Do not follow the links or provide personal or health information. Verify health information with qualified healthcare professionals and report unsolicited deceptive promotions through the appropriate channel.

## Stage 3 — Evidence status
- No Sample 03 screenshots have been supplied yet.
- Capture the source/headers, main email body and primary promotional link.
- Redact recipient information and remove/obscure long tracking identifiers before publishing screenshots.

## Stage 4 — Header analysis (not yet completed)
Google Admin Toolbox and MXToolbox results have not yet been added. The source includes SPF and DKIM results; record the tool's actual output separately in Stage 4.

## Limitations
- Recipient information is redacted by the source.
- Full delivery-routing information is not present in the supplied source.
- The destination URLs were not visited or independently confirmed malicious.
- The investigation does not assess whether the advertised medical claims are scientifically valid.
