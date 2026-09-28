# Project 001 Completion Checklist

## AI-Powered CI Failure Triage Engine

Use this checklist to track your progress through the complete project.

This is not only a list of files to open.

Each checkbox represents something you should **read, understand, build, test, investigate, verify, or explain** before considering the project complete.

Do not mark an item complete simply because you opened the corresponding file.

Mark it complete when you can demonstrate the expected result and understand what you did.

---

## How to Use This Checklist

Work through the project in this order:

```text
Learn
  ↓
Understand
  ↓
Build
  ↓
Test
  ↓
Evaluate
  ↓
Break
  ↓
Investigate
  ↓
Recover
  ↓
Challenge
  ↓
Prove
  ↓
Explain
```

You do not need to finish the entire project in one session.

Return to this file whenever you want to see:

- what you have completed
- what remains
- which phase comes next
- what evidence you still need
- whether you are actually ready to call the project complete

---

# Phase 0 — Understand the Goal

Before working through the technical material, make sure you understand what you are building.

- [ ] I have read the main [`README.md`](README.md).
- [ ] I understand the CI failure triage problem this project addresses.
- [ ] I understand why raw CI logs can be difficult to investigate.
- [ ] I understand why sending raw CI logs directly to an AI model is unsafe.
- [ ] I understand that this project uses AI for bounded analysis, not unrestricted automation.
- [ ] I understand that deterministic evidence and AI interpretation are different.
- [ ] I understand that model output must be validated.
- [ ] I understand that the AI provider is an external dependency that can fail.
- [ ] I understand that the completed system must remain useful when AI analysis is unavailable.
- [ ] I understand that AI is not permitted to execute remediation commands in this project.
- [ ] I understand the overall learning path before beginning implementation.

### Phase 0 Checkpoint

Before continuing, you should be able to explain:

> I am building a CI failure triage service that ingests failed pipeline logs, normalizes them, redacts sensitive information, extracts deterministic evidence, uses AI for bounded failure analysis, validates the model response, and produces a structured report for an engineer.

- [ ] I can explain that description in my own words.

---

# Phase 1 — Learn the Foundations

Start with:

**[`notes/README.md`](notes/README.md)**

The notes teach the concepts you will use later.

Do not rush through this section.

## Required Notes

- [ ] [`01-what-you-need-to-know.md`](notes/01-what-you-need-to-know.md)
- [ ] [`02-ci-cd-failure-fundamentals.md`](notes/02-ci-cd-failure-fundamentals.md)
- [ ] [`03-understanding-ci-logs.md`](notes/03-understanding-ci-logs.md)
- [ ] [`04-exit-codes-stdout-and-stderr.md`](notes/04-exit-codes-stdout-and-stderr.md)
- [ ] [`05-structured-vs-unstructured-logs.md`](notes/05-structured-vs-unstructured-logs.md)
- [ ] [`06-secret-redaction.md`](notes/06-secret-redaction.md)
- [ ] [`07-evidence-vs-ai-analysis.md`](notes/07-evidence-vs-ai-analysis.md)
- [ ] [`08-llms-in-operational-systems.md`](notes/08-llms-in-operational-systems.md)
- [ ] [`09-structured-ai-output.md`](notes/09-structured-ai-output.md)
- [ ] [`10-json-schema-validation.md`](notes/10-json-schema-validation.md)
- [ ] [`11-model-failure-and-fallbacks.md`](notes/11-model-failure-and-fallbacks.md)
- [ ] [`12-prompt-injection-in-operational-data.md`](notes/12-prompt-injection-in-operational-data.md)
- [ ] [`13-observability-for-ai-services.md`](notes/13-observability-for-ai-services.md)
- [ ] [`14-security-and-trust-boundaries.md`](notes/14-security-and-trust-boundaries.md)
- [ ] [`15-production-design-considerations.md`](notes/15-production-design-considerations.md)
- [ ] [`16-commands-and-reference.md`](notes/16-commands-and-reference.md)

## Knowledge Check

Before leaving this phase:

- [ ] I can explain what a CI pipeline is.
- [ ] I understand jobs, stages, steps, and commands.
- [ ] I understand what a process exit code represents.
- [ ] I understand the difference between stdout and stderr.
- [ ] I can identify useful failure information inside a CI log.
- [ ] I understand structured and unstructured logs.
- [ ] I understand why CI logs may contain sensitive information.
- [ ] I understand secret redaction.
- [ ] I understand why redaction must occur before model submission.
- [ ] I understand the difference between observed evidence and AI-generated interpretation.
- [ ] I understand why AI output should not automatically be trusted.
- [ ] I understand structured model output.
- [ ] I understand why a schema is useful.
- [ ] I understand what happens when an AI provider becomes unavailable.
- [ ] I understand the basic prompt-injection risk presented by untrusted operational data.
- [ ] I understand why an AI-powered service still requires observability.
- [ ] I understand what a trust boundary represents.
- [ ] I understand the difference between a working demonstration and a production-ready system.

