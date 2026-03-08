# Project Context — Israride

## 1. Purpose of This Document

This document serves as a persistent context anchor for the **Israride project** and its associated documentation environment.

It ensures continuity of:

* architectural decisions
* development methodology
* documentation structure
* system design rationale

This file allows work on the project to resume from any point without relying on external discussion history.

It acts as the primary reference for understanding the project's technical context and documentation architecture.

---

# 2. Project Overview

Project name: **Israride**
Type: **Web application (Taxi platform MVP)**
Deployment target: **Firebase Hosting**
Frontend architecture: **Vite + Vanilla JavaScript**
Repository model: **Git-based, documentation-driven**

The project serves two primary purposes:

1. Development of a **startup MVP for a taxi platform operating in Israel**.
2. Creation of a **fully structured technical documentation environment** that documents the system architecture, development workflow, and engineering decisions.

The documentation environment is designed to reflect the evolution of a real engineering project.

---

# 3. Development Model

The project follows a **documentation-driven engineering workflow**.

Development activities are performed alongside structured documentation of:

* architectural decisions
* environment configuration
* system structure
* development processes

Artificial intelligence tools may assist during development and documentation preparation, but the documentation structure, content decisions, and architecture of the documentation system are designed and maintained within the project itself.

---

# 4. Methodology

The project follows a **documentation-driven development model**.

Core workflow principles:

Architectural decision → documented as ADR

Environment change → documented in Development Environment documentation

Structural change → documented before implementation

Implementation → committed as atomic logical steps

Documentation updated alongside code changes

This ensures that the documentation always reflects the current state of the system architecture.

---

# 5. Tooling Stack

## Development

* Vite (build tool)
* Node.js 20 (enforced via `.nvmrc`)
* npm
* VS Code
* Git

## Hosting & CI/CD

* Firebase Hosting
* GitHub Actions (Node 20)

## Documentation

* Markdown (Git-based documentation)
* ADR methodology (Architecture Decision Records)
* Architecture and environment documentation

Planned additions:

* OpenAPI / Swagger for API documentation

---

# 6. Current Architecture Baseline

The project has completed a transition from:

**Static HTML → Vite-based modular frontend architecture**

Current structure:

index.html — template entry processed by Vite

src/ — application source code

src/main.js — application entry point

public/ — static assets copied without processing

dist/ — production build output (deployment artifact)

Deployment flow:

src → npm run build → dist → Firebase Hosting

---

# 7. Established Governance

## Version Control

* Atomic commits
* One logical change per commit
* Semantic commit prefixes:

```
docs:
feat:
chore:
refactor:
```

---

## Environment Governance

Node.js version locked via `.nvmrc`

CI aligned with Node 20

`.gitignore` configured for:

* node_modules
* dist
* .firebase
* environment files

---

# 8. Documentation Structure

```
docs/
  00_project_context.md
  00_documentation_audit.md
  01_product_overview.md
  02_development_environment.md
  04_vite_migration_plan.md
  adr/
    ADR_001_frontend_migration_to_vite.md
```

Planned additions:

* ADR-002 — UI modularization
* Frontend architecture guide
* API documentation (OpenAPI)

---

# 9. Documentation Objectives

The documentation system aims to provide a structured description of:

* system architecture
* development environment
* engineering decisions
* product design constraints
* regulatory considerations

Key documentation components include:

* Architecture Decision Records (ADR)
* Environment configuration documentation
* Architecture and module structure documentation
* Git-based documentation workflow
* Information architecture for developer documentation
* API documentation (planned)

The objective is to maintain documentation that evolves together with the system.

---

# 10. Current Development Stage

Completed:

* Vite initialization
* Development environment governance
* Architecture baseline documentation

Next stage:

UI modularization inside `src/`:

* Layout module
* Header module
* Bottom sheet module
* Map module
* State management modules

This stage will be preceded by **ADR-002 (UI modularization decision)**.

---

# 11. Operational Rules

No architectural change without documentation.

No mixed commits (infrastructure + feature).

Documentation must be updated within the same iteration as code changes.

`dist/` is never edited manually.

Firebase deploys only the production build output.

---

# 12. Continuity Protocol

If project context needs to be restored:

1. Read this document
2. Read `02_development_environment.md`
3. Read the latest ADR
4. Check Git history for the last architectural commit
5. Resume from the **Current Development Stage** section

This process guarantees full recovery of the project's architectural and development context.
