# AI-Powered DevOps Projects


<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/06dafafd-b4a2-4f49-9d8c-3e4f7a2c9172" />


Build production-minded systems that apply artificial intelligence to software delivery, cloud operations, platform engineering, site reliability, security, observability, infrastructure, and cost management.

This repository contains 100 hands-on projects based on problems engineers encounter in real environments. Each project goes beyond a short tool demonstration. You will design the system, write the code, provision the infrastructure, integrate delivery pipelines, secure the AI workflow, observe its behavior, test failure conditions, recover safely, and document the result.

The goal is not to add an AI chatbot to ordinary DevOps tasks. The goal is to learn where AI provides useful decision support, where deterministic engineering must remain in control, and how to build systems that can be trusted in production.

## Who this repository is for

These projects are designed for:

- DevOps engineers
- Site reliability engineers
- Platform engineers
- Cloud engineers
- Infrastructure engineers
- DevSecOps engineers
- Systems engineers
- Software engineers moving into cloud operations
- Students building practical AI and DevOps portfolios

You do not need to complete all 100 projects. Choose a learning path that matches your current role, experience, and career direction.

## What makes these projects different

Every project begins with a realistic engineering problem and leads to a complete, demonstrable result.

Depending on its scope, a project may include:

1. A realistic engineering problem and clearly defined users
2. A complete functioning system
3. Reproducible infrastructure as code
4. CI/CD integration
5. Security controls and documented trust boundaries
6. AI safety controls and structured output validation
7. Logs, metrics, traces, dashboards, and alerts
8. Controlled failure injection, recovery, and verification
9. Cost, latency, capacity, and performance analysis
10. Automated tests and measurable acceptance criteria
11. A production-readiness review
12. Interview questions and portfolio guidance

Not every project needs every component. The implementation must include every component required to solve the stated problem safely and credibly.

## Engineering principles

The repository follows several non-negotiable principles:

- Verified evidence and AI-generated conclusions must remain clearly separated.
- Model output must be treated as untrusted until it passes validation.
- Operational systems must continue safely when the model is unavailable.
- Destructive or high-impact actions must require explicit authorization.
- Agents and automation must use the minimum permissions required.
- Sensitive data must be removed or protected before it reaches an external model.
- Every automated action must produce an auditable record.
- Failure recovery must include verification, not only remediation.
- Cost, security, reliability, and maintainability are part of the design.

## Project levels

| Level | Description |
| --- | --- |
| Foundation | A focused project that teaches essential practices while producing a useful system. |
| Intermediate | A multi-component project with deployment, testing, security, and operational requirements. |
| Advanced | A production-oriented project involving distributed systems, governance, scale, or controlled automation. |
| Capstone | An end-to-end platform that combines multiple DevOps disciplines and requires defensible engineering decisions. |

## How to use this repository

1. Choose a project from the catalogue or select a recommended learning path.
2. Open the project folder and read its `README.md` before installing anything.
3. Complete the project-specific prerequisites and environment checks.
4. Use the starter project to build the system through the numbered labs.
5. Compare each milestone with the documented expected result.
6. Complete the failure exercises and verify recovery.
7. Run the automated tests and acceptance checks.
8. Review the reference implementation only after attempting the work.
9. Complete the production-readiness review.
10. Document the finished project in your own repository and prepare to explain your decisions.


## Project catalogue

