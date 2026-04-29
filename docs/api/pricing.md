# Pricing API

This document describes how to interact with the pricing service in the Israride system.

For pricing logic, calculation rules, and policy configuration, see:
`docs/architecture/pricing-engine.md`

---

## 🎯 Overview

The pricing API calculates the total trip cost based on trip parameters.

Pricing is determined by system-defined policies. Clients provide trip data only, while pricing rules and rates are applied internally.

---

## 📡 Endpoint

POST /pricing/calculate

---

## 📥 Request

```json
{
  "distance": 10,
  "duration": 15,
  "pricing_policy": "standard"
}

📌 Parameters

| Field          | Type   | Description                               |
| -------------- | ------ | ----------------------------------------- |
| distance       | number | Trip distance in kilometers               |
| duration       | number | Estimated trip duration in minutes        |
| pricing_policy | string | Identifier of the pricing policy to apply |

⚙️ Processing (High-Level)

The request is processed in three stages:

Base fare calculation (distance and time)
Policy application (fees, constraints, adjustments)
Final price aggregation

Detailed logic is defined in:       `docs/architecture/pricing-engine.md`


📤 Response

{
  "base_fare": 25.0,
  "distance_cost": 20.0,
  "time_cost": 5.0,
  "adjustments": 3.0,
  "total_price": 28.0,
  "currency": "ILS"
}

📌 Response Fields

| Field         | Type   | Description                                 |
| ------------- | ------ | ------------------------------------------- |
| base_fare     | number | Fixed component derived from pricing policy |
| distance_cost | number | Cost calculated from distance               |
| time_cost     | number | Cost calculated from duration               |
| adjustments   | number | Policy-based fees and adjustments           |
| total_price   | number | Final trip price                            |
| currency      | string | Currency code                               |

## 🧠 Pricing Behavior Notes

The pricing calculation depends on configurable parameters such as:

- price per kilometer
- price per minute
- applied fees (e.g. regulatory or platform fees)

These values are not hardcoded and may vary depending on region and system configuration.

The pricing engine follows a modular approach, where each component (distance, time, fees) is calculated independently and then aggregated into the final price.

🔍 Example

Request:

- distance: 10 km
- duration: 15 min

Response:

- total_price: 28.0 ILS

⚠️ Notes
Pricing parameters (rates, fees) are defined by the system and are not provided by the client
Pricing behavior is fully controlled by policy configuration
The API returns a transparent price breakdown

🧠 Key Idea

The API separates input from pricing logic:

clients provide trip parameters
the system applies pricing rules and policies

This ensures consistency, flexibility, and regulatory compliance.