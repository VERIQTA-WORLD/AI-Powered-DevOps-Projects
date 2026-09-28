

Before you can build a system that analyzes CI/CD failures, you need to understand what a CI/CD failure actually is.

That sounds simple:

> A pipeline ran and something failed.

But real CI/CD failures are more complicated.

A failed job can be caused by:

- application code
- tests
- dependencies
- build tooling
- configuration
- credentials
- permissions
- networking
- external services
- container builds
- deployment targets
- timeouts
- resource constraints
- runner problems
- infrastructure problems

Sometimes the most visible error is the root cause.

Sometimes it is only a consequence of something that happened earlier.

Project 001 is designed around that reality.

The goal of this note is to teach you how to think about CI/CD failures **before AI enters the investigation**.

---

# 1. What Is CI/CD?

CI/CD commonly refers to:

```text
Continuous Integration
        +
Continuous Delivery
        or
Continuous Deployment
```

These practices automate parts of the software delivery process.

A simplified workflow might look like:

```text
Developer Changes Code
        ↓
Pushes to Repository
        ↓
CI Pipeline Starts
        ↓
Dependencies Installed
        ↓
Code Checked
        ↓
Tests Run
        ↓
Application Built
        ↓
Artifact Created
        ↓
Deployment Process
```

Different organizations build different pipelines.

There is no single universal CI/CD pipeline.

A Python service might have:

```text
Checkout
   ↓
Install Dependencies
   ↓
Lint
   ↓
Unit Tests
   ↓
Build
```

A containerized application might have:

```text
Checkout
   ↓
Install Dependencies
   ↓
Tests
   ↓
Docker Build
   ↓
Container Scan
   ↓
Push Image
   ↓
Deploy
```

A large production system may have many more stages.

The important idea is that a pipeline is a sequence of automated work.

---

# 2. Continuous Integration

Continuous Integration focuses on integrating software changes frequently and verifying them automatically.

A developer might:

```text
Modify Code
    ↓
Commit
    ↓
Push
    ↓
CI Runs
```

The CI system may then:

- check out the repository
- install dependencies
- compile code
- run linting
- execute tests
- perform security checks
- build artifacts

If one of those checks fails, the change may be prevented from progressing further.

For example:

```text
Checkout             PASS
Install Dependencies PASS
Lint                 PASS
Unit Tests           FAIL
Build                NOT RUN
```

The pipeline has failed.

But saying:

> The pipeline failed.

is not enough for an investigation.

You need to determine **where**, **how**, and potentially **why** it failed.

---

# 3. Continuous Delivery and Continuous Deployment

Continuous Delivery extends automation toward releasing software.

The software is kept in a state where it can be deployed through a controlled release process.

Continuous Deployment goes further by automatically deploying qualifying changes when the required checks succeed.

A simplified delivery pipeline could look like:

```text
Code Change
    ↓
CI Validation
    ↓
Build Artifact
    ↓
Security Checks
    ↓
Deploy to Staging
    ↓
Verification
    ↓
Production Release
```

Failures can therefore occur long after compilation or testing.

For example:

```text
Unit Tests        PASS
Build             PASS
Container Build   PASS
Registry Push     PASS
Deployment        FAIL
```

The application was successfully built.

The pipeline still failed.

This is why failure classification matters.

---

# 4. Pipelines, Jobs, Steps, and Commands

CI/CD platforms use slightly different terminology, but you should understand four useful concepts:

```text
Pipeline
   ↓
Job
   ↓
Step
   ↓
Command
```

These terms are not perfectly universal across every CI/CD platform, but they provide a useful mental model for Project 001.

---

## Pipeline

The pipeline represents the broader automated workflow.

Example:

```text
Application CI Pipeline
```

It may contain several jobs.

---

## Job

A job is a unit of work executed by a runner or execution environment.

Example:

```text
test
```

or:

```text
build-container
```

---

## Step

A job often contains multiple steps.

Example:

```text
Checkout repository
Install Python
Install dependencies
Run tests
```

---

## Command

A step may execute one or more commands.

Example:

```bash
python -m pytest
```

Understanding these levels matters because:

```text
pipeline failure
```

is much less precise than:

```text
job: test
step: run-unit-tests
command: python -m pytest
exit code: 1
```

The second description contains useful evidence.

---

# 5. What Does It Mean for a CI Job to Fail?

At the simplest level, a CI job fails when the CI platform determines that the required work did not complete successfully.

One common signal is a non-zero process exit code.

For example:

```bash
python -m pytest
```

might finish with:

```text
exit code 1
```

The CI runner sees that result and marks the step or job as failed.

Conceptually:

```text
Command
   ↓
Process Executes
   ↓
Process Exits
   ↓
Exit Status
   ↓
CI Runner Interprets Result
   ↓
Job Status
```

But not every failure is represented in exactly the same way.

A CI platform may also terminate work because of:

- timeout
- cancellation
- runner failure
- infrastructure interruption
- resource exhaustion
- failed dependency
- policy decision

So you should not reduce all CI failures to:

```text
non-zero exit code
```

Exit codes are important evidence.

They are not the entire failure model.

---

# 6. A Pipeline Can Fail at Different Layers

One reason CI troubleshooting becomes difficult is that several layers are involved.

Consider:

```text
CI Platform
    ↓
Runner
    ↓
Shell
    ↓
Tool
    ↓
Application
    ↓
External Dependency
```

A visible failure may originate at any of these layers.

For example:

```text
pytest failed
```

could mean:

- an application test assertion failed
- test collection failed
- a required module could not be imported
- configuration was missing
- a test dependency was unavailable
- the process was terminated
- the environment was misconfigured

The command name alone does not establish the cause.

---

# 7. Failure Stage Is Valuable Evidence

One of the first useful questions during triage is:

