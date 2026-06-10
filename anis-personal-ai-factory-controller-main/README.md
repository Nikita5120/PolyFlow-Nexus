Here's the cleaned-up, humanized version of your README:

---

**ANIS – Personal AI Factory Controller**

---

**Executive Summary**

ANIS (Autonomous Neural Intelligence Supervisor) is a personal AI factory controller built to orchestrate data ingestion, transformation, analysis, and reporting workflows through a single intent-driven interface. The system combines Custom GPT Actions, n8n workflow orchestration, Google Workspace automation, and a serverless OCR microservice to deliver a fully automated, auditable, and production-ready data pipeline.

ANIS is designed as a control plane, not a monolithic processor. It delegates execution to specialized agents — Ingest, Clean, Analyze, and Report — while enforcing strict contracts, schemas, logging, and observability across the entire data lifecycle.

---

**Table of Contents**

1. Project Overview
2. System Philosophy and Design Principles
3. Objectives and Goals
4. Acceptance Criteria
5. Prerequisites
6. Installation and Setup
7. API Documentation
8. Custom GPT Configuration
9. UI / Frontend Architecture
10. Status Codes
11. Features
12. Tech Stack and Architecture
13. Workflow and Implementation
14. Agent Responsibilities
15. Data Lake Design
16. Testing and Validation
17. Validation Summary
18. Verification Tools
19. Troubleshooting
20. Security and Secrets
21. Deployment
22. Quick-Start Cheat Sheet
23. Usage Notes
24. Performance and Optimization
25. Enhancements
26. Maintenance and Future Work
27. Key Achievements
28. High-Level Architecture
29. Folder Structure
30. How to Demonstrate Live
31. Summary, Closure and Compliance

---

**Project Overview**

ANIS provides a unified command interface that allows users or systems to trigger complex automation pipelines using a single structured JSON command. The platform abstracts workflow complexity while preserving transparency, traceability, and governance.

Core capabilities include:

- Automated Gmail attachment ingestion
- RAW to CLEAN to GOLD data lake transitions
- OCR-based PDF text extraction
- Structured normalization of CSV, XLS, JSON, and TXT formats
- AI-driven analysis and KPI generation
- Daily scheduled execution via cron

---

**System Philosophy and Design Principles**

- **Single Responsibility Agents** — Each agent performs exactly one domain function
- **Contract-First Design** — All interactions validated via schemas
- **Auditability by Default** — Every action is logged
- **Stateless Execution** — Workflows remain restart-safe
- **Enterprise Observability** — Logs, metrics, and artifacts are persisted

---

**Objectives and Goals**

- Establish a centralized AI automation control plane driven by structured intent
- Enable deterministic, schema-driven execution across ingestion, cleaning, analysis, and reporting
- Decouple AI reasoning (GPT) from execution logic (n8n workflows)
- Provide audit-ready data pipelines with full traceability
- Support both interactive on-demand and scheduled automation

---

**Acceptance Criteria**

| Area | Acceptance Requirement |
|---|---|
| API | All requests validated via OpenAPI and JSON schemas |
| Agents | Each agent executes independently with clear responsibility |
| Data | RAW to CLEAN to GOLD data lifecycle enforced |
| Logging | Every execution logged with timestamp and status |
| Security | No secrets committed to repository |
| Scheduling | Cron workflows execute without manual intervention |

---

**Prerequisites**

- Node.js 18 or above
- n8n 1.x (self-hosted or cloud)
- Google Workspace (Gmail, Drive, Sheets)
- OpenAI API access
- Vercel account for OCR microservice

---

**Installation and Setup**

1. Clone the repository
2. Create environment variables from `.env.example`
3. Install serverless dependencies
4. Import n8n workflows (agents, interactive, scheduled)
5. Configure Google OAuth credentials
6. Deploy OCR service on Vercel

---

**API Documentation**

Endpoint:
```
POST /webhook/anis
```

Core Request Fields:

| Field | Description |
|---|---|
| agent | Target agent: ingest, clean, analyze, or report |
| source | Optional data source parameters |
| options | Execution controls |
| return | Expected response format |

