# 🚴 CoolRide: Thermal Comfort Routing for Cyclists

> **A Prototype for mitigating Urban Heat Island (UHI) exposure for bike and cycle riders in Singapore.**

## 🌍 Project Overview
CoolRide is an intelligent routing engine that prioritizes **thermal safety** over speed. Unlike Google Maps, which optimizes for distance, CoolRide calculates the **Wet Bulb Globe Temperature (WBGT)** exposure and finds routes that maximize shade coverage using Park Connectors (PCN) and urban tree canopy data.

## 🚀 Key Features
* **Live Weather Intelligence:** Connects to NEA APIs to fetch real-time WBGT from 15 sensors across Singapore.
* **Predictive AI:** Uses a custom Linear Regression model (with physics clamping) to forecast heat stress 15 minutes into the future.
* **Micro-Shade Analysis:** Integrates `SGTrees` data to identify specific tree-lined streets vs. exposed asphalt.
* **Fail-Safe Protocol:** Includes a "Government Override" mode to force maximum safety during national heatwave alerts.

## 📊 Data Sources
* **Weather:** [National Environment Agency (NEA) API](https://data.gov.sg/)
* **Road Network:** OpenStreetMap (via OSMnx)
* **Vegetation:** [Trees.sg](https://exploretrees.sg/) (Processed via SGTrees)
* **Infrastructure:** NParks Park Connector Network (GeoJSON)

## 🏃 How to Run
1.  Open the [Colab Notebook](<YOUR_COLAB_LINK_HERE>).
2.  The code is configured to pull data directly from this repository's `/data` folder.
3.  Run all cells to generate the `.kml` route file.
4.  Upload the KML to Google My Maps for visualization.

## 👥 Team
* **Maintainer:** Swaminaatha Krishnan
