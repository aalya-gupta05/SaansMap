# 🌬️ SaansMap — Delhi Clean Air Map

**Google shows you that the air is bad. SaansMap shows you where the clean air is.**

Delhi-NCR's first Clean Air Score map that combines **live air quality** with
**green cover** to give every neighbourhood a 0–100 score — which areas are
safe to breathe, when to go outside, and where to take a walk.

Built for **Amazon Environmental Hacks** (DTU, Oct 2026).

## 😷 The Problem
~2 crore people in Delhi breathe air up to 10x worse than WHO limits.
Existing AQI apps show a number — "AQI 320" — but never answer the real
question: *"So what should I do — where do I go?"* Monitoring exists;
actionable guidance does not.

## 💡 The Solution — SaansMap Score
**SaansMap Score = 70% Air Score + 30% Green Cover (within 1 km)**

For every monitoring station:
- **Air Score** = `max(0, 100 − PM2.5 / 2.5)` — from live WAQI data
- **Green Cover %** — share of the 1 km circle covered by parks/forests
  (Overpass API, point-in-polygon sampling)
- Combined into a single 0–100 score, colour-coded on the map (green → red)

## ✨ Features
- 🗺️ Live Delhi-NCR map; marker size = pollution severity
- 📊 Station popup: PM2.5, Air Score, Green Cover %, SaansMap Score, data age
- 🌳 "Green Areas" layer — polygons of all Delhi parks/forests with toggle
- ⏱️ Freshness rules: readings older than 24h turn grey and are excluded
  from the city average
- 📋 Ranked station list (best → worst); tap a row to zoom & open popup
- 🛡️ Reliability by design: green data is cached; if Overpass is down the
  air map still works

## 🛠️ Tech Stack
| Layer | Tools |
|---|---|
| Map | Leaflet.js + OpenStreetMap |
| Air quality | WAQI API (live PM2.5) |
| Green cover | Overpass API (OSM parks, forests, gardens) |
| Hosting | **AWS Amplify** (static hosting + CloudFront CDN) |
| Language | Plain HTML/CSS/JS — zero build step |

## ☁️ AWS
The app is hosted on **AWS Amplify** (static hosting served through the
CloudFront edge CDN).
Roadmap: Lambda-based scheduled data refresh + DynamoDB for historical trends.

## 🎥 Demo Video
[Add your YouTube link here]

## 🚀 Run Locally
Just open `index.html` in a browser. No build step, no install.
(You need to add your own WAQI token in the code.)

## 🤖 AI Tools Used (declared as per rules)
Replit Agent (initial build & debugging), AI assistant (research, code review,
documentation).

## 🔮 Roadmap
- Safe-hour recommendations ("best walk window today: 7–8 AM")
- Ward-level score aggregation
- Alexa skill: *"Alexa, is it safe to go to Anand Vihar?"*
- Low-cost community sensor network feeding the score

## 🙋 Author
Solo build — Amazon Environmental Hacks 2026 (Online track)
