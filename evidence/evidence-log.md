# Investigation Evidence Log

**Project:** Phishing Email Detection & Awareness System  
**Dataset:** [cw-l/message-corpus](https://github.com/cw-l/message-corpus)

This log records the evidence currently included in the repository and the status of the remaining investigation artefacts.

## Sample 01 — Google / Cloud Account Alert

**Source:** [Original Sample 01](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml)

| Evidence | Repository file | Status |
|---|---|---|
| Sender and available headers | `sample-01/sender_info.png` | Captured |
| Main Google-style message and primary link | `sample-01/main_body_and_link.png` | Captured; tracking query values obscured |
| Secondary footer links | — | Excluded from published evidence as they are not the primary call to action |
| Unrelated concatenated MIME fragments | — | Excluded from published evidence |
| MXToolbox header analysis | Captured in conversation | SPF pass; DKIM/DMARC results not displayed in the supplied capture |

## Sample 02 — SiriusXM Payment-Failure Email

**Source:** [Original Sample 02](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml)

| Evidence | Repository file | Status |
|---|---|---|
| Sender and available headers | — | Not yet captured |
| Main email body | — | Not yet captured |
| Primary payment link | — | Not yet captured |
| MXToolbox header analysis | Captured in conversation | SPF and DKIM pass; DMARC result not displayed |

## Sample 03 — Diabetes-Treatment Promotion

**Source:** [Original Sample 03](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)

| Evidence | Repository file | Status |
|---|---|---|
| Sender and available headers | — | Not yet captured |
| Main email body | — | Not yet captured |
| Primary promotional link | — | Not yet captured |
| Google Admin Toolbox result | — | Pending |
| MXToolbox result | — | Pending |

## Evidence handling and scope

The repository contains selected screenshots and analysis notes linked to the source dataset; the original `.eml` files are not duplicated here. Recipient details are redacted in the source material. Published URL references retain defanged hosts and omit message-specific tracking values. Suspicious destinations were examined from the raw source and were not opened.

The three supplied messages contain some unrelated or concatenated MIME content. Only the sections relevant to each primary email investigation are represented in the selected evidence set.
