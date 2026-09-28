# Changelog

All notable changes to **Project 001 — AI-Powered CI Failure Triage Engine** are documented in this file.

This changelog tracks meaningful changes to the project's:

- learning material
- architecture
- application behavior
- AI integration
- security controls
- schemas
- tests
- evaluations
- failure scenarios
- observability
- sample data
- challenge
- evidence requirements
- portfolio guidance
- reference solution

Minor spelling corrections, formatting adjustments, and other changes that do not affect the learning experience or system behavior may not receive individual entries.

---

## How to Read This Changelog

Changes are grouped into the following categories when applicable:

### Added

New functionality, learning material, tests, exercises, documentation, or project components.

### Changed

Existing behavior, architecture, instructions, interfaces, or learning material that has been modified.

### Fixed

Corrections to defects, incorrect behavior, broken instructions, inaccurate examples, or documentation problems.

### Security

Changes that affect:

- secret handling
- data exposure
- trust boundaries
- prompt-injection defenses
- permissions
- model access
- input validation
- output validation
- unsafe AI behavior
- other security controls

### Deprecated

Functionality or project material that remains available temporarily but is planned for removal or replacement.

### Removed

Functionality, files, dependencies, exercises, or project material that has been intentionally removed.

---

# Unreleased

Changes listed here are part of the current development version and have not yet been included in a tagged project release.

## Added

### Project Foundation

- Added the initial Project 001 repository structure.
- Added the public-facing project [`README.md`](README.md).
- Added the master [`PROJECT-CHECKLIST.md`](PROJECT-CHECKLIST.md).
- Added project-level configuration placeholders and development files.
- Added the initial learning progression:

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

### Learning Notes

Added the `notes/` learning path covering:

- project prerequisites
- CI/CD failure fundamentals
- CI log interpretation
- exit codes
- stdout and stderr
- structured and unstructured logs
- secret redaction
- deterministic evidence versus AI analysis
- LLMs in operational systems
- structured AI output
- JSON Schema validation
- model failure and fallback behavior
- prompt injection in operational data
- observability for AI-powered services
- security and trust boundaries
- production design considerations
- commands and reference material

### Project Preparation

Added the `learn/` sequence for understanding:

- the engineering problem
- the system being built
- how a CI failure moves through the system
- system architecture
- data flow
- trust boundaries
- environment preparation
- repository organization
- build readiness

### Guided Build

Added the `build/` learning path with progressive milestones for:

1. project foundation
2. CI failure data ingestion
3. log normalization
4. sensitive-data redaction
5. deterministic evidence extraction
6. failure-context classification
7. AI analyzer integration
8. structured triage output
9. model-output validation
10. fallback behavior
11. API integration
12. observability
13. security controls
14. end-to-end workflow
15. system testing
16. production hardening

### Application Architecture

Added the initial modular application structure under `src/ci_triage/`.

The application is separated into components for:

- ingestion
- normalization
- redaction
- deterministic evidence extraction
- failure classification
- AI analysis
- fallback behavior
- validation
- safety checks
- reporting
- observability
- configuration

### Architecture Documentation

Added documentation for:

- system architecture
- data flow
- component responsibilities
- trust boundaries
- failure flow
- AI boundary
- engineering decisions

### API

Added the project API structure for:

- application startup
- routes
- request models
- response models

### AI Prompt Management

Added version-controlled prompt resources for:

- system-level AI instructions
- CI triage instructions
- prompt rules and constraints

### Structured Data Contracts

Added schemas for:

- triage input
- triage output

The project uses explicit contracts so AI-generated output can be validated before it is treated as usable application data.

### Sample CI Data

Added reproducible synthetic failure samples covering:

- dependency installation failures
- unit-test failures
- lint failures
- build failures
- Docker build failures
- authentication failures
- deployment failures
- timeout failures

Added dedicated security-oriented samples containing synthetic:

- API-key-like values
- token-like values
- credential-like values

Added malformed samples covering:

- empty logs
- truncated logs
- malformed logs

### Testing

Added the initial testing structure.

#### Unit Tests

Coverage is planned for:

- log loading
- log normalization
- secret redaction
- evidence extraction
- failure classification
- output validation

#### Integration Tests

