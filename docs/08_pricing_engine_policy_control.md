# Pricing Engine — Policy-Controlled Architecture

**Status:** Implemented  
**Date:** 2026-02-26  
**Scope:** Web MVP → Future mobile platforms  
**Applies to:** Fare calculation, regulatory compliance, monetization control  

---

## Overview

The Israride Pricing Engine is a policy-controlled system that calculates trip fares based on administrator-selected rules.

The system does not automatically choose pricing models. All pricing behavior is governed by platform policy and can be modified via future admin controls.

This ensures regulatory compliance, transparency, and operational flexibility.

Meter pricing is the **primary fare model** to ensure transparency and regulatory compatibility. Bargaining remains available as a policy-controlled fallback where permitted.

---

## Architecture

Admin Policy → Pricing Engine → Fee Pipeline → Final Fare

### Flow

1. Administrator selects pricing mode and rules.  
2. Pricing engine calculates the base fare.  
3. Fee pipeline applies regulatory and platform fees.  
4. Final fare and full breakdown are stored in the trip record.

---

## Supported Pricing Modes

### 1. Meter Pricing (Primary Mode)

Fare is calculated based on distance and time.

fare = distance * perKmRate + time * perMinuteRate


#### Key Principles

- No base fare  
- No pickup fee  
- Transparent calculation  
- Optional minimum fare if required by regulation  

```js
pricingModel: "meter"

2. Bargaining (Driver Offer) — Policy Fallback

Passengers and drivers negotiate a fare.

Passenger proposes price

Driver accepts or counter-offers

Agreed fare becomes base fare

pricingModel: "driver_offer"
Purpose

Driver autonomy

Flexible market pricing

Enabled only if permitted by regulation

3. Fixed Pricing (Future)

Predefined fares for zones, airports, or special routes.

pricingModel: "fixed"
Pricing Principles

Israride explicitly rejects artificial fare inflation mechanisms.

Not Supported

Base fare

Pickup fee

Hidden start charges

Supported (Regulatory Only)

Minimum fare (if required by law)

Price ranges

Mandatory levies

Policy-Controlled Configuration

All pricing behavior is controlled through pricingPolicy.

Example Policy
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

2. Bargaining (Driver Offer) — Policy Fallback

Passengers and drivers negotiate a fare.

Passenger proposes price

Driver accepts or counter-offers

Agreed fare becomes base fare

pricingModel: "driver_offer"
Purpose

Driver autonomy

Flexible market pricing

Enabled only if permitted by regulation

3. Fixed Pricing (Future)

Predefined fares for zones, airports, or special routes.

pricingModel: "fixed"
Pricing Principles

Israride explicitly rejects artificial fare inflation mechanisms.

Not Supported

Base fare

Pickup fee

Hidden start charges

Supported (Regulatory Only)

Minimum fare (if required by law)

Price ranges

Mandatory levies

Policy-Controlled Configuration

All pricing behavior is controlled through pricingPolicy.

Example Policy
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

Fee Pipeline Integration

After base fare calculation, the fee pipeline applies additional charges.

Fee	Purpose	Default
Compensation Levy	Taxi fund	Enabled
Regulatory Fee	Government requirement	Disabled
Platform Fee	Monetization fallback	Disabled

The pipeline returns a full breakdown and final total.

Hybrid Compensation Levy

The compensation levy supports both fixed and percentage-based models to comply with evolving legislation.

Configuration
compensationLevyEnabled: true,
compensationLevyType: "fixed" | "percent",
compensationLevyValue: number
Modes

Fixed — adds a constant amount per trip

Percent — adds a percentage of the base fare

Examples
Mode	Base Fare	Levy	Total
Fixed (₪5)	100	5	105
Percent (7%)	100	7	107
Purpose

Support current fixed levy discussions

Support future percentage-based regulation

Enable policy switching without code changes

Fare Breakdown Transparency

The platform stores and exposes a full fare breakdown for regulatory compliance and user transparency.

Breakdown Includes

Base fare

Compensation levy

Regulatory fee

Platform fee

Total fare

Supports

Legal transparency requirements

Dispute resolution

Tax reporting

Future invoice generation

Trip Data Model

Trips store a full fare breakdown for transparency and audits.

trip = {
  baseFare: 40,
  compensationLevy: 5,
  regulatoryFee: 0,
  platformFee: 0,
  totalFare: 45
}
Admin Panel Concept (Future)

The pricing engine is designed for manual control via an admin dashboard.

Policy Toggles
Pricing Mode

( ) Meter

( ) Bargaining

( ) Fixed

Fee Controls

[✓] Compensation Levy

 Regulatory Fee

 Platform Fee

Levy Mode

( ) Fixed amount

( ) Percentage

Rate Controls

Per Km Rate

Per Minute Rate

Minimum Fare (if required)

Regulatory Adaptability

The policy-driven architecture allows the platform to adapt to evolving legislation without code changes.

Supported Scenarios
Regulation	Policy Action
Levy required	enable compensationLevy
Levy becomes percentage	set levyType = percent
Levy removed	disable compensationLevy
Subscriptions banned	enable platformFee
Bargaining banned	pricingModel = "meter"
Price floor required	enable minFare
Strategic Impact

This architecture enables:

Legal compliance

Market flexibility

Transparent pricing

Protection from regulatory shifts

Future admin control

Resilience to regulatory changes without code refactoring

Related Modules

src/pricing/pricingPolicy.js

src/pricing/pricingEngine.js

src/pricing/meterPricing.js

src/pricing/feePipeline.js

src/modules/trip/trip.js