> Where did the pipeline fail?

Suppose a pipeline contains:

```text
1. Checkout
2. Install Dependencies
3. Lint
4. Unit Tests
5. Build
6. Container Build
7. Deploy
```

If it fails during:

```text
2. Install Dependencies
```

that immediately narrows the investigation.

You probably do not begin by investigating production deployment behavior.

Likewise, if:

```text
2. Install Dependencies  PASS
3. Lint                  PASS
4. Unit Tests            PASS
5. Build                 PASS
6. Container Build       PASS
7. Deploy                FAIL
```

the evidence suggests the failure occurred later in the delivery process.

This does not automatically identify the root cause.

But it reduces the search space.

---

# 8. Project 001 Failure Categories

The sample data for Project 001 introduces eight primary failure types:

```text
dependency installation failure
unit-test failure
lint failure
build failure
Docker build failure
authentication failure
deployment failure
timeout failure
```

These correspond to the files under:

```text
sample-data/failures/
```

The project structure contains:

```text
dependency-install-failure.log
unit-test-failure.log
lint-failure.log
build-failure.log
docker-build-failure.log
authentication-failure.log
deployment-failure.log
timeout-failure.log
```

These categories provide a controlled learning environment.

Real production systems can have many additional failure types.

---

# 9. Dependency Installation Failures

Modern applications depend on external packages and libraries.

A Python project might install dependencies with:

```bash
python -m pip install -r requirements.txt
```

A failure could produce output conceptually similar to:

```text
ERROR: Could not find a version that satisfies the requirement example-package==9.9.9
ERROR: No matching distribution found
```

Potential causes might include:

- incorrect package name
- invalid version
- unavailable package version
- repository configuration problem
- incompatible runtime
- network failure
- authentication failure to a private package source

Notice the distinction.

The observed evidence might be:

```text
No matching distribution found
```

But:

```text
The package version was deleted
```

would be an interpretation unless additional evidence proves it.

Project 001 preserves that difference.

---

# 10. Unit-Test Failures

A unit-test failure occurs when automated tests do not complete successfully.

Example:

```text
FAILED tests/test_api.py::test_create_user

AssertionError: expected 201, received 500
```

Useful evidence might include:

```text
test:
tests/test_api.py::test_create_user

expected:
201

actual:
500

exception:
AssertionError
```

Possible explanations include:

- application regression
- incorrect test expectation
- configuration problem
- missing dependency
- unexpected application state
- test isolation problem

Again:

```text
AssertionError
```

is evidence.

The exact reason the assertion failed may require further investigation.

---

# 11. Lint Failures

Linting tools analyze source code for defined quality or correctness rules.

A pipeline might execute:

```bash
ruff check .
```

and report a violation.

A lint failure is different from an application runtime failure.

The application may never have executed.

For example:

```text
src/example.py:18:1: F401 imported but unused
```

The useful context includes:

```text
file
line
rule
message
lint command
exit status
```

This distinction helps prevent an investigation from jumping to unrelated runtime theories.

---

# 12. Build Failures

A build failure occurs when software cannot be transformed into the expected build artifact.

Depending on the technology, building might involve:

- compilation
- packaging
- bundling
- artifact creation
- dependency resolution
- static generation

A build might fail because of:

- syntax problems
- missing files
- incompatible dependencies
- compilation errors
- invalid configuration
- unavailable build tools

For example:

```text
Build started...
Compiling...
ERROR: required module could not be resolved
Build failed
```

A build failure should not automatically be classified as:

```text
application runtime failure
```

The application may never have reached runtime.

---

# 13. Docker Build Failures

Container builds introduce another layer.

A pipeline may execute:

```bash
docker build -t example-app .
```

The build might fail because of:

- invalid Dockerfile instruction
- missing build context
- unavailable base image
- package installation failure
- failed `RUN` command
- file permission problem
- network dependency
- authentication problem
- incorrect file path

Example:

```text
Step 5/8 : RUN python -m pip install -r requirements.txt
...
ERROR: Could not find requirements file
```

The outer failure is:

```text
Docker build failed
```

But the useful inner evidence is:

```text
requirements file could not be found
```

This introduces an important troubleshooting concept:

> Failures can be nested.

---

# 14. Authentication Failures

CI pipelines frequently communicate with external systems.

Examples include:

- package registries
- container registries
- cloud APIs
- artifact repositories
- deployment platforms
- source-control APIs

These systems may require authentication.

A failure might contain:

```text
401 Unauthorized
```

or:

```text
authentication failed
```

Potential causes could include:

- missing credential
- expired credential
- revoked credential
- wrong credential
- incorrect permissions
- incorrect authentication configuration

But be careful.

The presence of:

```text
401 Unauthorized
```

does not tell you which one occurred.

The evidence establishes authentication failure.

Further investigation establishes why.

---

# 15. Authentication Failures Create a Security Challenge

Authentication failures are especially relevant to Project 001 because diagnostic output may expose credential-related information.

Imagine:

```text
Authenticating with token abc123...
Authentication failed.
```

The failure investigation needs the fact:

```text
Authentication failed.
```

It probably does not need:

```text
abc123
```

That creates a security requirement:

```text
Useful Failure Evidence
        +
Sensitive Value
```

must become:

```text
Useful Failure Evidence
        -
Sensitive Value
```

before external AI processing.

Later notes will cover redaction in depth.

For now, remember:

> Troubleshooting value and sensitive data are not the same thing.

---

# 16. Deployment Failures

Deployment failures occur after software has progressed into a release or deployment stage.

A pipeline might successfully:

```text
PASS  Tests
PASS  Build
PASS  Container Build
PASS  Push Artifact
FAIL  Deploy
```

Possible deployment problems include:

- invalid deployment configuration
- unavailable target environment
- authorization failure
- rollout failure
- health-check failure
- incompatible artifact
- missing configuration
- platform error