All requests and responses are validated against versioned schemas to ensure backward compatibility and contract safety.

---

**Custom GPT Configuration**

| Component | Purpose |
|---|---|
| action-schema.yaml | Defines allowed commands and payload structure |
| instructions.md | Constrains GPT behavior and output format |
| description.md | System-level role definition |
| conversation-starters.md | Guided user interaction examples |

GPT operates strictly as an intent interpreter. It does not execute logic directly and cannot bypass schemas or workflows.

---

**UI / Frontend Architecture**

This project intentionally avoids a traditional UI layer. Instead it uses:

- Custom GPT as the conversational interface
- n8n as the visual execution canvas
- Google Sheets as operational dashboards

State flow:
```
User Intent → GPT → Webhook → Workflow State → Logs / Files
```

Styling, visualization, and reporting are delegated to Google Workspace and GPT responses.

---

**Status Codes**

| Code | Meaning |
|---|---|
| 200 | Success |
| 400 | Invalid payload |
| 401 | Unauthorized |
| 500 | Execution failure |

---

**Features**

ANIS is a production-grade AI factory control plane that unifies LLM intent, workflow orchestration, and data engineering into a single deterministic, auditable, and scalable platform. Unlike typical AI automations, ANIS enforces strict governance, contract-first execution, and end-to-end data lineage.

**Core Capability Domains**

| Domain | Capability | Implementation |
|---|---|---|
| AI Governance | Schema-Locked GPT Control | GPT is sandboxed by OpenAPI and JSON Schema. It cannot generate arbitrary commands or bypass workflows. |
| Orchestration | Agent-Based Execution | Each business function is isolated into independently deployable Ingest, Clean, Analyze, and Report agents. |
| Data Engineering | RAW to CLEAN to GOLD Data Lake | Immutable RAW inputs, reproducible CLEAN data, and versioned GOLD analytics. |
| Observability | Event Ledger | Every API call, transformation, KPI, and file write is logged into Google Sheets with timestamps. |
| Unstructured Data | OCR and Document Intelligence | Serverless OCR extracts text from PDFs and images and feeds it into the CLEAN pipeline. |
| Automation | Cron-Driven Execution | Fully automated daily execution via scheduled workflows. |

**Feature Execution Flow**
```
User / System
      ↓
Custom GPT (Intent → Structured JSON)
      ↓
OpenAPI Schema Validation
      ↓
n8n Control Plane
      ↓
Ingest → Clean → Analyze → Report
      ↓
Data Lake + KPI Ledger
```

---

**Tech Stack and Architecture**

| Layer | Technology | Role |
|---|---|---|
| AI Interface | Custom GPT + OpenAPI | Intent parsing, schema-validated command generation |
| Orchestration | n8n | Workflow execution engine and control plane |
| Data Lake | Google Drive | RAW / CLEAN / GOLD storage |
| Metadata and Logs | Google Sheets | Catalogs, KPIs, audit trails |
| OCR | Vercel Serverless | PDF and image text extraction |
| Contracts | JSON Schema + YAML | Validation and deterministic execution |

**Control Plane Architecture**
```
User / API
      ↓
Custom GPT (Intent Interpreter)
      ↓
OpenAPI + JSON Schema (Contract Layer)
      ↓
n8n Orchestration (Execution Fabric)
      ↓
Ingest | Clean | Analyze | Report (Stateless Agents)
      ↓
Google Drive (RAW / CLEAN / GOLD)
Google Sheets (Logs / KPIs)
```

---

**Workflow and Implementation**

**End-to-End Execution Pipeline**
```
User Prompt → GPT Intent → JSON Command → Schema Validation
→ ANIS Webhook → n8n Control Plane → Agent Pipelines
→ Data Lake + KPI Ledger
```

**Agent Workflow Topology**
```
Ingest  →  Gmail, APIs, Drive
   ↓
Clean   →  Normalize, OCR, validate
   ↓
Analyze →  KPIs, metrics, insights
   ↓
Report  →  Summaries, links
```

