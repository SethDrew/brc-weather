# BRC wind history — 2025 build + event

Source: Open-Meteo archive API (ERA5/IFS reanalysis) at 40.786, −119.204, Aug 11 – Sep 1, 2025. Event was Aug 24 – Sep 1.

Caveat: reanalysis is ~9–25 km resolution and smooths sub-grid convective gusts and dust squalls — treat peak gusts as a floor. A "27 mph" reanalysis peak was plausibly 35+ on the ground. Trends, timing, and direction are trustworthy; absolute peaks are conservative.

| Date | Peak gust | At | From | Hrs ≥25 | Hi/Lo °F | Precip |
|---|---|---|---|---|---|---|
| Aug 11 | 10 | 1 PM | N | 0 | 97/67 | — |
| Aug 12 | 21 | 7 PM | W | 0 | 100/70 | — |
| Aug 13 | 24 | 4 PM | SW | 0 | 97/67 | — |
| Aug 14 | 20 | 7 PM | W | 0 | 93/65 | — |
| Aug 15 | 20 | 5 PM | SW | 0 | 91/66 | — |
| Aug 16 | 24 | 9 PM | NW | 0 | 89/65 | — |
| Aug 17 | 20 | 7 PM | W | 0 | 86/64 | — |
| Aug 18 | 20 | 6 PM | W | 0 | 87/62 | — |
| Aug 19 | 18 | 4 PM | SW | 0 | 88/58 | — |
| Aug 20 | 12 | 5 PM | SW | 0 | 90/58 | — |
| Aug 21 | 12 | 7 PM | NW | 0 | 92/63 | — |
| Aug 22 | 12 | 4 PM | N | 0 | 96/66 | — |
| Aug 23 | 27 | 7 PM | SW | 1 | 97/70 | — |
| Aug 24 (gate) | 17 | 6 PM | W | 0 | 86/71 | 0.02″ |
| Aug 25 | 22 | 5 PM | W | 0 | 86/63 | — |
| Aug 26 | 26 | 8 PM | S | 1 | 84/65 | — |
| Aug 27 | 27 | 3 PM | SW | 2 | 82/59 | 0.08″ |
| Aug 28 | 12 | 3 PM | N | 0 | 83/58 | — |
| Aug 29 | 12 | 8 PM | NE | 0 | 85/59 | — |
| Aug 30 | 27 | 6 PM | NW | 1 | 89/62 | — |
| Aug 31 | 18 | 6 PM | SW | 0 | 92/63 | — |
| Sep 1 | 19 | 5 PM | SW | 0 | 92/64 | — |

## Takeaways for 2026 planning

- Every single daily peak fell between 1 PM and 9 PM, most 4–8 PM. Mornings were consistently calm — heavy lifting, shade-structure raising, and lag-bolt work belong before noon.
- Direction at peak was SW/W on 13 of 22 days. N/NE/NW peaks were the exception and mostly on the calmest days — consistent with the prevailing-sector assumption baked into the app's off-prevailing flag.
- The roughest stretch was Aug 23–27 (late build into early event): the only ≥25 mph hours, the only rain, and a cold front (highs dropped 97→82). It then died down completely Aug 28–29 — the mid-event calm you remembered.
- Build week proper (Aug 11–22) was mild in 2025: no hour reached 25 mph in reanalysis. Don't anchor on that — 2026's own forecast already shows 32–34 mph days in late August.

Raw hourly JSON can be re-pulled anytime:
`https://archive-api.open-meteo.com/v1/archive?latitude=40.786&longitude=-119.204&start_date=2025-08-11&end_date=2025-09-01&hourly=wind_speed_10m,wind_gusts_10m,wind_direction_10m,temperature_2m,precipitation&wind_speed_unit=mph&temperature_unit=fahrenheit&timezone=America/Los_Angeles`
