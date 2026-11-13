# Phishing Email Detection & Awareness System
## Future Interns Cybersecurity Internship – Task 2

**Author:**  
**Date:**  
**Repository:** https://github.com/coco4ttv/FUTURE_CS_02

## 1. Executive summary
This report documents the methodology and results of a review of three email samples for phishing indicators. The analysis will assess email authentication, sender identity, routing information, message content, URLs and other observable artefacts.

**Current status:** This is a structured report draft. Sample-specific findings and verdicts are pending examination of the supplied email samples. No results are assumed.

## 2. Objectives
- Identify suspicious email characteristics and phishing indicators.
- Review email headers and authentication outcomes.
- Examine links, domains and other indicators safely.
- Classify each sample using documented evidence.
- Provide practical recommendations to improve awareness and reporting.

## 3. Methodology
For each sample:
1. Record its filename and preserve the original.
2. Review From, Reply-To, Return-Path, Received and authentication-result headers.
3. Assess SPF, DKIM and DMARC outcomes, including alignment where available.
4. Inspect the body for impersonation, urgency, unusual requests and link mismatches.
5. Extract URLs and assess domains using safe reputation and DNS resources.
6. Record evidence, limitations and confidence.
7. Assign a verdict only where the evidence supports it.

## 4. Tools and evidence
Record the tool, purpose, date used, query and result for each check. Store redacted screenshots or exports in the corresponding `evidence/` folder. Do not upload credentials, tokens or unnecessary personal information.

## 5. Sample findings
### Sample 01
See [analysis/sample-01.md](../analysis/sample-01.md). Classification: **Pending**.

### Sample 02
See [analysis/sample-02.md](../analysis/sample-02.md). Classification: **Pending**.

### Sample 03
See [analysis/sample-03.md](../analysis/sample-03.md). Classification: **Pending**.

## 6. Comparative assessment
Complete this table after all three samples have been analysed.

| Criterion | Sample 01 | Sample 02 | Sample 03 |
|---|---|---|---|
| SPF / DKIM / DMARC | Pending | Pending | Pending |
| Sender alignment | Pending | Pending | Pending |
| Suspicious URLs | Pending | Pending | Pending |
| Social-engineering indicators | Pending | Pending | Pending |
| Final classification | Pending | Pending | Pending |
| Confidence | Pending | Pending | Pending |

## 7. Recommendations
- Provide a simple reporting route for suspected phishing.
- Use MFA and never share one-time codes.
- Verify payment or account-change requests out of band.
- Keep email filtering, endpoint protection and patching current.
- Deliver recurring awareness exercises and reinforce prompt reporting.
- Review and update detections based on confirmed incidents.

## 8. Conclusion
The project provides a repeatable framework for examining suspicious emails and communicating risks to users. The final conclusion must be updated after the three supplied samples have been examined and the evidence table completed.

## 9. Appendix
Add evidence filenames, hashes, relevant redacted header excerpts and tool outputs here.
