# 🚴 CoolRide: Thermal Comfort Routing for Cyclists

**A Prototype for mitigating Urban Heat Island (UHI) exposure for bike and cycle riders in Singapore.**

### 🌍 Project Overview
CoolRide is an intelligent routing engine that prioritizes **thermal safety** over speed. Unlike standard navigation apps that optimize for distance, CoolRide calculates the **Wet Bulb Globe Temperature (WBGT)** exposure and finds routes that maximize shade coverage.

It uses a "Blue-Green-Grey" infrastructure approach, prioritizing **Park Connectors (PCN)**, **Urban Tree Canopies**, **Water Bodies**, and **Building Shadows** to find the coolest possible path.

---

### 🚀 Key Features (New in V4)

* **☀️ Dynamic Building Shadows:** Calculates real-time shadows cast by buildings based on the sun's exact position (Elevation & Azimuth) and building height data.
* **⏰ Time-Aware Routing:** The optimal route changes throughout the day. A path shaded by buildings at 9 AM might be exposed at 12 PM. CoolRide adapts.
* **🤖 Hybrid AI Engine:** Combines real-time NEA weather data with a custom Linear Regression model (with physics clamping) to forecast heat stress 15 minutes into the future.
* **🌳 Blue-Green Infrastructure:** Integrates **SGTrees** (Canopy), **Park Connectors** (PCN), and **Water Bodies** (Cooling effect) for holistic thermal scoring.
* **🛡️ Fail-Safe Protocol:** Includes a "Government Override" mode to force maximum safety routes during national heatwave alerts.

---

### 📂 Project Structure

The repository is organized into two main components: the Geospatial Engine (Python) and the User Interface (ASP.NET Core).

```text
Cool_Route_prototype/
├── CoolRider-1/                 # 🖥️ ASP.NET Core Web Application (The Interface)
│   ├── Controllers/             # MVC Controllers (Account, Map, Home)
│   ├── Models/                  # Data Models (User Authentication, DB Context)
│   ├── Views/                   # Razor Views (Login, Dashboard, Map Display)
│   └── wwwroot/                 # Static assets (CSS, JS, Images)
│
├── data/                        # 💾 Geospatial Data Lake
│   ├── trees.csv                # Urban Tree Canopy Data (Trees.sg)
│   ├── ParkConnectorLoop.geojson # NParks Cycling Path Network
│   └── HawkerCentresGEOJSON.geojson # Shelter Locations
│
├── output/                      # ☁️ Live Route Deployments
│   └── latest_route.kml         # The active AI-generated route (Pushed by Python)
│
├── Cool_route_v4.ipynb          # 🧠 The Brain: AI & Spatial Analysis Engine
├── index.html                   # 🗺️ Standalone Leaflet Viewer (For rapid testing)
└── README.md                    # Project Documentation
```

### 🏗️ Architecture
The system operates as a Hybrid Cloud application:

* **The Brain (Python/Colab)**: Processes geospatial data (OSM, Trees, Buildings) and runs the routing algorithm. It pushes the calculated route (latest_route.kml) to the ```output/``` folder in this repository.

* **The Interface (ASP.NET Core)**: A secure web application that handles user registration/login and renders the live route on an interactive Leaflet.js map by fetching the KML file from GitHub.

### 📊 Data Sources
* Weather: National Environment Agency (NEA) API ([Real-time WBGT](https://data.gov.sg/datasets?query=wbgt&resultId=d_87884af1f85d702d4f74c6af13b4853d))

* Road Network & Buildings: OpenStreetMap (via OSMnx)

* Vegetation: Trees.sg (Processed via [SGTrees](https://github.com/cheeaun/sgtreesdata/tree/main))

* Infrastructure: [NParks Park Connector Network (GeoJSON)](https://data.gov.sg/datasets/d_a69ef89737379f231d2ae93fd1c5707f/view)

* Blue Spaces: OpenStreetMap Water Features

### 🏃 How to Run (The Engine)
* Open the Colab Notebook (Cool_route_v4.ipynb).

* The code is configured to pull data directly from this repository's /data folder.

* Run all cells. The script will:

* * Calculate sun position and building shadows.

* * Fetch live weather from the nearest NEA sensor.

* * Generate a .kml route file in the ```output/``` folder.

* View the Route:

* * Option A (Web App): The ASP.NET web app automatically pulls the latest route.

* * Option B (Manual): Download latest_route.kml and view it in index.html (Leaflet Viewer) or Google My Maps.

### 👥 Team
* Swaminaatha Krishnan *
* Arishya Jindal
* Luo Ziyi
* Stefanus Arda 
