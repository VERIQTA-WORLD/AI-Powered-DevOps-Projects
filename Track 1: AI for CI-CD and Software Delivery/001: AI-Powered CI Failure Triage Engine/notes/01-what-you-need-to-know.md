# 01 — What You Need to Know

Project 001 begins with an important idea:

You do **not** need to be an AI engineer, machine-learning specialist, senior DevOps engineer, or SRE to complete this project.

You do need enough foundational knowledge to understand the system you are about to build.

This note explains that foundation.

Do not rush through it just because there are no major implementation steps yet. The decisions made later in this project—especially around evidence, secret redaction, AI boundaries, validation, fallback behavior, and failure handling—will make much more sense if these fundamentals are clear first.

---

## What You Are Building

Throughout Project 001, you will build an:

> **AI-Powered CI Failure Triage Engine**

The system accepts information from a failed CI job and turns it into a structured engineer-facing triage report.

At a high level:

```text
CI Failure
    ↓
Ingestion
    ↓
Normalization
    ↓
Secret Redaction
    ↓
Deterministic Evidence Extraction
    ↓
Bounded AI Analysis
    ↓
Schema Validation
    ↓
Safety Checks
    ↓
Triage Report
