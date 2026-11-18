# Investigation Evidence Register

**Project:** Phishing Email Detection & Awareness System  
**Dataset:** [cw-l/message-corpus](https://github.com/cw-l/message-corpus)  
**Header-analysis tool:** [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)

## Sample 01 - Google / Cloud Account Alert

**Source:** [Original email sample](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/00448d97a6dde39113273dd71a4e9c3e60102dbbff5c2af266efc30a60ddbe01.eml)

| Evidence | File / record | Result |
|---|---|---|
| Sender and available headers | `sample-01/sender_info.png` | Captured |
| Main message and primary link | `sample-01/main_body_and_link.png` | Captured |
| MXToolbox parsed headers | `sample-01/MX Toolbox_output_01.png` | SPF pass recorded; no DKIM or DMARC result displayed |
| MXToolbox analysed-header summary | `sample-01/MX Toolbox_output_02.png` | Captured; analyser displayed a 0-second relay delay |

## Sample 02 - SiriusXM Payment-Failure Email

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

## Sample 03 - Diabetes-Treatment Promotion

**Source:** [Original email sample](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/055b7167bba921026083b0a58b437b19458c6b98c28755f6979ccda14b82e4ea.eml)

| Evidence | File / record | Result |
|---|---|---|
| Sender, recipient and message headers | `sample-03/From_and_to.png` | Captured |
| Main body, health claims and call to action | `sample-03/Body_and_urge_to_click_link.png` | Captured |
| Additional HTML links and remote image | `sample-03/Other_Links.png` | Captured |
| SPF and DKIM authentication information | `sample-03/SPF_AND_DKIM.png` | SPF pass; DKIM pass; no DMARC result displayed |
| MXToolbox parsed headers | `sample-03/MX_output_01.png` | Captured |
| MXToolbox analysed-header summary | `sample-03/MX_Output_02.png` | Captured; displayed relay delay 0 seconds |
| Full analysis | [Sample 03 analysis](../analysis/sample-03.md) | Body, links, MIME context, header results and risk assessment documented |

## Evidence summary

The analysis files contain my source details, message observations, link findings, authentication results, classifications and risk rationale for all three samples. I saved the sender/header, message-content, link and MXToolbox screenshots in each sample's evidence folder. I used MXToolbox for all three header reviews; Google Admin Toolbox did not produce a usable result from the supplied corpus headers, so no output from that tool is included. The evidence files listed above are present in the repository.