### Track 1: AI for CI/CD and software delivery

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 001 | [AI-Powered CI Failure Triage Engine](projects/001-ai-powered-ci-failure-triage-engine/README.md) | Foundation | Analyze failed pipeline logs, identify evidence, classify likely causes, redact secrets, and produce validated remediation guidance. |
| 002 | [Intelligent Flaky Test Detection Service](projects/002-intelligent-flaky-test-detection-service/README.md) | Intermediate | Detect nondeterministic tests from historical CI runs, calculate confidence scores, and recommend quarantine or investigation without hiding genuine failures. |
| 003 | [Pull Request Risk Scoring Gate](projects/003-pull-request-risk-scoring-gate/README.md) | Intermediate | Evaluate code changes, ownership, dependency impact, test coverage, and deployment history before assigning a review and release risk score. |
| 004 | [AI-Assisted Pipeline Generator with Policy Guardrails](projects/004-ai-assisted-pipeline-generator-with-policy-guardrails/README.md) | Intermediate | Generate pipeline configurations from repository evidence, validate them against schemas and policy, and test them in an isolated environment. |
| 005 | [Deployment Log Root-Cause Correlator](projects/005-deployment-log-root-cause-correlator/README.md) | Intermediate | Correlate pipeline, deployment, application, and infrastructure events to explain why a release failed. |
| 006 | [Release Readiness Decision Support System](projects/006-release-readiness-decision-support-system/README.md) | Advanced | Combine test results, vulnerabilities, change risk, SLO health, approvals, and rollback readiness into an evidence-based release recommendation. |
| 007 | [CI Pipeline Performance Advisor](projects/007-ci-pipeline-performance-advisor/README.md) | Intermediate | Find slow stages, repeated work, cache misses, and runner bottlenecks, then measure the effect of approved improvements. |
| 008 | [Build Dependency Failure Predictor](projects/008-build-dependency-failure-predictor/README.md) | Advanced | Use dependency metadata, lockfile changes, outage information, and build history to identify releases at risk of dependency-related failure. |
| 009 | [Pipeline Configuration Drift Detector](projects/009-pipeline-configuration-drift-detector/README.md) | Intermediate | Compare approved pipeline baselines with active configurations and explain security or reliability consequences of detected drift. |
| 010 | [Multi-Repository Release Orchestrator](projects/010-multi-repository-release-orchestrator/README.md) | Capstone | Coordinate versioning, tests, approvals, deployment order, evidence collection, rollback, and AI-assisted risk analysis across dependent services. |

### Track 2: AI for incident response and SRE

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 011 | [Incident Evidence Collection Assistant](projects/011-incident-evidence-collection-assistant/README.md) | Foundation | Gather bounded logs, metrics, traces, deployment events, and configuration changes into a timestamped incident evidence package. |
| 012 | [Alert Deduplication and Incident Clustering Service](projects/012-alert-deduplication-and-incident-clustering-service/README.md) | Intermediate | Group related alerts into incidents using deterministic signals and explainable similarity scoring. |
| 013 | [SLO Breach Investigation Assistant](projects/013-slo-breach-investigation-assistant/README.md) | Intermediate | Trace an SLO breach to affected services, recent changes, resource pressure, and dependency failures without claiming an unverified root cause. |
| 014 | [Incident Timeline Reconstruction Engine](projects/014-incident-timeline-reconstruction-engine/README.md) | Intermediate | Normalize events from multiple systems, handle clock differences, and create an evidence-linked incident timeline. |
| 015 | [Runbook Retrieval and Recommendation Service](projects/015-runbook-retrieval-and-recommendation-service/README.md) | Intermediate | Retrieve approved runbook steps based on incident context while enforcing version, ownership, authorization, and freshness controls. |
| 016 | [Human-in-the-Loop Incident Commander Copilot](projects/016-human-in-the-loop-incident-commander-copilot/README.md) | Advanced | Maintain incident state, surface missing evidence, track decisions, prepare updates, and require humans to approve operational actions. |
| 017 | [Post-Incident Review Drafting System](projects/017-post-incident-review-drafting-system/README.md) | Intermediate | Convert a verified incident timeline into a blameless review draft with contributing factors, evidence links, and action-item validation. |
| 018 | [Recurring Incident Pattern Detector](projects/018-recurring-incident-pattern-detector/README.md) | Advanced | Identify repeated failure signatures across incident records and rank preventive engineering work by frequency, impact, and confidence. |
| 019 | [On-Call Handover Intelligence Service](projects/019-on-call-handover-intelligence-service/README.md) | Intermediate | Produce a concise shift handover from active alerts, recent changes, degraded SLOs, open incidents, and unfinished actions. |
| 020 | [Enterprise Incident Intelligence Platform](projects/020-enterprise-incident-intelligence-platform/README.md) | Capstone | Combine ingestion, correlation, retrieval, timelines, communications, runbooks, audit trails, and safe action recommendations in one incident system. |