**Reliability and Determinism**

- Stateless workflows allow safe retries
- Schema validation prevents malformed executions
- All data transformations are reproducible
- Failures are isolated to individual agents

---

**Agent Responsibilities**

| Agent | Primary Responsibility | Key Outputs |
|---|---|---|
| Ingest | Acquire raw data from external sources (Gmail, Drive, APIs) | RAW files, metadata entries |
| Clean | Normalize, validate, and convert raw data into structured formats | CLEAN datasets (CSV / JSON) |
| Analyze | Compute KPIs, metrics, and analytical insights | GOLD datasets, KPI tables |
| Report | Generate summaries, reports, and shareable outputs | Reports, Drive links |

Each agent is independently deployable, restart-safe, and stateless, ensuring fault isolation and operational resilience.

---

**Data Lake Design**

| Zone | Description | Mutability |
|---|---|---|
| RAW | Original ingested data, unchanged and immutable | Read-only |
| CLEAN | Normalized, schema-aligned datasets | Rebuildable |
| GOLD | Analytics-ready, business-consumable outputs | Versioned |

```
RAW → CLEAN → GOLD
```

---

**Testing and Validation**

| ID | Area | Command | Expected Output | Notes |
|---|---|---|---|---|
| T01 | Ingest | POST /webhook/anis | RAW files created | Gmail ingestion |
| T02 | Clean | Agent clean | CLEAN files created | Normalization |

---

**Validation Summary**

- All inbound requests validated via OpenAPI schemas
- All transformations validated against structural schemas
- All outputs verified before persistence
- No silent failures or implicit transformations

Validation is enforced at every boundary to ensure deterministic behavior across environments.

---

**Verification Tools**

| Tool | Purpose |
|---|---|
| Postman | Manual API verification |
| n8n UI | Workflow execution tracing |
| Google Sheets | Log and KPI verification |
| Drive Audit Logs | Artifact validation |

---

**Troubleshooting**

| Issue | Likely Cause | Resolution |
|---|---|---|
| Webhook returns 400 | Schema violation | Validate request payload |
| No files generated | OAuth permission issue | Reauthorize Google credentials |
| Scheduled job not running | Cron workflow disabled | Enable workflow in n8n |

---

**Security and Secrets**

- Secrets stored in `.env` and never committed to source control
- OAuth credentials isolated per service
- Webhook endpoints protected via schema-enforced contracts

---

**Deployment**

- Serverless OCR deployed on Vercel
- Environment isolation maintained across stages
- Stateless execution model supports zero-downtime redeploys

---

**Quick-Start**

```bash
git clone repo
cp .env.example .env
npm install
n8n start
```

---

**Usage Notes**

- Designed for non-technical operators
- All execution controlled via structured intent
- No manual data manipulation required
- Safe for repeated execution

---

**Performance and Optimization**

- Parallel agent execution where applicable
- Stateless workflows reduce memory overhead
- Incremental processing minimizes rework
- Serverless OCR scales automatically

---

**Planned Enhancements**

- Multi-tenant support
- Role-based access control
- Advanced KPI dashboards
- Pluggable data sources

---

**Maintenance and Future Work**

- Schema versioning strategy
- Automated regression validation
- Agent marketplace expansion
- Enterprise monitoring integration

---

**Key Achievements**

- Production-grade AI control plane with full auditability and governance
- Zero hardcoded logic — all execution driven by versioned schemas
- Enterprise-ready automation framework with stateless, fault-tolerant agents
- End-to-end data lineage from raw ingestion to analytics-ready outputs

---

**High-Level Architecture**

```
Human / System
        ↓
Custom GPT Control (Intent → JSON)
        ↓
OpenAPI + JSON Schema (Contract Enforcement)
        ↓
n8n Control Plane (Workflow Execution)
        ↓
Ingest → Clean → Analyze → Report (Stateless Agents)
        ↓
Google Drive (RAW / CLEAN / GOLD)
Google Sheets (Logs and KPIs)
```

---

**Folder Structure**

