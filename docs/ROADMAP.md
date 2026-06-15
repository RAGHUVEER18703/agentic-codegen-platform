# Project Roadmap

## Phase 0: Repository and Planning

Goal: create the clean foundation.

Tasks:

- Create GitHub repository
- Add README.md
- Add docs/ARCHITECTURE.md
- Add docs/ROADMAP.md
- Decide initial stack
- Create monorepo skeleton
- Add .gitignore and .env.example
- Set up branch strategy

Outcome:

- Team has a shared repo and documentation baseline.

## Phase 1: Backend Skeleton

Goal: create the API control plane.

Tasks:

- Create Python 3.12 project
- Add FastAPI
- Add Pydantic
- Add health check API
- Add generate-app API stub
- Add basic request and response models
- Add local run instructions

Outcome:

- Backend starts locally and exposes Swagger UI.

## Phase 2: Common Data Contracts

Goal: define the shared language between workflow steps.

Tasks:

- Create UserRequirement model
- Create AppSpec model
- Create GeneratedArtifact model
- Create WorkflowState model
- Add validation rules
- Add example JSON files

Outcome:

- All future generation steps use stable contracts.

## Phase 3: Code Generation Agent Stub

Goal: build the first unified agent structure.

Tasks:

- Create code_generation agent folder
- Add agent.py
- Add internal step modules
- Add deterministic stub outputs
- Generate sample Shipment Tracker artifacts without real AI first

Outcome:

- The backend can simulate the full generation workflow.

## Phase 4: Shipment Tracker Demo Output

Goal: generate the first sample app blueprint.

Tasks:

- Generate shipment tracker AppSpec
- Generate architecture.md
- Generate database schema
- Generate API contract
- Generate UI plan
- Generate starter frontend/backend code skeleton

Outcome:

- The platform can produce a basic generated app package.

## Phase 5: Web UI

Goal: create a simple user interface for business users.

Tasks:

- Create frontend app
- Add requirement input form
- Add generate button
- Show generation status
- Display generated app summary
- Display/download generated artifacts

Outcome:

- User can generate an app from the browser.

## Phase 6: AI Integration

Goal: replace static stub outputs with LLM-generated outputs.

Tasks:

- Add LLM provider configuration
- Add prompt templates
- Add structured output validation
- Add retry and error handling
- Keep outputs aligned to Pydantic contracts

Outcome:

- Code Generation Agent produces dynamic results from user input.

## Phase 7: Azure Deployment

Goal: deploy the first version to Azure.

Tasks:

- Containerize backend
- Deploy backend to Azure App Service or Azure Container Apps
- Deploy frontend to Azure Static Web Apps
- Store generated artifacts in Azure Blob Storage
- Configure environment variables
- Add basic logging

Outcome:

- First hosted demo is available on Azure.

## Phase 8: Microsoft Fabric Integration

Goal: use Fabric for analytics and reporting.

Tasks:

- Store generation metadata
- Track number of apps generated
- Track app types and requested features
- Build Fabric dashboard
- Analyze usage patterns

Outcome:

- Business stakeholders can view platform usage and impact.

## Phase 9: Quality, Testing, and Governance

Goal: make the platform safer and more reliable.

Tasks:

- Add unit tests
- Add API tests
- Add generated code validation
- Add security checks
- Add approval workflow before deployment
- Add audit logs

Outcome:

- Platform becomes more enterprise-ready.

## Phase 10: Future Agents

Goal: expand beyond the single Code Generation Agent.

Possible future agents:

- Testing Agent
- Deployment Agent
- Triage Agent
- Security Review Agent
- Documentation Agent
- App Modernization Agent

Outcome:

- Platform evolves into a broader agentic software delivery system.

