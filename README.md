# Israride — Architecture & Regulatory System Design

> ⚠️ **Warning**
>
> GitHub mobile interface may not display the **docs folder** correctly.  
> If you are using a phone, enable **Desktop site** in your browser  
> or open GitHub from a computer.

**Policy-driven mobility platform architecture** designed for regulatory adaptability, dynamic pricing control, and advanced UX motion lifecycle.

This repository contains architectural documentation only.  
The implementation layer remains private to protect intellectual property and strategic system design.

---

## 🧠 Project Vision

Israride is designed as a regulatory-aware mobility platform capable of adapting to evolving legislation without requiring structural rewrites.

The system is built around a centralized policy layer that governs:

- Pricing modes
- Fee logic
- Compensation levy models
- Regulatory toggles
- Interaction behavior

The architecture prioritizes flexibility, compliance, and long-term scalability.

---

## 🧩 What This Repository Demonstrates

This public repository showcases:

- Policy-controlled pricing architecture  
- Hybrid compensation levy model (fixed / percentage)  
- Meter vs bargaining pricing abstraction  
- Fee pipeline modeling  
- Regulatory adaptability design  
- Map motion lifecycle system  
- Role-based geolocation flow  
- Architectural documentation discipline  

The goal is to demonstrate system thinking and product-level architecture — not just code implementation.

---

## 📁 Documentation Structure

```
/docs/
  00_project_context.md
  01_product_overview.md
  02_development_environment.md
  03_regulation_tracker.md
  04_monetization_strategy.md
  05_trip_module.md
  06_map_foundation.md
```

Each document explains a key subsystem or strategic design decision.

---

## 🏗 Core Architectural Concepts

### 1️⃣ Policy-Controlled Pricing Engine

The pricing system is governed entirely through centralized configuration.

Supported modes:

- Meter pricing (distance + time)
- Driver-offer bargaining model
- Fixed pricing (future-ready abstraction)

All behavior is administrator-controlled.

---

### 2️⃣ Hybrid Compensation Levy Model

The system supports regulatory levy scenarios:

- Fixed amount per trip
- Percentage of fare
- Toggle-based activation

This enables adaptation to government compensation fund requirements.

---

### 3️⃣ Fee Pipeline Architecture

Base Fare → Fee Pipeline → Final Fare

Pipeline supports:

- Compensation levy
- Regulatory fees
- Platform fees
- Future extensibility

Each trip stores a full breakdown for transparency and audits.

---

### 4️⃣ Motion Lifecycle System

The map interaction is architected in phases:

Cinematic Splash → Stabilized Interactive Mode → Role-Based Flow → Geolocation Focus

Motion continuity is preserved across transitions to create spatial coherence and perceived performance.

---

### 5️⃣ Role-Based Interaction Logic

Passenger and driver flows are separated at the architectural level.

Geolocation is triggered by role selection, not automatically at app load.

This ensures:

- Privacy awareness
- Explicit permission handling
- Controlled motion lifecycle

---

## 🔐 Why Implementation Is Private

The implementation layer is intentionally private because it contains:

- Proprietary pricing mechanics
- Strategic regulatory modeling
- Competitive system design decisions
- Business-sensitive configuration structures

This repository exists to present architectural capability and structured product thinking.

---

## 🛠 Implementation Stack (Private Layer)

- Modular JavaScript architecture
- Mapbox GL JS
- Policy-driven pricing configuration
- Centralized state management
- Compliance zone modeling
- Hybrid levy abstraction

---

## 🎯 Strategic Positioning

The architecture is built to survive regulatory volatility.

Instead of hardcoding pricing rules, the system abstracts regulation into policy toggles, enabling adaptation without structural rewrites.

This approach reduces legal risk and preserves operational flexibility.

---

## 👤 Author

Moralist1992  
Israel  

Mobility systems architecture  
Regulatory-adaptive product design  
Policy-driven pricing modeling