Coverage is planned for:

- complete triage pipeline behavior
- AI fallback behavior
- API behavior

#### Security Tests

Coverage is planned for:

- secret redaction
- prompt-injection handling
- unsafe model output

#### Acceptance Testing

Added a project-level acceptance test structure for verifying that the completed system satisfies its defined requirements.

### AI Evaluation

Added an AI evaluation framework covering:

- evaluation datasets
- expected behavior
- classification quality
- groundedness
- safety
- evaluation execution

This evaluation layer is intentionally separate from conventional deterministic software tests.

### Failure Engineering

Added controlled failure scenarios for:

1. invalid AI response
2. unavailable model API
3. secret leak attempt
4. malformed CI log
5. model timeout
6. prompt-injection attempt
7. unsupported or false root-cause analysis

Each scenario is designed around the investigation cycle:

```text
Failure
   ↓
Observe
   ↓
Collect Evidence
   ↓
Form Hypothesis
   ↓
Test
   ↓
Recover
   ↓
Verify Recovery
```

### Observability

Added project guidance for:

- application logging
- operational metrics
- alerts

The initial observability design includes visibility into important behaviors such as:

- processing success
- processing failure
- validation failure
- fallback activation
- model latency
- application errors

### Development Scripts

Added planned helper scripts for:

- environment setup
- environment validation
- demonstration
- testing
- AI evaluation
- cleanup

### Containerization

Added project containerization structure for:

- Docker image creation
- local Docker Compose execution

### Evidence Collection

Added a dedicated `evidence/` structure for recording proof of completed engineering work.

Evidence categories include:

- screenshots
- terminal output
- test results
- logs
- sample output

Added an evidence checklist so captured artifacts demonstrate specific project requirements instead of serving as arbitrary screenshots.

### Final Engineering Challenge

Added a dedicated `challenge/` phase.

The challenge introduces a larger operational scenario in which the learner must adapt the guided implementation to additional requirements involving:

- higher CI workload
- data-boundary restrictions
- response-time expectations
- AI-provider failure
- controlled remediation
- auditability

The challenge deliberately provides fewer exact implementation instructions.

### Portfolio Preparation

Added portfolio guidance covering:

- project summary
- demonstrated skills
- resume bullets
- recruiter explanation
- technical interview preparation
- GitHub presentation
- LinkedIn project description

Portfolio material is intended to help learners explain work they actually completed rather than provide claims to copy without implementation evidence.

### Reference Solution

Added the `solution/` area for:

- reference implementation guidance
- architecture notes
- learner-to-reference comparison

The solution is positioned as comparison material to be reviewed after a serious implementation attempt.

---

## Changed

### Learning Model

The project uses a progressive learning model rather than providing the same level of instruction throughout the entire build.

The intended progression is:

```text
Follow
  ↓
Understand
  ↓
Modify
  ↓
Diagnose
  ↓
Design
  ↓
Defend
```

Early Foundation stages provide more explicit guidance.

Later stages progressively require the learner to make and explain engineering decisions.

### AI Responsibility Boundary

Clarified that AI is used for bounded assistance such as:

- failure interpretation
- pattern reasoning
- failure classification
- explanation
- investigation recommendations

Deterministic application components remain responsible for:

- log loading
- normalization
- secret redaction
- evidence extraction
- configuration
- schema validation
- safety checks
- fallback behavior
- testing
- observability

### Remediation Boundary

Clarified that Project 001 is a **triage system**, not an autonomous remediation platform.

AI-generated output must not directly:

- execute shell commands
- modify infrastructure
- approve deployments
- restart production workloads
- delete resources
- access unrestricted credentials
- perform production remediation

### Evidence Model

Clarified that the project distinguishes between:

1. observed evidence
2. AI analysis
3. recommendations

AI-generated conclusions must not be presented as though they were directly observed system facts.

### Completion Requirements

Expanded project completion beyond successful application execution.

Completion now includes:

- knowledge checks
- environment verification
- implementation milestones
- deterministic testing
- AI evaluation
- security testing
- controlled failure exercises
- recovery verification
- production-hardening review
- evidence collection
- independent engineering challenge
- portfolio preparation
- technical explanation

---

## Security

### Secret Handling

