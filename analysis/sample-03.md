# Sample 03 — Diabetes-Treatment Promotion

## 1. Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml`
- Original source: [Sample 03 — original email](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)
- Date: Mon, 04 May 2026 21:25:05 +0000

## 2. Email overview
- Display name: `Reverse Type 2 Diabetes`
- From: `nooreplypad.32.195982@hotiaczu.courui.aventrox.my.id`
- Recipient: Redacted in the dataset
- Subject: `See how celebrities are reversing their type 2 diabetes`
- Claimed identity: A sender promoting a diabetes-related product or treatment; no recognised healthcare organisation is established in the supplied message.
- Reply-To: Not present in the supplied headers
- Sender: `coelrdvyqrvpscttzskld@hotiaczu.courui.aventrox.my.id`

## 3. Main message and requested action
The email promotes a “natural” home remedy. It claims that people are reversing Type 2 diabetes and that A1C can be lowered in three hours. It refers to fear of complications, including nerve damage, blindness and amputations, and invites the recipient to click a link to learn about the advertised protocol.

These are claims made by the email, not medical facts validated by this investigation.

## 4. Content indicators
- **Sensational health claims:** The subject refers to celebrities reversing Type 2 diabetes; the body claims an at-home remedy can lower A1C in three hours.
- **Fear-based wording:** It references serious complications to increase emotional pressure.
- **Unclear sender identity:** The From domain is `hotiaczu.courui.aventrox.my.id` and does not identify a recognised healthcare provider in the supplied message.
- **Promotional/tracking links:** The body contains repeated links and tracking references.
- **Unrelated unsubscribe identity:** The List-Unsubscribe header points to `consigntix.com`.

## 5. Link inspection
The primary promotional link uses the host `storage[.]googleapis[.]com` and path `/lithesome/reachflow[.]html`. The message also includes an image host at `i[.]imgur[.]com` and tracking references using `tinyurl[.]com`.

These destinations are promotional/tracking references. Their presence alone does not establish credential theft or malware delivery. The main destination is not presented as an official healthcare-provider domain. The link review was performed against the source text; the destinations were not opened.

## 6. Attachment review
No conventional named file attachment was identified in the inspected main message section. The message contains HTML and remote image references.

## 7. Classification and risk
**Classification: Suspicious**  
**Confidence: Medium**

The message is unsolicited promotional content with sensational health claims, fear-based wording, an unfamiliar sender domain and multiple tracking destinations. However, the supplied message does not by itself establish credential harvesting, payment diversion or malware delivery. “Suspicious” is therefore more defensible than asserting confirmed phishing on the current evidence.

**Potential impact:** Recipients could be misled into engaging with an untrustworthy health promotion, disclosing information through a landing page or making decisions based on unsupported claims. This investigation does not assess the medical validity of the claims.

**Recommended recipient action:** Do not follow the links or provide personal or health information. Verify health information with qualified healthcare professionals and report unsolicited deceptive promotions through the appropriate channel.

## 8. Evidence captured
Sample-specific screenshots have not yet been added to the repository. The source details, content indicators, primary link host and preliminary classification are documented in this analysis.

## 9. Header observations
The supplied Authentication-Results record SPF pass for envelope domain `courui.aventrox.my.id`, with sending IP `178.214.223.204`. DKIM pass is recorded for `hotiaczu.courui.aventrox.my.id`. No DMARC result is shown. Reply-To, Return-Path and Received routing details are not present in the supplied source. The source also includes `X-Originating-IP: 178.214.223.204`.

### MXToolbox — Email Header Analyzer
The MXToolbox result was reviewed. Its Authentication-Results row shows:
- SPF: `pass`
- SPF envelope-sender domain: `courui.aventrox.my.id`
- SPF sending IP: `178.214.223.204`
- DKIM: `pass`
- DKIM signing domain: `hotiaczu.courui.aventrox.my.id`
- DMARC: No result displayed

Both SPF and DKIM pass for the sending domains shown. These results do not validate the medical claims or establish that the sender is a recognised healthcare provider.

## 10. Limitations
The recipient is redacted and complete delivery-routing details are unavailable. The destination URLs were not opened or independently confirmed malicious. The investigation does not assess whether the advertised medical claims are scientifically valid. A passing SPF or DKIM result authenticates the relevant sending domain/signature; it does not establish that the content or offer is trustworthy.