The earlier successful stages matter.

They are part of the context.

If the build succeeded, the investigation should not pretend the build failed.

---

# 17. Timeout Failures

Some CI work fails because it does not complete within an allowed period.

Conceptually:

```text
Job Started
    ↓
Work Continues
    ↓
Time Limit Reached
    ↓
Runner Terminates Job
    ↓
Timeout Failure
```

Possible causes might include:

- hanging process
- deadlock
- slow test
- unavailable external dependency
- network delay
- overloaded runner
- insufficient timeout
- infinite retry behavior

But:

```text
job exceeded 15 minutes
```

does not prove:

```text
the network caused the timeout
```

The timeout is evidence.

Its cause requires investigation.

---

# 18. The Last Error Is Not Always the Root Cause

This is one of the most important lessons in failure analysis.

Consider:

```text
10:14:02 Connecting to package repository...
10:14:32 Connection timed out.
10:14:32 Dependency installation failed.
10:14:32 Build aborted.
10:14:32 Process exited with code 1.
```

If you only inspect the final line:

```text
Process exited with code 1.
```

you learn almost nothing.

If you inspect:

```text
Build aborted.
```

you know slightly more.

But the earlier event:

```text
Connection timed out.
```

may be far more useful.

Failures often propagate.

Conceptually:

```text
Initial Problem
      ↓
Component Failure
      ↓
Step Failure
      ↓
Job Failure
      ↓
Pipeline Failure
```

The final error may describe the consequence, not the origin.

---

# 19. Failure Chains

Consider this sequence:

```text
Private Package Repository Unavailable
              ↓
Dependency Cannot Be Downloaded
              ↓
Dependency Installation Fails
              ↓
Build Cannot Start
              ↓
CI Job Fails
```

What is the failure?

Several statements are true:

```text
The CI job failed.
Dependency installation failed.
A dependency could not be downloaded.
```

But they describe different levels of the failure chain.

A strong triage system should preserve enough evidence for engineers to reason about those relationships.

It should not flatten the entire chain into:

```text
Build failed.
```

---

# 20. Primary and Secondary Errors

A pipeline may produce many error messages.

Some are primary.

Others are consequences.

Example:

```text
ERROR: Could not connect to dependency repository
ERROR: Dependency installation failed
ERROR: Build step failed
ERROR: Job terminated
```

The number of times the word:

```text
ERROR
```

appears does not tell you which message is most important.

Evidence extraction therefore requires more reasoning than:

```text
collect every line containing ERROR
```

Project 001 will later build deterministic evidence extraction that attempts to preserve useful failure signals without pretending that keyword matching alone establishes root cause.

---

# 21. Warnings Are Not Automatically Failures

A log might contain:

```text
WARNING: package X is deprecated
```

and later:

```text
Tests passed.
Process completed with exit code 0.
```

If a triage engine simply searches for dramatic words, it might incorrectly focus on the warning.

A warning may be important.

But it does not automatically mean:

```text
this caused the pipeline failure
```

Context matters.

---

# 22. Errors Are Not Automatically Root Causes

Likewise:

```text
ERROR
```

does not mean:

```text
root cause
```

Suppose:

```text
ERROR: connection refused
ERROR: health check failed
ERROR: deployment failed
```

The investigation must determine how these events relate.

The first message might explain the later ones.

Or they might represent separate failures.

The system should not manufacture certainty.

---

# 23. Successful Steps Are Evidence Too

Failure analysis often focuses only on what failed.

But successful steps can eliminate possibilities.

Suppose:

```text
Checkout             PASS
Install Dependencies PASS
Lint                 PASS
Unit Tests           PASS
Build                PASS
Docker Build         FAIL
```

You now know:

- the repository was checked out
- dependencies were installed
- linting completed
- unit tests completed
- the normal build completed
- failure occurred during container construction

That information helps narrow the investigation.

Success is part of the evidence.

---

# 24. Missing Steps Can Also Matter

Consider:

```text
Checkout             PASS
Install Dependencies FAIL
Lint                 NOT RUN
Unit Tests           NOT RUN
Build                NOT RUN
```

You must not report:

```text
Unit tests passed.
```

They did not run.

There is an important difference between:

```text
PASS
FAIL
SKIPPED
CANCELLED
NOT RUN
```

A reliable triage system should not invent execution results for stages that never occurred.

---

# 25. Cancellation Is Different From Failure

A job can stop because someone or something cancelled it.

Example:

```text
Job cancelled by user.
```

That is different from:

```text
Test command failed.
```

Likewise, a pipeline may cancel downstream work because an earlier required job failed.

For example:

```text
Build       FAIL
Deploy      CANCELLED
```

The deploy job did not necessarily fail.

It may never have run.

Precise language matters.

---

# 26. Infrastructure Failure Is Different From Application Failure

Imagine:

```text
Runner lost communication with CI platform.
```

The application code may be completely correct.

The execution environment failed.

Similarly:

```text
No space left on device
```

may indicate a runner or build-environment problem rather than an application logic problem.

Useful triage should distinguish between categories such as:

```text
application
test
dependency
build
authentication
deployment
runner
infrastructure
external service
```

Project 001 begins with a controlled set of failure categories, but you should understand that real systems can require broader classification.

---

# 27. External Dependencies Complicate CI Failures

CI pipelines often depend on systems outside the repository.

For example:

```text
CI Job
  ├── Package Registry
  ├── Container Registry
  ├── Source Repository
  ├── Cloud API
  ├── Artifact Store
  └── Deployment Platform
```

If one external dependency fails, the CI job may fail.

This means:

```text
pipeline failure
```

does not automatically imply:

```text
bad code change
```

Sometimes the code is fine.

The surrounding delivery system is not.

---

