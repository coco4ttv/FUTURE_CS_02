# Future Interns Cyber Security Internship - Task 2
## Phishing Email Detection & Awareness System

I completed this project as part of the Future Interns Cyber Security Internship. I analysed three unsolicited email samples from the public [cw-l/message-corpus](https://github.com/cw-l/message-corpus) dataset. I examined the sender details, message content, embedded links, MIME structure and available email-authentication results.

The project brings together the individual investigations, supporting evidence, an employee awareness guide, a final written report and a dashboard concept.

## Findings

| Sample | Email theme | Assessment |
|---|---|---|
| 01 | Google-style cloud-account and device-security alert | **Phishing** |
| 02 | SiriusXM payment failure and subscription renewal | **Phishing** |
| 03 | Type 2 diabetes treatment promotion | **Suspicious** |

The reasoning and supporting observations for each classification are documented in the individual investigation files:

- [Sample 01 - Google / cloud-account alert](analysis/sample-01.md)
- [Sample 02 - SiriusXM payment-failure email](analysis/sample-02.md)
- [Sample 03 - Diabetes-treatment promotion](analysis/sample-03.md)

Across the three header reviews, SPF pass was shown for all three samples, DKIM pass was shown for Samples 02 and 03, and no DMARC result was shown. A missing authentication result is recorded as unavailable, not as a failed check.

## Project deliverables

| Deliverable | File |
|---|---|
| Final investigation report (PDF) | [Phishing Detection & Awareness Report](report/phishing-detection-awareness-report.pdf) |
| Report source (Markdown) | [phishing-detection-awareness-report.md](report/phishing-detection-awareness-report.md) |
| Phishing triage dashboard concept (PDF) | [Phishing triage dashboard.pdf](report/Phishing%20triage%20dashboard.pdf) |
| Employee awareness guide | [employee-awareness-guide.md](awareness/employee-awareness-guide.md) |
| Evidence register | [evidence-log.md](evidence/evidence-log.md) |

The dashboard is a static design concept created in Canva to show how an internal IT and Security team could organise email triage findings. It is not a live email-monitoring or automated detection system.

## Investigation approach and tools

I reviewed each source message in raw-text form. I recorded the available sender, subject and date fields, examined the main message content, compared the claimed organisation with the sender domain, inspected HTML link destinations without opening them, and reviewed the supplied MIME structure.

I used [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx) to review the available headers for all three samples. I also attempted to use Google Admin Toolbox Messageheader, but it did not produce a usable analysis from the supplied corpus headers. I therefore used MXToolbox consistently for the three header assessments and have not attributed any results to Google's tool.

**Tools and resources**
- [cw-l/message-corpus](https://github.com/cw-l/message-corpus) - source email samples
- [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx) - header analysis
- Browser-based raw email and HTML-source inspection
- Markdown and GitHub - investigation notes, evidence register and project documentation
- Canva - static phishing triage dashboard concept

## Repository structure

```text
FUTURE_CS_02/
├── README.md
├── analysis/
│   ├── sample-01.md
│   ├── sample-02.md
│   └── sample-03.md
├── awareness/
│   └── employee-awareness-guide.md
├── evidence/
│   ├── evidence-log.md
│   ├── sample-01/              # 4 screenshots
│   ├── sample-02/              # 12 screenshots
│   └── sample-03/              # 6 screenshots
└── report/
    ├── Phishing triage dashboard.pdf
    ├── phishing-detection-awareness-report.md
    └── phishing-detection-awareness-report.pdf
```

## Evidence, scope and limitations

I saved 22 supporting screenshots across the three sample folders and listed them in the [evidence register](evidence/evidence-log.md). The analysis files link to the original corpus records rather than republishing the original `.eml` messages.

I kept suspicious destinations in defanged form and reviewed them statically; I did not open the links. I did not claim that credentials were stolen, payments were lost or malware was executed.

The dataset does not preserve the complete original mail-routing path, including full `Received` and `Return-Path` information. Authentication results are recorded only where they are shown in the supplied headers or MXToolbox output. The absence of a field is recorded as a limitation rather than an authentication failure.

## Project status

The three sample investigations, supporting evidence, comparative assessment, employee awareness guide, final report and dashboard concept are included in this repository.

## References

- [Future Interns - Cyber Security Internship](https://futureinterns.com/)
- [cw-l/message-corpus](https://github.com/cw-l/message-corpus)
- [MXToolbox - Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
