# Flask-Cesium Integration

This repository contains a basic example of integrating **Flask** with **CesiumJS**, allowing you to visualize a 3D globe, interact with sensor data, and communicate seamlessly between the backend and frontend.

---

## Features

- **Flask Backend**:
  - Serves the Cesium client.
  - Provides API endpoints for:
    - Initial globe coordinates.
    - Receiving and retrieving sensor data.

- **CesiumJS Client**:
  - Displays a 3D globe using Cesium.
  - Fetches initial camera coordinates from the backend.
  - Allows interaction with sensor data (e.g., sending sample sensor details to the server).

---

## File Structure

```
.
├── app.py                 # Flask application entry point
├── templates/
│   └── index.html         # Cesium client served by Flask
└── static/                # Folder for static assets (if needed)
```

---

## How It Works

1. **Backend**:
   - The Flask server serves the CesiumJS client at the root endpoint (`/`).
   - API routes:
     - `/api/initial-coordinates`: Sends initial latitude, longitude, and altitude for the 3D globe.
     - `/api/sensor-data`:
       - `POST`: Receives and stores sensor data.
       - `GET`: Returns all stored sensor data.

2. **Frontend**:
   - The client initializes the Cesium Viewer with global terrain.
   - Camera position is set dynamically based on the backend-provided coordinates.
   - Example sensor data is sent to the backend via a `POST` request.

---

## Getting Started

### Prerequisites

- Python 3.7+
- Flask
- Internet connection (for CesiumJS CDN)

### Installation

1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <repository_name>
   ```

2. Install dependencies:
   ```bash
   pip install flask
   ```

3. Run the Flask server:
   ```bash
   python app.py
   ```

4. Open your browser and navigate to:
   ```
   http://127.0.0.1:5000
   ```

---

## API Endpoints

### 1. `/api/initial-coordinates`
**Method**: `GET`  
**Response**:  
Returns the initial camera coordinates for the Cesium globe.

```json
{
  "latitude": 40.7128,
  "longitude": -74.0060,
  "altitude": 1000
}
```

### 2. `/api/sensor-data`  
**Method**: `POST`  
**Body** (JSON): Sensor details sent by the client.

Example:
```json
{
  "sensor_name": "Ultrasonic",
  "range": 50,
  "field_of_view": 30,
  "color": "blue"
}
```

**Method**: `GET`  
**Response**:  
Returns a list of all stored sensor data.

---

## Future Improvements

- Add more advanced sensor visualizations.
- Integrate real-time data streams for IoT sensors.
- Optimize the 3D rendering with additional CesiumJS features.

---

## Credits

- **Flask**: [Flask Documentation](https://flask.palletsprojects.com/)
- **CesiumJS**: [CesiumJS Documentation](https://cesium.com/learn/cesiumjs-learn/)

---