### Phase 1 Checkpoint

- [ ] I can explain the major concepts without simply repeating definitions from the notes.

---

# Phase 2 — Understand the Project

Continue with:

**[`learn/README.md`](learn/README.md)**

This phase connects the concepts you learned to the system you are about to build.

## Project Preparation

- [ ] [`01-understand-the-problem.md`](learn/01-understand-the-problem.md)
- [ ] [`02-meet-the-system.md`](learn/02-meet-the-system.md)
- [ ] [`03-follow-a-failure-through-the-system.md`](learn/03-follow-a-failure-through-the-system.md)
- [ ] [`04-understand-the-architecture.md`](learn/04-understand-the-architecture.md)
- [ ] [`05-understand-the-data-flow.md`](learn/05-understand-the-data-flow.md)
- [ ] [`06-understand-the-trust-boundaries.md`](learn/06-understand-the-trust-boundaries.md)
- [ ] [`07-prepare-your-environment.md`](learn/07-prepare-your-environment.md)
- [ ] [`08-project-files-explained.md`](learn/08-project-files-explained.md)
- [ ] [`09-readiness-check.md`](learn/09-readiness-check.md)

## Architecture Understanding

Before building:

- [ ] I can describe how a failed CI log enters the system.
- [ ] I can explain what normalization does.
- [ ] I can explain where secret redaction occurs.
- [ ] I can explain why deterministic evidence extraction happens before AI analysis.
- [ ] I can identify where data crosses the AI trust boundary.
- [ ] I can explain what information should reach the model.
- [ ] I can explain what information should not reach the model.
- [ ] I understand how model output returns to the application.
- [ ] I understand why validation happens after AI analysis.
- [ ] I understand how the final triage report is produced.
- [ ] I understand the fallback path.

## Environment Readiness

- [ ] Git is available.
- [ ] Python is available.
- [ ] My Python environment is ready.
- [ ] Docker is available where required.
- [ ] Docker Compose is available where required.
- [ ] I understand the purpose of [`.env.example`](.env.example).
- [ ] I know that real secrets must not be committed.
- [ ] I have run the environment checks described in the project.
- [ ] I have completed the readiness check.

### Phase 2 Checkpoint

You should be able to draw this flow without copying it:

```text
CI Failure
    ↓
Ingestion
    ↓
Normalization
    ↓
Secret Redaction
    ↓
Evidence Extraction
    ↓
Bounded AI Analysis
    ↓
Schema Validation
    ↓
Safety Checks
    ↓
Triage Report
```

- [ ] I can explain every stage in that flow.

---

# Phase 3 — Review the Architecture

Use:

**[`architecture/README.md`](architecture/README.md)**

You are not expected to memorize diagrams.

You are expected to understand the reasoning behind them.

## Architecture Files

- [ ] [`system-architecture.md`](architecture/system-architecture.md)
- [ ] [`data-flow.md`](architecture/data-flow.md)
- [ ] [`component-responsibilities.md`](architecture/component-responsibilities.md)
- [ ] [`trust-boundaries.md`](architecture/trust-boundaries.md)
- [ ] [`failure-flow.md`](architecture/failure-flow.md)
- [ ] [`ai-boundary.md`](architecture/ai-boundary.md)
- [ ] [`decisions.md`](architecture/decisions.md)

## Architecture Check

- [ ] I can identify the major components.
- [ ] I understand each component's responsibility.
- [ ] I understand how data moves between components.
- [ ] I understand where sensitive information exists.
- [ ] I understand where trust boundaries exist.
- [ ] I understand where AI enters the workflow.
- [ ] I understand which components remain deterministic.
- [ ] I understand how failures move through the system.
- [ ] I understand the major architectural decisions.
- [ ] I can explain why the AI component is isolated from direct remediation.

---

# Phase 4 — Build the System

Start with:

**[`build/README.md`](build/README.md)**

Complete the build milestones in order.

Do not skip verification checkpoints just because the next command appears to work.

---

## Milestone 01 — Project Foundation

Read:

**[`build/01-project-foundation.md`](build/01-project-foundation.md)**

Complete:

- [ ] Project environment created.
- [ ] Python package structure created.
- [ ] Required dependencies installed.
- [ ] Configuration structure established.
- [ ] Environment variables handled safely.
- [ ] Basic application entry point works.
- [ ] Initial project verification passes.

