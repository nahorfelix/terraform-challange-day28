# Day 28 — Exam Preparation: Practice Exams 1 & 2

Repository for Day 28 of the Terraform Challenge focused on full exam simulation under timed conditions.

## Goal
- Run two full 57-question, 60-minute mock exams
- Log wrong answers with deep reasoning
- Calculate domain-level accuracy
- Do hands-on remediation for weak areas

## Structure
- `day28-exam-prep/docs/EXAM-1-RESULTS.md`
- `day28-exam-prep/docs/EXAM-2-RESULTS.md`
- `day28-exam-prep/docs/WRONG-ANSWER-REVIEW.md`
- `day28-exam-prep/docs/DOMAIN-ACCURACY.md`
- `day28-exam-prep/docs/HANDS-ON-REVISION.md`
- `day28-exam-prep/docs/DAY28-SUBMISSION.md`
- `day28-exam-prep/logs/` (raw timer/session notes)
- `day28-exam-prep/hands-on/` (mini exercises)

## Quick Workflow
1. Start Exam 1 (`docs/EXAM-1-RESULTS.md`)
2. Take 15-minute break
3. Start Exam 2 (`docs/EXAM-2-RESULTS.md`)
4. Fill wrong-answer analysis
5. Fill domain accuracy table
6. Complete hands-on drills for weak domains
7. Finalize `DAY28-SUBMISSION.md`

## Timer commands (PowerShell)
```powershell
# 60-minute exam timer
Measure-Command { Start-Sleep -Seconds 3600 }

# 15-minute break timer
Measure-Command { Start-Sleep -Seconds 900 }
```
