# 09 — Reverse Geocoding (Pin → Address)

## Overview

This module implements *reverse geocoding*, converting geographic coordinates into a human-readable address.

map center (lng, lat) → Mapbox API → address

It enables a core interaction model used in ride-hailing apps (Uber, Bolt):

👉 The user moves the map while the pin stays fixed.

---

## Core Concept

Instead of placing a marker manually:

- The *pin is fixed in the center of the screen*
- The *map moves underneath the pin*
- The *center of the map = selected location*

---

## User Interaction Flow

User drags map ↓ Map center changes ↓ moveend event fires ↓ Coordinates extracted (lng, lat) ↓ Reverse geocoding request ↓ Address returned from API ↓ UI updates address field

---

## Map Integration

### Getting coordinates

js
const center = map.getCenter();
const lng = center.lng;
const lat = center.lat;


---

Listening to movement

map.on('moveend', handleMove);


---

Reverse Geocoding API

Endpoint

https://api.mapbox.com/geocoding/v5/mapbox.places/{lng},{lat}.json


---

Example request

https://api.mapbox.com/geocoding/v5/mapbox.places/34.7818,32.0853.json?access_token=YOUR_TOKEN&language=en&types=address,poi,place


---

Parameters

access_token — Mapbox token

language=en — response language

types=address,poi,place — restricts results



---

Response Handling

Typical response structure:

{
  "features": [
    {
      "place_name": "Sderot David Ben Gurion 12, Tel Aviv, Israel"
    }
  ]
}


---

Extract address

const address = data.features[0]?.place_name;


---

UI Behavior

Address updates automatically after map movement

No typing required

Always reflects the pin position

Works in real time



---

Architecture

Modules involved

trip.js

Handles map movement

Triggers reverse geocoding


reverseGeocode.js

API request logic


map.js

Map initialization


uiState.js

UI state management




---

UX Characteristics

✔ No manual input required
✔ Fast interaction
✔ Mobile-friendly
✔ Familiar UX (Uber/Bolt pattern)


---

Limitations

Some locations do not have house numbers

Accuracy depends on Mapbox data

Rural areas may return only street or city

API rate limits apply



---

Error Handling (Recommended)

Future improvement:

if (!data.features.length) {
  return "Address not found";
}


---

Performance Notes

Reverse geocoding is triggered on moveend (not continuously)

Prevents excessive API calls

Can be improved with debounce if needed



---

Future Improvements

Address formatting (short vs full)

Caching results

Loading indicator while fetching

Fallback logic for missing addresses

Integration with forward geocoding (input)



---

Status

✅ Implemented
✅ Stable
🚀 Ready for integration with routing and input search