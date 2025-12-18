---
layout: post
title: "AgriSight: Monitoring Agricultural Stress from Space"
date: 2025-01-20
description: "A deep dive into AgriSight, a microservices-based platform leveraging satellite imagery and ML for agricultural stress detection."
categories: [Project, Geospatial, ML, Python]
image: "/images/agricultural_stress_simulation.jpeg"
---

AgriSight is one of my most ambitious projects, designed to bridge the gap between space technology and food security. It's a comprehensive platform that monitors agricultural health in conflict-affected regions using Sentinel-2 satellite data and Machine Learning.

### 🏗️ Architecture: Microservices & Cloud-Native

The system is built on a robust microservices architecture to ensure scalability and reliability:

- **Frontend:** React 19 + Vite + Tailwind CSS for a high-performance, responsive UI.
- **Backend API:** Django REST Framework serving as the central orchestration layer.
- **Geospatial Engine:** PostGIS enabled PostgreSQL for complex spatial queries.
- **Satellite Processing:** A dedicated service integrating with **Sentinel Hub API** and **Google Earth Engine** to fetch and process multi-spectral imagery.
- **Async Workers:** Celery + Redis for handling heavy image processing tasks and vegetation index (NDVI, EVI) calculations.
- **ML Layer:** Custom models trained to detect stress patterns and correlate them with local conflict events.

### 🛰️ Core Features

*   **Real-time Monitoring:** Automated ingestion of satellite tiles every time a new pass is available.
*   **Vegetation Indices:** On-the-fly calculation of NDVI (Normalized Difference Vegetation Index) to assess plant health.
*   **Conflict Correlation:** Overlaying ACLED data to visualize the impact of instability on agricultural productivity.
*   **Automated Alerts:** Location-based notifications sent via WebSockets when significant stress is detected.

AgriSight represents the future of ICT4D, providing data-driven insights to humanitarian organizations and policy makers in regions where ground-level data is hard to come by.

---

