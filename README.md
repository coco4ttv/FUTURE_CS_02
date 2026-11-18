# Future Interns Cyber Security Internship — Task 2
## Phishing Email Detection & Awareness System

I completed this project as part of the Future Interns Cyber Security Internship. I investigated three unsolicited email samples from the public [cw-l/message-corpus](https://github.com/cw-l/message-corpus) dataset, assessed their sender identities and content, inspected the links in their HTML source, and reviewed the authentication information available in their headers. I used the findings to prepare individual sample assessments and an employee phishing-awareness guide.

## My findings

| Sample | Email theme | My assessment |
|---|---|---|
| 01 | Google-style cloud-account and device-security alert | **Phishing** |
| 02 | SiriusXM payment failure and subscription renewal | **Phishing** |
| 03 | Type 2 diabetes treatment promotion | **Suspicious** |

I explain the evidence behind each assessment in the individual investigation files:

- [Sample 01 — Google / cloud-account alert](analysis/sample-01.md)
- [Sample 02 — SiriusXM payment-failure email](analysis/sample-02.md)
- [Sample 03 — Diabetes-treatment promotion](analysis/sample-03.md)

## How I carried out the investigation

I reviewed each source message in raw-text form. I recorded the available sender, subject and date fields, examined the main message content, compared the claimed organisation with the sender domain, and inspected the HTML link destinations without opening them. I also reviewed the MIME structure and checked for conventional named file attachments.

I used [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx) to review the available headers for all three samples. I also attempted to use Google Admin Toolbox Messageheader, but it did not produce a usable analysis from the supplied corpus headers. I therefore used MXToolbox consistently for the three header assessments and have not attributed any results to Google's tool.

The dataset does not preserve the complete original mail-routing path, including full `Received` and `Return-Path` information. I recorded SPF, DKIM and DMARC only where the supplied headers or MXToolbox output displayed a result. A missing result is treated as unavailable information, not as a failed authentication check.

## Tools and resources

- [cw-l/message-corpus](https://github.com/cw-l/message-corpus) — source email samples
- [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx) — header analysis for all three samples
- Browser-based raw email and HTML-source inspection
- GitHub — source references, investigation notes and screenshots
- Markdown — investigation, evidence register, awareness guide and report

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

I saved the supporting screenshots in the evidence folder for each sample and listed them in the [evidence register](evidence/evidence-log.md). The analysis files link to the original corpus records rather than republishing the original `.eml` messages. I kept suspicious destinations in defanged form and reviewed them statically; I did not open the links.

The corpus retains some sender and authentication information but does not provide a complete delivery route. Complete `Received` and `Return-Path` details are unavailable in the supplied records. The absence of a field is recorded as a limitation rather than an authentication failure.

## Project status

I have completed the three sample investigations, captured and organised the available MXToolbox evidence, recorded the comparative classifications, and drafted the employee-awareness guide and final report in Markdown. I am now preparing the formatted Word/PDF deliverables and carrying out the final repository review before publication.

## References

- [Future Interns — Cyber Security Task 2](https://futureinterns.com/)
- [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- [MXToolbox — Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)