Established the requirement that supported sensitive values must be redacted before relevant content crosses the external AI boundary.

### Model Trust

Established model output as untrusted application input.

AI responses must pass through the project's validation and safety mechanisms before being treated as usable triage output.

### Prompt Injection

Added explicit prompt-injection testing for untrusted operational data.

CI logs may contain arbitrary text and therefore must not automatically be treated as trusted model instructions.

### Credential Handling

Established that:

- credentials must not be hard-coded
- real secrets must not be committed
- configuration secrets should be provided through appropriate environment configuration
- credentials should not appear in public evidence
- credentials should not appear in intentionally published application logs

### AI Permissions

Established that the AI component does not receive unrestricted operational permissions.

### Data Minimization

Established that model-bound context should be limited to information required for the analysis rather than sending complete raw operational data without justification.

---

# Release History

No stable project release has been published yet.

Project 001 is currently being built and reviewed.

The first stable release will be added here after the complete learning path, implementation, tests, evaluations, failure scenarios, challenge, evidence requirements, and supporting documentation have passed project review.

---

# Versioning Approach

Project releases use semantic versioning:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
1.0.0
```

## MAJOR

A major version may be introduced when a change significantly alters the project's:

- architecture
- learning path
- primary interfaces
- core engineering problem
- compatibility expectations
- project completion requirements

Example:

```text
1.0.0 → 2.0.0
```

A major change may require learners using an older version to adjust their implementation substantially.

## MINOR

A minor version may introduce backward-compatible additions such as:

- new failure scenarios
- new sample data
- additional evaluations
- new tests
- expanded notes
- additional security controls
- new observability exercises
- optional implementation capabilities
- new challenge requirements that do not invalidate the existing core project

Example:

```text
1.0.0 → 1.1.0
```

## PATCH

A patch version may contain backward-compatible corrections such as:

- broken command fixes
- incorrect path fixes
- dependency corrections
- test fixes
- documentation corrections
- minor code defects
- inaccurate expected-output corrections

Example:

```text
1.0.0 → 1.0.1
```

Not every documentation edit requires a new project release.

---

# Changelog Entry Standard

Future notable changes should be recorded under `Unreleased` first.

Example:

```markdown
## Unreleased

### Added

- Added a new CI failure sample for container registry authentication errors.
- Added an evaluation case for insufficient evidence.

### Changed

- Updated the evidence extractor to preserve command exit codes consistently.
- Improved fallback reporting when AI analysis is unavailable.

### Fixed

- Fixed incorrect setup instructions for the local environment.

### Security

- Improved token-redaction coverage for supported authorization header formats.
```

When a release is created, move the relevant entries from `Unreleased` into a versioned section.

Example:

```markdown
## [1.1.0] - YYYY-MM-DD

### Added

- Added additional AI evaluation cases.

### Changed

- Improved fallback reporting.

### Fixed

- Corrected an environment setup instruction.

### Security

- Expanded supported secret-redaction patterns.
```

Do not invent a release date.

Use the actual release date when a version is published.

---

# What Belongs in This Changelog

Record changes that materially affect:

- what learners are taught
- how learners complete the project
- how the system behaves
- project architecture
- public interfaces
- data contracts
- AI behavior
- security
- testing
- evaluations
- failure scenarios
- operational behavior
- challenge requirements
- completion requirements
- compatibility
- portfolio expectations

Examples:

```text
Added a new failure scenario.
Changed the triage output schema.
Added a fallback strategy.
Changed the API request contract.
Added a security test.
Changed the architecture.
Fixed an incorrect build instruction.
Changed a project prerequisite.
Added an AI evaluation.
Removed a deprecated component.
```

---

# What Does Not Need an Individual Entry

Avoid turning the changelog into a commit history.

Changes such as these normally do not need individual entries:

```text
Fixed one typo.
Adjusted heading spacing.
Reworded a sentence without changing meaning.
Reformatted Markdown.
Renamed an internal variable without behavioral impact.
Cleaned up comments.
```

Git already records individual commits.

This changelog should help a learner or contributor understand **meaningful project evolution**.

---

# Breaking Changes

Breaking changes must be clearly identified.

Use:

```markdown
### Changed

