# Pricing API

This document describes how ride pricing is calculated in the Israride system.

---

## 🎯 Overview

The pricing system calculates the total ride cost based on:

- distance
- time
- pricing mode
- regulatory rules

The system is designed to be transparent and adaptable to future legislation.

---

## 📡 Endpoint

POST /pricing/calculate

---

## 📥 Request

```json
{
  "distance_km": 10,
  "duration_min": 15,
  "pricing_mode": "meter",
  "region": "IL"
}


📌 Parameters

Field	Type	Description
distance_km	number	Total ride distance in kilometers
duration_min	number	Estimated ride duration in minutes
pricing_mode	string	Pricing type ("meter" or "fixed")
region	string	Region code (e.g., "IL")


⚙️ Processing Logic

Pricing is calculated in multiple steps:

Base fare calculation
Fee pipeline processing
Final price aggregation

1. Base Fare

Base fare is calculated using:

cost per kilometer
cost per minute

Example:

base_fare = (distance_km * price_per_km) + (duration_min * price_per_min)

2. Fee Pipeline

Additional fees may be applied:

regulatory fees
platform fees (if enabled)
special conditions (future extension)

Each fee is processed independently.

3. Final Price

Final price is calculated as:

total_price = base_fare + sum(fees)

📤 Response
{
  "base_fare": 25.0,
  "fees": [
    {
      "type": "regulatory",
      "amount": 3.0
    }
  ],
  "total_price": 28.0,
  "currency": "ILS"
}

📌 Response Fields

Field	    Type	Description

base_fare	number	Calculated base ride cost

fees	    array	List of applied fees

total_price	number	Final ride price

currency	string	Currency code

🔍 Example

Input:

Distance: 10 km
Duration: 15 min

Output:

Base fare: 25
Fees: 3
Total: 28

⚠️ Notes

All pricing values are configurable
Fee logic may change depending on regulation
The system is designed to remain transparent and auditable

🔮 Future Extensions

surge pricing
subscription adjustments
dynamic regulatory fees
location-based pricing

🧠 Key Idea

The pricing system is designed to:

remain transparent for users
be configurable for developers
adapt to regulatory requirements