# 001 — AI-Powered CI Failure Triage Engine

> Build a production-minded service that turns failed CI pipeline logs into structured, evidence-backed triage reports while protecting secrets, validating AI output, and remaining useful when the AI provider fails.

**Level:** Foundation  
**Track:** AI for CI/CD and Software Delivery  
**Project:** 001 of 100  
**Primary Focus:** CI/CD · Python · AI/LLMs · Log Analysis · Security · Testing · Observability  
**Learning Style:** Guided Build → Failure Investigation → Independent Engineering Challenge

---

## Table of Contents

- [What You Are Building](#what-you-are-building)
- [The Engineering Problem](#the-engineering-problem)
- [Why This Project Matters](#why-this-project-matters)
- [Who Would Use This System](#who-would-use-this-system)
- [What the Finished System Does](#what-the-finished-system-does)
- [What AI Does and Does Not Do](#what-ai-does-and-does-not-do)
- [Architecture Overview](#architecture-overview)
- [How a Failure Moves Through the System](#how-a-failure-moves-through-the-system)
- [What You Will Learn](#what-you-will-learn)
- [Technologies and Engineering Concepts](#technologies-and-engineering-concepts)
- [Prerequisites](#prerequisites)
- [Project Environment](#project-environment)
- [Repository Structure](#repository-structure)
- [How to Complete This Project](#how-to-complete-this-project)
- [Build Milestones](#build-milestones)
- [Testing Strategy](#testing-strategy)
- [AI Evaluation](#ai-evaluation)
- [Security Model](#security-model)
- [Failure Engineering](#failure-engineering)
- [Observability](#observability)
- [Evidence You Will Collect](#evidence-you-will-collect)
- [Final Engineering Challenge](#final-engineering-challenge)
- [Definition of Done](#definition-of-done)
- [What You Should Be Able to Explain](#what-you-should-be-able-to-explain)
- [Portfolio and Resume Outcome](#portfolio-and-resume-outcome)
- [Responsible AI Use](#responsible-ai-use)
- [Common Mistakes to Avoid](#common-mistakes-to-avoid)
- [Using the Solution](#using-the-solution)
- [Cleanup](#cleanup)
- [Where to Start](#where-to-start)

---

# What You Are Building

Imagine this situation.

A CI pipeline fails.

The engineer sees:

```text
Job failed with exit code 1
```

But that message does not explain what actually happened.

The useful evidence may be buried inside hundreds or thousands of lines produced by:

- dependency installation
- compilation
- linting
- unit tests
- integration tests
- container builds
- authentication
- artifact publishing
- deployment tooling
- infrastructure commands
- shell scripts

Some of those logs may also contain information that should never be sent to an external AI service.

Your job is to build a system that turns that noisy failure into something an engineer can investigate.

The completed workflow will resemble:

```text
Failed CI Job
      │
      ▼
Log Ingestion
      │
      ▼
Normalization
      │
      ▼
Secret Redaction
      │
      ▼
Deterministic Evidence Extraction
      │
      ▼
Bounded AI Analysis
      │
      ▼
Structured Output Validation
      │
      ▼
Safety Checks
      │
      ▼
Triage Report
      │
      ▼
Engineer Reviews Evidence
```

This is not an autonomous remediation system.

The AI does **not** receive unrestricted control of the CI environment.

It does **not** execute shell commands.

It does **not** restart workloads.

It does **not** change infrastructure.

It does **not** approve deployments.

It assists with triage.

You remain responsible for building the deterministic controls around it.

---

# The Engineering Problem

CI/CD systems generate large amounts of diagnostic information.

When a pipeline fails, an engineer often needs to determine:

1. Which stage failed?
2. Which command or process failed?
3. What exit code was returned?
4. What errors appeared before the failure?
5. Is the failure related to tests, dependencies, configuration, authentication, infrastructure, networking, or deployment?
6. Which evidence supports that conclusion?
7. Does the log contain sensitive information?
8. What should the engineer inspect next?

An AI model can help interpret complex logs, but introducing an AI model creates another set of engineering problems.

What if the model invents a cause?

What if the logs contain credentials?

What if malicious text inside a log attempts to manipulate the model?

What if the model returns malformed output?

What if the model provider is unavailable?

What if the request times out?

What if the model's recommendation conflicts with the actual evidence?

A useful AI-assisted DevOps system therefore needs much more than a prompt.

That is the system you will build.

---

# Why This Project Matters

AI can generate plausible explanations very easily.

Production engineering requires something stronger:

**evidence.**

Consider this response:

```text
The deployment probably failed because the Kubernetes
cluster did not have enough memory.
```

It sounds reasonable.

But where is the evidence?

Now compare it with:

```text
Failure category:
Dependency installation

Observed evidence:
- npm exited with code 1
- package @example/core@4.2.0 could not be resolved
- failure occurred during dependency installation
- deployment stage was never reached

Likely cause:
A required package version could not be resolved.

Confidence:
High

Recommended next checks:
1. Inspect package.json.
2. Inspect the lockfile.
3. Verify that the requested version exists.
4. Verify package registry availability.

Automatic remediation:
Not permitted.
```

The second output is useful because the conclusion is tied to observable evidence.

That distinction runs through the entire project.

---

# Who Would Use This System

A system like this could support:

- DevOps engineers
- software engineers
- site reliability engineers
- platform engineers
- release engineers
- build engineers
- cloud engineers
- DevSecOps teams
- internal developer platform teams
- engineering support teams

It could eventually be integrated with systems that receive CI/CD failure information from platforms such as GitHub Actions, GitLab CI/CD, Jenkins, or other build systems.

For this Foundation project, however, the priority is understanding the engineering pipeline before adding unnecessary integrations.

---

# What the Finished System Does

Your completed system should be able to:

### 1. Accept CI failure data

The system receives failed CI log content for analysis.

### 2. Normalize the input

Different logs may contain inconsistent formatting, timestamps, whitespace, control characters, or other noise.

Normalization prepares the data for later processing.

### 3. Detect and redact sensitive values

Potential secrets are removed before information crosses the AI trust boundary.

Examples may include:

```text
API keys
access tokens
authorization headers
password-like values
private credentials
connection strings
```

### 4. Extract deterministic evidence

Code examines the failure before the AI model does.

Useful evidence may include:

```text
exit code
failed stage
error lines
exception names
failed tests
dependency errors
HTTP status codes
authentication errors
timeout indicators
```

### 5. Prepare bounded AI context

Only the information required for analysis should be supplied to the model.

### 6. Request structured analysis

The AI analyzes the bounded evidence and returns a defined structure instead of unrestricted prose.

### 7. Validate the response

Model output is treated as untrusted input.

The application verifies that the response matches the expected schema.

### 8. Apply safety checks

Invalid or unsafe responses are rejected rather than blindly displayed or executed.

### 9. Produce a triage report

The final report clearly separates:

```text
Observed Evidence

AI Analysis

Likely Cause

Confidence

Recommended Investigation

Safety / Validation Status
```

### 10. Degrade safely

If the AI provider is unavailable, deterministic evidence should still be available to the engineer.

The system should not become completely useless because an AI dependency failed.

---

# What AI Does and Does Not Do

This distinction is central to the project.

## Deterministic components handle

```text
Log loading
Normalization
Secret redaction
Evidence extraction
Configuration
Schema validation
Safety checks
Permissions
Fallback behavior
Testing
Observability
```

## AI assists with

```text
Failure interpretation
Pattern reasoning
Failure classification
Explanation
Suggested investigation steps
```

## AI does not control

```text
Shell execution
Infrastructure changes
Deployment approval
Credential access
Rollback execution
Resource deletion
Production remediation
```

A strong explanation of your project should sound like this:

> I used AI for bounded failure classification and explanation. Deterministic code handled log ingestion, normalization, secret redaction, evidence extraction, output validation, safety controls, fallback behavior, and acceptance testing.

That is much more meaningful than saying:

> I used AI to analyze logs.

---

# Architecture Overview

The initial system is intentionally understandable.

```text
                    ┌───────────────────────┐
                    │    Failed CI Job      │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │     Log Ingestion     │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │     Normalization     │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │   Secret Redaction    │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │ Evidence Extraction   │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Context Preparation  │
                    └───────────┬───────────┘
                                │
                     TRUST BOUNDARY
                                │
                                ▼
                    ┌───────────────────────┐
                    │     AI Analyzer       │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │  Schema Validation    │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │     Safety Checks     │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │     Triage Report     │
                    └───────────────────────┘
```

You will study this architecture before implementing it.

See:

**[Architecture Overview](architecture/README.md)**

---

# How a Failure Moves Through the System

Suppose a pipeline contains this failure:

```text
npm ERR! code ETARGET
npm ERR! notarget No matching version found for @example/core@4.2.0
Process completed with exit code 1.
```

The raw log should not simply be sent directly to a model.

Instead:

### Stage 1 — Ingestion

The system loads the log.

### Stage 2 — Normalization

Formatting is cleaned and prepared for processing.

### Stage 3 — Redaction

Sensitive values are removed before AI processing.

### Stage 4 — Evidence Extraction

The application may deterministically identify:

```text
exit_code: 1
tool: npm
error_code: ETARGET
failure_stage: dependency_installation
evidence:
  - No matching version found for @example/core@4.2.0
```

### Stage 5 — AI Analysis

The model receives the relevant sanitized context.

### Stage 6 — Validation

The model response must satisfy the expected output contract.

### Stage 7 — Reporting

The engineer receives a structured triage report.

The distinction is important:

**The model helps interpret evidence. It does not create the evidence.**

---

# What You Will Learn

By completing this project, you should understand more than how to call an AI API.

## CI/CD fundamentals

You will learn about:

- CI pipelines
- jobs and stages
- failed commands
- process exit codes
- stdout and stderr
- build logs
- test failures
- dependency failures
- deployment failures

## Log engineering

You will work with:

- raw logs
- normalization
- structured data
- unstructured data
- error extraction
- failure signals
- malformed input

## Python application design

You will practice:

- modules
- packages
- configuration
- separation of responsibilities
- error handling
- APIs
- testing
- reusable components

## AI engineering

You will learn about:

- model requests
- prompts
- bounded context
- structured outputs
- schemas
- output validation
- model failure
- evaluation
- fallback behavior

## Security

You will work with:

- secret redaction
- sensitive data boundaries
- least privilege
- input validation
- prompt injection
- unsafe output
- trust boundaries

## Reliability

You will learn to ask:

- What happens if the model is unavailable?
- What happens if it times out?
- What happens if the output is invalid?
- What happens if the input is malformed?
- Can the useful deterministic parts of the system continue working?

## Observability

You will introduce:

- application logs
- operational metrics
- failure visibility
- latency measurement
- error tracking

## Engineering communication

You will practice explaining:

- architecture
- trade-offs
- security decisions
- failure behavior
- testing
- limitations
- production improvements

---

# Technologies and Engineering Concepts

This project may use:

| Area | Technology / Concept |
| --- | --- |
| Language | Python |
| API | Python API framework |
| AI | LLM provider integration |
| Data Contract | JSON / JSON Schema |
| Testing | Automated Python testing |
| Packaging | `pyproject.toml` |
| Containers | Docker |
| Local Orchestration | Docker Compose |
| CI/CD | CI failure samples and pipeline concepts |
| Security | Secret redaction and trust boundaries |
| AI Safety | Structured output and validation |
| Observability | Logging and metrics |
| Evaluation | AI behavior evaluation |

The project is designed around engineering concepts rather than dependence on one AI vendor.

Where practical, model-specific code should remain isolated behind an interface so that the rest of the system does not depend directly on a single provider.

---

# Prerequisites

This is a **Foundation** project.

You are not expected to be an expert before beginning.

You should be comfortable with basic terminal usage and have some familiarity with:

- files and directories
- Git
- GitHub
- basic Python
- command-line tools
- basic CI/CD concepts

You do **not** need advanced knowledge of:

- machine learning
- Kubernetes
- distributed systems
- advanced SRE
- production AI platforms

The project notes will introduce the concepts you need as they become relevant.

Start with:

**[Project Notes](notes/README.md)**

---

# Project Environment

The project is designed to be reproducible on a local development machine.

You will eventually need tools such as:

```text
Git
Python
A Python package/environment manager
Docker
Docker Compose
An editor or IDE
```

An AI provider may also require credentials when you reach the AI integration stage.

Do not add credentials directly to source code.

Do not commit credentials to Git.

Use the provided:

**[`.env.example`](.env.example)**

for the expected configuration structure.

Environment preparation is covered in:

**[Prepare Your Environment](learn/07-prepare-your-environment.md)**

---

# Repository Structure

```text
001-ai-powered-ci-failure-triage-engine/
│
├── README.md
├── PROJECT-CHECKLIST.md
├── CHANGELOG.md
├── .env.example
├── .gitignore
├── pyproject.toml
├── Makefile
│
├── notes/
├── learn/
├── build/
├── architecture/
│
├── src/
├── api/
├── prompts/
├── schemas/
├── sample-data/
│
├── tests/
├── evaluations/
├── failures/
├── monitoring/
├── scripts/
├── docker/
│
├── evidence/
├── challenge/
├── portfolio/
│
└── solution/
```

Here is what each section is for.

| Path | Purpose |
| --- | --- |
| [`notes/`](notes/) | Learn the concepts required for the project. |
| [`learn/`](learn/) | Understand how those concepts apply to this system. |
| [`build/`](build/) | Build the system through guided milestones. |
| [`architecture/`](architecture/) | Study system design, data flow, boundaries, and decisions. |
| [`src/`](src/) | Main application implementation. |
| [`api/`](api/) | API interface for submitting failures and retrieving triage results. |
| [`prompts/`](prompts/) | Versioned AI instructions and prompt rules. |
| [`schemas/`](schemas/) | Input and output contracts. |
| [`sample-data/`](sample-data/) | Reproducible CI failure logs used during learning and testing. |
| [`tests/`](tests/) | Unit, integration, security, and acceptance tests. |
| [`evaluations/`](evaluations/) | Evaluate AI behavior beyond traditional software tests. |
| [`failures/`](failures/) | Controlled failure scenarios for troubleshooting practice. |
| [`monitoring/`](monitoring/) | Logging, metrics, and operational visibility. |
| [`scripts/`](scripts/) | Reusable setup, test, demo, evaluation, and cleanup commands. |
| [`docker/`](docker/) | Containerization and local runtime configuration. |
| [`evidence/`](evidence/) | Proof that your implementation and tests worked. |
| [`challenge/`](challenge/) | Independent final engineering challenge. |
| [`portfolio/`](portfolio/) | Guidance for explaining and presenting your own work. |
| [`solution/`](solution/) | Reference material to compare after attempting the project yourself. |

---

# How to Complete This Project

Follow the project in order.

## Phase 1 — Discover

Start with this README.

Understand:

- what you are building
- why it exists
- what the finished system should do

## Phase 2 — Learn

Go to:

**[`notes/`](notes/)**

Learn the underlying concepts before being asked to implement them.

## Phase 3 — Understand

Continue to:

**[`learn/`](learn/)**

Study the problem, architecture, data flow, trust boundaries, environment, and project structure.

## Phase 4 — Build

Continue to:

**[`build/`](build/)**

Build the system milestone by milestone.

## Phase 5 — Verify

Run:

**[`tests/`](tests/)**

Do not assume that a successful startup means the system works correctly.

## Phase 6 — Evaluate the AI

Continue to:

**[`evaluations/`](evaluations/)**

Test whether AI behavior is useful, grounded, structured, and safe.

## Phase 7 — Break the System

Continue to:

**[`failures/`](failures/)**

Introduce controlled failures.

Investigate them.

Recover.

Verify recovery.

## Phase 8 — Complete the Engineering Challenge

Continue to:

**[`challenge/`](challenge/)**

At this stage, you receive fewer exact instructions.

You make the engineering decisions.

## Phase 9 — Collect Evidence

Use:

**[`evidence/`](evidence/)**

Capture proof that important behaviors actually work.

## Phase 10 — Prepare Your Portfolio

Finish with:

**[`portfolio/`](portfolio/)**

Learn how to explain what **you actually built**.

---

# Build Milestones

The guided implementation is divided into progressive milestones.

| Milestone | What You Build |
| --- | --- |
| [01](build/01-project-foundation.md) | Project foundation |
| [02](build/02-load-ci-failure-data.md) | CI failure data ingestion |
| [03](build/03-normalize-ci-logs.md) | Log normalization |
| [04](build/04-redact-sensitive-data.md) | Secret redaction |
| [05](build/05-extract-deterministic-evidence.md) | Deterministic evidence extraction |
| [06](build/06-classify-failure-context.md) | Initial failure classification |
| [07](build/07-integrate-the-ai-analyzer.md) | AI analyzer integration |
| [08](build/08-create-structured-triage-output.md) | Structured triage output |
| [09](build/09-validate-model-output.md) | Model output validation |
| [10](build/10-build-the-fallback-path.md) | Non-AI fallback behavior |
| [11](build/11-add-api-interface.md) | API interface |
| [12](build/12-add-observability.md) | Logging and metrics |
| [13](build/13-add-security-controls.md) | Security controls |
| [14](build/14-run-the-complete-workflow.md) | End-to-end workflow |
| [15](build/15-test-the-system.md) | Complete testing |
| [16](build/16-production-hardening.md) | Production-minded improvements |

The early milestones provide more guidance.

Later milestones expect more decisions from you.

---

# Testing Strategy

AI does not remove the need for conventional testing.

It increases it.

This project separates several types of tests.

## Unit Tests

Verify individual deterministic components.

Examples:

- log loading
- normalization
- redaction
- evidence extraction
- classification
- schema validation

See:

**[`tests/unit/`](tests/unit/)**

## Integration Tests

Verify that components work together.

Examples:

```text
Log
 ↓
Redaction
 ↓
Evidence
 ↓
AI
 ↓
Validation
 ↓
Report
```

See:

**[`tests/integration/`](tests/integration/)**

## Security Tests

Verify behaviors such as:

- secrets do not cross the model boundary
- malicious log content does not bypass controls
- unsafe AI output is rejected

See:

**[`tests/security/`](tests/security/)**

## Acceptance Tests

Acceptance tests answer a larger question:

> Does the completed project satisfy its engineering requirements?

See:

**[`tests/acceptance/`](tests/acceptance/)**

---

# AI Evaluation

Traditional tests can tell you whether deterministic code returned an expected value.

AI behavior requires additional evaluation.

You will examine qualities such as:

### Groundedness

Does the analysis remain connected to available evidence?

### Classification quality

Does the system identify the appropriate failure category?

### Structural correctness

Does output satisfy the required schema?

### Safety

Does the system reject unsafe or invalid behavior?

### Fallback behavior

What happens when model analysis cannot be produced?

### Consistency

Does the system remain useful across different examples of similar failures?

Evaluation resources are located in:

**[`evaluations/`](evaluations/)**

---

# Security Model

CI logs can contain sensitive operational information.

For this reason, the model boundary is treated as a trust boundary.

The intended flow is:

```text
Raw CI Log
     │
     │ Trusted Environment
     ▼
Normalization
     │
     ▼
Secret Detection
     │
     ▼
Redaction
     │
     ▼
Evidence Extraction
     │
     ▼
Context Minimization
     │
═════╪══════════════════════
     │ External AI Boundary
     ▼
AI Provider
```

The model should receive only the information required for its task.

You will learn why:

- redaction happens before model submission
- model output is treated as untrusted
- AI does not receive infrastructure credentials
- AI does not execute remediation
- structured output is validated
- sensitive raw evidence remains protected

Study:

**[Trust Boundaries](architecture/trust-boundaries.md)**

and:

**[Security and Trust Boundaries](notes/14-security-and-trust-boundaries.md)**

---

# Failure Engineering

You are going to intentionally break the system.

That is part of the project.

Failure exercises include:

| Scenario | What You Investigate |
| --- | --- |
| [Invalid AI Response](failures/01-invalid-ai-response.md) | Model returns data that violates the contract. |
| [Model API Unavailable](failures/02-model-api-unavailable.md) | External AI dependency cannot be reached. |
| [Secret Leak Attempt](failures/03-secret-leak-attempt.md) | Sensitive values appear in CI input. |
| [Malformed CI Log](failures/04-malformed-ci-log.md) | Input is incomplete or malformed. |
| [Model Timeout](failures/05-model-timeout.md) | AI analysis exceeds its allowed time. |
| [Prompt Injection Attempt](failures/06-prompt-injection-attempt.md) | Log content contains instructions targeting the model. |
| [False Root Cause](failures/07-false-root-cause.md) | AI analysis conflicts with available evidence. |

For every exercise, ask:

```text
What failed?

What evidence tells you that?

What should you inspect?

What is your hypothesis?

How will you test it?

How will you recover?

How will you verify recovery?

How could you prevent recurrence?
```

Do not consider a failure resolved merely because an error disappeared.

**Recovery must be verified.**

---

# Observability

A triage system that cannot explain its own operational behavior becomes another system engineers need to troubleshoot blindly.

You will introduce visibility into areas such as:

```text
requests processed
analysis success
analysis failure
redaction events
validation failures
fallback usage
model latency
application errors
```

Operational documentation lives in:

**[`monitoring/`](monitoring/)**

The goal is not to build a huge observability platform inside a Foundation project.

The goal is to understand what you would need to observe if this service were running for real users.

---

# Evidence You Will Collect

Do not fill your GitHub repository with random screenshots.

Collect evidence that proves specific engineering behavior.

Your evidence should eventually demonstrate examples such as:

### Evidence 01 — Application starts successfully

Show that the system can be launched in the documented environment.

### Evidence 02 — Secret redaction works

Show that a sensitive value entered the pipeline but did not reach AI-bound context.

### Evidence 03 — Deterministic evidence is extracted

Show that the application identifies useful facts before model analysis.

### Evidence 04 — Valid triage succeeds

Show a complete evidence-backed triage result.

### Evidence 05 — Invalid model output is rejected

Prove that malformed AI output cannot silently pass validation.

### Evidence 06 — AI outage does not destroy the entire workflow

Show the fallback result.

### Evidence 07 — Prompt injection is handled

Demonstrate the expected behavior against malicious instructions embedded in log content.

### Evidence 08 — Automated tests pass

Capture the final test result.

### Evidence 09 — Failure recovery is verified

Show both the failure and the verified recovered state.

Use:

**[`evidence/EVIDENCE-CHECKLIST.md`](evidence/EVIDENCE-CHECKLIST.md)**

to track required evidence.

---

# Final Engineering Challenge

The guided build teaches you how the system works.

The final challenge asks whether you can engineer it.

Your organization now processes approximately:

```text
5,000 CI jobs per day
```

New requirements arrive.

### Security

Raw CI logs cannot leave the trusted environment.

### Performance

Developers expect triage results within 30 seconds.

### Reliability

The external model provider occasionally becomes unavailable.

### Safety

AI-generated recommendations cannot directly execute remediation actions.

### Auditability

The organization must be able to determine:

- what evidence was extracted
- what information was sent for AI analysis
- what the model returned
- whether validation succeeded
- whether fallback behavior was used

Your task is to review the system you built and decide what needs to change.

You will:

1. review the architecture
2. identify weaknesses
3. document your engineering decisions
4. modify the implementation
5. test the new behavior
6. simulate relevant failures
7. verify recovery
8. collect evidence
9. explain your final architecture

Start here only after completing the guided project:

**[Final Engineering Challenge](challenge/README.md)**

There will not be an exact command for every decision.

That is intentional.

---

# Definition of Done

Do not mark the project complete just because the happy path works.

Your project is complete when you can demonstrate that:

- [ ] You understand the engineering problem.
- [ ] Your development environment is reproducible.
- [ ] CI logs can be loaded successfully.
- [ ] Logs are normalized.
- [ ] Sensitive values are redacted before AI processing.
- [ ] Deterministic evidence is extracted.
- [ ] AI analysis receives bounded context.
- [ ] AI output follows a defined contract.
- [ ] Invalid model output is rejected.
- [ ] The system has useful fallback behavior.
- [ ] AI cannot execute remediation actions.
- [ ] Unit tests pass.
- [ ] Integration tests pass.
- [ ] Security tests pass.
- [ ] Acceptance tests pass.
- [ ] AI evaluations have been completed.
- [ ] Controlled failure exercises have been completed.
- [ ] Recovery has been verified.
- [ ] Important operational behavior is observable.
- [ ] Required evidence has been collected.
- [ ] The final engineering challenge has been completed.
- [ ] Your architecture decisions are documented.
- [ ] You can explain the system without reading from the guide.
- [ ] Your portfolio description reflects what you actually implemented.

You can also track your progress using:

**[PROJECT-CHECKLIST.md](PROJECT-CHECKLIST.md)**

---

# What You Should Be Able to Explain

When you finish this project, you should be able to answer questions such as:

## The problem

- Why is CI failure triage difficult?
- Why are raw logs not enough?
- What makes an AI-assisted triage system useful?

## Architecture

- What happens from log ingestion to final report?
- Why are components separated?
- Where is the AI trust boundary?
- What happens when the model is unavailable?

## AI

- What does the model actually do?
- What does deterministic code do?
- Why is AI output untrusted?
- Why use structured output?
- How do you evaluate model behavior?

## Security

- Why redact logs before AI analysis?
- What information should never reach the model?
- How could log content be used for prompt injection?
- Why is automatic remediation prohibited in this project?

## Reliability

- What happens on timeout?
- What happens when output is malformed?
- What is the fallback path?
- How do you verify recovery?

## Production

- What would need to change at higher scale?
- How would you reduce latency?
- How would you control AI cost?
- How would you make the system multi-tenant?
- How would requirements change in a regulated organization?
- What additional monitoring would you add?

These questions are not separate from the project.

Being able to answer them is part of completing it.

---

# Portfolio and Resume Outcome

This project is designed to become something you can discuss professionally.

But do not copy a description for work you did not perform.

Your final project summary should reflect **your implementation**.

A weak description would be:

```text
Built an AI application that analyzes CI logs.
```

A stronger description could explain that you built a system that:

- ingests failed CI logs
- normalizes input
- redacts sensitive information
- extracts deterministic evidence
- performs bounded AI-assisted analysis
- validates structured model responses
- handles provider failures
- tests adversarial conditions
- produces auditable triage results

Your own architecture, modifications, testing, evidence, and final challenge should determine how you describe the project.

Use:

**[`portfolio/`](portfolio/)**

when you reach this stage.

---

# Responsible AI Use

You are welcome to use AI tools while learning and building this project.

But there is an important rule:

> Do not keep code, commands, architecture decisions, or explanations that you cannot understand and defend.

If AI helps you:

- understand Python
- explain an error
- generate a test
- review code
- explore an architecture
- debug a failure
- improve documentation

use it as a learning tool.

Then verify the result.

When presenting this project, be able to distinguish between:

```text
What you designed

What you implemented

What you tested

What AI helped you with

What the runtime AI component does
```

Those are not the same thing.

---

# Common Mistakes to Avoid

## Sending raw logs directly to AI

This bypasses one of the main engineering lessons of the project.

Redact and minimize first.

## Trusting plausible explanations

A confident answer is not evidence.

Always ask what observable facts support the conclusion.

## Mixing evidence and recommendations

Keep facts separate from interpretation.

## Skipping validation

Model output is input from an external dependency.

Validate it.

## Building only the happy path

Test unavailable providers, malformed input, invalid output, timeouts, secret exposure, and adversarial content.

## Allowing automatic remediation

This project is a triage engine, not an autonomous production operator.

## Ignoring fallback behavior

A useful engineering tool should have defined behavior when an optional intelligent dependency fails.

## Copying the solution

You lose most of the value of the project if you skip the investigation and implementation process.

## Collecting meaningless screenshots

Capture evidence that proves requirements and engineering behavior.

## Finishing without understanding

The final goal is not:

```text
"It ran."
```

The goal is:

```text
"I understand why it works,
how it fails,
how it is protected,
how I tested it,
and what I would change in production."
```

---

# Using the Solution

The [`solution/`](solution/) directory exists for comparison and learning.

Do **not** start there.

Try the project first.

When you become stuck:

1. investigate the problem
2. inspect the evidence
3. review the relevant notes
4. review the build guidance
5. form a hypothesis
6. test it

Then use the solution when necessary to compare approaches or understand an alternative implementation.

A reference implementation is not automatically the only correct architecture.

Engineering frequently involves trade-offs.

You should eventually be able to explain yours.

---

# Cleanup

Do not leave unnecessary containers, temporary files, test services, credentials, or other resources running after completing exercises.

Use the project cleanup guidance and:

```bash
./scripts/cleanup.sh
```

when appropriate.

Before deleting anything, understand what the cleanup process will remove.

Never run destructive commands you do not understand.

---

# Where to Start

If this is your first time opening the project, do not start inside `src/`.

Do not start with the AI prompt.

Do not start with the solution.

Start here:

### Step 1

Read:

**[Project Notes](notes/README.md)**

### Step 2

Continue to:

**[Understand the Problem](learn/01-understand-the-problem.md)**

### Step 3

Follow the learning sequence until you reach:

**[Readiness Check](learn/09-readiness-check.md)**

### Step 4

Begin building:

**[Build 01 — Project Foundation](build/01-project-foundation.md)**

---

## Your Learning Path

```text
README
   │
   ▼
NOTES
Learn what you need
   │
   ▼
LEARN
Understand this system
   │
   ▼
BUILD
Create it step by step
   │
   ▼
TEST
Prove deterministic behavior
   │
   ▼
EVALUATE
Test AI behavior
   │
   ▼
BREAK
Introduce controlled failures
   │
   ▼
INVESTIGATE
Use evidence
   │
   ▼
RECOVER
Fix and verify
   │
   ▼
CHALLENGE
Make your own engineering decisions
   │
   ▼
EVIDENCE
Prove what you built
   │
   ▼
PORTFOLIO
Explain it professionally
```

---

## One Final Rule

Do not measure your progress by how quickly you reach the end of this repository.

Measure it by what you can explain without the repository open.

By the end of Project 001, you should not simply be able to say:

> I built an AI-powered CI failure triage engine.

You should be able to explain:

**what problem it solves, how data moves through it, what evidence is deterministic, where AI is used, where AI is deliberately not trusted, how secrets are protected, how model output is validated, what happens when dependencies fail, how you tested the system, how you proved recovery, and what you would change before operating it in production.**

That is the project.