### Track 3: AI for observability and AIOps

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 021 | [Telemetry Quality Auditor](projects/021-telemetry-quality-auditor/README.md) | Foundation | Detect missing labels, broken trace propagation, inconsistent service names, high-cardinality fields, and unsafe sensitive data in telemetry. |
| 022 | [Log Pattern Discovery and Noise Reduction Service](projects/022-log-pattern-discovery-and-noise-reduction-service/README.md) | Intermediate | Cluster recurring log patterns, preserve rare events, and propose filters with measurable false-suppression limits. |
| 023 | [Metric Anomaly Detection with Seasonal Baselines](projects/023-metric-anomaly-detection-with-seasonal-baselines/README.md) | Intermediate | Detect meaningful deviations while accounting for daily, weekly, and release-related patterns. |
| 024 | [Distributed Trace Bottleneck Investigator](projects/024-distributed-trace-bottleneck-investigator/README.md) | Intermediate | Analyze spans and service dependencies to find latency concentration, retries, queue delay, and downstream contention. |
| 025 | [Observability Query Assistant](projects/025-observability-query-assistant/README.md) | Intermediate | Translate operational questions into read-only PromQL, LogQL, or trace queries, validate syntax, and restrict expensive or unsafe queries. |
| 026 | [Service Health Summary Generator](projects/026-service-health-summary-generator/README.md) | Foundation | Combine golden signals, SLOs, deployments, incidents, and dependency health into an evidence-linked operational summary. |
| 027 | [Cardinality and Telemetry Cost Controller](projects/027-cardinality-and-telemetry-cost-controller/README.md) | Advanced | Detect cardinality explosions, estimate cost impact, and recommend safer attribute or sampling policies. |
| 028 | [Adaptive Trace Sampling Controller](projects/028-adaptive-trace-sampling-controller/README.md) | Advanced | Adjust sampling using errors, latency, service importance, and incident state while protecting diagnostic coverage and budgets. |
| 029 | [Observability Coverage Gap Analyzer](projects/029-observability-coverage-gap-analyzer/README.md) | Intermediate | Compare service architecture with emitted telemetry and identify blind spots before production incidents expose them. |
| 030 | [Unified AIOps Correlation Platform](projects/030-unified-aiops-correlation-platform/README.md) | Capstone | Correlate logs, metrics, traces, changes, alerts, and topology while preserving evidence, uncertainty, and operator control. |

### Track 4: AI for Kubernetes and cloud operations

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 031 | [Kubernetes Workload Failure Investigator](projects/031-kubernetes-workload-failure-investigator/README.md) | Foundation | Diagnose common Pending, CrashLoopBackOff, ImagePullBackOff, probe, scheduling, and resource failures from cluster evidence. |
| 032 | [Kubernetes Manifest Safety Reviewer](projects/032-kubernetes-manifest-safety-reviewer/README.md) | Intermediate | Review manifests for schema errors, insecure settings, resource omissions, availability risks, and policy violations before deployment. |
| 033 | [Kubernetes Event Correlation Engine](projects/033-kubernetes-event-correlation-engine/README.md) | Intermediate | Connect events, pod states, controller activity, node pressure, and releases into a structured failure explanation. |
| 034 | [Resource Request and Limit Advisor](projects/034-resource-request-and-limit-advisor/README.md) | Advanced | Recommend Kubernetes CPU and memory settings from historical usage while accounting for startup, peaks, reliability, and cost. |
| 035 | [Cluster Capacity and Scheduling Forecaster](projects/035-cluster-capacity-and-scheduling-forecaster/README.md) | Advanced | Predict capacity pressure, unschedulable workloads, autoscaling constraints, and upgrade headroom. |
| 036 | [Safe Kubernetes Remediation Assistant](projects/036-safe-kubernetes-remediation-assistant/README.md) | Advanced | Propose and simulate bounded remediations, require approval, execute through least-privilege workflows, and verify recovery. |
| 037 | [Multi-Cluster Configuration Drift Intelligence](projects/037-multi-cluster-configuration-drift-intelligence/README.md) | Advanced | Detect and explain drift across clusters, environments, policies, versions, and add-on configurations. |
| 038 | [Kubernetes Upgrade Risk Analyzer](projects/038-kubernetes-upgrade-risk-analyzer/README.md) | Advanced | Examine API removals, add-on compatibility, workload constraints, disruption budgets, and rollback plans before an upgrade. |
| 039 | [Cloud Resource Misconfiguration Investigator](projects/039-cloud-resource-misconfiguration-investigator/README.md) | Intermediate | Analyze cloud inventory and policy evidence to identify unsafe, unavailable, or inconsistent resources across accounts. |
| 040 | [AI-Assisted Cloud Operations Control Plane](projects/040-ai-assisted-cloud-operations-control-plane/README.md) | Capstone | Provide evidence-driven investigation and approval-gated operations across Kubernetes and cloud resources with complete auditability. |

