# Investigation Evidence Register

**Project:** Phishing Email Detection & Awareness System  
**Dataset:** [cw-l/message-corpus](https://github.com/cw-l/message-corpus)  
**Header-analysis tool:** [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)

## Sample 01 — Google / Cloud Account Alert

**Source:** [Original email sample](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml)

| Evidence | File / record | Result |
|---|---|---|
| Sender and available headers | `sample-01/sender_info.png` | Captured |
| Main message and primary link | `sample-01/main_body_and_link.png` | Captured |
| MXToolbox header analysis | [Sample 01 analysis](../analysis/sample-01.md) | SPF pass; no DKIM or DMARC result displayed |

## Sample 02 — SiriusXM Payment-Failure Email

**Source:** [Original email sample](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml)

| Evidence | File / record | Result |
|---|---|---|
| Sender and recipient header | `sample-02/from and to.png` | Captured |
| Encoded subject inspection | `sample-02/Decoding subject line.png` | Captured |
| Encoded sender inspection | `sample-02/Decoding of the from email_03.png` | Captured |
| Email body and payment-failure claim | `sample-02/Body.png` | Captured |
| Account-style details | `sample-02/information on reciepiants account.png` | Captured; recipient fields redacted |
| Urgency and payment action | `sample-02/urgency message and link.png` | Captured |
| Primary link destination | `sample-02/Link.png` | Captured in defanged form |
| MXToolbox parsed headers | `sample-02/MX Toolbox output.png` | SPF and DKIM pass; DMARC result not displayed |
| MXToolbox header summary | `sample-02/MX Toolbox output2.png` | Header analysed; no hop-by-hop relay path shown |
| Complete MIME/HTML source review | [Sample 02 analysis](../analysis/sample-02.md) | Main SiriusXM message separated from unrelated hidden/appended content |
| HTML link extraction | [Sample 02 analysis](../analysis/sample-02.md) | Six HTML hyperlinks identified; destinations retained in defanged form and not opened |
| MIME structure review | [Sample 02 analysis](../analysis/sample-02.md) | Multiple HTML parts, differing charset declarations, hidden objects and unrelated appended message fragments recorded |

## Sample 03 — Diabetes-Treatment Promotion

**Source:** [Original email sample](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)

| Evidence | File / record | Result |
|---|---|---|
| Email content and sender analysis | [Sample 03 analysis](../analysis/sample-03.md) | Investigation documented |
| MXToolbox header analysis | [Sample 03 analysis](../analysis/sample-03.md) | SPF and DKIM pass; no DMARC result displayed |
| Sample screenshots | — | Not yet added to this repository |

## Evidence summary

The analysis files contain the source details, message indicators, link observations, authentication results, classification and risk rationale for each sample. Sample 01 and Sample 02 have supporting screenshots in their respective evidence folders. Sample 03 content and header analysis is documented; its screenshot evidence remains to be added.
