# AI-Powered DevOps Projects


<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/06dafafd-b4a2-4f49-9d8c-3e4f7a2c9172" />


> Build AI-powered systems for real DevOps, cloud, SRE, platform engineering, security, observability, infrastructure, reliability, and FinOps problems.

This repository contains **100 hands-on engineering projects** designed to help you learn by building systems based on problems engineers encounter in real environments.

You will not just connect an AI API to a script and call it an AI project.

You will learn the engineering concepts behind each system, design the architecture, build the implementation, test it, break it safely, investigate failures, recover it, secure it, observe it, and document what you built.

By the time you complete a project, you should be able to explain:

- **What you built**
- **What problem it solves**
- **How the architecture works**
- **Why you made your engineering decisions**
- **Where AI is used**
- **Where deterministic engineering remains in control**
- **How you tested the system**
- **How the system fails**
- **How you recover it**
- **What you would change before production**

---

## Repository Navigation

- [Project Catalogue](#project-catalogue)
- [Learning Paths](docs/learning-paths.md)
- [Project Standards](PROJECT-STANDARDS.md)
- [Portfolio Guidance](docs/portfolio-guidance.md)
- [Submission Guidelines](docs/submission-guidelines.md)
- [AI Safety Standards](docs/ai-safety-standards.md)
- [Security Policy](SECURITY.md)
- [Contributing](CONTRIBUTING.md)
- [Roadmap](ROADMAP.md)
- [License](LICENSE)

---

# What You Will Do Here

Each project places you inside an engineering problem.

A CI pipeline is failing.

A Kubernetes workload will not start.

Infrastructure has drifted from its approved configuration.

An incident is generating hundreds of alerts.

Cloud spending suddenly increases.

A deployment succeeds, but production becomes unhealthy.

An AI-assisted operational system receives unsafe input.

A critical service needs to recover from infrastructure failure.

Your job is not simply to follow commands.

You will learn enough about the problem to understand it, build a solution, verify the result, investigate failures, and make engineering decisions of your own.

```text
Learn
  ↓
Understand
  ↓
Design
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
Document
  ↓
Explain
```

---

# Who This Repository Is For

This repository is designed for you if you are learning or working in:

- DevOps Engineering
- Site Reliability Engineering
- Platform Engineering
- Cloud Engineering
- Infrastructure Engineering
- DevSecOps
- Systems Engineering
- Kubernetes
- Infrastructure as Code
- Observability
- FinOps
- Reliability Engineering
- AI for IT Operations
- Software Engineering with cloud or operations responsibilities

You can also use these projects if you are:

- preparing for your first engineering role
- moving into DevOps, cloud, SRE, or platform engineering
- building a technical GitHub portfolio
- preparing for technical interviews
- learning how AI fits into engineering workflows
- moving beyond isolated tutorials
- strengthening your production engineering skills

You do not need to complete all 100 projects.

Choose the projects that support the engineer you want to become.

---

# How the Learning Experience Works

These are not copy-and-paste projects.

You will receive guidance, explanations, commands, architecture diagrams, expected results, troubleshooting guidance, tests, failure scenarios, and reference material.

But the amount of guidance changes as projects become more advanced.

## Foundation

You receive detailed explanations and guided implementation.

```text
Learn → Follow → Build → Verify
```

## Intermediate

You receive requirements, guidance, checkpoints, and troubleshooting support while making more implementation decisions yourself.

```text
Understand → Build → Troubleshoot → Improve
```

## Advanced

You make and defend architecture, security, reliability, scalability, and operational decisions.

```text
Design → Implement → Test → Defend
```

## Capstone

You receive an engineering problem, requirements, constraints, and acceptance criteria.

You determine how the system should be built.

```text
Problem → Architecture → Engineering → Operations → Evidence
```

The goal is to gradually remove the training wheels.

---

# What Makes These Projects Different

A project is not complete because an application starts successfully.

Depending on the system, you may need to prove that it can:

- handle expected workloads
- reject invalid input
- protect sensitive information
- survive dependency failure
- detect unsafe AI output
- continue safely when AI is unavailable
- produce useful telemetry
- enforce permissions
- recover from controlled failures
- verify that recovery actually worked

Projects may include:

- realistic engineering scenarios
- architecture design
- working implementations
- infrastructure as code
- CI/CD pipelines
- automated tests
- security controls
- AI guardrails
- structured output validation
- logs, metrics, and traces
- dashboards and alerts
- controlled failure injection
- troubleshooting exercises
- recovery verification
- performance testing
- cost analysis
- policy validation
- production-readiness reviews
- engineering decision records
- portfolio evidence
- interview preparation

Not every project needs every component.

You will use the components required to solve the actual engineering problem.

---

# How Each Project Is Organized

Projects share a familiar learning structure without forcing every engineering system into the same technical architecture.

```text
projects/
└── NNN-project-name/
    │
    ├── README.md
    │
    ├── notes/
    ├── learn/
    ├── build/
    ├── architecture/
    │
    ├── [project-specific implementation]
    │
    ├── tests/
    ├── failures/
    ├── evidence/
    ├── portfolio/
    │
    └── solution/
```

## `README.md`

Start here.

The project README explains:

- the engineering problem
- what you will build
- why the system matters
- prerequisites
- difficulty
- estimated completion time
- technologies
- architecture
- expected outcome
- project milestones
- completion requirements

## `notes/`

Learn the concepts you need before implementing them.

The notes may cover:

- Linux
- networking
- APIs
- Python
- containers
- Kubernetes
- Terraform
- CI/CD
- observability
- cloud services
- security
- distributed systems
- reliability
- AI models
- structured outputs
- agents
- retrieval
- evaluation
- prompt injection
- model failure
- cost
- permissions

## `learn/`

Connect the theory to the project.

You will understand:

```text
Engineering problem
        ↓
Architecture
        ↓
Components
        ↓
Data flow
        ↓
Environment
        ↓
Implementation strategy
```

## `build/`

Build the system through progressive engineering milestones.

Each milestone should help you understand:

- what you are building
- why you need it
- how it works
- what commands or code you need
- what result to expect
- how to verify the result
- what can fail
- how to troubleshoot it

## `architecture/`

Understand and document how the system works.

Depending on the project, this may contain:

- system architecture
- component diagrams
- data flows
- trust boundaries
- dependency diagrams
- deployment architecture
- failure domains
- architecture decision records

## Project-Specific Implementation

The actual implementation directories depend on the system.

A Kubernetes project might contain:

```text
kubernetes/
helm/
policies/
```

An infrastructure project might contain:

```text
terraform/
modules/
policies/
```

An observability project might contain:

```text
monitoring/
dashboards/
alerts/
```

An AI system might contain:

```text
prompts/
schemas/
evaluations/
```

A service might contain:

```text
src/
api/
config/
```

The learning structure stays familiar.

The engineering architecture changes when the problem changes.

## `tests/`

Prove that the system behaves as expected.

Tests may include:

- unit tests
- integration tests
- infrastructure tests
- policy tests
- security tests
- AI evaluation tests
- acceptance tests
- performance tests

## `failures/`

Break the system safely.

You may intentionally create:

- invalid configurations
- dependency failures
- network problems
- authentication failures
- permission errors
- malformed data
- resource exhaustion
- unavailable services
- model failures
- invalid AI responses
- timeouts
- unsafe model output

Then investigate:

```text
What failed?
     ↓
What evidence exists?
     ↓
What changed?
     ↓
What is your hypothesis?
     ↓
How can you test it?
     ↓
How can you recover?
     ↓
How do you verify recovery?
```

## `evidence/`

Keep proof of what you built and tested.

Evidence may include:

```text
evidence/
├── screenshots/
├── terminal-output/
├── test-results/
├── logs/
└── sample-output/
```

Do not collect screenshots just to fill your repository.

Capture evidence that proves something important happened.

## `portfolio/`

Turn the engineering work into something you can explain professionally.

This section may include:

- project summary
- skills demonstrated
- resume guidance
- recruiter explanation
- interview preparation
- GitHub presentation guidance
- LinkedIn project guidance

## `solution/`

Use the solution only after attempting the project yourself.

The solution exists to help you:

- compare approaches
- investigate differences
- understand another implementation
- study alternative engineering decisions
- verify difficult sections

Do not present the provided solution as your own work.

---

# Build With AI, Not Around AI

These projects use AI where AI provides useful engineering assistance.

AI does not replace deterministic engineering controls.

You will learn to distinguish between:

```text
FACTS
Evidence directly supported by the system.

AI ANALYSIS
Interpretation generated from available evidence.

RECOMMENDATIONS
Possible actions that still require validation or authorization.
```

Where appropriate, you will implement:

- input validation
- structured outputs
- schema validation
- secret redaction
- data minimization
- prompt-injection defenses
- least-privilege access
- tool restrictions
- human approval
- audit logging
- timeouts
- rate limits
- deterministic verification
- non-AI fallback behavior

Read the [AI Safety Standards](docs/ai-safety-standards.md) before implementing model or agent integrations.

---

# Project Catalogue

The repository contains **100 projects across 10 engineering tracks**.

Click any project to open its project directory.

---

## Track 1: AI for CI/CD and Software Delivery

| ID | Project | Level |
| --- | --- | --- |
| 001 | [AI-Powered CI Failure Triage Engine](projects/001-ai-powered-ci-failure-triage-engine/README.md) | Foundation |
| 002 | [Intelligent Flaky Test Detection Service](projects/002-intelligent-flaky-test-detection-service/README.md) | Intermediate |
| 003 | [Pull Request Risk Scoring Gate](projects/003-pull-request-risk-scoring-gate/README.md) | Intermediate |
| 004 | [AI-Assisted Pipeline Generator with Policy Guardrails](projects/004-ai-assisted-pipeline-generator-with-policy-guardrails/README.md) | Intermediate |
| 005 | [Deployment Log Root-Cause Correlator](projects/005-deployment-log-root-cause-correlator/README.md) | Intermediate |
| 006 | [Release Readiness Decision Support System](projects/006-release-readiness-decision-support-system/README.md) | Advanced |
| 007 | [CI Pipeline Performance Advisor](projects/007-ci-pipeline-performance-advisor/README.md) | Intermediate |
| 008 | [Build Dependency Failure Predictor](projects/008-build-dependency-failure-predictor/README.md) | Advanced |
| 009 | [Pipeline Configuration Drift Detector](projects/009-pipeline-configuration-drift-detector/README.md) | Intermediate |
| 010 | [Multi-Repository Release Orchestrator](projects/010-multi-repository-release-orchestrator/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 2: AI for Incident Response and SRE

| ID | Project | Level |
| --- | --- | --- |
| 011 | [Incident Evidence Collection Assistant](projects/011-incident-evidence-collection-assistant/README.md) | Foundation |
| 012 | [Alert Deduplication and Incident Clustering Service](projects/012-alert-deduplication-and-incident-clustering-service/README.md) | Intermediate |
| 013 | [SLO Breach Investigation Assistant](projects/013-slo-breach-investigation-assistant/README.md) | Intermediate |
| 014 | [Incident Timeline Reconstruction Engine](projects/014-incident-timeline-reconstruction-engine/README.md) | Intermediate |
| 015 | [Runbook Retrieval and Recommendation Service](projects/015-runbook-retrieval-and-recommendation-service/README.md) | Intermediate |
| 016 | [Human-in-the-Loop Incident Commander Copilot](projects/016-human-in-the-loop-incident-commander-copilot/README.md) | Advanced |
| 017 | [Post-Incident Review Drafting System](projects/017-post-incident-review-drafting-system/README.md) | Intermediate |
| 018 | [Recurring Incident Pattern Detector](projects/018-recurring-incident-pattern-detector/README.md) | Advanced |
| 019 | [On-Call Handover Intelligence Service](projects/019-on-call-handover-intelligence-service/README.md) | Intermediate |
| 020 | [Enterprise Incident Intelligence Platform](projects/020-enterprise-incident-intelligence-platform/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 3: AI for Observability and AIOps

| ID | Project | Level |
| --- | --- | --- |
| 021 | [Telemetry Quality Auditor](projects/021-telemetry-quality-auditor/README.md) | Foundation |
| 022 | [Log Pattern Discovery and Noise Reduction Service](projects/022-log-pattern-discovery-and-noise-reduction-service/README.md) | Intermediate |
| 023 | [Metric Anomaly Detection with Seasonal Baselines](projects/023-metric-anomaly-detection-with-seasonal-baselines/README.md) | Intermediate |
| 024 | [Distributed Trace Bottleneck Investigator](projects/024-distributed-trace-bottleneck-investigator/README.md) | Intermediate |
| 025 | [Observability Query Assistant](projects/025-observability-query-assistant/README.md) | Intermediate |
| 026 | [Service Health Summary Generator](projects/026-service-health-summary-generator/README.md) | Foundation |
| 027 | [Cardinality and Telemetry Cost Controller](projects/027-cardinality-and-telemetry-cost-controller/README.md) | Advanced |
| 028 | [Adaptive Trace Sampling Controller](projects/028-adaptive-trace-sampling-controller/README.md) | Advanced |
| 029 | [Observability Coverage Gap Analyzer](projects/029-observability-coverage-gap-analyzer/README.md) | Intermediate |
| 030 | [Unified AIOps Correlation Platform](projects/030-unified-aiops-correlation-platform/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 4: AI for Kubernetes and Cloud Operations

| ID | Project | Level |
| --- | --- | --- |
| 031 | [Kubernetes Workload Failure Investigator](projects/031-kubernetes-workload-failure-investigator/README.md) | Foundation |
| 032 | [Kubernetes Manifest Safety Reviewer](projects/032-kubernetes-manifest-safety-reviewer/README.md) | Intermediate |
| 033 | [Kubernetes Event Correlation Engine](projects/033-kubernetes-event-correlation-engine/README.md) | Intermediate |
| 034 | [Resource Request and Limit Advisor](projects/034-resource-request-and-limit-advisor/README.md) | Advanced |
| 035 | [Cluster Capacity and Scheduling Forecaster](projects/035-cluster-capacity-and-scheduling-forecaster/README.md) | Advanced |
| 036 | [Safe Kubernetes Remediation Assistant](projects/036-safe-kubernetes-remediation-assistant/README.md) | Advanced |
| 037 | [Multi-Cluster Configuration Drift Intelligence](projects/037-multi-cluster-configuration-drift-intelligence/README.md) | Advanced |
| 038 | [Kubernetes Upgrade Risk Analyzer](projects/038-kubernetes-upgrade-risk-analyzer/README.md) | Advanced |
| 039 | [Cloud Resource Misconfiguration Investigator](projects/039-cloud-resource-misconfiguration-investigator/README.md) | Intermediate |
| 040 | [AI-Assisted Cloud Operations Control Plane](projects/040-ai-assisted-cloud-operations-control-plane/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 5: AI for Infrastructure as Code and Configuration

| ID | Project | Level |
| --- | --- | --- |
| 041 | [Terraform Plan Risk Explainer](projects/041-terraform-plan-risk-explainer/README.md) | Foundation |
| 042 | [Infrastructure Drift Detection and Triage Service](projects/042-infrastructure-drift-detection-and-triage-service/README.md) | Intermediate |
| 043 | [Infrastructure Policy Remediation Assistant](projects/043-infrastructure-policy-remediation-assistant/README.md) | Intermediate |
| 044 | [Cloud Architecture to Terraform Generator](projects/044-cloud-architecture-to-terraform-generator/README.md) | Advanced |
| 045 | [Configuration Change Blast-Radius Analyzer](projects/045-configuration-change-blast-radius-analyzer/README.md) | Advanced |
| 046 | [Ansible Failure Diagnosis Engine](projects/046-ansible-failure-diagnosis-engine/README.md) | Intermediate |
| 047 | [GitOps Reconciliation Intelligence Service](projects/047-gitops-reconciliation-intelligence-service/README.md) | Intermediate |
| 048 | [Infrastructure Module Quality Scoring Platform](projects/048-infrastructure-module-quality-scoring-platform/README.md) | Advanced |
| 049 | [Environment Parity Analyzer](projects/049-environment-parity-analyzer/README.md) | Intermediate |
| 050 | [Governed Infrastructure Change Platform](projects/050-governed-infrastructure-change-platform/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 6: AI for DevSecOps and Software Supply Chains

| ID | Project | Level |
| --- | --- | --- |
| 051 | [Vulnerability Triage and Remediation Prioritizer](projects/051-vulnerability-triage-and-remediation-prioritizer/README.md) | Foundation |
| 052 | [Secret Exposure Investigation and Response System](projects/052-secret-exposure-investigation-and-response-system/README.md) | Intermediate |
| 053 | [Software Bill of Materials Risk Intelligence Service](projects/053-software-bill-of-materials-risk-intelligence-service/README.md) | Intermediate |
| 054 | [Container Image Trust and Risk Gate](projects/054-container-image-trust-and-risk-gate/README.md) | Intermediate |
| 055 | [CI/CD Supply-Chain Attack Detector](projects/055-ci-cd-supply-chain-attack-detector/README.md) | Advanced |
| 056 | [Infrastructure Threat Modeling Assistant](projects/056-infrastructure-threat-modeling-assistant/README.md) | Intermediate |
| 057 | [Prompt Injection Defense Gateway for DevOps Agents](projects/057-prompt-injection-defense-gateway-for-devops-agents/README.md) | Advanced |
| 058 | [DevOps Agent Permission and Tool-Use Firewall](projects/058-devops-agent-permission-and-tool-use-firewall/README.md) | Advanced |
| 059 | [Compliance Evidence Collection and Validation Platform](projects/059-compliance-evidence-collection-and-validation-platform/README.md) | Advanced |
| 060 | [Secure AI-Augmented Software Factory](projects/060-secure-ai-augmented-software-factory/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 7: AI for Platform Engineering and Developer Experience

| ID | Project | Level |
| --- | --- | --- |
| 061 | [Repository Onboarding Assistant](projects/061-repository-onboarding-assistant/README.md) | Foundation |
| 062 | [Service Catalogue Metadata Quality Agent](projects/062-service-catalogue-metadata-quality-agent/README.md) | Intermediate |
| 063 | [Golden Path Recommendation Engine](projects/063-golden-path-recommendation-engine/README.md) | Intermediate |
| 064 | [Self-Service Environment Provisioning Portal](projects/064-self-service-environment-provisioning-portal/README.md) | Advanced |
| 065 | [Developer Documentation Freshness Monitor](projects/065-developer-documentation-freshness-monitor/README.md) | Intermediate |
| 066 | [Platform Support Ticket Triage Service](projects/066-platform-support-ticket-triage-service/README.md) | Intermediate |
| 067 | [Internal Developer Platform Adoption Analyzer](projects/067-internal-developer-platform-adoption-analyzer/README.md) | Advanced |
| 068 | [API and Service Dependency Discovery Platform](projects/068-api-and-service-dependency-discovery-platform/README.md) | Advanced |
| 069 | [Ephemeral Preview Environment Manager](projects/069-ephemeral-preview-environment-manager/README.md) | Advanced |
| 070 | [AI-Native Internal Developer Platform](projects/070-ai-native-internal-developer-platform/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 8: AI for FinOps, Capacity, and Performance

| ID | Project | Level |
| --- | --- | --- |
| 071 | [Cloud Cost Anomaly Investigation Service](projects/071-cloud-cost-anomaly-investigation-service/README.md) | Foundation |
| 072 | [Idle and Orphaned Resource Discovery Engine](projects/072-idle-and-orphaned-resource-discovery-engine/README.md) | Intermediate |
| 073 | [Kubernetes Cost Allocation and Waste Advisor](projects/073-kubernetes-cost-allocation-and-waste-advisor/README.md) | Intermediate |
| 074 | [Workload Rightsizing Recommendation System](projects/074-workload-rightsizing-recommendation-system/README.md) | Advanced |
| 075 | [AI Workload Token and Inference Cost Governor](projects/075-ai-workload-token-and-inference-cost-governor/README.md) | Intermediate |
| 076 | [Capacity Forecasting and Procurement Advisor](projects/076-capacity-forecasting-and-procurement-advisor/README.md) | Advanced |
| 077 | [Performance Regression Detection Gate](projects/077-performance-regression-detection-gate/README.md) | Intermediate |
| 078 | [Cloud Commitment Risk Analyzer](projects/078-cloud-commitment-risk-analyzer/README.md) | Advanced |
| 079 | [Cost-Aware Multi-Region Placement Advisor](projects/079-cost-aware-multi-region-placement-advisor/README.md) | Advanced |
| 080 | [Autonomous FinOps Decision Support Platform](projects/080-autonomous-finops-decision-support-platform/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 9: AI for Reliability, Resilience, and Recovery

| ID | Project | Level |
| --- | --- | --- |
| 081 | [Backup Integrity and Restore Verification System](projects/081-backup-integrity-and-restore-verification-system/README.md) | Foundation |
| 082 | [Disaster Recovery Readiness Auditor](projects/082-disaster-recovery-readiness-auditor/README.md) | Intermediate |
| 083 | [Chaos Experiment Design Assistant](projects/083-chaos-experiment-design-assistant/README.md) | Intermediate |
| 084 | [Automated Failure Injection Laboratory](projects/084-automated-failure-injection-laboratory/README.md) | Advanced |
| 085 | [Dependency Failure Impact Simulator](projects/085-dependency-failure-impact-simulator/README.md) | Advanced |
| 086 | [Auto-Scaling Policy Validation System](projects/086-auto-scaling-policy-validation-system/README.md) | Intermediate |
| 087 | [Multi-Region Failover Decision Assistant](projects/087-multi-region-failover-decision-assistant/README.md) | Advanced |
| 088 | [Resilience Regression Detection Pipeline](projects/088-resilience-regression-detection-pipeline/README.md) | Advanced |
| 089 | [Production Recovery Verification Engine](projects/089-production-recovery-verification-engine/README.md) | Advanced |
| 090 | [Intelligent Resilience Engineering Platform](projects/090-intelligent-resilience-engineering-platform/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

## Track 10: Enterprise AI Operations Capstones

| ID | Project | Level |
| --- | --- | --- |
| 091 | [Model Gateway for Enterprise DevOps Tools](projects/091-model-gateway-for-enterprise-devops-tools/README.md) | Advanced |
| 092 | [LLM Evaluation Pipeline for Operational Assistants](projects/092-llm-evaluation-pipeline-for-operational-assistants/README.md) | Advanced |
| 093 | [DevOps Knowledge Retrieval Platform](projects/093-devops-knowledge-retrieval-platform/README.md) | Advanced |
| 094 | [AI Agent Sandbox and Execution Broker](projects/094-ai-agent-sandbox-and-execution-broker/README.md) | Advanced |
| 095 | [Multi-Agent Change Review Board Simulator](projects/095-multi-agent-change-review-board-simulator/README.md) | Capstone |
| 096 | [Production Model Reliability Control Plane](projects/096-production-model-reliability-control-plane/README.md) | Capstone |
| 097 | [Natural-Language Operations Interface with Approval Gates](projects/097-natural-language-operations-interface-with-approval-gates/README.md) | Capstone |
| 098 | [AI Governance and Audit Platform for Engineering Teams](projects/098-ai-governance-and-audit-platform-for-engineering-teams/README.md) | Capstone |
| 099 | [Enterprise Autonomous Remediation System](projects/099-enterprise-autonomous-remediation-system/README.md) | Capstone |
| 100 | [AI-Powered DevOps Operations Center](projects/100-ai-powered-devops-operations-center/README.md) | Capstone |

[Back to top](#ai-powered-devops-projects)

---

# Choose Your Learning Path

You do not need to complete Projects 001 through 100 sequentially.

Choose a path based on the engineering direction you want to develop.

For the complete sequences and prerequisites, see:

**[Learning Paths](docs/learning-paths.md)**

## DevOps Engineer

Start with:

`001 → 005 → 021 → 031 → 041 → 051 → 071 → 081`

Then continue through CI/CD, Kubernetes, cloud operations, and infrastructure as code.

## Site Reliability Engineer

Start with:

`011 → 013 → 014 → 021 → 024 → 083 → 089`

Then continue through incident response, observability, resilience, and recovery.

## Platform Engineer

Start with:

`031 → 041 → 061 → 062 → 063 → 064`

Then progress toward:

`070 → 091 → 093 → 097`

## DevSecOps Engineer

Start with:

`032 → 043 → 051 → 052 → 053 → 054`

Then progress toward:

`055 → 057 → 058 → 060 → 098`

## Cloud or Infrastructure Engineer

Start with:

`039 → 041 → 042 → 049 → 071 → 081`

Then continue into capacity planning, multi-region architecture, recovery, and governed infrastructure change.

---

# How to Complete a Project

For your first project, follow the complete learning path.

```text
1. Read the project README
              ↓
2. Study the required notes
              ↓
3. Understand the architecture
              ↓
4. Prepare your environment
              ↓
5. Build each milestone
              ↓
6. Verify every checkpoint
              ↓
7. Run the tests
              ↓
8. Complete the failure exercises
              ↓
9. Investigate and recover
              ↓
10. Complete the final engineering challenge
              ↓
11. Collect your evidence
              ↓
12. Document your version
              ↓
13. Prepare your portfolio explanation
              ↓
14. Practice defending your decisions
```

Do not race through the repository.

Completing 50 projects you cannot explain is less useful than completing five projects you deeply understand.

---

# Make Every Project Your Own

Do not finish the guided implementation and immediately move to the next project.

Change something.

You might:

- add a feature
- change part of the architecture
- support another environment
- improve security
- add another failure scenario
- introduce additional tests
- improve observability
- automate a manual step
- reduce cost
- improve performance
- replace one technology
- support another cloud
- improve recovery behavior

Document what you changed and why.

Your completed repository should eventually represent your engineering work, not a clone of this repository.

---

# Final Engineering Challenge

Projects conclude with an engineering challenge appropriate to their level.

You may receive requirements such as:

```text
Traffic has increased by 10x.

Sensitive data can no longer leave the environment.

The external AI provider occasionally becomes unavailable.

The service must remain useful during model failure.

Operational actions now require human approval.

Infrastructure cost cannot increase.

Redesign the necessary parts of the system.

Implement your changes.

Test them.

Document your decisions.

Prove the result.
```

You will not always receive the exact commands.

That is intentional.

---

# Build Your Portfolio

Your completed project should demonstrate more than the technologies you used.

Someone reviewing your repository should be able to determine:

- what problem you solved
- who uses the system
- how the architecture works
- how data moves through the system
- how you provisioned the environment
- how you tested the implementation
- where AI is used
- where deterministic engineering remains in control
- what information can reach the model
- what permissions exist
- what requires human approval
- how model output is validated
- how the system behaves when AI fails
- how sensitive information is protected
- how the system is monitored
- how failure conditions were tested
- how recovery works
- how recovery was verified
- what limitations remain
- what you would change before production

See **[Portfolio Guidance](docs/portfolio-guidance.md)** before publishing your work.

---

# Prepare to Explain What You Built

You should be prepared to discuss your project at three levels.

## Explain

- What did you build?
- What problem does it solve?
- Who would use it?
- How does the architecture work?
- What technologies did you use?
- Where does AI fit into the system?

## Defend

- Why did you choose this architecture?
- Why did you choose these technologies?
- What alternatives did you consider?
- Where are the trust boundaries?
- What happens when a dependency fails?
- What happens when the model is unavailable?
- How do you prevent unsafe AI output from affecting the system?

## Redesign

- What changes at 10x traffic?
- How would you support multiple teams?
- How would you reduce operating cost?
- How would you deploy globally?
- What would you change for a regulated environment?
- What would you change before production?
- What is currently the weakest part of your architecture?

If you can build the system and answer those questions from your own implementation, you have done more than complete a tutorial.

---

# Responsible AI

Projects may process source code, build output, logs, infrastructure metadata, security findings, incident records, configuration, or other sensitive operational information.

Before connecting any external model:

- use synthetic or explicitly authorized data
- remove credentials and tokens
- protect personal and confidential information
- review the provider's data-handling requirements
- restrict the amount of context sent
- apply request timeouts
- validate model output
- test prompt-injection scenarios
- test malformed and unsafe output
- keep safe fallback behavior for critical workflows
- restrict model access to tools
- use minimum required permissions
- require authorization for high-impact actions

Never allow unrestricted model-generated commands to execute directly against infrastructure.

Read:

- [AI Safety Standards](docs/ai-safety-standards.md)
- [Security Policy](SECURITY.md)

---

# Project Status

Every project has a development status.

| Status | Meaning |
| --- | --- |
| **Planned** | The project has been accepted into the catalogue. |
| **In Development** | The project guide, implementation, tests, and learning material are being built. |
| **Review** | The project is undergoing technical and learning-path review. |
| **Ready** | You can complete the entire project from beginning to end. |
| **Maintenance** | The project is complete and receives dependency, security, and documentation updates. |

---

# Contributing

Contributions that improve technical accuracy, accessibility, safety, testing, documentation, or the learning experience are welcome.

Before opening a pull request:

1. Read [CONTRIBUTING.md](CONTRIBUTING.md).
2. Follow [PROJECT-STANDARDS.md](PROJECT-STANDARDS.md).
3. Keep examples reproducible.
4. Keep exercises safe to run.
5. Include tests where appropriate.
6. Never commit secrets or private information.
7. Explain what you changed.
8. Explain why you changed it.
9. Explain how you verified the result.

---

# Security

Do not publish:

- credentials
- API keys
- access tokens
- private keys
- customer information
- confidential logs
- private infrastructure information
- proprietary source code
- sensitive incident information

Do not report vulnerabilities through public GitHub issues.

Follow [SECURITY.md](SECURITY.md) for private security reporting.

---

# License

Review [LICENSE](LICENSE) before copying, adapting, redistributing, teaching from, or commercially using material from this repository.

---

# Start Building

Choose a project that matches your current level and career direction.

**Learn before you build.**

**Understand before you automate.**

**Verify before you trust.**

**Break systems safely.**

**Investigate with evidence.**

**Recover deliberately.**

**Document your decisions.**

And when someone asks what you built, do not just list the tools you used.

Explain the problem, the architecture, the decisions, the failures, the evidence, and the result.