# 28. Environment Differences Matter

A command might work locally and fail in CI.

Why?

Because the environments may differ.

Possible differences include:

- operating system
- runtime version
- installed packages
- environment variables
- permissions
- network access
- working directory
- filesystem layout
- available CPU
- available memory
- secrets
- service dependencies

For example:

```text
Developer Laptop:
Python 3.12

CI Runner:
Python 3.11
```

If the application requires Python 3.12 behavior, the difference may matter.

This is why:

> It works on my machine.

does not close a CI investigation.

---

# 29. Reproducibility Matters

A failure that happens every time is often easier to investigate than one that appears occasionally.

Consider:

```text
Run 1  PASS
Run 2  PASS
Run 3  FAIL
Run 4  PASS
Run 5  FAIL
```

This may indicate an intermittent problem.

Possible areas of investigation include:

- timing
- concurrency
- shared state
- external dependencies
- network instability
- test isolation
- resource contention

Project 001 does not attempt to solve every class of flaky behavior, but you should understand that:

```text
same pipeline
```

does not always mean:

```text
same result
```

under every environmental condition.

---

# 30. Failure Context Matters

A single error line is often insufficient.

Suppose you see:

```text
Permission denied
```

Useful questions include:

- Which command produced it?
- Which file or resource was involved?
- Which stage was running?
- What happened immediately before it?
- What was the exit code?
- Was authentication successful?
- Was the same operation previously successful?

Compare:

```text
Permission denied
```

with:

```text
Stage: deployment
Command: ./scripts/deploy.sh
Target: deployment artifact
Error: Permission denied
Exit code: 126
```

The second representation provides much more context.

This is one reason Project 001 performs evidence extraction before AI analysis.

---

# 31. Temporal Context Matters

Logs usually represent events over time.

Example:

```text
10:01:00 Job started
10:01:02 Dependencies installed
10:01:15 Tests started
10:01:40 External test service became unavailable
10:01:45 Integration test failed
10:01:46 Job failed
```

Order matters.

If you remove temporal relationships, you may lose useful clues.

This becomes especially important in more advanced incident-analysis systems.

For Project 001, the key lesson is simpler:

> Preserve enough context to understand how the failure developed.

---

# 32. Noise Makes Failure Analysis Harder

CI logs can be large.

They may contain:

- progress indicators
- dependency download messages
- repeated status messages
- warnings
- debug output
- timestamps
- framework banners
- successful operations
- irrelevant environment information

The useful failure evidence may represent only a small portion of the log.

Conceptually:

```text
10,000 Log Lines
       ↓
Normalization
       ↓
Relevant Signals
       ↓
Evidence
```

But reducing logs must be done carefully.

Remove too little and the system is overwhelmed with noise.

Remove too much and you may destroy the evidence needed for investigation.

---

# 33. Normalization Is Not Root-Cause Analysis

Project 001 includes a normalization stage:

```text
Raw CI Input
     ↓
Normalization
```

Normalization prepares input for consistent processing.

It might eventually deal with things such as:

- line endings
- formatting inconsistencies
- empty lines
- repeated noise
- representation differences

But normalization should not secretly become:

```text
guess the root cause
```

Each component should have a clear responsibility.

You will build normalization later in:

```text
build/03-normalize-ci-logs.md
```

---

# 34. Redaction Is Not Failure Classification

Likewise:

```text
Redaction
```

has a security responsibility.

Its job is not to decide whether the failure was:

```text
dependency
test
build
deployment
```

It protects supported sensitive values.

Keeping responsibilities separated makes the system easier to:

- reason about
- test
- secure
- debug
- replace

This separation is reflected throughout the Project 001 architecture.

---

# 35. Evidence Extraction Is Not AI Analysis

The evidence extractor should identify useful observable information.

For example:

```text
stage: unit-tests
exit_code: 1
error_type: AssertionError
relevant_line: expected 200, received 500
```

That is different from:

```text
The API implementation probably contains a regression.
```

The second statement is interpretation.

Project 001 intentionally keeps these responsibilities separate:

```text
Deterministic Evidence
        ↓
Bounded AI Analysis
```

Not:

```text
AI decides what happened
        ↓
AI declares its own evidence
```

---

# 36. A Useful Failure Record

As you progress through the project, think about the kinds of information that make a CI failure useful for investigation.

A conceptual failure record might contain:

```text
Pipeline:
application-ci

Job:
test

Stage:
unit-tests

Command:
python -m pytest

Status:
failed

Exit Code:
1

Relevant Evidence:
AssertionError: expected 201, received 500
```

Not every CI platform provides exactly these fields.

Not every failure contains all of them.

But this structure demonstrates the type of context an investigation benefits from.

---

# 37. Missing Evidence Must Remain Missing

Suppose the system does not know the exit code.

A bad implementation might produce:

```text
exit_code: 1
```

because:

> Most failures use exit code 1.

That is fabrication.

A safer representation is conceptually:

```text
exit_code: unknown
```

or another explicit missing-value representation defined by the system contract.

Never replace missing evidence with a plausible guess.

This rule applies to both deterministic code and AI-generated analysis.

---

# 38. Unknown Is a Valid Engineering Answer

Engineers sometimes feel pressure to identify a root cause immediately.

But:

```text
insufficient evidence
```

can be the correct conclusion.

Suppose the only available information is:

```text
Job failed.
```

A model might generate an elaborate explanation.

That does not mean the explanation is supported.

A responsible system should be able to communicate:

> The available evidence is insufficient to determine a likely cause with useful confidence.

Project 001 values grounded uncertainty over confident fabrication.

---

# 39. Confidence Must Be Grounded in Evidence

Later, AI-generated triage may include a confidence assessment.

Do not interpret:

```text
confidence: high
```

as proof.

Confidence should help communicate the strength of the interpretation.