### Track 5: AI for infrastructure as code and configuration

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 041 | [Terraform Plan Risk Explainer](projects/041-terraform-plan-risk-explainer/README.md) | Foundation | Parse Terraform plans, identify impactful changes, and produce a structured explanation that distinguishes facts from recommendations. |
| 042 | [Infrastructure Drift Detection and Triage Service](projects/042-infrastructure-drift-detection-and-triage-service/README.md) | Intermediate | Detect unmanaged changes, determine likely sources, rank risk, and guide safe reconciliation. |
| 043 | [Infrastructure Policy Remediation Assistant](projects/043-infrastructure-policy-remediation-assistant/README.md) | Intermediate | Explain policy failures and generate minimal candidate patches that must pass policy, tests, and human review. |
| 044 | [Cloud Architecture to Terraform Generator](projects/044-cloud-architecture-to-terraform-generator/README.md) | Advanced | Convert an approved architecture specification into modular Terraform with validation, tests, cost estimates, and security controls. |
| 045 | [Configuration Change Blast-Radius Analyzer](projects/045-configuration-change-blast-radius-analyzer/README.md) | Advanced | Map proposed configuration changes to services, environments, dependencies, owners, and recovery procedures. |
| 046 | [Ansible Failure Diagnosis Engine](projects/046-ansible-failure-diagnosis-engine/README.md) | Intermediate | Analyze inventory, playbook, connectivity, privilege, idempotency, and module errors across managed hosts. |
| 047 | [GitOps Reconciliation Intelligence Service](projects/047-gitops-reconciliation-intelligence-service/README.md) | Intermediate | Explain reconciliation failures, source drift, health-check errors, and unsafe manual changes in GitOps environments. |
| 048 | [Infrastructure Module Quality Scoring Platform](projects/048-infrastructure-module-quality-scoring-platform/README.md) | Advanced | Score reusable modules for tests, documentation, security, versioning, portability, maintenance, and operational safety. |
| 049 | [Environment Parity Analyzer](projects/049-environment-parity-analyzer/README.md) | Intermediate | Compare development, staging, and production infrastructure to expose differences that could invalidate testing or recovery assumptions. |
| 050 | [Governed Infrastructure Change Platform](projects/050-governed-infrastructure-change-platform/README.md) | Capstone | Combine plan analysis, policy, cost, drift, approvals, deployment evidence, rollback, and post-change verification. |

