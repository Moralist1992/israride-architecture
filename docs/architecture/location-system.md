# Location & Interaction Lifecycle

*Status:* Implemented\
*Date:* 2026-03-23

------------------------------------------------------------------------

# Overview

This document describes the interaction lifecycle between user role
selection, UI state transitions, geolocation acquisition, accuracy
validation, and map positioning.

The system ensures that geolocation is requested only after explicit
user interaction and that unreliable location data does not break the
user experience.

The lifecycle transitions the application from cinematic presentation
mode into a stable, precision-focused interaction mode suitable for
ride-hailing operations.

------------------------------------------------------------------------

# Interaction Lifecycle

Application Launch\
↓\
Cinematic Map Intro\
↓\
Role Selection UI\
↓\
Passenger Role Selected\
↓\
UI Transition (Exit Animation)\
↓\
Geolocation Permission Request\
↓\
Location Accuracy Validation\
↓\
Map Centering\
↓\
Pickup Interaction Mode

------------------------------------------------------------------------

# Role Selection & UI Interaction Layer

    [ EN ]                 [ 🌙 ]

          Choose your role

       [ Passenger ] [ Driver ]

Top controls are visually separated and do not interfere with role
selection.

------------------------------------------------------------------------

## Interaction Flow

1.  User selects a role\
2.  Exit animation is triggered\
3.  UI state is updated (`roleSelected = true`)\
4.  Role selection UI is removed\
5.  Map becomes the primary interaction surface

------------------------------------------------------------------------

## Exit Animation

-   Passenger button moves bottom-left\
-   Driver button moves bottom-right\
-   Role selection fades and scales down\
-   Top controls move to corners

------------------------------------------------------------------------

## UI State Management

``` js
roleSelected: boolean
```

------------------------------------------------------------------------

## Top Controls Behavior

Initial → centered\
Active → corners

------------------------------------------------------------------------

# Role-Triggered Geolocation

Passenger → requestUserLocation() → map.flyTo()

------------------------------------------------------------------------

# Location Service Module

enableHighAccuracy: true\
timeout: 8000\
maximumAge: 0

------------------------------------------------------------------------

# Location Accuracy Handling

  Source   Accuracy
  -------- ------------
  GPS      5--20m
  Wi-Fi    20--80m
  Cell     200--2000m
  IP       up to 10km

------------------------------------------------------------------------

# Accuracy Tiers

-   High \<200 → center map\
-   Medium → warning\
-   Low \>5000 → block

------------------------------------------------------------------------

# Retry Strategy

Low accuracy → retry → fallback skip

------------------------------------------------------------------------

# Notification System

showLocationWarning(message)

------------------------------------------------------------------------

# Map Integration

map.flyTo() after validation

------------------------------------------------------------------------

# Pickup Interaction Model

    Map moves → pin stays fixed → location is selected

------------------------------------------------------------------------

# Architectural Outcome

-   role-triggered geolocation\
-   UI state-driven rendering\
-   stable UI transitions\
-   accuracy-aware positioning\
-   map-centered interaction

------------------------------------------------------------------------

# Next Step

Pickup Confirmation Layer:

-   reverse geocoding\
-   address under pin\
-   confirm pickup