---

## Milestone 02 — Load CI Failure Data

Read:

**[`build/02-load-ci-failure-data.md`](build/02-load-ci-failure-data.md)**

Complete:

- [ ] CI log loader implemented.
- [ ] Valid log files can be loaded.
- [ ] Missing files are handled.
- [ ] Empty input is handled.
- [ ] Unsupported or malformed input is handled appropriately.
- [ ] Loader behavior is verified.

---

## Milestone 03 — Normalize CI Logs

Read:

**[`build/03-normalize-ci-logs.md`](build/03-normalize-ci-logs.md)**

Complete:

- [ ] Normalizer implemented.
- [ ] Input formatting is handled consistently.
- [ ] Unnecessary noise is handled without destroying useful evidence.
- [ ] Normalization preserves important error information.
- [ ] Normalization behavior is tested.

---

## Milestone 04 — Redact Sensitive Data

Read:

**[`build/04-redact-sensitive-data.md`](build/04-redact-sensitive-data.md)**

Complete:

- [ ] Redaction component implemented.
- [ ] API-key-like values are detected where supported.
- [ ] Token-like values are detected where supported.
- [ ] Credential-like values are detected where supported.
- [ ] Redacted values do not appear in AI-bound context.
- [ ] Original sensitive values are not exposed through application logs.
- [ ] Redaction tests pass.

### Security Gate

Do not continue to external AI integration until this gate passes.

- [ ] I have demonstrated that the project's supported sensitive values are redacted before AI submission.

---

## Milestone 05 — Extract Deterministic Evidence

Read:

**[`build/05-extract-deterministic-evidence.md`](build/05-extract-deterministic-evidence.md)**

Complete:

- [ ] Evidence extractor implemented.
- [ ] Exit codes can be captured where present.
- [ ] Error indicators can be identified.
- [ ] Relevant failure lines can be extracted.
- [ ] Failure-stage information can be preserved where available.
- [ ] Deterministic evidence is stored separately from AI interpretation.
- [ ] Evidence extraction tests pass.

### Evidence Gate

- [ ] I can show what the application knows **before** AI analysis begins.

---

## Milestone 06 — Classify Failure Context

Read:

**[`build/06-classify-failure-context.md`](build/06-classify-failure-context.md)**

Complete:

- [ ] Initial classification component implemented.
- [ ] Supported failure categories are defined.
- [ ] Classification does not overwrite raw evidence.
- [ ] Unknown or ambiguous failures are handled.
- [ ] Classification behavior is tested.

---

## Milestone 07 — Integrate the AI Analyzer

Read:

**[`build/07-integrate-the-ai-analyzer.md`](build/07-integrate-the-ai-analyzer.md)**

Complete:

- [ ] AI client implemented.
- [ ] AI analyzer implemented.
- [ ] Credentials are loaded through configuration.
- [ ] Credentials are not committed to the repository.
- [ ] Only sanitized context reaches the AI layer.
- [ ] Prompt instructions are versioned in [`prompts/`](prompts/).
- [ ] Timeouts are handled.
- [ ] Provider errors are handled.
- [ ] AI integration can be tested safely.

---

# Phase 5 — Define and Validate the AI Contract

## Milestone 08 — Create Structured Triage Output

Read:

**[`build/08-create-structured-triage-output.md`](build/08-create-structured-triage-output.md)**

Complete:

- [ ] Triage output structure defined.
- [ ] Input schema defined.
- [ ] Output schema defined.
- [ ] Observed evidence has a dedicated field.
- [ ] AI interpretation has a dedicated field.
- [ ] Likely cause has a defined representation.
- [ ] Confidence is represented consistently.
- [ ] Recommended investigation steps are structured.
- [ ] Safety or validation status is represented.

Review:

- [ ] [`schemas/triage-input.schema.json`](schemas/triage-input.schema.json)
- [ ] [`schemas/triage-output.schema.json`](schemas/triage-output.schema.json)

---

## Milestone 09 — Validate Model Output

Read:

**[`build/09-validate-model-output.md`](build/09-validate-model-output.md)**

Complete:

- [ ] Output validator implemented.
- [ ] Valid model responses are accepted.
- [ ] Missing required fields are rejected.
- [ ] Invalid field types are rejected.
- [ ] Malformed structured output is rejected.
- [ ] Safety checks run before output is trusted.
- [ ] Validation failures are observable.
- [ ] Validation tests pass.

### Validation Gate

- [ ] I have demonstrated that model output cannot bypass the application's expected contract simply because it came from the AI provider.

---

# Phase 6 — Build for Failure

