# Future Interns Cybersecurity Task 2
## Phishing Email Detection & Awareness System

This repository documents the practical work for Future Interns Cybersecurity Internship – Task 2.

## Objective
Analyse a set of email samples for phishing indicators, document the evidence, classify each sample based on observed artefacts, and produce practical security-awareness guidance.

## Project structure
```text
FUTURE_CS_02/
├── README.md
├── analysis/
│   ├── sample-01.md
│   ├── sample-02.md
│   └── sample-03.md
├── evidence/
│   ├── sample-01/
│   ├── sample-02/
│   └── sample-03/
├── awareness/
│   └── employee-awareness-guide.md
└── report/
    └── phishing-detection-awareness-report.md
```

## Workflow
1. Preserve each provided email sample and record its source.
2. Inspect sender, reply-to, return-path, received chain, authentication results (SPF, DKIM, DMARC), subject and message content.
3. Extract URLs and visible link text without opening suspicious links directly.
4. Review domains, sender infrastructure and relevant indicators using safe analysis tools.
5. Record objective evidence, distinguish observations from assumptions, and classify each sample.
6. Capture screenshots or exports in the matching evidence folder.
7. Consolidate findings in the final report and provide awareness recommendations.

## Tools
Use only tools appropriate to the task and follow their current safe-use guidance. Examples may include a text editor, email-header analyser, URL/domain reputation services, DNS lookups and a sandbox where authorised.

## Status
Project structure and documentation templates are prepared. **Sample findings and verdicts remain pending** until the actual email samples and supporting evidence have been analysed. No indicators or conclusions have been fabricated.

## Evidence handling
- Do not upload real passwords, access tokens, personal data or confidential email content.
- Redact personal addresses and identifiers in screenshots where possible.
- Do not click or download from suspicious links on a normal workstation.
- Record tool names, dates, queries and results so the analysis is reproducible.