It does not transform interpretation into evidence.

Conceptually:

```text
Evidence
   ↓
Interpretation
   ↓
Confidence
```

Not:

```text
Confidence
   ↓
Truth
```

---

# 40. Correlation Is Not Automatically Causation

Suppose a warning appears five seconds before a test failure.

That does not automatically mean the warning caused the failure.

Example:

```text
WARNING: deprecated configuration option
...
AssertionError: expected 200, received 500
```

The events occurred in the same log.

That alone does not establish a causal relationship.

AI systems can be especially prone to constructing plausible stories around nearby events.

Project 001 therefore emphasizes evidence-grounded analysis.

---

# 41. CI Logs Can Contain Contradictory Signals

Real logs are not always clean.

You might encounter:

```text
Build completed successfully
...
ERROR: artifact upload failed
...
Job status: failed
```

Did the build fail?

The build itself may have succeeded.

The job failed later during artifact upload.

A weak triage system might say:

```text
Build failed.
```

A better investigation distinguishes:

```text
Build:
successful

Artifact upload:
failed

Overall job:
failed
```

Precision matters.

---

# 42. The Overall Job Status Is Not the Root Cause

A CI platform might provide:

```text
status: failed
```

That tells you the outcome.

It does not explain the cause.

Think of:

```text
status = failed
```

as a trigger for investigation.

Not the investigation result.

---

# 43. Start With Facts

When investigating a CI failure manually, begin with what you can establish.

For example:

```text
Pipeline: application-ci
Job: test
Stage: unit-tests
Status: failed
Exit code: 1
Failed test: test_create_user
Observed error: AssertionError
```

Then ask:

```text
What does this evidence suggest?
```

Do not begin with:

```text
I think the database is broken.
```

and then search only for evidence supporting that theory.

That creates confirmation bias.

The same principle should influence the triage engine.

---

# 44. A Practical Failure Investigation Sequence

A useful starting sequence is:

```text
1. Confirm the failure
2. Identify the failed job
3. Identify the failed stage or step
4. Identify the command or operation
5. Check the exit status if available
6. Read the immediate error
7. Inspect surrounding context
8. Look for earlier contributing failures
9. Separate warnings from failure evidence
10. Identify successful preceding stages
11. Identify skipped or cancelled work
12. Determine what is known
13. Determine what is unknown
14. Form a hypothesis
15. Test the hypothesis
16. Verify recovery
```

Project 001 automates parts of this process.

It does not eliminate the engineering reasoning behind it.

---

# 45. Example Investigation — Dependency Failure

Consider:

```text
[10:02:01] Starting dependency installation
[10:02:02] python -m pip install -r requirements.txt
[10:02:05] ERROR: Could not find a version that satisfies the requirement example-package==9.9.9
[10:02:05] ERROR: No matching distribution found for example-package==9.9.9
[10:02:05] Process completed with exit code 1
```

What can you directly observe?

```text
Stage:
dependency installation

Command:
python -m pip install -r requirements.txt

Requested dependency:
example-package==9.9.9

Observed error:
No matching distribution found

Exit code:
1
```

What can you **not** yet prove?

You cannot automatically prove:

```text
The package repository deleted version 9.9.9.
```

You also cannot automatically prove:

```text
The developer typed the wrong version.
```

Both might be hypotheses.

Neither is direct evidence from this log alone.

---

# 46. Example Investigation — Unit-Test Failure

Consider:

```text
[10:15:00] Running unit tests
[10:15:03] tests/test_api.py::test_health PASSED
[10:15:04] tests/test_api.py::test_create_user FAILED
[10:15:04] AssertionError: expected 201, received 500
[10:15:05] 1 failed, 41 passed
[10:15:05] Process completed with exit code 1
```

Observed evidence:

```text
Test stage ran.
41 tests passed.
1 test failed.
Failed test:
tests/test_api.py::test_create_user

Expected:
201

Received:
500

Exit code:
1
```

Possible interpretation:

```text
The create-user path returned an unexpected server error.
```

But the log does not yet prove exactly why the server returned 500.

Further evidence may be required.

---

# 47. Example Investigation — Authentication Failure

Consider:

```text
[11:00:00] Authenticating to container registry
[11:00:01] ERROR: authentication failed
[11:00:01] ERROR: unauthorized
[11:00:01] Process completed with exit code 1
```

Observed evidence:

```text
Operation:
registry authentication

Result:
failed

Message:
unauthorized

Exit code:
1
```

Potential hypotheses include:

```text
missing credential
invalid credential
expired credential
insufficient permission
incorrect registry configuration
```

The available evidence may not distinguish among them.

The correct triage report should preserve that uncertainty.

---

# 48. Example Investigation — Timeout

Consider:

```text
[12:00:00] Integration tests started
[12:15:00] ERROR: Job exceeded maximum execution time of 15 minutes
[12:15:00] Job terminated
```

Observed evidence:

```text
Stage:
integration tests

Maximum duration:
15 minutes

Outcome:
job terminated after timeout
```

You cannot immediately conclude:

```text
The tests contain a deadlock.
```

That may be one hypothesis.

Other possibilities exist.

Again:

```text
evidence first
interpretation second
```

---

# 49. How Project 001 Processes a Failure

The project eventually transforms CI failure information through several controlled stages.

```text
Raw CI Failure
      ↓
Ingestion
      ↓
Normalization
      ↓
Secret Redaction
      ↓
Deterministic Evidence Extraction
      ↓
Failure Context Classification
      ↓
Bounded AI Analysis
      ↓
Structured Output Validation
      ↓
Safety Checks
      ↓
Triage Report
```

Each stage has a different responsibility.

This separation is deliberate.

---

# 50. Ingestion

Ingestion answers:

> Can the system accept and load the failure data?

