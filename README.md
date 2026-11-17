# Future Interns Cyber Security — Task 2
## Phishing Email Detection & Awareness System

This project documents the investigation of three unsolicited email samples from the public [cw-l/message-corpus](https://github.com/cw-l/message-corpus) dataset. The work examines sender identity, message content, link destinations and the authentication information retained in each sample. The investigation also develops practical phishing-awareness guidance for employees.

## Project findings

| Sample | Email theme | Assessment |
|---|---|---|
| 01 | Google-style cloud-account and device-security alert | **Phishing** |
| 02 | SiriusXM payment failure and subscription renewal | **Phishing** |
| 03 | Type 2 diabetes treatment promotion | **Suspicious** |

The classifications and supporting rationale are recorded in the individual analysis files.

- [Sample 01 — Google / cloud-account alert](analysis/sample-01.md)
- [Sample 02 — SiriusXM payment-failure email](analysis/sample-02.md)
- [Sample 03 — Diabetes-treatment promotion](analysis/sample-03.md)

## Investigation method

The three source messages were reviewed in raw-text form. The investigation recorded the sender and subject fields, examined the main message content, compared the claimed organisation with the sender domain, and inspected HTML link destinations without opening them. The supplied MIME content was also reviewed for conventional named file attachments.

The source corpus retains some authentication results but does not preserve the complete mail-routing path. SPF, DKIM and DMARC are therefore reported only where the supplied headers contain an explicit result. Google Admin Toolbox Messageheader and MXToolbox analysis is recorded separately from the source-header observations.

## Tools and resources

- [cw-l/message-corpus](https://github.com/cw-l/message-corpus) — source email samples
- [Google Admin Toolbox Messageheader Analyzer](https://toolbox.googleapps.com/apps/messageheader/analyzeheader)
- [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
- Browser raw-text and HTML-source inspection
- Microsoft Word / PDF — report and awareness document
- GitHub — source references, analysis and evidence

## Repository structure

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

## Evidence and scope

The repository links to the original dataset records and contains investigation notes and selected screenshots rather than copies of the original email files. Published screenshots use redacted recipient information and omit message-specific tracking values and credential-like strings. URLs are recorded in defanged form. The link review was static; suspicious destinations were not opened.

The source files contain limited routing information. In particular, complete `Received` and `Return-Path` details are unavailable in this corpus. Absence of a field is treated as unavailable evidence, not as an authentication failure.

## Current project status

The repository structure, source selection and initial content investigations for all three samples are documented. Sample 01 has sender/header evidence and a main-body/primary-link capture in its evidence folder. The earlier secondary footer-link captures and screenshots of unrelated concatenated MIME fragments are excluded from the published evidence set.

Sample 02 and Sample 03 content investigations are documented; their screenshot evidence has not yet been added. Google Admin Toolbox and MXToolbox results are also outstanding. The employee-awareness guide is drafted, and the final report is being developed from the sample findings.

## References

- [Future Interns — Cyber Security Task 2](https://futureinterns.com/)
- [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- [Google Admin Toolbox — Messageheader Analyzer](https://toolbox.googleapps.com/apps/messageheader/analyzeheader)
- [MXToolbox — Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