## Milestone 10 — Build the Fallback Path

Read:

**[`build/10-build-the-fallback-path.md`](build/10-build-the-fallback-path.md)**

Complete:

- [ ] Fallback component implemented.
- [ ] Model-unavailable behavior is defined.
- [ ] Timeout behavior is defined.
- [ ] Provider-error behavior is defined.
- [ ] Deterministic evidence remains available during AI failure.
- [ ] The system clearly indicates when AI analysis was unavailable.
- [ ] Fallback behavior is tested.

### Reliability Gate

- [ ] I have demonstrated that losing the AI provider does not erase already extracted deterministic evidence.

---

# Phase 7 — Add the Service Interface

## Milestone 11 — Add the API Interface

Read:

**[`build/11-add-api-interface.md`](build/11-add-api-interface.md)**

Review:

**[`api/README.md`](api/README.md)**

Complete:

- [ ] API application created.
- [ ] Request model defined.
- [ ] Response model defined.
- [ ] Triage route created.
- [ ] Invalid requests are handled.
- [ ] Application errors are handled safely.
- [ ] API behavior is tested.
- [ ] The API does not expose secrets through error responses.

---

# Phase 8 — Add Operational Visibility

## Milestone 12 — Add Observability

Read:

**[`build/12-add-observability.md`](build/12-add-observability.md)**

Review:

**[`monitoring/README.md`](monitoring/README.md)**

Complete:

- [ ] Application logging configured.
- [ ] Useful operational events are logged.
- [ ] Sensitive values are not intentionally logged.
- [ ] Request or analysis success can be observed.
- [ ] Analysis failure can be observed.
- [ ] Validation failures can be observed.
- [ ] Fallback usage can be observed.
- [ ] Model latency can be measured where supported.
- [ ] Error behavior is observable.

Review:

- [ ] [`monitoring/metrics.md`](monitoring/metrics.md)
- [ ] [`monitoring/logging.md`](monitoring/logging.md)
- [ ] [`monitoring/alerts.md`](monitoring/alerts.md)

---

# Phase 9 — Add Security Controls

## Milestone 13 — Add Security Controls

Read:

**[`build/13-add-security-controls.md`](build/13-add-security-controls.md)**

Complete:

- [ ] Secret redaction is enforced before model submission.
- [ ] Input is treated as untrusted.
- [ ] AI output is treated as untrusted.
- [ ] Prompt-injection scenarios are considered.
- [ ] AI does not receive infrastructure credentials.
- [ ] AI cannot directly execute shell commands.
- [ ] AI cannot modify infrastructure.
- [ ] AI cannot approve deployments.
- [ ] AI cannot perform remediation.
- [ ] Error messages avoid unnecessary sensitive information.
- [ ] Security tests pass.

### Security Gate

- [ ] I can identify the major trust boundaries in the application.
- [ ] I can explain why the AI provider sits outside the trusted deterministic core.
- [ ] I can explain why model output must pass through validation and safety checks.

---

# Phase 10 — Run the Complete Workflow

## Milestone 14 — End-to-End Workflow

Read:

**[`build/14-run-the-complete-workflow.md`](build/14-run-the-complete-workflow.md)**

Demonstrate:

```text
Failed CI Log
      ↓
Load
      ↓
Normalize
      ↓
Redact
      ↓
Extract Evidence
      ↓
Classify Context
      ↓
AI Analysis
      ↓
Validate
      ↓
Safety Checks
      ↓
Triage Report
```

Complete:

- [ ] Dependency-install failure processed.
- [ ] Unit-test failure processed.
- [ ] Lint failure processed.
- [ ] Build failure processed.
- [ ] Docker-build failure processed.
- [ ] Authentication failure processed.
- [ ] Deployment failure processed.
- [ ] Timeout failure processed.
- [ ] Sensitive sample processed safely.
- [ ] Malformed input handled safely.
- [ ] Final report separates evidence from interpretation.

---

# Phase 11 — Test the System

## Milestone 15 — Complete Testing

Read:

**[`build/15-test-the-system.md`](build/15-test-the-system.md)**

Then review:

**[`tests/README.md`](tests/README.md)**

---

## Unit Tests

- [ ] `test_loader.py`
- [ ] `test_normalizer.py`
- [ ] `test_redactor.py`
- [ ] `test_evidence_extractor.py`
- [ ] `test_classifier.py`
- [ ] `test_output_validator.py`

- [ ] All required unit tests pass.

---

## Integration Tests

- [ ] `test_triage_pipeline.py`
- [ ] `test_ai_fallback.py`
- [ ] `test_api.py`

- [ ] All required integration tests pass.