It should not immediately ask:

> What is the root cause?

Those are different responsibilities.

Later you will implement ingestion under:

```text
src/ci_triage/ingestion/
```

with:

```text
loader.py
normalizer.py
```

The guided implementation begins in:

```text
build/02-load-ci-failure-data.md
```

---

# 51. Normalization

Normalization answers:

> Can this input be represented consistently enough for downstream processing?

It prepares the data.

It does not decide the final cause.

You will implement it in:

```text
src/ci_triage/ingestion/normalizer.py
```

through:

```text
build/03-normalize-ci-logs.md
```

---

# 52. Redaction

Redaction answers:

> Does the input contain supported sensitive values that must not continue unchanged toward the external AI boundary?

This stage belongs before AI processing.

You will implement it under:

```text
src/ci_triage/redaction/
```

The implementation includes:

```text
redactor.py
patterns.py
```

and is introduced in:

```text
build/04-redact-sensitive-data.md
```

---

# 53. Deterministic Evidence Extraction

Evidence extraction answers:

> What useful observable failure signals can deterministic code identify?

Examples may include:

- exit codes
- error lines
- failed stage
- relevant failure messages
- recognized failure context

The implementation lives under:

```text
src/ci_triage/evidence/
```

with:

```text
extractor.py
classifier.py
```

The build begins in:

```text
build/05-extract-deterministic-evidence.md
```

---

# 54. Failure Context Classification

Classification helps organize the failure.

For the Project 001 learning environment, useful categories may correspond to scenarios such as:

```text
dependency installation
unit test
lint
build
Docker build
authentication
deployment
timeout
unknown or ambiguous
```

The classifier should not pretend every failure fits perfectly into a known category.

Unknown or ambiguous input must remain possible.

---

# 55. Bounded AI Analysis

Only after earlier controls have prepared the context does AI analysis occur.

Conceptually:

```text
Raw CI Data
      ↓
Local Processing
      ↓
Sensitive Data Redaction
      ↓
Evidence Extraction
      ↓
Context Minimization
      ↓
-----------------------------
     AI TRUST BOUNDARY
-----------------------------
      ↓
Bounded AI Analysis
```

The AI receives context for analysis.

It does not receive operational authority.

---

# 56. Structured Validation

The model's response is not automatically trusted.

It moves through:

```text
AI Response
    ↓
Output Validation
    ↓
Safety Checks
```

Only then can the application produce an accepted AI-assisted triage result.

If validation fails, the project has explicit failure handling.

---

# 57. Fallback

If the AI provider is unavailable:

```text
Deterministic Evidence
        ↓
AI Request
        ↓
Provider Unavailable
        ↓
Fallback
        ↓
Deterministic Evidence Preserved
        ↓
Engineer-Facing Report
```

The project does not throw away useful evidence merely because one external dependency failed.

This is an important reliability principle.

---

# 58. Why AI Comes Later in the Pipeline

You may wonder:

> If AI can read logs, why not send the raw log directly to the model?

Because that would bypass several engineering controls.

You would lose explicit control over:

- secret handling
- evidence extraction
- context minimization
- trust boundaries
- deterministic behavior
- validation
- fallback
- auditability

Project 001 is intentionally teaching:

> AI should be integrated into a system, not substituted for the system.

---

# 59. Common Failure-Analysis Mistakes

Avoid these habits.

## Mistake 1 — Reading Only the Last Line

```text
Process exited with code 1
```

may only tell you the final outcome.

---

## Mistake 2 — Treating Every Error as Root Cause

Multiple errors can belong to one failure chain.

---

## Mistake 3 — Ignoring Successful Steps

Successful stages help narrow the investigation.

---

## Mistake 4 — Treating Skipped Work as Failed Work

```text
NOT RUN
```

is not the same as:

```text
FAIL
```

---

## Mistake 5 — Assuming the Code Change Caused the Failure

External services and CI infrastructure can fail too.

---

## Mistake 6 — Guessing Missing Evidence

Unknown information should remain unknown.

---

## Mistake 7 — Sending Everything to AI

Raw logs may contain noise, secrets, and adversarial content.

---

## Mistake 8 — Treating AI Confidence as Proof

Confidence does not replace evidence.

---

## Mistake 9 — Fixing Before Understanding

A random change that makes the pipeline green does not necessarily establish what failed.

---

## Mistake 10 — Declaring Recovery Without Verification

A system is not proven healthy simply because one error disappeared.

---

# 60. A Better Troubleshooting Mindset

Instead of asking only:

> What broke?

ask:

```text
What failed?

Where did it fail?

What executed successfully before the failure?

What did not execute?

What evidence do I have?

What evidence am I missing?

What is observed?

What is inferred?

What external dependencies were involved?

Could this be an environment problem?

Could this be an authentication problem?

Could this be infrastructure rather than application code?

What hypothesis best fits the evidence?

How can I test that hypothesis?

How will I verify recovery?
```

That mindset is more valuable than memorizing error messages.

---

# 61. What AI Adds

AI can help after useful context has been prepared.

For example:

```text
Deterministic Evidence

Stage:
dependency-install

Exit Code:
1

Relevant Error:
No matching distribution found for example-package==9.9.9
```

AI may help produce:

```text
Likely Cause:
The requested dependency version may not be available from the
configured package source.

Recommended Investigation:
Verify the dependency declaration and confirm that the requested
version exists in the configured package repository.
```

That is useful because it translates evidence into an investigation path.

But the evidence remains available separately.

---

# 62. What AI Must Not Add

AI must not fabricate missing facts.

If the log does not contain:

```text
registry.example.com
```

the model should not invent:

```text
The failure occurred because registry.example.com was unavailable.
```

Likewise, if the evidence does not establish:

```text
expired token
```

the report should not present token expiration as observed fact.

