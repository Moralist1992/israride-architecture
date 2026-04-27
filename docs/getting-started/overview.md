# Getting Started

This section helps you quickly understand how the Israride system is structured and how its core components interact.

---

## 🧭 What Is This System

Israride is a ride-hailing platform designed for a future legal framework in Israel that allows private drivers to offer transportation services.

The platform is built to support a regulated market where private ride services become legal, transparent, and compliant with government requirements.

It is positioned as an alternative to traditional platforms like Uber, focusing on a different economic model and pricing transparency.

Unlike traditional platforms, Israride offers:

- transparent pricing (distance + time + regulatory fees)
- no commission per ride
- subscription-based access for drivers
- adaptability to evolving legislation

---

## 🎯 What Problem It Solves

Traditional ride-hailing systems:

- use hardcoded pricing logic
- rely on platform commissions
- lack transparency in cost calculation

Israride introduces:

- configurable pricing policies
- transparent fee pipeline
- subscription-based monetization model

---

## 🧩 Core Components

The system is divided into several key parts:

### 1. Pricing Engine
Responsible for calculating ride cost based on:
- distance
- time
- selected pricing mode

📄 See: `../architecture/pricing-engine.md`

---

### 2. Trip Module
Handles ride lifecycle:
- request
- matching
- execution
- completion

📄 See: `../architecture/trip-module.md`

---

### 3. Map & Interaction System
Controls:
- map behavior
- geolocation triggering
- user interaction flow

📄 See: `../architecture/map-system.md`

---

## 🔄 Example Flow

1. User opens the app  
2. Selects role (driver or passenger)  
3. Geolocation is triggered  
4. Ride parameters are defined  
5. Pricing engine calculates cost  
6. Ride is executed  

📄 See detailed flow: `../flows/pickup-flow.md`

---

## 📊 Pricing Model (Simplified)

The ride price is calculated as:

Base Fare → Fee Pipeline → Final Price

Where:
- Base Fare = distance + time
- Fees = regulatory / platform / additional rules

---

## 🚀 How to Continue

To explore the system in more detail:

- Pricing logic → `../architecture/pricing-engine.md`
- Ride flow → `../flows/pickup-flow.md`
- Product context → `../concepts/product-overview.md`

---

## 🧠 Key Idea

The system is designed to be:

- configurable instead of hardcoded
- transparent instead of opaque
- adaptable instead of rigid

This makes it suitable for evolving regulatory environments.