### Track 6: AI for DevSecOps and software supply chains

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 051 | [Vulnerability Triage and Remediation Prioritizer](projects/051-vulnerability-triage-and-remediation-prioritizer/README.md) | Foundation | Rank findings using exploitability, reachability, asset criticality, exposure, and compensating controls instead of severity alone. |
| 052 | [Secret Exposure Investigation and Response System](projects/052-secret-exposure-investigation-and-response-system/README.md) | Intermediate | Detect exposed secrets, trace affected assets, coordinate rotation, preserve evidence, and verify containment. |
| 053 | [Software Bill of Materials Risk Intelligence Service](projects/053-software-bill-of-materials-risk-intelligence-service/README.md) | Intermediate | Ingest SBOMs, map vulnerable components to deployed workloads, and prioritize verified exposure. |
| 054 | [Container Image Trust and Risk Gate](projects/054-container-image-trust-and-risk-gate/README.md) | Intermediate | Validate provenance, signatures, packages, malware results, configuration, and policy before an image can be promoted. |
| 055 | [CI/CD Supply-Chain Attack Detector](projects/055-ci-cd-supply-chain-attack-detector/README.md) | Advanced | Detect suspicious pipeline edits, dependency substitution, artifact tampering, runner misuse, and unauthorized release activity. |
| 056 | [Infrastructure Threat Modeling Assistant](projects/056-infrastructure-threat-modeling-assistant/README.md) | Intermediate | Build and validate threat models from architecture evidence while requiring engineers to approve assets, flows, boundaries, and risks. |
| 057 | [Prompt Injection Defense Gateway for DevOps Agents](projects/057-prompt-injection-defense-gateway-for-devops-agents/README.md) | Advanced | Detect untrusted instructions in logs, tickets, repositories, and tool output before they influence an operational AI agent. |
| 058 | [DevOps Agent Permission and Tool-Use Firewall](projects/058-devops-agent-permission-and-tool-use-firewall/README.md) | Advanced | Enforce identity, scoped tools, argument validation, approvals, rate limits, and immutable audit records around agent actions. |
| 059 | [Compliance Evidence Collection and Validation Platform](projects/059-compliance-evidence-collection-and-validation-platform/README.md) | Advanced | Continuously gather control evidence, test freshness and completeness, and map results to approved compliance requirements. |
| 060 | [Secure AI-Augmented Software Factory](projects/060-secure-ai-augmented-software-factory/README.md) | Capstone | Integrate source, build, test, signing, provenance, policy, deployment, runtime evidence, and guarded AI assistance. |

### Track 7: AI for platform engineering and developer experience

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 061 | [Repository Onboarding Assistant](projects/061-repository-onboarding-assistant/README.md) | Foundation | Inspect a repository and generate verified setup guidance, dependency checks, architecture entry points, and first-contribution steps. |
| 062 | [Service Catalogue Metadata Quality Agent](projects/062-service-catalogue-metadata-quality-agent/README.md) | Intermediate | Detect incomplete ownership, lifecycle, dependency, documentation, SLO, and operational metadata in a service catalogue. |
| 063 | [Golden Path Recommendation Engine](projects/063-golden-path-recommendation-engine/README.md) | Intermediate | Recommend an approved service template from workload requirements, compliance needs, availability targets, and team constraints. |
| 064 | [Self-Service Environment Provisioning Portal](projects/064-self-service-environment-provisioning-portal/README.md) | Advanced | Provision policy-compliant environments through templates, approvals, quotas, expiration, observability, and automated cleanup. |
| 065 | [Developer Documentation Freshness Monitor](projects/065-developer-documentation-freshness-monitor/README.md) | Intermediate | Test commands, links, API examples, version claims, and architecture references to identify documentation drift. |
| 066 | [Platform Support Ticket Triage Service](projects/066-platform-support-ticket-triage-service/README.md) | Intermediate | Categorize platform tickets, retrieve verified guidance, identify duplicates, route ownership, and measure resolution quality. |
| 067 | [Internal Developer Platform Adoption Analyzer](projects/067-internal-developer-platform-adoption-analyzer/README.md) | Advanced | Measure golden-path adoption, friction, lead time, failure rates, support demand, and developer feedback without misleading vanity metrics. |
| 068 | [API and Service Dependency Discovery Platform](projects/068-api-and-service-dependency-discovery-platform/README.md) | Advanced | Build a continuously updated service dependency graph from code, runtime telemetry, deployment data, and catalogue metadata. |
| 069 | [Ephemeral Preview Environment Manager](projects/069-ephemeral-preview-environment-manager/README.md) | Advanced | Create, secure, observe, budget, expire, and destroy per-change environments with AI-assisted diagnostics. |
| 070 | [AI-Native Internal Developer Platform](projects/070-ai-native-internal-developer-platform/README.md) | Capstone | Combine a service catalogue, golden paths, self-service infrastructure, documentation, policy, scorecards, and guarded operational assistance. |