---

## Security Tests

- [ ] `test_secret_redaction.py`
- [ ] `test_prompt_injection.py`
- [ ] `test_unsafe_output.py`

- [ ] All required security tests pass.

---

## Acceptance Test

- [ ] `test_project_acceptance.py`
- [ ] Project acceptance test passes.

### Testing Gate

- [ ] I have not marked the system complete based only on manual testing.
- [ ] I understand what each test category is proving.

---

# Phase 12 — Evaluate AI Behavior

Start with:

**[`evaluations/README.md`](evaluations/README.md)**

Review:

- [ ] [`evaluation-dataset.json`](evaluations/evaluation-dataset.json)
- [ ] [`expected-behavior.md`](evaluations/expected-behavior.md)
- [ ] [`accuracy-evaluation.md`](evaluations/accuracy-evaluation.md)
- [ ] [`groundedness-evaluation.md`](evaluations/groundedness-evaluation.md)
- [ ] [`safety-evaluation.md`](evaluations/safety-evaluation.md)
- [ ] [`evaluation-runner.py`](evaluations/evaluation-runner.py)

Evaluate:

- [ ] Supported failure classifications.
- [ ] Evidence grounding.
- [ ] Structured output compliance.
- [ ] Unsafe recommendation handling.
- [ ] Behavior with insufficient evidence.
- [ ] Behavior with malformed input.
- [ ] Behavior with adversarial input.
- [ ] Fallback behavior.

### AI Evaluation Gate

- [ ] I understand why conventional unit tests alone cannot fully evaluate probabilistic AI behavior.
- [ ] I have recorded the evaluation results.
- [ ] I can identify at least one limitation in the AI analysis.

---

# Phase 13 — Break the System Deliberately

Start with:

**[`failures/README.md`](failures/README.md)**

For every scenario:

1. introduce or reproduce the failure
2. observe the symptoms
3. collect evidence
4. form a hypothesis
5. investigate
6. recover
7. verify recovery
8. record what you learned

---

## Failure 01 — Invalid AI Response

- [ ] Completed [`01-invalid-ai-response.md`](failures/01-invalid-ai-response.md)
- [ ] Invalid response detected.
- [ ] Invalid response rejected.
- [ ] Failure remained observable.
- [ ] Recovery verified.

---

## Failure 02 — Model API Unavailable

- [ ] Completed [`02-model-api-unavailable.md`](failures/02-model-api-unavailable.md)
- [ ] Provider outage reproduced or simulated.
- [ ] Fallback path activated.
- [ ] Deterministic evidence remained available.
- [ ] Recovery verified.

---

## Failure 03 — Secret Leak Attempt

- [ ] Completed [`03-secret-leak-attempt.md`](failures/03-secret-leak-attempt.md)
- [ ] Sensitive test input introduced.
- [ ] Redaction behavior observed.
- [ ] Sensitive value prevented from reaching AI-bound context.
- [ ] Relevant security test passed.

---

## Failure 04 — Malformed CI Log

- [ ] Completed [`04-malformed-ci-log.md`](failures/04-malformed-ci-log.md)
- [ ] Malformed input tested.
- [ ] Application behavior observed.
- [ ] Failure handled without uncontrolled crash.
- [ ] Recovery verified.

---

## Failure 05 — Model Timeout

- [ ] Completed [`05-model-timeout.md`](failures/05-model-timeout.md)
- [ ] Timeout reproduced or simulated.
- [ ] Timeout handled.
- [ ] Fallback behavior observed.
- [ ] Recovery verified.

---

## Failure 06 — Prompt Injection Attempt

- [ ] Completed [`06-prompt-injection-attempt.md`](failures/06-prompt-injection-attempt.md)
- [ ] Adversarial log content introduced.
- [ ] Model-facing controls observed.
- [ ] Unsafe instructions were not treated as trusted operational commands.
- [ ] Security behavior documented.

---

## Failure 07 — False Root Cause

- [ ] Completed [`07-false-root-cause.md`](failures/07-false-root-cause.md)
- [ ] Conflicting AI interpretation reproduced or simulated.
- [ ] Deterministic evidence compared with AI analysis.
- [ ] Unsupported conclusion identified.
- [ ] Failure documented.
- [ ] Safe system behavior verified.

---

# Phase 14 — Production Hardening

Read:

**[`build/16-production-hardening.md`](build/16-production-hardening.md)**

Review the system from an engineering perspective.

