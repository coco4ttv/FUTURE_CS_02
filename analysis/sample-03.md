# Sample 03 - Diabetes-Treatment Promotion

## 1. Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml`
- Original source: [Sample 03 - original email](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)
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
The HTML body opens with a claim that thousands of Americans are reversing Type 2 diabetes at home using a natural remedy, with the hint that A1C can be lowered in just three hours. It refers to blood sugar remaining out of control despite insulin use, then lists feared complications including nerve damage, blindness and amputations. It asserts that “early research in 2026” has discovered a safe at-home protocol that reverses Type 2 diabetes and restores normal blood sugar, including in severe cases.

The message ends this section with a call to learn the protocol and start enjoying normal blood sugar levels in three hours. These are claims made by the sender; the email supplies no research citation or clinical evidence in the captured content, and this investigation does not validate the medical claims.

## 4. Content indicators
- **Sensational health claims:** The subject refers to celebrities reversing Type 2 diabetes; the body claims a natural home remedy can lower A1C in three hours and reverse the condition, including in severe cases.
- **Unsupported research reference:** The body refers vaguely to “early research in 2026” but the captured email provides no study title, authors, institution or supporting citation.
- **Fear-based wording:** It refers to nerve damage, blindness and amputations to intensify concern about blood sugar.
- **Unclear sender identity:** The From address uses `hotiaczu.courui.aventrox.my.id`; the supplied message does not establish a recognised healthcare provider behind this sender.
- **Promotional call to action:** The recipient is invited to click through to learn about the claimed three-hour protocol.
- **Hosted promotional destination:** The primary link uses a Google Cloud Storage hostname rather than an evident healthcare-provider domain.
- **Tracking-style URL fragments and additional links:** More than one HTML anchor points to the hosted object with different fragment values.
- **Unrelated unsubscribe identity:** The List-Unsubscribe header points to `consigntix.com`, a domain unrelated to the sender identity shown in the message.
- **Remote image:** The HTML references an image hosted at `i[.]imgur[.]com`.

## 5. Link inspection
The primary promotional link points to `hxxps://storage[.]googleapis[.]com/lithesome/reachflow[.]html`. The captured HTML includes more than one anchor using this hosted object and different fragment values. The call-to-action text reads “Learn this simple natural protocol and start enjoying normal blood sugar levels in just 3 hours”.

The HTML also references an image hosted at `i[.]imgur[.]com`. Separately, the `List-Unsubscribe` header points to `hxxp://consigntix[.]com/LEAVE=To`; the body includes an additional unsubscribe anchor using the Google Cloud Storage object.

The primary destination is not presented as an official healthcare-provider domain. The hostname belongs to a genuine cloud-hosting service, but that does not establish who controls the specific object or whether its content is legitimate. The fragment values contain tracking-style data; I have not reproduced them. I inspected the URL strings in the source and screenshots. I did not open the destinations or establish any server-side redirects.

## 6. Attachment review
No conventional named file attachment is indicated in the supplied message excerpt. The captured MIME section identifies an HTML part with UTF-8 character encoding and quoted-printable transfer encoding. The body also contains a remote image reference.

## 7. Classification and risk
**Classification: Suspicious**  
**Confidence: Medium**

The message is unsolicited promotional content with sensational health claims, fear-based wording, an unfamiliar sender domain and multiple tracking destinations. However, the supplied message does not by itself establish credential harvesting, payment diversion or malware delivery. “Suspicious” is therefore more defensible than asserting confirmed phishing on the current evidence.

**Potential impact:** Recipients could be misled into engaging with an untrustworthy health promotion, disclosing information through a landing page or making decisions based on unsupported claims. This investigation does not assess the medical validity of the claims.

**Recommended recipient action:** Do not follow the links or provide personal or health information. Verify health information with qualified healthcare professionals and report unsolicited deceptive promotions through the appropriate channel.

## 8. Evidence captured
I captured and added six Sample 03 screenshots to the repository: sender/recipient fields, the main claim and call to action, other HTML links, the parsed MXToolbox header output, the MXToolbox summary and the SPF/DKIM information. The captures support the observations recorded in this analysis.

## 9. Header observations
The supplied Authentication-Results record reports SPF pass for envelope domain `courui.aventrox.my.id`, with sending IP `178.214.223.204`. It reports DKIM pass for `hotiaczu.courui.aventrox.my.id`. No DMARC result is shown. The captured headers include `X-Originating-IP: 178.214.223.204`; Reply-To, Return-Path and a complete Received route are not available in the supplied source.

### MXToolbox - Email Header Analyzer
I analysed the headers using [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx). The captured output shows:
- SPF: `pass`
- SPF envelope-sender domain: `courui.aventrox.my.id`
- SPF sending IP: `178.214.223.204`
- DKIM: `pass`
- DKIM signing domain: `hotiaczu.courui.aventrox.my.id`
- DMARC: No result displayed
- Received delay shown by MXToolbox: `0 seconds`

Both SPF and DKIM pass for the sending domains shown. These results confirm the checks reported for the relevant sending infrastructure; they do not validate the medical claims or establish that the sender is a recognised healthcare provider. MXToolbox displays a zero-second delay, but no complete hop-by-hop Received route is present in the source to establish a delivery timeline.

## 10. Evidence captured

| Evidence file | What it records |
|---|---|
| `From_and_to.png` | From, To, Sender, subject, date and other available header fields |
| `Body_and_urge_to_click_link.png` | Main health claims, fear-based language and call to action |
| `Other_Links.png` | Additional HTML anchor, remote image reference and unsubscribe link in the body |
| `SPF_AND_DKIM.png` | Authentication-Results, SPF pass and DKIM pass |
| `MX_output_01.png` | MXToolbox parsed headers, including SPF/DKIM information |
| `MX_Output_02.png` | MXToolbox analysed-header summary and displayed relay delay |

## 11. Limitations

The recipient is redacted and complete delivery-routing details are unavailable. The destination URLs were not opened or independently confirmed malicious. The captured email does not provide supporting research for its medical claims, and this investigation does not independently assess their scientific validity. A passing SPF or DKIM result confirms the relevant sending-domain check; it does not establish that the content or offer is trustworthy.
