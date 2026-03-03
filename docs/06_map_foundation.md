# Map Foundation — Israel Default View

**Status:** Implemented  
**Date:** 2026-02-22  
**Last Updated:** 2026-03-03

---

## Overview

The Map Foundation introduces Mapbox as the background layer of the Israride application.

The map is initialized with a dark theme and centered on Israel, establishing a localized user experience.

The foundation includes a cinematic motion system for application launch, followed by a stabilized interactive mode optimized for geolocation accuracy and user control.

---

## Goals

- Provide geographic context for ride interactions
- Establish Israel as the default operational region
- Enable GPS-based passenger positioning
- Support future compliance zone visualization
- Deliver a premium launch experience without sacrificing interaction precision

---

## Implementation Details

### Map Provider
- Mapbox GL JS

### Default View
- Center: Israel geographic center
- Zoom: Regional fly-in transitioning to city-level focus

### Map Style
- Dark theme (`mapbox/dark-v11`)

### Bounds Restriction
Map navigation is currently constrained to the Israel region to maintain contextual relevance during MVP.

---

## Cinematic Intro & Motion System

### Capabilities

- Satellite fly-in from regional zoom to city level (Tel Aviv default focus)
- Seamless splash-to-map transition with no static frames
- Camera docking via zoom-only stabilization (no center shift)
- Controlled splash breathing via subtle zoom in/out loop
- Motion timing synchronized with UI overlay appearance
- Single-trajectory fly-in ensuring seamless cinematic motion

---

## Motion Lifecycle Architecture

The motion system is divided into two distinct operational stages:

### Stage 1 — Cinematic Mode (Splash)

Active during application launch.

Includes:

- Fly-in animation
- Zoom-only docking
- Controlled breathing effect

Breathing is active only while the role selection screen is visible.

---

### Stage 2 — Interactive Mode

Activated immediately after role selection.

Characteristics:

- Breathing is explicitly stopped
- Map becomes fully stabilized
- Camera control prioritizes precision over cinematic effect
- No automatic zoom cycles are permitted

This separation prevents motion interference with geolocation accuracy and user interactions.

---

## Role-Based Geolocation Control

Geolocation is not requested at application start.

It is triggered only after the user selects the Passenger role.

### Passenger Flow

1. Breathing stops
2. Browser geolocation permission is requested
3. If granted, the map flies to the user's coordinates
4. Map stabilizes at zoom level 14
5. No cinematic motion resumes

This ensures:

- Accurate pickup positioning
- Elimination of visual drift
- Clear transition from cinematic to functional mode

---

## Accuracy Handling Strategy

Geolocation behavior adapts based on reported accuracy:

- High accuracy (WiFi/GPS) → zoom 14
- Medium accuracy → zoom 13
- Low accuracy (IP fallback) → conservative centering

Breathing is never active during geolocation.

---

## Architectural Role

The map acts as the foundational UI layer:

- Background: Map
- Overlay: UI modules (driver, ride flow, controls)
- Data source: future trip and compliance modules
- Motion layer: splash-only cinematic system
- Interaction layer: precision-stabilized camera control

---

## Future Enhancements

- Pickup point pin system
- Route rendering
- Compliance zone overlays
- Theme switching (light/dark)
- Multilingual map labels
- Adaptive zoom based on pickup confirmation
- Performance tuning for low-end devices
- Role-based motion transitions refinement

---

## Related Modules

- `modules/map/map.js`
- `modules/layout/layout.js`
- `modules/trip/trip.js`
- `modules/compliance/zoneEngine.js`
- `modules/splash/splash.js`
- `modules/location/locationService.js`
- `modules/ui/roleSelection.js`