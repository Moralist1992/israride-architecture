# Location & Interaction Lifecycle

*Status:* Implemented  
*Date:* 2026-03-10

---

# Overview

This document describes the interaction lifecycle between user role selection, geolocation acquisition, accuracy validation, and map positioning.

The system ensures that geolocation is requested only after explicit user interaction and that unreliable location data does not break the user experience.

The lifecycle transitions the map from cinematic presentation mode into a stable, precision-focused interaction mode suitable for ride-hailing operations.

---

# Interaction Lifecycle

The application follows a structured interaction sequence:

Application Launch 
↓ 
Cinematic Map Intro 
↓ 
Role Selection Screen 
↓ 
Passenger Role Selected 
↓ 
Geolocation Permission Request 
↓ 
Location Accuracy Validation 
↓ 
Map Centering

This sequence guarantees that map positioning occurs only after the user explicitly requests location access.

---

# Role-Triggered Geolocation

The application does not request geolocation automatically during startup.

Location detection is triggered only after the user selects the **Passenger** role.

Passenger button 
↓ 
requestUserLocation() 
↓ 
map.flyTo(userLocation)

This interaction design ensures:

- explicit user consent
- privacy-aware behavior
- predictable map interaction flow

---

# Location Service Module

Geolocation logic is encapsulated in a dedicated module:
src/modules/location/locationService.js

The module provides a Promise-based wrapper around the browser geolocation API.

Primary function:
requestUserLocation()

Configuration used:
enableHighAccuracy: true timeout: 8000 maximumAge: 0

This configuration prioritizes accurate positioning while preventing outdated cached coordinates.

---

# Location Accuracy Handling

Geolocation accuracy depends on the available device sensors and network environment.

Typical sources of location data include:

| Source | Typical Accuracy |
|------|------|
GPS | 5–20 meters
Wi-Fi positioning | 20–80 meters
Cell tower triangulation | 200–2000 meters
IP fallback | up to 10 km

Because browser accuracy varies widely, the application implements a multi-tier accuracy handling strategy.

---

# Accuracy Tiers

## High Accuracy
accuracy < 200


Assumes reliable GPS or Wi-Fi positioning.

Behavior:

- map centers directly on detected location
- zoom level 14 is applied

---

## Medium Accuracy
200 < accuracy < 5000


Assumes coarse positioning from cellular triangulation.

Behavior:

- map centers on detected location
- user receives a warning suggesting improved connectivity

Example notification:
For better location accuracy enable Wi-Fi or Mobile Internet

---

## Low Accuracy
accuracy > 5000

Assumes unreliable IP-based geolocation.

Behavior:

- user receives a warning notification
- map centering is prevented

This prevents the application from jumping to incorrect coordinates caused by ISP-level location detection.

---

# Retry Strategy

Some browsers return poor accuracy immediately after permission approval.

To improve reliability the system performs a retry request when extremely low accuracy is detected.

accuracy > 5000 
↓ 
retry geolocation request

If the retry still produces inaccurate results, map centering is skipped.

---

# Notification System

The platform introduces a reusable notification component used to communicate location accuracy issues.

Module:
src/modules/ui/locationWarning.js

Primary function:
showLocationWarning(message)

Key characteristics:

- non-blocking UI
- automatic dismissal
- reusable across modules
- customizable message text

This component forms the foundation of the application's notification system.

Future use cases include:

- driver search status
- connectivity warnings
- address resolution feedback
- ride status notifications

---

# Map Integration

After valid coordinates are obtained and validated, the map centers on the user location using:
map.flyTo()

This action occurs only after:

- role selection
- successful geolocation request
- accuracy validation

This ensures stable map behavior and prevents unexpected camera movements.

---

# Architectural Outcome

The implemented interaction system establishes a robust bridge between user input and map behavior.

The platform now includes:

- role-triggered geolocation
- accuracy-aware positioning
- retry logic for unreliable geolocation
- reusable notification UI
- centralized map layer registry

These systems provide the foundation for upcoming ride-hailing functionality including:

- pickup point selection
- driver discovery
- route rendering
- trip state visualization