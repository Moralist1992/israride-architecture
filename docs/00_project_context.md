Project Context — Israride
1. Purpose of This Document

This document serves as a persistent context anchor for the Israride project and the associated technical writing training workflow.

It ensures continuity of:

architectural decisions

development methodology

documentation strategy

learning objectives

This file allows work to resume from any point without relying on chat history.

2. Project Overview

Project name: Israride
Type: Web application (Taxi platform MVP)
Deployment target: Firebase Hosting
Frontend architecture: Vite + Vanilla JavaScript
Repository: Git-based, documentation-driven

The project is being developed as:

A startup MVP for a taxi platform in Israel

A portfolio case demonstrating technical writing competencies in a real engineering environment

3. Dual Role Model

The workflow follows a simulated team structure:

Development Lead (AI role)
Responsible for architecture, technical decisions, and implementation strategy.

Technical Writer (User role)
Responsible for:

documenting architecture and processes

maintaining ADRs

structuring documentation

ensuring reproducibility of environment

producing developer-facing documentation

4. Methodology

The project follows documentation-driven development:

Architectural decision → documented as ADR

Environment changes → documented in Development Environment

Structural changes → documented before implementation

Implementation → committed as atomic logical steps

Documentation updated alongside code

5. Tooling Stack
Development

Vite (build tool)

Node.js 20 (enforced via .nvmrc)

npm

VS Code

Git

Hosting & CI/CD

Firebase Hosting

GitHub Actions (Node 20)

Documentation

Markdown (Git-based documentation)

ADR methodology

Architecture and environment documentation

Planned: OpenAPI / Swagger for API documentation

6. Current Architecture Baseline

The project has completed the transition from:

Static HTML → Vite-based modular frontend architecture

Current structure:

index.html — template entry processed by Vite

src/ — application source code

src/main.js — application entry point

public/ — static assets (copied as-is)

dist/ — production build output (deployment artifact)

Deployment flow:

src → npm run build → dist → Firebase Hosting

7. Established Governance
Version Control

Atomic commits

One logical change per commit

Semantic commit prefixes (docs:, feat:, chore:, refactor:)

Environment Governance

Node.js version locked via .nvmrc

CI aligned with Node 20

.gitignore configured for:

node_modules

dist

.firebase

environment files

8. Documentation Structure
docs/
  00_project_context.md
  00_documentation_audit.md
  01_product_overview.md
  02_development_environment.md
  04_vite_migration_plan.md
  adr/
    ADR_001_frontend_migration_to_vite.md


Planned additions:

ADR-002 — UI modularization

Frontend architecture guide

API documentation (OpenAPI)

9. Training Objectives

This project is used to develop practical technical writing competencies:

ADR creation and lifecycle management

Environment documentation

Architecture documentation

Git-based documentation workflows

Information architecture for developer docs

Documentation aligned with real development changes

API documentation (planned)

The goal is to produce a portfolio demonstrating the ability to document a live engineering project.

10. Current Development Stage

Completed:

Vite initialization

Environment governance

Architecture baseline documentation

Next stage:

UI modularization inside src/:

Layout module

Header module

Bottom sheet module

Map module

State management modules

This will be preceded by ADR-002 (UI modularization decision).

11. Operational Rules

No architectural change without documentation.

No mixed commits (infrastructure + feature).

Documentation updated in the same iteration as code.

dist/ is never edited manually.

Firebase deploys only production build output.

12. Continuity Protocol

If chat context is lost:

Read this document

Read 02_development_environment.md

Read latest ADR

Check Git history for last architectural commit

Resume from the “Current Development Stage” section

This guarantees full recovery of project and training context.