- **BREAKING:** Changed the triage output contract from ...
```

A breaking change may include:

- renaming required schema fields
- removing supported configuration
- changing required environment variables
- changing public API behavior
- restructuring required project interfaces
- changing data formats
- removing previously supported behavior

Where appropriate, include migration guidance.

Example:

```markdown
- **BREAKING:** Renamed the output field `cause` to `likely_cause`.

  Existing implementations using `cause` must update their
  response parsing and validation logic.
```

Do not hide breaking changes inside general documentation updates.

---

# Security Changes

Security changes deserve explicit changelog entries.

Use the `Security` category when a change affects areas such as:

```text
Secret redaction
Credential handling
Authentication
Authorization
Data exposure
Trust boundaries
Prompt injection
Model permissions
Unsafe output
External AI data flow
Sensitive logging
Input validation
Output validation
```

Do not include information in this changelog that would unnecessarily expose an unresolved vulnerability.

Follow the repository's security reporting process for vulnerabilities that should not be publicly disclosed before remediation.

---

# Changes to AI Behavior

Changes to AI-related behavior should be recorded when they materially affect the project.

Examples include:

- prompt-contract changes
- model-interface changes
- schema changes
- context-selection changes
- fallback changes
- validation changes
- safety-control changes
- evaluation changes
- provider-interface changes

Do not describe an AI behavior change only as:

```text
Improved AI.
```

Describe what actually changed.

For example:

```text
Changed the triage prompt to require evidence references for each
proposed root cause.

Added validation that rejects responses missing the required
evidence field.
```

This makes the project easier to review and reproduce.

---

# Changes to Tests and Evaluations

Tests and AI evaluations are different and should be described accurately.

A conventional software test might verify:

```text
A redaction function removes a supported token pattern.
```

An AI evaluation might examine:

```text
Whether the model's failure classification remains grounded in
the supplied evidence.
```

When updating either area, state which one changed.

Do not describe a new AI evaluation as a unit test if it is measuring probabilistic model behavior.

---

# Changes to Failure Scenarios

When adding or changing a controlled failure exercise, record:

- what failure was added or changed
- what behavior the learner is expected to observe
- whether recovery behavior changed
- whether verification requirements changed

Failure exercises are part of the project's learning contract.

They should not change silently.

---

# Changes to Project Completion

Any change that affects the definition of a completed Project 001 should be recorded.

Examples include:

- adding a mandatory test
- adding a required failure exercise
- changing evidence requirements
- adding a security gate
- changing final challenge acceptance criteria
- adding a required AI evaluation

The [`PROJECT-CHECKLIST.md`](PROJECT-CHECKLIST.md) should be updated whenever a change modifies a learner's required completion path.

---

# Documentation Alignment

Project documentation should remain aligned.

When a change affects multiple parts of the project, update every relevant location.

For example, changing the output schema may require updates to:

```text
schemas/
    ↓
src/
    ↓
tests/
    ↓
evaluations/
    ↓
build/
    ↓
sample output
    ↓
architecture/
    ↓
PROJECT-CHECKLIST.md
```

Similarly, adding a new required failure scenario may require updates to:

```text
failures/
    ↓
tests/
    ↓
evidence/
    ↓
PROJECT-CHECKLIST.md
    ↓
README.md
```

Do not update one part of the learning path while leaving contradictory instructions elsewhere.

---

# Project Philosophy

Project 001 is designed around a simple progression:

```text
Learn
  ↓
Build
  ↓
Verify
  ↓
Break
  ↓
Investigate
  ↓
Recover
  ↓
Improve
  ↓
Prove
  ↓
Explain
```

Changes to this project should strengthen that learning experience.

A new feature is not automatically an improvement.

A change should help you better understand, build, test, operate, secure, investigate, or explain the system without adding unnecessary complexity.

The goal is not to make Project 001 look large.

The goal is to make it a credible Foundation-level engineering experience.

---

## Current Status

**Project:** 001 — AI-Powered CI Failure Triage Engine  
**Track:** AI for CI/CD and Software Delivery  
**Level:** Foundation  
**Status:** In Development  
**Stable Release:** Not yet published

---

A stable release will be recorded here only after the complete Project 001 experience has been implemented, reviewed, tested, and verified.