```
ANIS-PERSONAL-AI-FACTORY-CONTROLLER/
│
├── diagrams/
│   ├── high-level-architecture.png
│   ├── gpt-execution-flow.png
│   ├── scheduled-execution-flow.png
│   └── data-lake-layout.png
│
├── gpt/
│   ├── action-schema.yaml
│   ├── instructions.md
│   ├── description.md
│   ├── conversation-starters.md
│   └── name.md
│
├── schemas/
│   ├── webhook-request.schema.json
│   ├── webhook-response.schema.json
│   └── control-sheet.schema.md
│
├── screenshots/
│   ├── google-drive/
│   ├── google-sheets/
│   │   ├── data-catalog/
│   │   ├── event-log/
│   │   └── tasks-inbox/
│   ├── gpt-controller/
│   └── workflows/
│       ├── interactive/
│       └── scheduled/
│
├── serverless/
│   └── ocr-pdf-text-extraction-service/
│
├── workflows/
│   ├── agents/
│   │   ├── ingest_agent.json
│   │   ├── clean_agent.json
│   │   ├── analyze_agent.json
│   │   └── report_agent.json
│   ├── interactive/
│   │   └── ANIS_HUB_gpt_webhook.json
│   └── scheduled/
│       ├── ANIS_DAILY_CRON.json
│       ├── analyze_agent_sub_workflow.json
│       └── report_agent_sub_workflow.json
│
├── .env.example
├── .gitignore
└── README.md
```

---

**How to Demonstrate Live**

**Entry Points**

- **Primary (Recommended):** Custom GPT → OpenAPI Action → n8n Webhook
- **Secondary:** Direct API invocation via Postman or curl
- **Automated:** Scheduled execution via cron workflows

**GPT Prompt to Webhook Flow**

Example prompt:
```
Ingest Gmail attachments from the last 7 days, clean and normalize the data,
analyze the results, and generate a report.
```

Execution steps:
1. Custom GPT interprets user intent
2. Prompt is validated against the OpenAPI action schema
3. GPT generates a single schema-compliant JSON command
4. Command is dispatched to the ANIS webhook
5. n8n orchestrates agent-based workflows
6. Outputs are written to Google Drive and Google Sheets
7. Structured results are returned to GPT

**Sample API Calls**

Ingest:
```json
{
  "agent": "ingest",
  "source": { "gmailQuery": "has:attachment", "days": 7 },
  "options": { "attachmentsOnly": true, "fileTypes": ["pdf", "csv", "xlsx"] },
  "return": "summary"
}
```

Clean:
```json
{ "agent": "clean", "return": "log" }
```

Analyze:
```json
{ "agent": "analyze", "return": "kpis" }
```

Report:
```json
{ "agent": "report", "return": "files" }
```

**Where to Observe Outputs**

| Component | Location |
|---|---|
| RAW Files | Google Drive → RAW |
| CLEAN Data | Google Drive → CLEAN |
| GOLD Outputs | Google Drive → GOLD |
| Event Logs | Google Sheets → EVENT_LOG |
| KPIs | Google Sheets → DATA_CATALOG |
| Reports | Google Drive → REPORT |

---

**Summary and Compliance**

ANIS is a well-engineered automation system that demonstrates how AI-driven intent, workflow orchestration, and governed data pipelines can be unified into a single, compliant, and extensible platform.

**Architectural Maturity** — Agent-based workflows enforce strict separation of concerns. Each agent operates with a single clearly defined responsibility, and stateless orchestration enables safe retries and fault tolerance.

**Schema-Driven Execution** — All inputs are validated against OpenAPI and JSON schemas. Transformations are controlled and predictable, with no implicit or hidden execution paths.

**Auditability and Traceability** — Every action is logged with timestamps and agent identity. The RAW to CLEAN to GOLD data lineage is enforced throughout, and all outputs are reproducible and reviewable.

**Security** — No credentials are committed to source control. Environment-based secret injection and isolated OAuth scopes are enforced by default.

**Operational Reliability** — Supports both interactive and scheduled execution. Failure isolation at the agent level ensures the system is production-safe by default and operable by non-technical users.
