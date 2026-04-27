# Trip Module — Architecture

**Status:** Implemented  
**Date:** 2026-02-21  
**Scope:** Web MVP  

---

## Purpose

The Trip Module represents the core domain entity of the Israride platform.

It manages the lifecycle of trips and serves as the integration point between:

- map and routing
- compliance validation
- pricing and monetization
- audit and regulatory logging

---

## Responsibilities

- Create trips
- Store trip data in global state
- Track trip lifecycle (active → completed)
- Support compliance validation
- Support geospatial data (origin, destination)
- Prepare for pricing and regulatory fees
- Provide audit-ready trip records

---

## Trip Data Model

```js
trip = {
  id: string,
  driverId: string,

  origin: { lat, lng } | null,
  destination: { lat, lng } | null,
  route: null,

  status: "active" | "completed" | "cancelled",
  createdAt: ISODate,
  endedAt: ISODate | null,

  proposedFare: number | null,
  agreedFare: number | null,
  regulatoryFee: number | null,
  platformFee: number,
  pricingModel: "driver_offer"
}