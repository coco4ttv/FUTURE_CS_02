# Sample 02 — SiriusXM Payment-Failure Email

## 1. Source details
- Dataset: [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- Original filename: `03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml`
- Original source: [Sample 02 — original email](https://github.com/cw-l/message-corpus/blob/main/submissions/email/cd73657af8d9165a/1.0.0/03eb531b9a4b525a9247a4ca47c995fb31b2811ef558b33c969547ff653be878.eml)
- Date: Thu, 01 Oct 2026 05:10:28 +0000

## 2. Email overview
- Decoded display name: `Payment_Declined` (the encoded header contains replacement characters)
- From: `ctlelqj.32.195982@btjgbfyk.aroke.hugunenav.biz`
- To: Redacted by the dataset
- Decoded subject: `Your SiriusXM Account will Be Removed Today Please Renew Now!` (the encoded header contains replacement characters)
- Claimed organisation: SiriusXM
- Reply-To: Not present in the supplied headers
- Sender: `wfxezkcnaxytrerlhvdbi@btjgbfyk.aroke.hugunenav.biz`

## 3. Main message and requested action

The main visible HTML message presents itself as a SiriusXM / SXM subscription notice. It says a monthly payment failed, claims the subscription has been cancelled and states that the recipient must renew or update payment details. It displays account-style fields for a customer ID, email address, account status and expiry date. The supplied recipient details are redacted and the account claims have not been independently verified.

The message uses the subject “Your SiriusXM Account will Be Removed Today Please Renew Now!” and warns that services will be completely suspended within 24 hours. The visible message therefore matches the subject's payment-failure and account-removal pretext.

The body contains a prominent “UPDATE MY PAYMENT DETAILS” call to action. I identified several additional links in the HTML, including footer unsubscribe links; their destinations are reviewed below.

## 4. Content indicators

- **Brand impersonation:** The message presents SiriusXM / SXM branding, while the visible sender address uses `btjgbfyk.aroke.hugunenav.biz`, not an evident SiriusXM domain.
- **Urgency:** The subject says the account will be removed “Today”.
- **Threat of service loss:** The body threatens complete suspension within 24 hours.
- **Financial pretext:** The message claims a monthly payment failed and asks the recipient to renew or update payment details.
- **Unusual sender domain:** The sender uses a random-looking subdomain under `hugunenav.biz`.
- **Different Sender and From mailbox names:** The `Sender` header contains a different mailbox local-part from the visible `From` address, although both use the same subdomain.
- **Unrelated unsubscribe identity:** The `List-Unsubscribe` header points to `bicobuluj.biz`, which does not match the claimed subscription provider.
- **Multiple hosted links:** I identified six HTML hyperlinks. They share the same Google Cloud Storage object URL but contain different fragment values.
- **Hidden and unrelated content:** Additional MIME/HTML content contains unrelated rental, software-demo, account-registration, newsletter and article text, as well as credential-like strings. This is not part of the main visible SiriusXM notice and is recorded as an unusual source-content finding.
- **Hidden trust statement:** A hidden HTML object contains the words “This message was sent from a trusted sender”. Text written inside an email cannot independently establish that the sender is trusted.
- **Encoded header artefacts:** The MIME-encoded From display name and subject contain replacement characters when decoded. This is a formatting/data-quality anomaly; the classification is based on the combined sender, content and link indicators rather than encoding artefacts alone.

## 5. Link inspection

I extracted six hyperlink destinations from the HTML source. All six use the same base object URL:

`hxxps://storage[.]googleapis[.]com/worklinks/evrtinggood[.]html`

The links contain different values after the `#` fragment, including path-like strings and tracking parameters. I have not reproduced those message-specific values in this report. The fragment is client-side URL data and is not, by itself, proof of the final destination or of a server-side redirect. The actual destination after any page script runs has not been established.

The main “UPDATE MY PAYMENT DETAILS” call to action is enclosed by an anchor using this hosted object. Other links are associated with the message layout and footer unsubscribe text. The separate `List-Unsubscribe` header points to `bicobuluj.biz`.

Google Cloud Storage is a genuine hosting service, but the presence of its hostname does not establish that this particular object is an official SiriusXM billing page. The use of an unexpected hosted object for a payment-update request is inconsistent with the claimed billing context.

I inspected the link strings in the source and kept them defanged. I did not open the links or attempt to resolve the hosted page.

## 6. MIME and HTML structure

I reviewed the complete raw body rather than relying only on the first readable text fragment. The message declares `multipart/digest` and contains multiple HTML parts with different charset declarations, including `iso-8859-1` and `utf-8`. One part specifies `Content-Transfer-Encoding: amazonses`, an unusual value in the supplied MIME source. The HTML also contains repeated document/body elements, malformed or nested markup and hidden elements.

The primary visible section is the SiriusXM payment-failure notice described above. Elsewhere in the MIME content, I found additional hidden or appended material unrelated to SiriusXM, including Enterprise Plus rental welcome text, an Event Temple demo follow-up, a YNAB email-confirmation message, account-registration text, article/news excerpts and Parsec instructions. The source also contains random-looking strings and credential-like login/password fields. I have not reproduced those strings in this report.

The body includes hidden text stating that the message was sent from a trusted sender, along with repeated encoded non-breaking spaces. These are observations about the supplied HTML/MIME structure; they do not prove how the message was assembled or whether the unrelated fragments were deliberately inserted. I record them as an unusual content-structure finding rather than treating every embedded fragment as part of the visible SiriusXM message.

No conventional named file attachment was identified in the supplied message. The multipart format itself does not establish that a separate file attachment is present.

## 7. MXToolbox header analysis

I analysed the message headers using [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx).

| Header check | Result | Observed detail |
|---|---|---|
| SPF | **Pass** | Envelope domain: `aroke.hugunenav.biz` |
| SPF sending IP | — | `129.121.93.85` |
| DKIM | **Pass** | Signing domain: `btjgbfyk.aroke.hugunenav.biz` |
| DMARC | Not displayed | No DMARC outcome is available in the captured result |
| Return-Path | Not present in supplied corpus | The corpus removes routing headers |
| Received route | Not present in supplied corpus | MXToolbox does not show a hop-by-hop delivery route |
| Received delay shown by MXToolbox | 0 seconds | This is the analyser's displayed value; without the Received chain it should not be interpreted as proof of instantaneous delivery |

Both SPF and DKIM pass for the sending infrastructure shown. These results authenticate the relevant sending domain/signature; they do not establish that the email was sent by SiriusXM. The visible From domain is `btjgbfyk.aroke.hugunenav.biz`, while the SPF envelope domain is `aroke.hugunenav.biz`. No DMARC result is shown, so a DMARC outcome cannot be inferred from the screenshot.

The source also contains an ARC set signed with `d=google.com`. This identifies the domain shown in the ARC signature; it does not mean Google authored the original message or endorses the sender. The raw `DKIM-Signature` header specifies `a=rsa-sha1`, while the captured `Authentication-Results` field reports `dkim=pass`. I record both observations separately and do not treat the presence of the algorithm value as evidence that the reported DKIM check failed.

## 8. Classification and risk
**Classification: Phishing**  
**Confidence: High**

The message impersonates a subscription provider, uses a failed-payment pretext, threatens service suspension within 24 hours and asks the recipient to update payment details through an unexpected hosted destination. The sender domain does not match the claimed brand. These combined indicators support a phishing classification.

**Potential impact:** A recipient could disclose payment-card or account information. No payment loss or credential compromise was observed during this analysis.

**Recommended recipient action:** Do not use the payment link or reply to the message. Check subscription status by navigating independently to the genuine SiriusXM website and report the email through the organisation's security process.

## 9. Evidence captured

The Sample 02 evidence folder contains the following investigation captures:

| Evidence file | What it records |
|---|---|
| `from and to.png` | Original From and To header fields |
| `Decoding subject line.png` | CyberChef decoding of the MIME-encoded subject |
| `Decoding of the from email_03.png` | Base64 decoding of the MIME-encoded From field |
| `Body.png` | Message text referring to the failed monthly payment and cancelled subscription |
| `information on reciepiants account.png` | Account-style details displayed in the email, with recipient information redacted |
| `urgency message and link.png` | 24-hour suspension warning and payment-update call to action |
| `Link.png` | Defanged primary link destination |
| `MX Toolbox output.png` | Parsed message headers and SPF/DKIM authentication results |
| `MX Toolbox output2.png` | MXToolbox header summary and relay information |
| `Decoding of the from email.png` | CyberChef inspection of the encoded From header |
| `Decoding of the from email_02.png` | Search result used during the sender-string investigation; not treated as an independent technical verdict |
| `assesment of link.png` | Supplementary automated interpretation of the link; not treated as a URL reputation scan or independent confirmation |

## 10. Limitations
The dataset redacts the recipient and removes routing headers such as `Received` and `Return-Path`, preventing a complete hop-by-hop delivery analysis. The MXToolbox output shows SPF and DKIM passing but does not display a DMARC result. The hosted destination was not opened or independently confirmed malicious through a live reputation service. The account-style details in the email were not independently verified.
