# ADR-004 — Automatic Documentation Synchronization Between Private and Public Repositories

## Status

Accepted

## Date

2026-03-08

---

# Context

The Israride project is developed using two separate Git repositories with different visibility levels.

The goal is to keep **source code private** while maintaining **public access to system architecture documentation**.

To achieve this, the project uses the following repository structure:

1. **Private Development Repository**

Contains:

* application source code
* frontend implementation
* infrastructure configuration
* internal development files
* architecture documentation (`docs/`)

Repository visibility:

Private

---

2. **Public Architecture Repository**

Contains only:

* system architecture documentation
* product design documentation
* architectural decision records (ADR)
* regulatory and pricing system documentation

Repository visibility:

Public

This repository exists specifically to allow external reviewers (for example employers or collaborators) to study the architecture of the system without gaining access to the source code.

---

# Problem

Documentation is written and updated during development inside the private development repository.

Without automation this would require manually copying updated documentation into the public architecture repository.

Manual synchronization introduces several problems:

* documentation may become outdated
* additional manual work for the developer
* risk of forgetting to update public documentation
* inconsistency between repositories

A reliable automated solution is therefore required.

---

# Decision

The project implements **automatic documentation synchronization** using a Git hook and a PowerShell synchronization script.

The synchronization pipeline is triggered automatically after every push to the development repository.

Only the `docs/` directory is synchronized.

---

# Synchronization Architecture

The synchronization workflow operates as follows:

Developer push

↓

Git post-push hook

↓

PowerShell synchronization script

↓

robocopy mirrors documentation directory

↓

commit to architecture repository

↓

push to public architecture repository

---

# Implementation

## 1. Git Hook

Location:

.git/hooks/post-push

Content:

```
#!/bin/sh
"C:/Windows/System32/WindowsPowerShell/v1.0/powershell.exe" -ExecutionPolicy Bypass -File "C:/Projects/Israride/sync-docs.ps1"
```

This hook triggers the synchronization script automatically after each `git push`.

---

## 2. Synchronization Script

Location:

sync-docs.ps1

Responsibilities:

1. Copy documentation from development repository
2. Mirror documentation to architecture repository
3. Commit and push changes automatically

Example implementation:

```
$source = "C:\Projects\Israride\docs"
$target = "C:\Projects\israride-architecture\docs"

Write-Host "Syncing docs..."

robocopy $source $target /MIR

cd C:\Projects\israride-architecture

git add .

git commit -m "sync docs from dev repo" 2>$null

git push origin main

Write-Host "Docs synced successfully."
```

The `/MIR` flag ensures that the destination directory mirrors the source directory.

---

# Security Model

This architecture guarantees strict separation between implementation and documentation.

| Component               | Visibility |
| ----------------------- | ---------- |
| Development repository  | Private    |
| Architecture repository | Public     |
| Source code             | Private    |
| Documentation           | Public     |

Only the `docs/` directory is synchronized.

Sensitive components remain private, including:

* application source code
* pricing algorithms
* internal APIs
* infrastructure configuration
* environment variables

---

# Benefits

1. Documentation always remains up to date
2. Architecture can be shared publicly without exposing source code
3. No manual synchronization is required
4. Clear separation between **implementation** and **system architecture**
5. Architecture repository becomes a public documentation portal for the system

---

# Consequences

Developers must ensure that sensitive information is never placed inside the `docs/` directory.

Documentation must not include:

* `.env` files
* API keys
* internal service URLs
* private credentials
* sensitive code fragments

---

# Result

Architecture documentation is now automatically synchronized between repositories.

After each `git push` in the development repository:

1. Documentation changes are detected
2. Documentation is mirrored to the architecture repository
3. Changes are committed automatically
4. Public architecture documentation is updated immediately

This ensures that the architecture repository always reflects the latest system design.
