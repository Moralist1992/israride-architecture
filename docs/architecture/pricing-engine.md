# Pricing Engine — Policy-Controlled Architecture

## Overview

The Israride Pricing Engine is a policy-controlled system responsible for calculating trip fares based on administrator-defined rules.

Pricing behavior is not hardcoded. All calculation logic is governed by configurable policies, enabling regulatory compliance, transparency, and operational flexibility.

---

## Core Flow

Admin Policy → Pricing Engine → Fee Pipeline → Final Fare

1. A pricing policy defines calculation parameters  
2. The pricing engine calculates the base fare  
3. The fee pipeline applies additional charges  
4. A full fare breakdown is stored in the trip record  

---

## Pricing Models

### Meter Pricing (Primary)

Fare is calculated using distance and time:


fare = distance × perKmRate + time × perMinuteRate


**Characteristics:**
- Transparent calculation  
- No artificial base charges  
- Optional minimum fare (if required by regulation)  

---

### Driver Offer (Bargaining)

Fare is determined through negotiation between passenger and driver.

**Flow:**
- Passenger proposes price  
- Driver accepts or counter-offers  
- Agreed value becomes base fare  

**Purpose:**
- Flexible pricing  
- Driver autonomy  
- Enabled only if permitted by policy  

---

### Fixed Pricing (Future)

Predefined fares for specific routes or zones.

---

## Policy Configuration

All pricing behavior is controlled via `pricingPolicy`.

```js
pricingPolicy = {
  pricingModel: "meter",
  perKmRate: 4,
  perMinuteRate: 0.5,

  compensationLevyEnabled: true,
  compensationLevyType: "fixed",
  compensationLevyValue: 5,

  regulatoryFeeEnabled: false,
  platformFeeEnabled: false
}

Fee Pipeline

After base fare calculation, additional charges are applied through a fee pipeline.

| Fee               | Purpose          | Default  |
| ----------------- | ---------------- | -------- |
| Compensation Levy | Regulatory fund  | Enabled  |
| Regulatory Fee    | Government rules | Disabled |
| Platform Fee      | Monetization     | Disabled |


Compensation Levy Modes

The compensation levy supports multiple calculation models:

| Mode    | Description                    |
| ------- | ------------------------------ |
| Fixed   | Adds a constant amount         |
| Percent | Adds a percentage of base fare |


Fare Breakdown

The system generates a full pricing breakdown:

- base fare
- compensation levy
- regulatory fee
- platform fee
- total fare

Data Model

trip = {
  baseFare: 40,
  compensationLevy: 5,
  regulatoryFee: 0,
  platformFee: 0,
  totalFare: 45
}

Key Principles

- Pricing is policy-driven
- No hidden or artificial charges
- Transparent calculation model
- Adaptable to regulatory changes

Regulatory Adaptability

The system supports dynamic policy changes without code modification:

| Scenario                | Action                   |
| ----------------------- | ------------------------ |
| Levy required           | enable compensationLevy  |
| Levy becomes percentage | set levyType = percent   |
| Levy removed            | disable compensationLevy |
| Bargaining banned       | pricingModel = "meter"   |


Related Modules
- pricingPolicy.js
- pricingEngine.js
- meterPricing.js
- feePipeline.js
- trip.js