Project 001 will evaluate AI groundedness specifically because plausible fabrication is dangerous in operational systems.

---

# 63. Why Groundedness Matters

A model response can sound technically impressive and still be wrong.

For example:

```text
The deployment failed because Kubernetes exhausted the node's memory.
```

That may sound plausible.

But if the input contains no Kubernetes information and no memory evidence, the conclusion is unsupported.

A grounded response should stay close to the supplied evidence.

When evidence is insufficient, uncertainty is preferable to invention.

---

# 64. Failure Classification Is Useful but Imperfect

Categories help engineers organize incidents.

For example:

```text
dependency_failure
test_failure
lint_failure
build_failure
container_build_failure
authentication_failure
deployment_failure
timeout
```

But real failures can overlap.

Example:

```text
Docker build
    ↓
RUN pip install
    ↓
Private registry authentication fails
```

Is that:

```text
Docker build failure
```

or:

```text
authentication failure
```

Both descriptions contain useful information.

The system design should avoid pretending that operational failures always fit perfectly into one label.

---

# 65. Failure Stage and Failure Cause Are Different

This distinction is critical.

Consider:

```text
Failed Stage:
Docker Build
```

and:

```text
Likely Cause:
Dependency repository authentication failed during a RUN instruction.
```

The stage tells you:

```text
where
```

The likely cause tries to explain:

```text
why
```

Do not confuse them.

---

# 66. Failure Category and Root Cause Are Different

Likewise:

```text
category:
authentication_failure
```

does not necessarily tell you the root cause.

The underlying cause might be:

```text
expired credential
```

or:

```text
incorrect secret mapping
```

or:

```text
insufficient permission
```

Classification organizes evidence.

It does not magically complete the investigation.

---

# 67. Root Cause Requires Evidence

The phrase:

```text
root cause
```

should be used carefully.

A likely explanation is not automatically a confirmed root cause.

During initial triage, language such as:

```text
likely cause
```

may be more appropriate when the available evidence is incomplete.

That is why Project 001 uses a triage report rather than pretending every analysis is a completed post-incident investigation.

---

# 68. A Green Pipeline Does Not Prove Everything Is Healthy

This project focuses on failed CI jobs, but remember:

```text
pipeline passed
```

does not prove:

```text
system is perfect
```

Tests may be incomplete.

Observability may be missing.

A production problem may not be covered by CI.

Security issues may remain undetected.

A pipeline tells you about the checks it actually performed.

Nothing more.

This same discipline applies to failure analysis:

> Know what the evidence proves and what it does not prove.

---

# 69. A Failed Pipeline Does Not Prove the Code Is Bad

Likewise:

```text
pipeline failed
```

does not automatically mean:

```text
developer introduced defective code
```

The failure could originate from:

```text
CI infrastructure
external dependency
credential configuration
network
runner
artifact repository
deployment platform
```

Good triage avoids premature blame.

It follows evidence.

---

# 70. What You Should Capture From a Failure

When examining a CI failure, useful information may include:

```text
pipeline identifier
job
stage or step
command
status
exit code
timestamp
relevant stdout
relevant stderr
error messages
warnings
successful preceding stages
skipped or cancelled stages
external dependency involved
failure duration
timeout information
```

Not every source provides every field.

The system should represent what it knows without fabricating what it does not.

---

# 71. The Investigation Loop

A useful engineering loop is:

```text
Observe
   ↓
Collect Evidence
   ↓
Form Hypothesis
   ↓
Test Hypothesis
   ↓
Change Something
   ↓
Observe Again
   ↓
Verify
```

If the hypothesis is wrong:

```text
Evidence
   ↓
New Hypothesis
   ↓
New Test
```

This is normal.

Troubleshooting is often iterative.

---

# 72. Do Not Change Multiple Things Without Reason

Imagine a pipeline fails.

You simultaneously:

```text
upgrade Python
change dependency versions
replace credentials
increase timeout
modify Dockerfile
```

The pipeline passes.

What fixed it?

You may not know.

That makes the investigation less useful.

When practical, make controlled changes that test specific hypotheses.

This creates stronger evidence.

---

# 73. Preserve the Original Failure Evidence

Before changing the system, preserve enough information to understand the original state.

Otherwise:

```text
Failure
   ↓
Random Changes
   ↓
Pipeline Passes
   ↓
Original Evidence Lost
```

You may have restored service without learning what happened.

Project 001's evidence and failure exercises encourage you to preserve useful investigation artifacts.

---

# 74. CI Failure Triage Is Not Incident Response

These areas can overlap, but they are not identical.

A CI failure may affect only software delivery.

A production incident may affect customers or live systems.

For Project 001, the focus is:

```text
failed CI/CD execution
```

not:

```text
full autonomous production incident management
```

Keeping scope clear prevents the Foundation project from becoming unnecessarily complex.

Later VERIQTA projects can build on these concepts.

---

# 75. CI Failure Triage Is Not Log Summarization

Another important distinction:

A triage engine is not valuable merely because it can shorten a log.

This:

```text
The build failed. There were several errors.
```

is a summary.

Useful triage should organize information around investigation.

For example:

```text
Failed Stage:
dependency-install

Exit Code:
1

Observed Evidence:
Requested package version could not be resolved.

Likely Cause:
The requested dependency version may not be available from the
configured package source.

Recommended Investigation:
Verify the dependency declaration and package source.

AI Remediation:
Not permitted
```

That is much closer to an engineering aid.

---

# 76. CI Failure Triage Is Not Autonomous Operations

Project 001 stops before autonomous action.

The flow ends with:

```text
Triage Report
      ↓
Engineer Review
```

It does not become:

```text
Triage Report
      ↓
AI Executes Fix
      ↓
Production Modified
```

That boundary is intentional.

