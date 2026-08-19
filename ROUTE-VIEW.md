# Route view — deferred feature

Context for building the drive-day route view. Ask for this a day or two before departure ("build the route view from ROUTE-VIEW.md").

## Purpose
Answer "when should I leave Oakland, and where will crosswinds threaten the load?" One glance per waypoint at your expected passing time.

## Design (agreed 2026-08-18)
- Lives in the same `index.html` as a second section or a `route.html` page — same styling, cache, and attribution.
- User enters a departure time; app computes ETA per waypoint from hardcoded leg durations and shows forecast gusts + direction at each waypoint at that passing time, colored with the same LEVELS thresholds (<15 Calm / <25 Breezy / <35 Dusty / 35+ Whiteout risk).
- Crosswind emphasis: the 447 stretch through the Pyramid Lake corridor (Wadsworth→Nixon→Gerlach) is where side gusts threaten loads. Flag wind direction roughly perpendicular to the road heading there (road runs ~N–S; W or E winds are the bad case).

## Waypoints (lat, lon, cumulative drive time from Oakland, no stops)
| Waypoint | Lat | Lon | Cum. hrs |
|---|---|---|---|
| Oakland | 37.8044 | -122.2712 | 0.0 |
| Sacramento | 38.5816 | -121.4944 | 1.5 |
| Donner Summit | 39.3157 | -120.3282 | 3.0 |
| Reno | 39.5296 | -119.8138 | 3.8 |
| Fernley | 39.6080 | -119.2518 | 4.3 |
| Wadsworth/Nixon (447) | 39.8455 | -119.3374 | 4.7 |
| Empire | 40.5730 | -119.3435 | 5.7 |
| Gerlach | 40.6518 | -119.3554 | 5.9 |
| BRC | 40.786 | -119.204 | 6.3 |

Loaded trailer: multiply durations ~1.2×, plus user-entered stop padding.

## API
Open-Meteo supports comma-separated coords in one call:
`latitude=37.8044,38.5816,...&longitude=-122.2712,...` → returns an array of per-location responses. Same hourly vars and models as the dashboard (`wind_speed_10m,wind_gusts_10m,wind_direction_10m,temperature_2m,precipitation`, models `gfs_hrrr,gfs_seamless,ecmwf_ifs025,icon_seamless`, `wind_speed_unit=mph`). HRRR covers the whole route (CONUS) but only ~48h out — so this view is only useful within 2 days of departure, which is exactly when it will be built. Fall back to GFS/ECMWF where HRRR is null (same `bestGust` pattern as index.html).

Timezone note: whole route is America/Los_Angeles; request that timezone and no conversion is needed.

## UI sketch
One row per waypoint: name · ETA (local) · gust with status dot + level name · direction arrow + compass · temp. A departure-time `<input type="datetime-local">` defaulting to tomorrow 6am. Recompute on change. Highlight the 447 rows when crosswind case triggers.
