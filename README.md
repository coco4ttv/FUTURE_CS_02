# Future Interns Cybersecurity Task 2
## Phishing Email Detection & Awareness System

This repository documents the investigation of three unsolicited email samples, the identification of phishing indicators, email-header observations, risk classifications and practical employee-awareness guidance.

## Dataset and source samples

All three samples are from the public [cw-l/message-corpus](https://github.com/cw-l/message-corpus) repository. The original messages are linked from each analysis file; the raw `.eml` files are not republished here.

| Sample | Description | Preliminary classification | Analysis |
|---|---|---|---|
| 01 | Google / cloud-account security and subscription alert | Phishing | [Sample 01](analysis/sample-01.md) |
| 02 | SiriusXM payment-failure and renewal alert | Phishing | [Sample 02](analysis/sample-02.md) |
| 03 | Diabetes-treatment promotion | Suspicious | [Sample 03](analysis/sample-03.md) |

Classifications are based on the supplied source content and may be updated if further evidence changes the assessment.

## Objectives

- Inspect sender identity, subject, message body and requested actions.
- Identify brand impersonation, urgency, fear-based language and suspicious links.
- Inspect link destinations statically without visiting them.
- Review the available SPF, DKIM and DMARC information.
- Classify messages as Safe, Suspicious or Phishing.
- Explain potential business impact and recommended recipient action.
- Produce an employee phishing-awareness guide and a professional report.

## Tools and methods

- Raw text view of the original `.eml` samples in the public dataset.
- Google Admin Toolbox Messageheader Analyzer.
- MXToolbox Email Header Analyzer.
- Static inspection of HTML `href` destinations.
- Microsoft Word / PDF for client-ready documentation.
- GitHub for project documentation and evidence.

Header-analyser results are pending until the tools have been run and their actual outputs captured. The source corpus does not preserve all transport-routing headers, so complete route reconstruction may not be possible.

## Project structure

```text
FUTURE_CS_02/
├── README.md
├── analysis/
│   ├── sample-01.md
│   ├── sample-02.md
│   └── sample-03.md
├── evidence/
│   ├── evidence-log.md
│   ├── sample-01/
│   ├── sample-02/
│   └── sample-03/
├── awareness/
│   └── employee-awareness-guide.md
└── report/
    └── phishing-detection-awareness-report.md
```

## Investigation workflow

1. Identify the source sample and preserve its original source link.
2. Review sender information, available headers, subject and message body.
3. Inspect HTML link destinations statically; do not visit suspicious URLs.
4. Check whether named file attachments are actually present.
5. Submit only the available header section to the header-analysis tools and record actual results or errors.
6. Document evidence, limitations, classification, impact and recommended action.
7. Develop employee-awareness guidance and consolidate the findings into a PDF report.

## Evidence and privacy

See [evidence/evidence-log.md](evidence/evidence-log.md) for screenshot status and required captures.

- Do not upload original `.eml` files.
- Redact recipient addresses, personal information and message-specific tracking values.
- Do not publish apparent usernames, passwords, tokens or other credentials embedded in the samples.
- Keep suspicious URLs defanged (for example, `hxxps://example[.]com`).
- Do not visit suspicious destinations.
- Do not claim a header field failed authentication when the result is simply absent.
- Distinguish observations from assumptions and potential impact from actual outcomes.

## Current status

Stages 1–3 (repository setup, source selection and initial content investigation) are documented for all three samples. Sample 01 screenshots have been supplied, but some need to be recaptured because they show unrelated embedded MIME fragments or footer links rather than the primary message body and main call-to-action. Sample 02 and Sample 03 screenshots are still to be added.

Stage 4 (Google Admin Toolbox and MXToolbox), the final awareness guide and final report remain to be completed.

## References

- [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- [Google Admin Toolbox — Messageheader Analyzer](https://toolbox.googleapps.com/apps/messageheader/analyzeheader)
- [MXToolbox — Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
- [Future Interns](https://futureinterns.com/)
