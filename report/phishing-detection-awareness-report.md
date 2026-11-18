# Phishing Email Detection & Awareness System
## Future Interns Cyber Security Internship — Task 2

**Prepared by:**  
**Assessment date:** 17 November 2026  
**Repository:** [FUTURE_CS_02](https://github.com/coco4ttv/FUTURE_CS_02)

## 1. Executive summary

This project reviews three unsolicited email samples from the public `cw-l/message-corpus` dataset. The analysis examines sender identity, claimed organisation, message content, requested action, link destinations and the authentication information retained in the source headers.

The current assessment classifies Sample 01 (Google-style cloud/device-security alert) and Sample 02 (SiriusXM payment-failure message) as **Phishing**. Sample 03 (diabetes-treatment promotion) is classified as **Suspicious**, because its sensational health claims and promotional links are concerning but the supplied message does not establish credential harvesting, payment diversion or malware delivery.

The source corpus removes or does not retain complete routing information, including `Received` and `Return-Path` fields. MXToolbox Email Header Analyzer was used for all three samples. Its results are included in the sample findings. The source corpus does not preserve complete routing information.

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

Three source records were reviewed in raw-text form. The original messages remain linked in the corresponding sample analysis files. The investigation covered available sender and subject fields, the main message content, HTML link destinations, List-Unsubscribe information, MIME structure and the authentication results present in the supplied headers.

Link destinations were inspected statically in defanged form. No suspicious destination was opened. Conventional named file attachments were not identified in the inspected main message sections.

**Header-analysis tool used:** [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)

MXToolbox was used to review the available headers for all three samples. The reported SPF and DKIM results are recorded in the corresponding sample sections. The supplied dataset does not contain the complete original delivery-routing information.

## 4. Sample findings

### 4.1 Sample 01 — Google / Cloud Account Alert

**Classification: Phishing — High confidence**

The message uses Google-style branding and a “Support Team” identity, but the visible sender is `nooreply@csl.yusoilxyhryni.us`. The email combines a cloud-storage/account warning, a device-virus warning and a subscription-renewal demand. It uses fear-based language and a 48-hour deadline. Its primary links use the unexpected host `storage[.]googleapis[.]com`.

The supplied Authentication-Results record SPF pass for the envelope-sender domain `pispszltq.voaxodovlpu.synrg.co.za`, with sending IP `95.173.180.123`. No DKIM pass or DMARC result is shown. The SPF pass does not authenticate the visible From identity as Google.

**Potential impact:** Disclosure of account or payment information or interaction with deceptive hosted content.

Full analysis: [analysis/sample-01.md](../analysis/sample-01.md)

### 4.2 Sample 02 — SiriusXM Payment-Failure Email

**Classification: Phishing — High confidence**

The email claims a SiriusXM payment failed, states that the account will be removed and threatens service suspension within 24 hours. It asks the recipient to update payment details. The sender domain `btjgbfyk.aroke.hugunenav.biz` does not match an evident SiriusXM domain. The payment link uses `storage[.]googleapis[.]com`, and the unsubscribe host is `bicobuluj[.]biz`.

The supplied Authentication-Results record SPF pass for `aroke.hugunenav.biz`, with sending IP `129.121.93.85`, and DKIM pass for `btjgbfyk.aroke.hugunenav.biz`. No DMARC result is shown. These passes authenticate the relevant sending domain/signature; they do not establish that the message is from SiriusXM.

**Potential impact:** Disclosure of payment-card or account information.

Full analysis: [analysis/sample-02.md](../analysis/sample-02.md)

### 4.3 Sample 03 — Diabetes-Treatment Promotion

**Classification: Suspicious — Medium confidence**

The email promotes a “natural” treatment and claims that Type 2 diabetes can be reversed and A1C lowered within three hours. It uses fear-based language about complications and links to a promotional destination hosted under `storage[.]googleapis[.]com`, with additional image and tracking references.

The supplied Authentication-Results record SPF pass for `courui.aventrox.my.id`, with sending IP `178.214.223.204`, and DKIM pass for `hotiaczu.courui.aventrox.my.id`. No DMARC result is shown. Authentication of the sending domain does not validate the health claims or demonstrate that the offer is trustworthy.

**Potential impact:** Recipients could be misled into engaging with an untrustworthy health promotion or disclosing personal information.

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

## 6. Recommendations

- Verify account, payment and security alerts through the organisation's known official website or contact channel.
- Treat unexpected deadlines and threats of account closure as reasons to pause and verify.
- Check the full sender address rather than relying on display names or logos.
- Inspect link destinations and be cautious when they do not match the claimed organisation.
- Never provide passwords, one-time passcodes or payment details through an unexpected email link.
- Report suspicious emails through the organisation's approved security process.
- Provide recurring employee awareness training using realistic examples and clear reporting guidance.

## 7. Evidence and limitations

The repository includes source references and Sample 01 and Sample 02 investigation screenshots. MXToolbox header analysis has been completed for all three samples and the SPF/DKIM results are recorded in the sample findings. Sample 03 email-content screenshots remain to be added.

The source corpus does not preserve a complete mail-routing chain; in particular, `Received` and `Return-Path` information is unavailable. DMARC results are not shown in the supplied authentication fields. The absence of a result is not treated as a failed check.

The embedded links were reviewed from the raw message source and were not opened. No live destination reputation check, credential theft, financial loss or malware execution is claimed. Sample 01 also contains unrelated concatenated MIME fragments; these are noted as a source-data anomaly and are not treated as part of the main Google-themed message.

## 8. Conclusion

The three samples demonstrate different social-engineering approaches: impersonation and fear-based account warnings, payment pressure, and exaggerated health-product promotion. Two samples have sufficient indicators for a phishing classification, while the third is more appropriately recorded as suspicious on the available evidence.

The investigation demonstrates why message content, sender identity, link context and authentication results must be assessed together. The remaining header-tool outputs and Sample 02/03 screenshots will complete the technical evidence record.

## 9. References

- [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
- [Future Interns](https://futureinterns.com/)