### Track 8: AI for FinOps, capacity, and performance

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 071 | [Cloud Cost Anomaly Investigation Service](projects/071-cloud-cost-anomaly-investigation-service/README.md) | Foundation | Detect unusual spending, attribute changes to resources or deployments, and produce evidence-based investigation reports. |
| 072 | [Idle and Orphaned Resource Discovery Engine](projects/072-idle-and-orphaned-resource-discovery-engine/README.md) | Intermediate | Find unused infrastructure, verify ownership and dependencies, estimate savings, and use approval-based cleanup workflows. |
| 073 | [Kubernetes Cost Allocation and Waste Advisor](projects/073-kubernetes-cost-allocation-and-waste-advisor/README.md) | Intermediate | Allocate cluster cost to teams and services, detect waste, and recommend changes without ignoring reliability requirements. |
| 074 | [Workload Rightsizing Recommendation System](projects/074-workload-rightsizing-recommendation-system/README.md) | Advanced | Recommend instance, database, and container capacity using demand patterns, performance limits, commitments, and resilience targets. |
| 075 | [AI Workload Token and Inference Cost Governor](projects/075-ai-workload-token-and-inference-cost-governor/README.md) | Intermediate | Track model usage, token cost, cache efficiency, latency, user attribution, budgets, and abnormal consumption. |
| 076 | [Capacity Forecasting and Procurement Advisor](projects/076-capacity-forecasting-and-procurement-advisor/README.md) | Advanced | Forecast compute, storage, database, and accelerator requirements with uncertainty bands and scenario comparison. |
| 077 | [Performance Regression Detection Gate](projects/077-performance-regression-detection-gate/README.md) | Intermediate | Compare releases using load-test and production signals, then block or warn on statistically meaningful regressions. |
| 078 | [Cloud Commitment Risk Analyzer](projects/078-cloud-commitment-risk-analyzer/README.md) | Advanced | Evaluate reserved capacity or savings commitments against forecast demand, growth uncertainty, and architecture changes. |
| 079 | [Cost-Aware Multi-Region Placement Advisor](projects/079-cost-aware-multi-region-placement-advisor/README.md) | Advanced | Compare latency, resilience, data rules, service availability, transfer charges, and operational cost across deployment options. |
| 080 | [Autonomous FinOps Decision Support Platform](projects/080-autonomous-finops-decision-support-platform/README.md) | Capstone | Unite allocation, anomaly detection, forecasting, rightsizing, budgets, approvals, savings verification, and executive reporting. |

