# 10 — UI: Map Controls, Pin UX & Theme Fix

## 📅 Date
2026-04-13

---

## 🎯 Summary

Implemented core UX improvements for the map interface:

- Unified map control buttons (zoom + GPS)
- Improved pickup pin visibility and behavior
- Added pin animation (Uber-style)
- Fixed theme switching logic
- Implemented dynamic text color based on theme

---

## 🧭 Map Controls (Zoom + GPS)

### Added

- Zoom controls:
  - + zoom in
  - - zoom out
- Positioned above GPS button (bottom-right)

### Behavior

- Zoom buttons use map.easeTo
- Zoom is centered on screen (pickup pin)

### UI

- Introduced shared class:

css
.map-control-btn

Result

Consistent UI (same size, shadow, interaction)

Matches production apps (Uber/Bolt patterns)



---

📍 Pickup Pin Improvements

Visual

Reduced size for better balance

Improved contrast (visible on light & dark maps)


Behavior

Added animation:

movestart → pin lifts

moveend → pin drops



Implementation

map.on('movestart', ...)
map.on('moveend', ...)

Result

Clear feedback when selecting location

Feels more "alive" and interactive



---

🎬 Pin Animation

Subtle vertical lift effect

Shadow scaling for depth illusion


UX Goal

Simulate "picking up" a location point like in Uber


---

🎛 Theme System Fix

Problem

Theme required double click

Multiple light styles were used


Solution

Synced UI state with DOM:


document.body.classList.add(`theme-${theme}`)

Removed conflicting styles



---

🎨 Dynamic Text Color

Target

"Choose your role" title

Behavior

Light theme → black text

Dark theme → white text


Implementation

body.theme-light .role-selection h2 { color: #111; }
body.theme-dark .role-selection h2 { color: #fff; }


---

🧱 Architecture Notes

No inline styles used

No DOM restructuring

Theme handled via global class (body)

UI remains reactive via uiState



---

🚀 Result

Stable UI (no regressions)

Improved usability

Cleaner visual hierarchy

Scalable styling approach



---

🔜 Next Step

Implement manual address input:

"Refine pickup location"

Address search (Mapbox Geocoding)

Map recentering based on result