# ADR_003 — State Container Architecture

**Status:** Draft  
**Date:** 2026-02-19  
**Deciders:** Israride Architecture  
**Technical Story:** Establish a single source of truth for application state in a SPA MVP with compliance requirements.

---

## Context

Israride is a Vite-based Single Page Application designed to support private ride services in Israel under emerging transportation regulations.

The platform must support:

- driver registration and verification
- trip lifecycle logging
- compliance zones and restrictions
- auditability and transparency

At the MVP stage:

- the application is frontend-only
- there is no backend
- state exists only at runtime
- modules are dynamically rendered
- simplicity and transparency are prioritized

Previously, modules operated with stateless runtime objects, which prevented:

- centralized audit logging
- cross-module data access
- compliance validation
- future persistence integration

A state container is required to serve as the single source of truth.

---

## Decision

Adopt a minimalist, event-driven state container implemented as a singleton module.

### Key characteristics

- Single source of truth for:
  - drivers
  - trips
  - compliance zones

- Direct module imports:
  ```js
  import { addDriver } from '../../state/store.js';