The project teaches how to use AI where interpretation is useful without giving probabilistic output unrestricted operational authority.

---

# 77. How This Note Connects to the Rest of Project 001

You now understand the failure domain that the project will operate on.

The next notes deepen individual parts of the system.

You will study:

```text
03-understanding-ci-logs.md
        ↓
04-exit-codes-stdout-and-stderr.md
        ↓
05-structured-vs-unstructured-logs.md
        ↓
06-secret-redaction.md
        ↓
07-evidence-vs-ai-analysis.md
        ↓
08-llms-in-operational-systems.md
        ↓
09-structured-ai-output.md
        ↓
10-json-schema-validation.md
        ↓
11-model-failure-and-fallbacks.md
        ↓
12-prompt-injection-in-operational-data.md
        ↓
13-observability-for-ai-services.md
        ↓
14-security-and-trust-boundaries.md
        ↓
15-production-design-considerations.md
        ↓
16-commands-and-reference.md
```

Each note prepares you for later implementation.

---

# 78. Knowledge Check

Answer these questions in your own words.

### Question 1

What is the difference between a pipeline, job, step, and command?

### Question 2

Why does a non-zero exit code not necessarily tell you the root cause?

### Question 3

What is the difference between the failed stage and the failure cause?

### Question 4

Why can the last error in a CI log be misleading?

### Question 5

How can successful pipeline stages help an investigation?

### Question 6

What is the difference between:

```text
FAIL
```

and:

```text
NOT RUN
```

### Question 7

Why should a cancelled job not automatically be classified as a failed command?

### Question 8

Give three examples of failures that could occur even when the application code itself is correct.

### Question 9

Why can authentication failures create an additional security concern during troubleshooting?

### Question 10

What is a failure chain?

### Question 11

Why should warnings not automatically be treated as root causes?

### Question 12

Why should missing evidence remain explicitly unknown rather than being guessed?

### Question 13

What is the difference between failure classification and root-cause determination?

### Question 14

Why might a Docker build failure actually involve a dependency or authentication problem?

### Question 15

Why is an external AI provider intentionally placed later in the Project 001 processing pipeline?

### Question 16

What useful information should remain available if the AI provider fails?

### Question 17

Why is:

```text
pipeline failed
```

not enough information for useful triage?

### Question 18

Why is a plausible AI explanation not automatically trustworthy?

### Question 19

Why should recovery be verified after a change?

### Question 20

Why is Project 001 better described as a triage system than an autonomous remediation system?

---

# 79. Practical Reasoning Exercise

Consider this pipeline:

```text
09:00:00 Checkout repository
09:00:03 Checkout completed

09:00:04 Install dependencies
09:00:20 Dependencies installed

09:00:21 Run lint
09:00:25 Lint completed successfully

09:00:26 Run unit tests
09:00:30 84 tests passed

09:00:31 Build application
09:00:50 Build completed successfully

09:00:51 Build container
09:00:55 Authenticating to private container registry
09:00:56 ERROR: unauthorized
09:00:56 ERROR: authentication failed
09:00:56 Container build workflow aborted
09:00:56 Process completed with exit code 1

09:00:57 Deploy
09:00:57 NOT RUN
```

Without using AI, answer:

1. Which stages completed successfully?
2. Which stage was active when the failure occurred?
3. What directly observed error is available?
4. What was the exit code?
5. Did deployment fail?
6. Did deployment run?
7. Is credential expiration proven?
8. Is authentication failure proven?
9. What information would you investigate next?
10. Which statements would be evidence?
11. Which statements would be hypotheses?

A careful answer should recognize:

```text
Checkout:
successful

Dependency installation:
successful

Lint:
successful

Unit tests:
successful

Application build:
successful

Container build workflow:
failed during registry authentication

Observed error:
unauthorized / authentication failed

Exit code:
1

Deployment:
not run
```

You can establish the authentication failure from the available evidence.

You cannot establish exactly why authentication failed without additional evidence.

That distinction is central to Project 001.

---

# 80. Readiness Check

Before continuing, you should be able to explain:

- what CI/CD pipelines do
- what pipelines, jobs, steps, and commands represent
- how commands contribute to CI job status
- why exit codes are useful but incomplete
- why failures can originate at different system layers
- why the failed stage is not automatically the root cause
- what a failure chain is
- why the final error may only be a consequence
- why successful stages matter
- why skipped work must not be described as failed
- why cancelled work is different from failed work
- why CI infrastructure can fail independently of application code
- why external dependencies complicate failure analysis
- why local and CI environments may behave differently
- why failure context matters
- why missing evidence must remain unknown
- why confidence does not turn interpretation into fact
- why correlation does not automatically prove causation
- why evidence extraction and AI analysis are separate
- why AI analysis comes after deterministic processing
- why fallback preserves deterministic evidence
- why triage ends with engineer review rather than automatic remediation

You do not need to diagnose every possible CI/CD failure.

You need to understand how to reason about the evidence.

---

# 81. Where You Go Next

Continue to:

```text
notes/03-understanding-ci-logs.md
```

The next note focuses specifically on the material that carries much of the evidence you will investigate:

**CI logs.**

You will learn how to read them as engineering evidence rather than as a wall of terminal output.

---

## Final Takeaway

A CI failure is not simply:

```text
something went wrong
```

A useful investigation asks:

```text
Where did it fail?
        ↓
What actually ran?
        ↓
What succeeded?
        ↓
What did not run?
        ↓
What was directly observed?
        ↓
What evidence is relevant?
        ↓
What remains unknown?
        ↓
What hypothesis fits the evidence?
        ↓
How can that hypothesis be tested?
        ↓
How will recovery be verified?
```

Project 001 will eventually automate parts of that process.

But the system should never lose the principle underneath it:

> **Evidence first. Interpretation second. Action only after appropriate human review.**
```
