# Development Workflow

This project follows a structured Git-based workflow with separation between frontend, backend, and documentation.

---

## Workflow Overview

1. Changes are implemented in feature branches
2. Pull requests are created for each change
3. Changes are merged into the main branch
4. Documentation is automatically synchronized via GitHub Actions

---

## Backend API Example

The pricing API was implemented as a separate backend service.

### Repository

👉 https://github.com/Moralist1992/israride-api

### What was implemented

* Pricing API endpoint
* Policy-driven pricing logic
* OpenAPI specification
* Swagger UI (local + public)
* Integration with frontend

---

## Development Process

* Feature branch created
* Pull request opened
* Changes reviewed and merged
* Documentation updated and synced

---

## Architecture

```plaintext
Frontend (private)
        ↓
Backend API (public)
        ↓
OpenAPI (source of truth)
        ↓
Swagger UI (public)
        ↓
Docs (synced via GitHub Actions)
```

---

## Notes

The frontend repository is private, but backend API and documentation are public and demonstrate the development workflow.
