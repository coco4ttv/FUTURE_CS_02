# Phishing Email Detection & Awareness System
## Future Interns Cyber Security Internship — Task 2

**Prepared by:** Samuel Evans-Adeluka  
**Assessment date:** 13 November 2026  
**Repository:** [FUTURE_CS_02](https://github.com/coco4ttv/FUTURE_CS_02)

## 1. Executive summary

I reviewed three unsolicited email samples from the public `cw-l/message-corpus` dataset. I examined sender identity, claimed organisation, message content, requested action, link destinations and the authentication information retained in the source headers.

The current assessment classifies Sample 01 (Google-style cloud/device-security alert) and Sample 02 (SiriusXM payment-failure message) as **Phishing**. Sample 03 (diabetes-treatment promotion) is classified as **Suspicious**, because its sensational health claims and promotional links are concerning but the supplied message does not establish credential harvesting, payment diversion or malware delivery.

I reviewed the three samples using the source material retained in the corpus. Complete `Received` and `Return-Path` routing information was not available. I used MXToolbox Email Header Analyzer for all three samples. I also attempted Google Admin Toolbox Messageheader, but it did not produce a usable result from the supplied corpus headers, so I based the header findings on the MXToolbox output and the authentication fields retained in the source.

## 2. Objectives

- Identify suspicious sender information, brand impersonation and social-engineering indicators.
- Examine the message content and actions requested of recipients.
- Inspect embedded link destinations without opening suspicious links.
- Review available SPF, DKIM and DMARC results.
- Classify email risk as Safe, Suspicious or Phishing.
- Explain potential impact and practical recipient actions.
- Produce clear employee phishing-awareness guidance.

## 3. Sources, scope and methodology

**Source dataset:** [cw-l/message-corpus](https://github.com/cw-l/message-corpus)

I reviewed three source records in raw-text form and linked each original message in its corresponding sample analysis. For each sample, I examined the available sender and subject fields, main message content, HTML link destinations, List-Unsubscribe information, MIME structure and authentication results present in the supplied headers.

I inspected link destinations statically in defanged form and did not open suspicious destinations. I did not identify conventional named file attachments in the inspected message sections.

**Header-analysis tool used:** [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)

I used MXToolbox to review the available headers for all three samples and recorded the reported SPF and DKIM results in the corresponding sample sections. I attempted Google Admin Toolbox Messageheader as well, but it did not produce a usable analysis from the supplied corpus headers. The dataset does not contain the complete original delivery-routing information.

## 4. Sample findings

### 4.1 Sample 01 — Google / Cloud Account Alert

**Classification: Phishing — High confidence**

The message uses Google-style branding and a “Support Team” identity, but the visible sender is `nooreply@csl.yusoilxyhryni.us`. The email combines a cloud-storage/account warning, a device-virus warning and a subscription-renewal demand. It uses fear-based language and a 48-hour deadline. Its primary links use the unexpected host `storage[.]googleapis[.]com`.

The supplied Authentication-Results record SPF pass for the envelope-sender domain `pispszltq.voaxodovlpu.synrg.co.za`, with sending IP `95.173.180.123`. No DKIM pass or DMARC result is shown. The SPF pass does not authenticate the visible From identity as Google.

The MXToolbox output also displays an ARC set signed with `d=google.com`. This identifies the signer of the ARC record added during mail handling; it does not establish that Google authored the original email. The analyser displays a relay delay of 0 seconds, but the source corpus does not preserve the Received chain needed to establish a complete delivery timeline.

**Potential impact:** Disclosure of account or payment information or interaction with deceptive hosted content.

Full analysis: [analysis/sample-01.md](../analysis/sample-01.md)

### 4.2 Sample 02 — SiriusXM Payment-Failure Email

**Classification: Phishing — High confidence**

The main visible HTML message claims a SiriusXM payment failed, says the subscription has been cancelled and threatens account removal and service suspension within 24 hours. It asks the recipient to update payment details. The visible sender domain `btjgbfyk.aroke.hugunenav.biz` does not match an evident SiriusXM domain. The payment action is linked through a Google Cloud Storage object URL, while the separate List-Unsubscribe header points to `bicobuluj.biz`.

The complete raw message contains six HTML hyperlinks using the same hosted object URL with different fragment values. The message source also contains additional hidden or appended material unrelated to SiriusXM, including rental, software-demo, account-registration, newsletter, news/article and Parsec content, as well as credential-like strings that are not reproduced. This makes the MIME/HTML structure notably irregular. The primary visible SiriusXM message does match the subject; the unrelated material appears elsewhere in the message source.

The supplied Authentication-Results record SPF pass for `aroke.hugunenav.biz`, with sending IP `129.121.93.85`, and DKIM pass for `btjgbfyk.aroke.hugunenav.biz`. The DKIM-Signature header specifies `rsa-sha1`. No DMARC result is shown. The SPF and DKIM passes indicate successful checks for the sending infrastructure shown; they do not establish that the message is from SiriusXM or validate its payment request. The message also contains a Google-signed ARC set, which does not establish that Google authored the original message.

**Potential impact:** Disclosure of payment-card or account information if a recipient follows the payment-update request. The source also contains credential-like material, but no credential use or compromise is established.

Full analysis: [analysis/sample-02.md](../analysis/sample-02.md)

### 4.3 Sample 03 — Diabetes-Treatment Promotion

**Classification: Suspicious — Medium confidence**

The email promotes a natural home remedy and claims that Type 2 diabetes can be reversed and A1C lowered in three hours. It uses fear-based wording about complications including nerve damage, blindness and amputations, and invites the recipient to click through to learn the advertised protocol. The captured body provides no study citation or clinical evidence for the claims. The primary link points to a Google Cloud Storage object under `storage[.]googleapis[.]com`; the HTML also references an image hosted at `i[.]imgur[.]com`. The List-Unsubscribe header points to `consigntix[.]com`.

The supplied Authentication-Results record reports SPF pass for `courui.aventrox.my.id`, with sending IP `178.214.223.204`, and DKIM pass for `hotiaczu.courui.aventrox.my.id`. No DMARC result is shown. MXToolbox displays a zero-second relay delay, but the source does not preserve a complete Received route. Authentication of the sending domain does not validate the health claims or demonstrate that the offer is trustworthy.

**Potential impact:** Recipients could be misled by unsupported health claims, engage with an untrustworthy promotional page or disclose personal or health information.

Full analysis: [analysis/sample-03.md](../analysis/sample-03.md)

## 5. Comparative assessment

| Criterion | Sample 01 | Sample 02 | Sample 03 |
|---|---|---|---|
| Claimed identity | Google Support | SiriusXM | Diabetes-treatment promotion |
| Sender domain | `csl.yusoilxyhryni.us` | `btjgbfyk.aroke.hugunenav.biz` | `hotiaczu.courui.aventrox.my.id` |
| SPF | Pass | Pass | Pass |
| DKIM | No pass result shown | Pass | Pass |
| DMARC | Not shown | Not shown | Not shown |
| Main lure | Device/account threat and subscription closure | Failed payment and service suspension | Sensational health claims |
| Main link host | `storage[.]googleapis[.]com` | `storage[.]googleapis[.]com` | `storage[.]googleapis[.]com` |
| Classification | **Phishing** | **Phishing** | **Suspicious** |

A passing SPF or DKIM result is not, by itself, proof that a message is legitimate. The visible sender identity, claimed organisation, content and authentication alignment must be considered together.

## 6. How the attacks work — simple explanation

The three emails use different stories, but each tries to influence the recipient into taking an action before checking whether the message is genuine.

### Sample 01 — Google / cloud account alert

The sender uses Google-style branding and a Support Team identity to make the email look familiar. It then warns about account or device problems and adds a deadline to create pressure. The aim is to make the recipient worry that access, files or a subscription are at risk and follow the links or renewal request without checking the sender first. The evidence shows an unexpected sender domain and hosted links. I did not open the links, so I cannot confirm what the pages would have asked the recipient to do.

### Sample 02 — SiriusXM payment-failure email

The email claims that a SiriusXM payment has failed and that the subscription will be removed unless the recipient updates payment details. This creates concern about losing a service and encourages the recipient to use the payment link in the message. A recipient who trusts the message could be taken to a page and persuaded to enter payment or account information. The sender domain does not match an evident SiriusXM domain, and the payment link uses a hosted Google Cloud Storage address. I did not open the destination, so the investigation does not establish what information the page collected or whether any information was stolen.

### Sample 03 — Diabetes-treatment promotion

This email uses a different approach. Instead of pretending to be an account provider, it makes dramatic health claims and promises a very quick result. It also mentions serious complications to make the reader feel worried and more likely to click the promotional link. The email provides no research citation to support its claims. The supplied evidence supports a suspicious health promotion, but it does not prove that the link delivered malware or collected credentials.

### What the examples have in common

In simple terms, the sender gives the recipient a reason to react — fear of losing an account, concern about a payment, or hope of a quick health improvement — and then encourages them to click a link or take another action. The risk arises when the recipient trusts the story without checking it independently. The final destination and any activity after a click were not tested in this investigation.

## 7. Prevention tips for users

The following steps help employees recognise suspicious messages and avoid acting on them.

1. **Pause before reacting.** Be careful with unexpected warnings, urgent deadlines, threats of account closure, payment problems and offers that promise unusually quick results.
2. **Check the full sender address.** Do not rely on the display name, logo or sign-off. Look at the domain after the `@` symbol and consider whether it matches the organisation the email claims to represent.
3. **Go to the organisation directly.** For account, security or payment messages, open the official app or type the organisation's known website address yourself. Check the account there instead of using the email's link.
4. **Verify unexpected requests separately.** Contact the organisation using a phone number or contact method from its official website, card or previous trusted correspondence — not details supplied only in the suspicious email.
5. **Do not share sensitive information through unexpected links.** Do not enter passwords, one-time passcodes, banking details or payment-card information because an email asks you to.
6. **Treat links and attachments carefully.** Check where a link is supposed to lead without opening it. Do not open unexpected attachments or download files when the sender or purpose is unclear.
7. **Check surprising health and financial claims.** Do not rely on an unsolicited email for medical or financial decisions. Confirm health information with a qualified healthcare professional and use reputable, independent sources.
8. **Report the message.** Use your organisation's phishing-reporting option or contact its IT/security team. Reporting helps the organisation check whether other employees received the same message.
9. **Act quickly if you have interacted with it.** Tell IT/security what happened. If you entered a password, change it through the genuine service's website and follow your organisation's response process. If you supplied card or bank details, contact your bank using its official contact details.

These precautions reduce the chance of account compromise, payment loss and exposure to misleading or harmful content. They also give employees a clear process: pause, check independently, avoid sharing sensitive details and report suspicious messages.

## 8. Evidence and limitations

I saved the sender/header, message-content, link and MXToolbox screenshots for all three samples in their respective evidence folders. I recorded the results from all three MXToolbox header reviews in the sample findings. The evidence register links each capture to the corresponding investigation.

The source corpus does not preserve a complete mail-routing chain; in particular, `Received` and `Return-Path` information is unavailable. DMARC results are not shown in the supplied authentication fields. The absence of a result is not treated as a failed check.

The embedded links were reviewed from the raw message sources and were not opened. No live destination reputation check, credential theft, financial loss or malware execution is claimed. Samples 01 and 02 each contain unrelated concatenated or hidden MIME/HTML content. These fragments are documented as source-content anomalies and are not treated as part of the main visible lure in either message.

## 9. Conclusion

The three samples demonstrate different social-engineering approaches: impersonation and fear-based account warnings, payment pressure, and exaggerated health-product promotion. Two samples have sufficient indicators for a phishing classification, while the third is more appropriately recorded as suspicious on the available evidence.

I found that the sender identity, message content, link context and authentication results need to be considered together. My final assessments are Phishing for Samples 01 and 02, and Suspicious for Sample 03. I documented the full MIME/HTML review for Sample 02 and included the Sample 03 screenshots and header findings in the repository.

## 10. References

- [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
- [Future Interns](https://futureinterns.com/)
