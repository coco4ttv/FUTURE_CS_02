# Future Interns Cyber Security — Task 2
## Phishing Email Detection & Awareness System

This project documents an independent investigation of three unsolicited email samples from the public [cw-l/message-corpus](https://github.com/cw-l/message-corpus) dataset. The corpus maintainers describe it as a collection of real-world, redacted spam, scam and phishing messages intended for security research and awareness training. The work examines sender identity, message content, link destinations and the authentication information retained in each sample, then develops practical phishing-awareness guidance for employees. The corpus does not assign a definitive spam/scam/phishing subtype to each message; the classifications in this project are the analyst's assessments based on the evidence.

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

The source corpus retains some authentication results but does not preserve the complete mail-routing path. SPF, DKIM and DMARC are therefore reported only where the supplied headers contain an explicit result. MXToolbox Email Header Analyzer was used to review the available headers for all three samples. The authentication values below agree with the supplied source-header fields.

## Tools and resources

- [cw-l/message-corpus](https://github.com/cw-l/message-corpus) — source email samples
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

The repository links to the original dataset records and contains the investigation notes and selected evidence screenshots. The sample messages are drawn from a public corpus released under the MIT License; the project credits the dataset and links to each original record. The corpus README describes the messages as real-world samples with contributor information redacted and URLs defanged. The link review in this project was static; suspicious destinations were not opened.

The source files contain limited routing information. In particular, complete `Received` and `Return-Path` details are unavailable in this corpus. Absence of a field is treated as unavailable evidence, not as an authentication failure.

## Current project status

The source selection and content investigations for all three samples are documented. Sample 01 and Sample 02 evidence records include captured sender/header, message-content, link and MXToolbox analysis screenshots. MXToolbox header analysis has been completed for all three samples, with the available SPF/DKIM results recorded in the corresponding analysis files; DMARC is recorded as unavailable where no result is shown. The full Sample 02 MIME/HTML source has also been reviewed, including its six HTML links and unrelated hidden/appended content. Sample 03 supporting screenshots remain to be added. The employee-awareness guide and report are drafted from the sample findings.

## References

- [Future Interns — Cyber Security Task 2](https://futureinterns.com/)
- [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- [MXToolbox — Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
