# Regulation Tracker — Ridesharing Law in Israel

## Purpose

This document tracks the status of legislation related to ridesharing and private drivers in Israel.

The goal is to ensure that the Israride platform remains compliant with evolving regulations.

---

## Current Status

- Law topic: Private drivers ridesharing legalization
- Status: Preliminary approval (first reading)
- Risk level: High (not yet enacted)
- Impact: Critical for MVP launch

---

## Key Requirements (Expected)

### Drivers
- Identity verification
- Minimum driving experience
- Background checks
- Valid insurance

### Vehicles
- Safety compliance
- Periodic inspection

### Platforms
- Registration with Ministry of Transport
- Complaint handling
- Driver rating system
- Data transparency

---

## Monitoring Sources

### Government
- Knesset legislation portal
- Ministry of Transport announcements

### News

Monitored via Google Alerts with site filters.

- Newsru Israel
- Calcalist
- Globes
- Ynet
- The Times of Israel


---

## Change Log

| Date | Source | Update | Impact |
|------|--------|--------|--------|
| 2026-02-19 | News | Law approved in preliminary reading | MVP still in risk zone |

---

## Product Impact Notes

- Driver onboarding must support document verification
- Platform must support ratings and complaints
- Insurance requirements may affect driver eligibility

---

## Compliance Zone Engine — Implemented (2026-02-21)

To support regulation-aware operations, Israride now includes a Compliance Zone Engine.

### Purpose
Enable enforcement of restricted geographic zones required by regulation or local transport policy.

### Capabilities
- Store restricted zones in global state
- Validate routes against restricted zones
- Provide explainable refusal reasons
- Prepare foundation for future geofencing

### Example refusal response

```json
{
  "allowed": false,
  "reason": "Route enters restricted zone: ben-gurion-airport",
  "zoneId": "ben-gurion-airport"
}