### Track 9: AI for reliability, resilience, and recovery

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 081 | [Backup Integrity and Restore Verification System](projects/081-backup-integrity-and-restore-verification-system/README.md) | Foundation | Discover backups, test recoverability, measure restore time, validate data integrity, and report unprotected assets. |
| 082 | [Disaster Recovery Readiness Auditor](projects/082-disaster-recovery-readiness-auditor/README.md) | Intermediate | Validate recovery objectives, dependencies, runbooks, credentials, replicas, backups, exercises, and evidence. |
| 083 | [Chaos Experiment Design Assistant](projects/083-chaos-experiment-design-assistant/README.md) | Intermediate | Generate bounded experiments from service risks, define safeguards and hypotheses, and reject unsafe test conditions. |
| 084 | [Automated Failure Injection Laboratory](projects/084-automated-failure-injection-laboratory/README.md) | Advanced | Provision an isolated environment, inject controlled faults, collect telemetry, guide recovery, and produce reliability evidence. |
| 085 | [Dependency Failure Impact Simulator](projects/085-dependency-failure-impact-simulator/README.md) | Advanced | Model service, queue, database, identity, network, and third-party failures to estimate propagation and degraded modes. |
| 086 | [Auto-Scaling Policy Validation System](projects/086-auto-scaling-policy-validation-system/README.md) | Intermediate | Test scaling policies against traffic bursts, slow dependencies, quotas, cooldowns, cost limits, and failure scenarios. |
| 087 | [Multi-Region Failover Decision Assistant](projects/087-multi-region-failover-decision-assistant/README.md) | Advanced | Evaluate health, replication, data loss risk, traffic controls, capacity, and approvals before recommending failover. |
| 088 | [Resilience Regression Detection Pipeline](projects/088-resilience-regression-detection-pipeline/README.md) | Advanced | Detect when application or infrastructure changes weaken redundancy, recovery, graceful degradation, or failure isolation. |
| 089 | [Production Recovery Verification Engine](projects/089-production-recovery-verification-engine/README.md) | Advanced | Confirm that services, data, queues, integrations, security controls, and SLOs have recovered after remediation. |
| 090 | [Intelligent Resilience Engineering Platform](projects/090-intelligent-resilience-engineering-platform/README.md) | Capstone | Manage risk discovery, experiment design, fault injection, recovery evidence, readiness scoring, and preventive work. |

### Track 10: Enterprise AI operations capstones

| ID | Project | Level | System you will build |
| --- | --- | --- | --- |
| 091 | [Model Gateway for Enterprise DevOps Tools](projects/091-model-gateway-for-enterprise-devops-tools/README.md) | Advanced | Provide one governed endpoint for model routing, authentication, quotas, redaction, caching, policy, fallback, and audit logs. |
| 092 | [LLM Evaluation Pipeline for Operational Assistants](projects/092-llm-evaluation-pipeline-for-operational-assistants/README.md) | Advanced | Test accuracy, groundedness, refusal behavior, prompt-injection resistance, schema compliance, latency, and cost before release. |
| 093 | [DevOps Knowledge Retrieval Platform](projects/093-devops-knowledge-retrieval-platform/README.md) | Advanced | Build a permission-aware retrieval system over runbooks, architecture records, incidents, repositories, and service metadata. |
| 094 | [AI Agent Sandbox and Execution Broker](projects/094-ai-agent-sandbox-and-execution-broker/README.md) | Advanced | Isolate agent-generated commands, validate intent and arguments, restrict network and filesystem access, and preserve execution evidence. |
| 095 | [Multi-Agent Change Review Board Simulator](projects/095-multi-agent-change-review-board-simulator/README.md) | Capstone | Use specialized agents to assess security, reliability, cost, compliance, and operability while a deterministic policy layer controls decisions. |
| 096 | [Production Model Reliability Control Plane](projects/096-production-model-reliability-control-plane/README.md) | Capstone | Operate model-backed services with routing, fallbacks, evaluations, circuit breakers, rate limits, telemetry, and incident procedures. |
| 097 | [Natural-Language Operations Interface with Approval Gates](projects/097-natural-language-operations-interface-with-approval-gates/README.md) | Capstone | Convert operator requests into read-only queries or proposed actions, validate every step, and require authorization for changes. |
| 098 | [AI Governance and Audit Platform for Engineering Teams](projects/098-ai-governance-and-audit-platform-for-engineering-teams/README.md) | Capstone | Inventory models and agents, track data use, evaluate risk, record approvals, monitor controls, and produce audit evidence. |
| 099 | [Enterprise Autonomous Remediation System](projects/099-enterprise-autonomous-remediation-system/README.md) | Capstone | Detect a narrow class of failures, gather evidence, select preapproved actions, simulate impact, obtain approval, execute, and verify recovery. |
| 100 | [AI-Powered DevOps Operations Center](projects/100-ai-powered-devops-operations-center/README.md) | Capstone | Integrate delivery intelligence, observability, incidents, security, infrastructure, cost, guarded agents, and executive operational reporting. |

## Recommended learning paths

