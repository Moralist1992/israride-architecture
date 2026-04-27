# Pickup Flow — Implementation (MVP)

## Overview

Implemented a dual-mode pickup selection system:

1. Automatic location detection (reverse geocoding)
2. Manual address refinement (forward geocoding)

The system is designed to be non-blocking, allowing users to either:
- accept the detected location
- or refine it manually

---

## Architecture

### Modules involved

- trip.js — pickup UI + orchestration
- reverseGeocode.js — coordinates → address
- forwardGeocode.js — text → coordinates
- pickupPin.js — visual map pin
- map.js — map instance control

---

## Features

### 1. Pickup Pin

- fixed at map center
- visually animated on map movement
- acts as primary location selector

---

### 2. Reverse Geocoding

- triggered on map move
- debounced (500ms)
- updates address dynamically

js
map.on('move', () => {
  debounce(updateAddress, 500)
});


---

3. Manual Search (Refine)

activated via Refine button

reveals:

input field

dropdown results

confirm button




---

4. Forward Geocoding

Implemented with:

debounce (350ms)

AbortController (cancels previous requests)


if (controller) controller.abort();
controller = new AbortController();


---

5. Dropdown Results

dynamic rendering

clickable items

triggers map flyTo



---

6. Confirm Logic

Two entry points:

Quick Confirm

button next to auto-detected address


Manual Confirm

button inside refine UI


Both currently:

close search UI

prepare for next flow step



---

UX Decisions

map-first interaction (not form-first)

user not forced into search

minimal UI obstruction

consistent control button design



---

UI System

Unified button styles:

.control-btn

.map-control-btn (temporary compatibility layer)


Goal: → migrate to single button system


---

Performance Considerations

debounce used in:

reverse geocode

forward geocode


request cancellation to prevent API flooding

minimal DOM updates



---

Known Limitations

selected location is not yet persisted

confirm action does not yet trigger trip creation

no route calculation yet



---

Next Steps

1. Persist selected coordinates in state


2. Connect pickup to trip creation


3. Add destination selection


4. Implement routing


5. Backend integration




---

Summary

This step establishes:

stable pickup selection system

scalable UI architecture

API-safe geocoding layer


Forms the foundation for full ride flow.