- [ ] Configuration is separated from code.
- [ ] Secrets are not hard-coded.
- [ ] Timeouts exist where required.
- [ ] Errors are handled intentionally.
- [ ] Logs are useful without exposing supported sensitive data.
- [ ] AI input is minimized.
- [ ] AI output is validated.
- [ ] Fallback behavior exists.
- [ ] Failure states are observable.
- [ ] Tests cover important behavior.
- [ ] Security assumptions are documented.
- [ ] Known limitations are documented.
- [ ] Production gaps are identified rather than hidden.

### Production Review

I can answer:

- [ ] What would break first at higher scale?
- [ ] What would I monitor in production?
- [ ] What additional security controls would production require?
- [ ] How would I manage AI cost?
- [ ] How would I reduce model latency?
- [ ] How would I handle multiple AI providers?
- [ ] How would I handle multiple engineering teams?
- [ ] What data should never leave the organization?
- [ ] What should happen during provider degradation?
- [ ] Which parts of this Foundation implementation would need redesign before real production use?

---

# Phase 15 — Container and Operational Workflow

Review:

**[`docker/README.md`](docker/README.md)**

- [ ] I understand the [`Dockerfile`](docker/Dockerfile).
- [ ] I understand [`docker-compose.yml`](docker/docker-compose.yml).
- [ ] I can build the project container.
- [ ] I can start the required local services.
- [ ] I can verify the application from the containerized environment.
- [ ] I can stop and remove the local environment safely.

Review:

**[`scripts/README.md`](scripts/README.md)**

- [ ] I understand `setup.sh`.
- [ ] I understand `check-environment.sh`.
- [ ] I understand `run-demo.sh`.
- [ ] I understand `run-tests.sh`.
- [ ] I understand `run-evaluations.sh`.
- [ ] I understand `cleanup.sh`.
- [ ] I do not run scripts I have not reviewed.

---

# Phase 16 — Collect Evidence

Start with:

**[`evidence/README.md`](evidence/README.md)**

Then use:

**[`evidence/EVIDENCE-CHECKLIST.md`](evidence/EVIDENCE-CHECKLIST.md)**

Do not collect random screenshots.

Each artifact should prove a specific requirement or behavior.

---

## Required Evidence

### Evidence 01 — Environment

- [ ] Environment readiness demonstrated.
- [ ] Required tools available.

### Evidence 02 — Application Startup

- [ ] Successful application startup captured.

### Evidence 03 — Log Ingestion

- [ ] CI failure log loaded successfully.

### Evidence 04 — Secret Redaction

- [ ] Sensitive input shown safely.
- [ ] Redacted output captured.
- [ ] Proof that the supported sensitive value did not reach AI-bound context captured.

### Evidence 05 — Deterministic Evidence

- [ ] Extracted evidence captured before AI analysis.

### Evidence 06 — Successful Triage

- [ ] Valid complete triage report captured.

### Evidence 07 — Structured Validation

- [ ] Valid structured response accepted.

### Evidence 08 — Rejected AI Output

- [ ] Invalid model output rejected.
- [ ] Rejection evidence captured.

### Evidence 09 — AI Provider Failure

- [ ] Model outage or simulated outage captured.
- [ ] Fallback result captured.

### Evidence 10 — Prompt Injection

- [ ] Adversarial input tested.
- [ ] Result captured.

### Evidence 11 — Automated Tests

- [ ] Unit-test results captured.
- [ ] Integration-test results captured.
- [ ] Security-test results captured.
- [ ] Acceptance-test result captured.

### Evidence 12 — AI Evaluations

- [ ] Evaluation results captured.

### Evidence 13 — Failure Investigation

- [ ] At least one complete failure investigation documented from symptom through verified recovery.

### Evidence 14 — Final System

- [ ] Final working workflow demonstrated.

---

# Phase 17 — Complete the Final Engineering Challenge

Do not begin this phase until you have completed the guided build.

Start with:

**[`challenge/README.md`](challenge/README.md)**

Read:

- [ ] [`requirements.md`](challenge/requirements.md)
- [ ] [`constraints.md`](challenge/constraints.md)
- [ ] [`acceptance-criteria.md`](challenge/acceptance-criteria.md)

Use:

- [ ] [`learner-decisions.md`](challenge/learner-decisions.md)

to document your own engineering decisions.

---

## Challenge Scenario

Your organization now processes approximately:

**5,000 CI jobs per day.**

The system must satisfy additional requirements.

### Security

- [ ] Raw CI logs cannot leave the trusted environment.
- [ ] Sensitive values must not reach the external model.

### Performance

- [ ] Triage results must target the challenge latency requirement.

### Reliability

- [ ] The system remains useful when the AI provider is unavailable.

### Safety

- [ ] AI recommendations cannot directly execute remediation.

### Auditability