### DevOps engineer

Begin with Projects 001, 005, 021, 031, 041, 051, 071, and 081. Continue through the CI/CD, Kubernetes, cloud operations, and infrastructure-as-code tracks.

### Site reliability engineer

Begin with Projects 011, 013, 014, 021, 024, 083, and 089. Continue through incident intelligence, observability, resilience, and recovery.

### Platform engineer

Begin with Projects 031, 041, 061, 062, 063, and 064. Continue toward Projects 070, 091, 093, and 097.

### DevSecOps engineer

Begin with Projects 032, 043, 051, 052, 053, and 054. Continue toward Projects 055, 057, 058, 060, and 098.

### Cloud or infrastructure engineer

Begin with Projects 039, 041, 042, 049, 071, and 081. Continue into capacity planning, multi-region design, recovery, and governed infrastructure change.

See [Learning Paths](docs/learning-paths.md) for detailed sequences and prerequisites.

## What a completed project should prove

A completed project repository should make it possible for another engineer to determine:

- What problem the system solves
- Who uses it and what decisions it supports
- How its components and data flows are designed
- How to create and remove the environment
- Which findings come from deterministic evidence
- Which findings or recommendations come from AI
- What information can reach the model
- Which actions the system is permitted to perform
- Which actions require human approval
- How the system behaves when the model is unavailable or wrong
- How permissions, policies, schemas, and outputs are validated
- How the system is monitored
- How normal behavior and failure conditions were tested
- What the system costs and how it behaves under load
- How recovery is performed and verified
- Whether the system is ready for production

## Build and document your own version

Participants are encouraged to create a separate repository for every completed project or maintain a clearly organized portfolio repository. Your work should show your decisions, implementation, tests, failures, corrections, and final results.

Do not present the reference implementation as your own work. Use it to check your understanding, investigate differences, and improve your implementation.

See [Submission Guidelines](docs/submission-guidelines.md) and [Portfolio Guidance](docs/portfolio-guidance.md) before publishing your work.

## Responsible AI use

These projects may process source code, build output, logs, infrastructure metadata, security findings, incident records, or other sensitive operational information.

Before connecting any external model:

- Use synthetic or explicitly authorized data.
- Remove credentials, tokens, personal information, and confidential values.
- Review the provider's data handling and retention settings.
- Apply input limits and request timeouts.
- Validate model output against an explicit schema.
- Test prompt-injection and unsafe-output scenarios.
- Keep a non-AI fallback for critical workflows.
- Never allow unrestricted model-generated commands to run against infrastructure.

Read [AI Safety Standards](docs/ai-safety-standards.md) and [Security Policy](SECURITY.md) before implementing model or agent integrations.

## Contributing

Contributions are welcome when they improve technical accuracy, accessibility, safety, testing, or the learning experience.

Before opening a pull request:

1. Read [CONTRIBUTING.md](CONTRIBUTING.md).
2. Follow [PROJECT-STANDARDS.md](PROJECT-STANDARDS.md).
3. Keep examples reproducible and safe to run.
4. Include tests for code or behavioral changes.
5. Do not include secrets, private logs, customer data, or copyrighted course material.
6. Explain the problem, the proposed change, and how the result was verified.

## Project status

The repository is being developed progressively. Each project README will show its current status:

| Status | Meaning |
| --- | --- |
| Planned | The project has been accepted into the catalogue. |
| In development | The guide, implementation, and tests are being built. |
| Review | The project is undergoing technical and learning-path review. |
| Ready | The project is available for complete follow-along use. |
| Maintenance | The project is ready and receives dependency, security, and documentation updates. |

## License

Review [LICENSE](LICENSE) before copying, adapting, redistributing, or using repository material commercially.

## Support and security

Use GitHub Issues for reproducible documentation errors, broken exercises, and technical defects. Do not report vulnerabilities or expose sensitive information in a public issue. Follow the private reporting process in [SECURITY.md](SECURITY.md).

---

Build carefully. Test what you automate. Verify what AI produces. Document what you learn.
