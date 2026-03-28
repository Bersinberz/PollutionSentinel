<div align="center">

<img src="client/asserts/logo.png" alt="Chennai Pollution Monitor Logo" width="100"/>

# Chennai Pollution Monitor

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Inter&weight=700&size=22&pause=1000&color=3498DB&center=true&vCenter=true&width=600&lines=Real-Time+Air+Quality+Monitoring;Powered+by+Google+Air+Quality+API;AI+Chatbot+%E2%80%94+Mr.+Pollution+Sentinel;ML-Based+AQI+Prediction;SMS+Alerts+via+Twilio" alt="Typing SVG" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white"/>
  <img src="https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white"/>
  <img src="https://img.shields.io/badge/Twilio-F22F46?style=for-the-badge&logo=twilio&logoColor=white"/>
  <img src="https://img.shields.io/badge/NVIDIA_AI-76B900?style=for-the-badge&logo=nvidia&logoColor=white"/>
  <img src="https://img.shields.io/badge/Leaflet.js-199900?style=for-the-badge&logo=leaflet&logoColor=white"/>
</p>

</div>

---

## Overview

Chennai Pollution Monitor is a full-stack, real-time air quality monitoring platform for Chennai, India. It tracks AQI across **90+ zones**, predicts next-hour pollution levels using machine learning, sends SMS alerts via Twilio, and features an AI-powered chatbot — **Mr. Pollution Sentinel** — backed by NVIDIA's LLM API.

---

## Features

| Feature | Description |
|---|---|
| **Live AQI Dashboard** | Real-time AQI data for 90+ Chennai zones via Google Air Quality API |
| **Interactive Map** | Leaflet.js map with color-coded zone markers and popups |
| **ML Prediction** | Linear regression model predicts next-hour AQI from historical CSV data |
| **AI Chatbot** | Mr. Pollution Sentinel — NVIDIA Qwen LLM with live AQI context |
| **SMS Alerts** | Twilio integration sends AQI alerts to users based on their GPS location |
| **Trends & Charts** | Chart.js visualizations — AQI distribution, pollutant breakdown, zone comparison |
| **Alert History** | Monthly alert history bar chart for the last 12 months |
| **Auto Refresh** | Dashboard auto-refreshes every hour; trends every 2 minutes |

---

## Project Structure

```
├── client/
│   ├── index.html          # Landing page — location input + chatbot
│   ├── dashboard.html      # Main dashboard — AQI cards, map, zone selector
│   ├── graph.html          # Trends — Chart.js visualizations & stats
│   ├── alerts.html         # Active alerts + monthly alert history chart
│   └── asserts/
│       ├── logo.png
│       └── sentinel.png    # Mr. Pollution Sentinel mascot
└── server/
    ├── server.js           # Express API — dashboard, chat, location check
    ├── predict_aqi.py      # Python ML script — linear regression AQI prediction
    └── chennai_hourly_aqi.csv  # Historical AQI dataset for training
```

---

## Tech Stack

**Frontend**
- Vanilla HTML/CSS/JS with Inter font
- Leaflet.js for interactive maps
- Chart.js for data visualizations

**Backend**
- Node.js + Express
- Google Air Quality API for live AQI data
- NVIDIA API (Qwen 3 Coder 480B) for AI chatbot responses
- Twilio for SMS alerts
- Python + scikit-learn for AQI prediction

---

## Getting Started

### Prerequisites

- Node.js v18+
- Python 3.8+
- API keys: Google Air Quality, NVIDIA, Twilio

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/chennai-pollution-monitor.git
cd chennai-pollution-monitor

# Install Node dependencies
cd server
npm install

# Install Python dependencies
pip install pandas scikit-learn numpy
```

### Environment Variables

Create a `.env` file inside the `server/` directory:

```env
GOOGLE_API_KEY=your_google_air_quality_api_key
NVIDIA_API_KEY=your_nvidia_api_key
TWILIO_SID=your_twilio_account_sid
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_PHONE=+1your_twilio_phone_number
PORT=3000
```

### Run

```bash
# From the server/ directory
node server.js
```

Then open `http://localhost:3000` in your browser.

---

## Pages

### Home (`index.html`)
Enter your name, phone number, and GPS coordinates (or use auto-detect). The server fetches your local AQI, shows a result dialog, and sends an SMS alert if AQI > 30.

### Dashboard (`dashboard.html`)
- Overall Chennai AQI + predicted next-hour AQI
- Zone dropdown with AQI bar indicator
- Leaflet map with color-coded markers per zone
- Scrollable alert list for zones with AQI > 50

### Trends (`graph.html`)
- Stats overview: overall AQI, predicted AQI, zone count, most polluted zone
- AQI distribution bar chart (top 15 zones)
- Dominant pollutants doughnut chart
- Top 10 most polluted zones horizontal bar chart
- Air quality status breakdown pie chart

### Alerts (`alerts.html`)
- Active alert cards for all zones with AQI > 50
- Monthly alert history bar chart (last 12 months)

---

## AQI Color Scale

| AQI Range | Status | Color |
|---|---|---|
| 0 – 50 | Good | 🟢 Green |
| 51 – 100 | Moderate | 🟡 Orange |
| 101 – 200 | Unhealthy | 🔴 Red |
| 201 – 300 | Very Unhealthy | 🟣 Purple |
| 300+ | Hazardous | ⚫ Dark Red |

---

## ML Prediction

`predict_aqi.py` loads `chennai_hourly_aqi.csv`, trains a `LinearRegression` model on historical hourly AQI data, and predicts the AQI for the next hour. The Node.js server spawns this script on each dashboard request and includes the result in the API response.

---

## AI Chatbot — Mr. Pollution Sentinel

The chatbot is powered by NVIDIA's **Qwen3-Coder-480B** model. On each message, the frontend sends the user's query along with live AQI context (overall AQI, zone data, predictions) to `/api/chat`. The model responds with concise, health-focused advice specific to Chennai's current air quality.

---

## License

MIT License — feel free to use, modify, and distribute.

---

<div align="center">
  <sub>Built with care for Chennai's air quality awareness</sub>
</div>