- [ ] Extracted evidence can be identified.
- [ ] AI-bound information can be identified.
- [ ] Model output can be identified.
- [ ] Validation outcome can be identified.
- [ ] Fallback usage can be identified.

---

## Your Engineering Work

- [ ] I reviewed the existing architecture.
- [ ] I identified which assumptions no longer hold.
- [ ] I identified the components that require changes.
- [ ] I documented my proposed design.
- [ ] I explained my trade-offs.
- [ ] I implemented my changes.
- [ ] I updated or added tests.
- [ ] I tested failure behavior.
- [ ] I verified recovery.
- [ ] I collected evidence.
- [ ] I documented limitations.
- [ ] I can defend my final design.

### Independence Gate

Before continuing:

- [ ] I can explain which decisions were mine.
- [ ] I can explain why I made them.
- [ ] I can describe at least one alternative I considered.
- [ ] I can explain the trade-off involved.

---

# Phase 18 — Prepare Your Portfolio

Start with:

**[`portfolio/README.md`](portfolio/README.md)**

Complete:

- [ ] [`project-summary.md`](portfolio/project-summary.md)
- [ ] [`skills-demonstrated.md`](portfolio/skills-demonstrated.md)
- [ ] [`resume-bullets.md`](portfolio/resume-bullets.md)
- [ ] [`recruiter-explanation.md`](portfolio/recruiter-explanation.md)
- [ ] [`interview-prep.md`](portfolio/interview-prep.md)
- [ ] [`github-presentation.md`](portfolio/github-presentation.md)
- [ ] [`linkedin-project-description.md`](portfolio/linkedin-project-description.md)

---

## Portfolio Integrity Check

Before publishing your version:

- [ ] My project description reflects what I actually built.
- [ ] My resume statements reflect work I actually completed.
- [ ] I did not claim features that I did not implement.
- [ ] I did not present the provided solution as my work.
- [ ] I documented meaningful modifications I made.
- [ ] My evidence supports my claims.
- [ ] My repository does not contain secrets.
- [ ] My repository does not contain private production data.
- [ ] My screenshots do not expose sensitive information.
- [ ] My documentation explains important limitations.

---

# Phase 19 — Prepare for Technical Interviews

You should be able to discuss the project without opening the implementation guide.

## Level 1 — Explain

- [ ] I can explain the problem the system solves.
- [ ] I can explain the complete architecture.
- [ ] I can explain the data flow.
- [ ] I can explain the technologies I used.
- [ ] I can explain where AI is used.
- [ ] I can explain where deterministic logic is used.
- [ ] I can explain the final output.

## Level 2 — Defend

- [ ] I can explain why logs are redacted before AI analysis.
- [ ] I can explain why evidence is extracted before AI analysis.
- [ ] I can explain why AI output is validated.
- [ ] I can explain why structured output is used.
- [ ] I can explain why AI cannot execute remediation.
- [ ] I can explain why fallback behavior exists.
- [ ] I can explain the system's trust boundaries.
- [ ] I can explain how prompt injection affects this type of system.
- [ ] I can explain the tests I wrote.
- [ ] I can explain a failure I investigated.

## Level 3 — Redesign

I can discuss how the design might change if:

- [ ] The system processes 10,000 failures per hour.
- [ ] The AI provider becomes unavailable for several hours.
- [ ] Multiple teams share the service.
- [ ] Different teams require data isolation.
- [ ] The organization operates in a regulated environment.
- [ ] AI inference cost must be reduced significantly.
- [ ] The organization requires multiple AI providers.
- [ ] Triage latency must be reduced.
- [ ] The service must run across multiple regions.
- [ ] Raw logs cannot leave an internal network.

---

# Phase 20 — Review the Reference Solution

Only after making a serious attempt at the project should you review:

**[`solution/README.md`](solution/README.md)**

Then:

- [ ] Review [`architecture-notes.md`](solution/architecture-notes.md).
- [ ] Complete [`comparison-checklist.md`](solution/comparison-checklist.md).
- [ ] Compare the reference approach with your approach.
- [ ] Identify similarities.
- [ ] Identify differences.
- [ ] Identify trade-offs.
- [ ] Identify something the reference solution does better.
- [ ] Identify something you would keep from your own design.
- [ ] Update your understanding where appropriate.

Do not automatically replace your implementation simply because it differs from the reference solution.

A different solution can still be valid if you can test it, explain it, and defend its trade-offs.

---

# Phase 21 — Final Cleanup

Before finishing:

