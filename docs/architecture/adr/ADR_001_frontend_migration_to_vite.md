# ADR-001: Frontend Migration to Vite

Status: Accepted
Approved by: Product & Development
Date: 2026-02-11  
Decision Owner: Development Team  
Documentation Owner: Technical Writer  

---

## 1. Context

The current frontend implementation is a monolithic single HTML file with inline CSS and JavaScript. 

Limitations identified:

- No modular structure
- No separation of concerns
- No scalable integration point for API layer
- No build process
- No production optimization
- Difficult maintainability as project complexity grows

The project is expected to evolve into a full Taxi MVP with backend API integration and role-based functionality.

---

## 2. Problem Statement

The existing frontend structure will not support:

- API integration
- Scalable feature growth
- Clean separation between UI logic and business logic
- Production-ready performance optimization

Without structural changes, future development will introduce technical debt and maintenance risks.

---

## 3. Decision

Adopt **Vite** as the frontend build tool and introduce a modular JavaScript architecture.

The new structure will include:

- `src/` directory for application source code
- Modular JS files
- Build step generating `/dist`
- Firebase deployment of production build artifacts

Migration approach:

- Incremental refactor
- Preserve UI design
- Gradually move inline logic into modules

---

## 4. Alternatives Considered

1. Keep current static structure  
   - Rejected due to scalability limitations.

2. Migrate to React  
   - Considered too complex for current MVP stage.

3. Use Vite + Vanilla JS  
   - Selected as balance between simplicity and scalability.

---

## 5. Consequences

### Positive

- Scalable architecture
- Cleaner code separation
- API-ready structure
- Production build optimization

### Negative

- Introduction of build complexity
- Need to update CI/CD pipeline
- Firebase configuration update required

---

## 6. Documentation Impact

The following documents must be updated:

- System Architecture
- Deployment Guide
- CI/CD Documentation
- Frontend Architecture Document

---

## 7. Status Tracking

This ADR will be marked as:

- Proposed → Accepted → Implemented

Implementation phase begins after approval.
