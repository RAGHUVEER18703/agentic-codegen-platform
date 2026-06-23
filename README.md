# Agentic Code Generation Platform

## Overview

This project is a first version of an agentic code generation platform for lightweight business applications.

The goal is to help business users and non-technical executives describe an application requirement in natural language and receive a generated application design, architecture, database model, API structure, UI plan, and starter codebase.

The first demo use case is a minimal Shipment Tracker application.

## Problem Statement

Business users often need small internal applications, dashboards, trackers, forms, and workflow tools. Today, these requests usually depend on technical teams for requirement understanding, architecture, development, deployment, and triaging.

This platform aims to reduce that dependency by using a backend Code Generation Agent that can convert natural language requirements into a structured application blueprint and generated code artifacts.

## First Version Scope

The first version will focus on a single backend agent:

**Code Generation Agent**

This agent will perform multiple internal steps:

- Understand user requirement
- Convert natural language into a structured app specification
- Generate application architecture
- Generate database design
- Generate API design
- Generate UI/page design
- Generate starter codebase
- Store generated artifacts in a generated apps workspace

The platform will not start with multiple independent agents. Instead, it will use one unified agent with modular internal steps. This keeps the first version simpler, easier to demo, and easier to extend later.

## Demo Application: Shipment Tracker

The Shipment Tracker app will be used as the first proof-of-concept.

Minimal features:

- Create shipment
- View shipment list
- View shipment details
- Update shipment status
- Search or filter shipments
- Basic dashboard with shipment counts by status

Out of scope for version 1:

- Route optimization
- Predictive delivery ETA
- Complex logistics planning
- Real carrier integration
- Advanced analytics

## Recommended Technology Stack

### Platform Backend

- Python 3.12
- FastAPI
- Pydantic
- LangGraph later, after deterministic workflow is stable
- uv or Poetry for dependency management

### Frontend

- React or Next.js
- TypeScript
- Simple business-focused UI

### Cloud

- Microsoft Azure for application hosting and cloud services
- Azure App Service or Azure Container Apps for backend deployment
- Azure Static Web Apps for frontend deployment
- Azure SQL Database or PostgreSQL for application data
- Azure Blob Storage for generated files/artifacts

### Microsoft Fabric

Microsoft Fabric can be used later for:

- storing generated project metadata
- reporting and analytics
- tracking generated app usage
- building dashboards for business users
- future data engineering and BI workflows

Fabric is not required for the very first working prototype, but it can be included in the roadmap.

## High-Level Workflow

```text
Business User
    |
    v
Web UI
    |
    v
FastAPI Backend
    |
    v
Code Generation Agent
    |
    v
Internal Workflow Steps
    - Requirement analysis
    - App specification
    - Architecture design
    - Database design
    - API design
    - UI design
    - Code generation
    |
    v
Generated App Workspace
    |
    v
Download / Review / Deploy
```

## Repository Structure

```text
agentic-codegen-platform/
  README.md
  docs/
    ARCHITECTURE.md
    ROADMAP.md
  api/
    main.py
  agents/
    code_generation/
      agent.py
      steps/
        analyze_requirement.py
        create_app_spec.py
        design_architecture.py
        design_database.py
        design_api.py
        design_ui.py
        generate_code.py
  contracts/
    app_spec.py
    generated_artifact.py
    user_requirement.py
    workflow_state.py
  prompts/
    code_generation/
      system_prompt.md
      app_spec_prompt.md
      architecture_prompt.md
      code_prompt.md
  generated_apps/
    .gitkeep
  infra/
    docker/
    azure/
  tests/
    .gitkeep
  pyproject.toml
  .env.example
  .gitignore
```

## First API Goal

The first backend API can expose one endpoint:

```text
POST /generate-app
```

Example request:

```json
{
  "app_name": "Shipment Tracker",
  "requirement": "Create a lightweight shipment tracker app where users can create shipments, update shipment status, and view shipment details."
}
```

Example response:

```json
{
  "status": "success",
  "app_name": "Shipment Tracker",
  "artifacts": [
    "app_spec.json",
    "architecture.md",
    "database_schema.sql",
    "api_contract.md",
    "ui_plan.md",
    "starter_code.zip"
  ]
}
```

## Development Principle

Start deterministic before becoming autonomous.

Version 1 should focus on:

- clear contracts
- predictable workflow steps
- reusable prompts
- generated artifacts
- simple UI
- simple deployment path

Avoid adding complex multi-agent collaboration, vector databases, long-term memory, or autonomous planning until the basic flow is stable.

## Demo Update

This line was added from feature/update-readme branch.