- [ ] Temporary resources removed.
- [ ] Unnecessary containers stopped.
- [ ] Temporary test files removed where appropriate.
- [ ] No credentials remain in local project files intended for publication.
- [ ] No credentials appear in Git history intended for publication.
- [ ] No sensitive information appears in evidence.
- [ ] No private CI logs have been committed.
- [ ] Final tests rerun after cleanup where appropriate.
- [ ] Repository status checked.
- [ ] Final documentation reviewed.

Review:

**[`scripts/cleanup.sh`](scripts/cleanup.sh)**

before running it.

Never execute destructive cleanup commands without understanding what they remove.

---

# Final Project Verification

You are almost finished.

Do one final end-to-end review.

## System

- [ ] The application starts successfully.
- [ ] CI failure data can be ingested.
- [ ] Input is normalized.
- [ ] Supported sensitive values are redacted.
- [ ] Deterministic evidence is extracted.
- [ ] AI analysis receives bounded sanitized context.
- [ ] Structured output is produced.
- [ ] Output validation works.
- [ ] Safety checks work.
- [ ] A useful triage report is produced.
- [ ] Fallback behavior works.

## Testing

- [ ] Unit tests pass.
- [ ] Integration tests pass.
- [ ] Security tests pass.
- [ ] Acceptance tests pass.
- [ ] Required AI evaluations have been completed.

## Failure Engineering

- [ ] Invalid AI output tested.
- [ ] Model outage tested.
- [ ] Secret exposure scenario tested.
- [ ] Malformed input tested.
- [ ] Timeout tested.
- [ ] Prompt injection tested.
- [ ] Unsupported or false AI conclusion investigated.
- [ ] Recovery verification completed.

## Security

- [ ] No hard-coded credentials.
- [ ] Sensitive values are not intentionally exposed in application logs.
- [ ] Sensitive values are redacted before external AI processing.
- [ ] AI output is treated as untrusted.
- [ ] AI cannot execute remediation actions.
- [ ] Trust boundaries are documented.

## Observability

- [ ] Important application behavior can be observed.
- [ ] Failures can be observed.
- [ ] Validation failures can be observed.
- [ ] Fallback activation can be observed.
- [ ] Relevant model behavior can be measured where supported.

## Documentation

- [ ] Architecture documentation is complete.
- [ ] Engineering decisions are documented.
- [ ] Known limitations are documented.
- [ ] Evidence is organized.
- [ ] Portfolio material reflects the implementation.
- [ ] Public documentation contains no sensitive information.

## Independent Engineering

- [ ] Final challenge completed.
- [ ] My own engineering decisions documented.
- [ ] My changes tested.
- [ ] My failure scenarios tested.
- [ ] My final design can be defended.

---

# Final Understanding Check

Do not use the project notes for this section.

Ask yourself whether you can explain each question from memory.

- [ ] What problem does this system solve?
- [ ] Why is CI failure triage difficult?
- [ ] What happens when a CI log enters the system?
- [ ] Why is normalization necessary?
- [ ] Why does redaction happen before AI analysis?
- [ ] What is deterministic evidence?
- [ ] Why should evidence be separated from AI interpretation?
- [ ] What information is sent to the model?
- [ ] What information should not be sent?
- [ ] Why use structured model output?
- [ ] Why validate AI output?
- [ ] What happens when validation fails?
- [ ] What happens when the model provider is unavailable?
- [ ] What happens when the model times out?
- [ ] How does the system handle prompt injection risk?
- [ ] Why can't the AI automatically execute remediation?
- [ ] How is the application tested?
- [ ] How is AI behavior evaluated?
- [ ] What does the application monitor?
- [ ] How did you test failure?
- [ ] How did you verify recovery?
- [ ] What are the system's current limitations?
- [ ] What did you change during the final challenge?
- [ ] What would you change before production?
- [ ] What did you personally learn from building it?

---

# Project Complete

Only check this box after completing the final verification.

- [ ] **PROJECT 001 COMPLETE**

Completing the project should mean more than:

> I followed the instructions and the application ran.

You should now be able to say:

> I built a CI failure triage system that separates deterministic evidence from AI interpretation. The system normalizes failed CI logs, redacts supported sensitive information before the AI boundary, extracts evidence, performs bounded AI-assisted analysis, validates structured model output, handles model failure safely, and produces an engineer-facing triage report. I tested normal and failure paths, evaluated AI behavior, investigated controlled failures, verified recovery, and documented the engineering decisions and limitations.

More importantly, you should be able to explain **why each of those controls exists**.

---

## Continue

If you still have unchecked items, return to the relevant project section and finish them.

If every required item is complete, review your evidence and portfolio documentation one final time.

Your goal was never to collect another finished tutorial.

Your goal was to understand, build, test, break, investigate, recover, improve, prove, and explain an engineering system.
