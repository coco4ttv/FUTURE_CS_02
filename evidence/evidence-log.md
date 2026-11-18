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
| Email content and sender analysis | [Sample 02 analysis](../analysis/sample-02.md) | Investigation documented |
| MXToolbox header analysis | [Sample 02 analysis](../analysis/sample-02.md) | SPF and DKIM pass; no DMARC result displayed |
| Sample screenshots | — | Not yet added to this repository |

## Sample 03 — Diabetes-Treatment Promotion

**Source:** [Original email sample](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)

| Evidence | File / record | Result |
|---|---|---|
| Email content and sender analysis | [Sample 03 analysis](../analysis/sample-03.md) | Investigation documented |
| MXToolbox header analysis | [Sample 03 analysis](../analysis/sample-03.md) | SPF and DKIM pass; no DMARC result displayed |
| Sample screenshots | — | Not yet added to this repository |

## Evidence summary

The analysis files contain the source details, message indicators, link observations, authentication results, classification and risk rationale for each sample. The evidence directory contains the selected Sample 01 screenshots. Sample 02 and Sample 03 screenshots have not yet been added to the repository.

The source corpus redacts contributor email addresses and defangs message URLs. The investigation preserves those protections and uses the corpus's original sample links for provenance.