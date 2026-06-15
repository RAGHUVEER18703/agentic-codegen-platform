# Architecture Design Flow

## Architecture Goal

The platform should allow a business user to enter a natural language application requirement and receive a generated lightweight application blueprint and starter codebase.

The first architecture uses one unified backend Code Generation Agent. Internally, the agent follows multiple modular steps, but externally the platform treats it as one agent.

## Logical Architecture

```text
┌─────────────────────┐
│ Business User       │
└──────────┬──────────┘
           │
           v
┌─────────────────────┐
│ Web UI              │
│ Requirement Form    │
│ Generated Output UI │
└──────────┬──────────┘
           │
           v
┌─────────────────────┐
│ FastAPI Backend     │
│ API Control Plane   │
└──────────┬──────────┘
           │
           v
┌─────────────────────┐
│ Code Generation     │
│ Agent               │
└──────────┬──────────┘
           │
           v
┌─────────────────────┐
│ Internal Workflow   │
│ Steps               │
└──────────┬──────────┘
           │
           v
┌─────────────────────┐
│ Generated Artifacts │
│ App Spec            │
│ Architecture        │
│ DB Schema           │
│ API Contract        │
│ UI Plan             │
│ Starter Code        │
└──────────┬──────────┘
           │
           v
┌─────────────────────┐
│ Azure Deployment    │
│ Future Step         │
└─────────────────────┘
```

## Main Components

### 1. Web UI

The UI is used by business users to enter application requirements.

Initial screens:

- New app requirement form
- Generated app summary
- Generated artifacts preview
- Download generated code
- Generation history later

### 2. FastAPI Backend

The backend acts as the control plane.

Responsibilities:

- receive user requirement
- validate request
- call Code Generation Agent
- return generated outputs
- store generated artifacts
- expose health and status APIs

### 3. Code Generation Agent

The Code Generation Agent is the main backend agent.

It performs:

- requirement analysis
- app specification generation
- architecture design
- database design
- API design
- UI design
- code generation

The first version should keep these as internal modules, not separate agents.

### 4. Contracts

Contracts are shared Pydantic models used across the platform.

Important contracts:

- UserRequirement
- AppSpec
- GeneratedArtifact
- WorkflowState

These contracts make the platform predictable and easier to test.

### 5. Prompt Templates

Prompts should be stored separately from code.

This allows the team to improve prompts without changing orchestration logic.

Prompt categories:

- requirement analysis prompt
- app specification prompt
- architecture prompt
- database design prompt
- API design prompt
- UI design prompt
- code generation prompt

### 6. Generated Apps Workspace

Generated application files should be stored separately from platform code.

Example:

```text
generated_apps/
  shipment_tracker/
    app_spec.json
    architecture.md
    backend/
    frontend/
    database/
    README.md
```

### 7. Azure Cloud

Azure can be used for hosting and storage.

Recommended first version services:

- Azure App Service or Azure Container Apps for backend
- Azure Static Web Apps for frontend
- Azure SQL Database or Azure Database for PostgreSQL for app data
- Azure Blob Storage for generated artifacts
- Azure Key Vault for secrets later

### 8. Microsoft Fabric

Fabric can be introduced after the first working prototype.

Possible uses:

- analytics on generated apps
- tracking business user requests
- dashboarding
- storing generated metadata
- future enterprise reporting

## Backend Request Flow

```text
1. User submits app requirement from UI
2. FastAPI validates the request
3. Backend creates WorkflowState
4. Code Generation Agent analyzes the requirement
5. Agent creates AppSpec
6. Agent creates architecture design
7. Agent creates DB schema
8. Agent creates API contract
9. Agent creates UI plan
10. Agent generates starter code
11. Backend stores artifacts
12. UI displays generated results
```

## First Version Design Decision

Use one Code Generation Agent, not multiple agents.

Reason:

- faster to build
- easier to explain
- easier to debug
- easier to demo
- fewer orchestration failures
- still extensible later

Future versions can split the internal steps into dedicated agents if needed.

## Future Multi-Agent Possibility

Later architecture may include:

- Requirement Agent
- Architecture Agent
- Database Agent
- UI Agent
- API Agent
- Code Agent
- Testing Agent
- Deployment Agent
- Triage Agent

But version 1 should keep a single-agent architecture.

