# AI Workflow Enablement Platform

A shipped, production AI automation platform that reduced manual clinical documentation effort by 80–85% per chart. Built to demonstrate how high-friction internal workflows can be discovered, scoped, automated, and operationalized quickly - in a regulated environment, with measurable impact.

The initial workflow automates inpatient discharge summarization, but the architecture is intentionally reusable: the same ingestion, redaction, prompt, output, and observability patterns apply to any document-heavy internal workflow.

## Operational Impact

| Workflow | Before | After | Impact |
|---|---:|---:|---:|
| Inpatient discharge abstraction | 15–20 min/chart | ~11–12 seconds end-to-end | ~85% time reduction |
| Scanned/faxed document handling | Manual review or separate OCR step | Single automated ingestion path | Eliminated manual routing |
| EMR-ready formatting | Manual restructuring by staff | Structured Markdown/RTF output | Zero reformatting effort |
| PHI handling safeguards | Ad hoc/manual process risk | Boundary redaction + transient processing | Repeatable, auditable control |
| Operational visibility | Limited run-level traceability | Structured run metadata: model, version, tokens, cost | Full per-run audit trail |

### Live Production Data - First 3 Months

The pipeline has been running in production against real patient records for three months since initial deployment. Figures pulled directly from Azure Cost Management:

| Metric | Value |
|---|---:|
| Pages processed | 8,735 |
| Document runs | ~500–550 |
| Total Azure cost | $27.30 |
| **Blended cost per document** | **~$0.05** |

### Live Production Data - 93 day historical view

| Metric | Value |
|---|---:|
| Pages processed | 26,935 |
| Document runs | 2117 |
| Total Azure cost | $211.60 |
| **Blended cost per document** | **~$0.1000** |

Cost per document is logged and queryable after every run. Enterprise PTU pricing eliminates per-token charges at scale, driving effective cost toward near-zero as volume grows.

The next three months are set for scaling the volume up by an order of approximately 8x

**First validated production run** - 11-page scanned fax (GFI FaxMaker, no native text layer):
- Full summary produced, no truncation, ~11–12 seconds end-to-end
- Clinical complexity: ICU admission, nonconvulsive status epilepticus, multi-substance withdrawal, 5 active consults, complex discharge medication regimen

[Full executive brief and cost breakdown →](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Executive-Brief)

## Why This Matches AI Enablement Work

This is not a single-purpose clinical app. It is a repeatable pattern for turning manual, time-intensive workflows into usable AI-powered internal tools - built and shipped to production standards.

The full AI enablement loop is demonstrated end-to-end:

1. **Discover** a high-friction process with measurable manual cost
2. **Scope** the first valuable workflow
3. **Build** a working solution quickly with production-quality execution
4. **Operationalize** it with CI/CD, IaC, telemetry, and secret management
5. **Support adoption** with runbooks, leadership briefs, and demo artifacts
6. **Generalize** the pattern for reuse across adjacent workflows

## Reusable AI Workflow Patterns

Each component was built as a standalone, reusable pattern - not glued together for a single use case:

| Pattern | What It Does |
|---|---|
| Document ingestion | Handles PDF, scanned image, and faxed document formats via a single pipeline |
| Boundary sanitization | Redacts PHI/PII at the envelope before LLM submission - reusable for any sensitive domain |
| Configurable domain prompt | Prompt template externalized per workflow - swap in a new use case without code changes |
| Structured output generation | Generates Markdown and RTF output with consistent, parseable structure |
| Run metadata capture | Records model, version, tokens, finish reason, cost, and timestamp per run |
| Token/cost observability | Surface usage and cost signals per run for operational monitoring |
| CI/CD deployment | GitHub Actions pipeline: lint, test, package, deploy to Azure Functions |
| Managed identity security | Zero-credential architecture using Azure Managed Identity + Key Vault references |
| Infrastructure as code | Full environment provisioned via Azure Bicep - repeatable, reviewable, auditable |
| Runbook and handoff | Operational documentation shipped alongside the code |

## Adaptable to Additional Internal Workflows

The same architecture ships value in adjacent use cases without rebuilding from scratch:

- Prior authorization summarization
- Referral packet processing
- Clinical intake documentation
- Claims and document triage
- Customer success case summarization
- Sales and support call note transformation
- Compliance evidence packaging
- Executive reporting from operational documents

## Operational Adoption

Operationalizing AI workflows requires more than working code. This project includes the full adoption surface:

- **Leadership brief** - one-page summary of workflow value, risk controls, and operational requirements for non-technical stakeholders
- **Demo walkthrough** - guided script showing end-to-end automation for live review
- **Runbooks** - step-by-step operator documentation for deployment, configuration, and recovery
- **Troubleshooting guide** - symptom-based diagnostics with CLI commands and Log Analytics queries
- **Smoke test procedure** - post-deploy validation steps to confirm the pipeline is live

## AI Enablement Builder: Capability Evidence

| Capability | Evidence In This Portfolio |
|---|---|
| Rapidly ship useful AI workflows | Fully automated discharge summarization workflow built and operationalized |
| Reduce measurable manual effort | 15–20 min/chart reduced to ~12 seconds - ~85% time reduction |
| Build secure internal tools | Azure Managed Identity, Key Vault, PHI-aware redaction, audit logging |
| Operate in regulated environments | HIPAA-conscious controls, data residency discipline, structured audit trail |
| Build reusable patterns | Modular ingestion, redaction, prompt, output, observability, and deployment components |
| Drive adoption | Demo script, leadership brief, runbooks, handoff documentation |
| Measure and report impact | Per-run metadata: processing time, token usage, model version, finish reason, cost |
| Infrastructure and deployment maturity | Azure Bicep IaC, GitHub Actions CI/CD, Key Vault secret management, Application Insights telemetry |

---

**[View full documentation in the Wiki →](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki)**

| Wiki Page | Description |
|-----------|-------------|
| [Home](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki) | Architecture, PHI redaction pipeline, summarization output, infrastructure overview |
| [Infrastructure](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Infrastructure) | Azure Bicep modules, blob handoff contract, HIPAA controls, monitoring |
| [Deployment Runbook](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Deployment-Runbook) | Prerequisites, Bicep deploy, Function package deploy, smoke test |
| [Azure Function Settings](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Azure-Function-Settings) | Runtime settings, Key Vault references, environment config |
| [Troubleshooting](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Troubleshooting) | Common symptoms, CLI checks, Log Analytics queries |
| [Demo](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Demo) | Guided walkthrough, output reference, reset steps |
| [Reusable AI Workflow Patterns](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Reusable-AI-Workflow-Patterns) | Pattern library, component map, and adaptation guide |
| [Operational Adoption and Impact](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Operational-Adoption-And-Impact) | Metrics, adoption artifacts, and enablement approach |
| [Executive Brief](https://github.com/Aptica-Solutions/a-portfolio-clinical-summary/wiki/Executive-Brief) | Full production data, cost breakdown, first validated run, and strategic value |

