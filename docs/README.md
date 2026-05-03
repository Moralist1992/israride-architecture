# Israride — Technical Documentation

This repository contains the technical documentation for **Israride**, a ride-hailing platform designed for a future regulated market in Israel, where private drivers can legally provide transportation services.

The system is built as a transparent, regulation-ready alternative to traditional platforms such as Uber.

---

## 🚗 About the Project

Israride is based on a different economic and pricing model:

* transparent pricing (distance + time + regulatory fees)
* no commission per ride
* subscription-based access for drivers
* adaptability to evolving regulatory requirements

The platform is designed with a strong emphasis on clarity, modularity, and system transparency.

---

## 🚀 Live System (API & Documentation)

The backend API is fully deployed and publicly accessible.

### 🔗 Backend API (Production)

👉 `https://israride-api.onrender.com/health`

---

### 🔗 Swagger UI (Interactive API)

👉 `https://moralist1992.github.io/israride-api/swagger/`

---

### 🔗 OpenAPI Specification (Source of Truth)

👉 `https://github.com/Moralist1992/israride-api/blob/main/docs/api/openapi.yaml`

---

## 🚀 Getting Started

Start here to quickly understand how the system works:

* Overview → `docs/getting-started/overview.md`
* Quick Start → `docs/getting-started/quick-start.md`

---

## 🧠 Product & Concepts

* Product Vision → `docs/concepts/product-vision.md`
* Monetization Model → `docs/concepts/monetization.md`
* Regulatory Context → `docs/concepts/regulation.md`
* Documentation Style Guide → `docs/concepts/documentation-style-guide.md`

---

## 📦 Product Planning

* MVP Scope → `docs/product/mvp-scope.md`
* Product Roadmap → `docs/product/roadmap.md`

---

## 🏗 System Architecture

* Pricing Engine → `docs/architecture/pricing-engine.md`
* Trip Module → `docs/architecture/trip-module.md`
* Map System → `docs/architecture/map-system.md`

---

## 🔄 User Flows

* Pickup Flow → `docs/flows/pickup-flow.md`

---

## 📡 API Documentation

* Pricing API → `docs/api/pricing.md`
* OpenAPI Specification → `docs/api/openapi.yaml`

---

## ⚙️ Backend Implementation (Pricing API)

The pricing calculation logic is implemented in a dedicated backend service.

This service exposes a REST API and defines its contract using OpenAPI. Interactive API documentation is available via Swagger UI.

### Repository

👉 `https://github.com/Moralist1992/israride-api`

### API Endpoint

POST `/api/v1/pricing/calculate`

---

## 🧠 Architecture Note

The frontend does not perform any pricing calculations.

It sends trip parameters (distance and duration) to the backend, which applies internal pricing policies and returns the final fare.

This ensures:

* centralized pricing logic
* consistency across the system
* adaptability to regulatory changes

---

## 🛠 Development Workflow

Detailed workflow documentation:

👉 `docs/architecture/development-workflow.md`

---

## 🎯 What This Documentation Covers

This documentation provides:

* a structured overview of the system
* clear explanation of product and architecture decisions
* developer-oriented specifications (API, flows, system behavior)
* a consistent and navigable documentation structure
