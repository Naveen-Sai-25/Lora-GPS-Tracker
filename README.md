<div align="center">

# 📡 LoRa Long Distance GPS Tracker

### Offline LoRa-Based GPS Tracking & Emergency Communication System

<img src="https://img.shields.io/badge/Arduino-C%2FC%2B%2B-blue?style=for-the-badge&logo=arduino">
<img src="https://img.shields.io/badge/Python-3.x-yellow?style=for-the-badge&logo=python">
<img src="https://img.shields.io/badge/LoRa-SX1278-green?style=for-the-badge">
<img src="https://img.shields.io/badge/Flask-Web%20Dashboard-black?style=for-the-badge&logo=flask">
<img src="https://img.shields.io/badge/OpenStreetMap-Live%20Tracking-brightgreen?style=for-the-badge">

</div>

---

# 📖 Overview

This project implements a **Long-Range Offline GPS Tracking and Emergency Communication System** using **LoRa SX1278 (433 MHz)** and **NEO-6M GPS** modules.

The system is designed for:

- Remote rural areas
- Disaster-hit zones
- Forests & trekking routes
- Military communication
- Vehicle / livestock / drone tracking
- Cellular dead zones

The communication between transmitter and receiver works **without internet, Wi-Fi, or GSM networks**.

The transmitter captures live GPS coordinates and sends them through LoRa radio communication.  
The receiver displays the data on an OLED display and also forwards it to a Flask web dashboard for live map visualization.

---

# 🚀 Features

✅ Long-range LoRa communication (433 MHz)  
✅ Works completely offline  
✅ Live GPS tracking using NEO-6M  
✅ Emergency/status message transmission  
✅ OLED display for receiver monitoring  
✅ Live web dashboard using Flask  
✅ OpenStreetMap integration  
✅ Road route visualization using OSRM  
✅ Straight-line distance calculation (Haversine)  
✅ GPS route history tracking  
✅ RSSI signal strength monitoring  
✅ Real-time coordinate updates  

---

# 🛠️ Hardware Components

| Component | Quantity |
|---|---|
| Arduino UNO / Nano | 2 |
| LoRa SX1278 (433 MHz) | 2 |
| NEO-6M GPS Module | 1 |
| OLED Display SSD1306 (I2C) | 1 |
| Jumper Wires | Required |
| Breadboard | Optional |
| USB Cable | 2 |

---

# 🧠 System Architecture

```text
+-------------------+
|   GPS Module      |
|    NEO-6M         |
+---------+---------+
          |
          v
+-------------------+
|  Arduino TX Node  |
|   LoRa SX1278     |
+---------+---------+
          |
     LoRa RF Signal
          |
          v
+-------------------+
|  Arduino RX Node  |
|   OLED Display    |
+---------+---------+
          |
      Serial USB
          |
          v
+-------------------+
| Flask Web Server  |
| Live Map Dashboard|
+-------------------+
```

---

# 📂 Project Structure

```text
LoRa-GPS-Tracker/
│
├── arduino/
│   ├── transmitter/
│   │   └── transmitter.ino
│   │
│   └── receiver/
│       └── receiver.ino
│
├── static/
│   └── assets/
│
├── templates/
│   └── index.html
│
├── tests/
│
├── README.md
├── QUICKSTART.md
├── SETUP_GUIDE.md
├── requirements.txt
└── server.py
=======
# LoRa Long Distance Tracker

Live GPS tracker over LoRa with a Flask web dashboard (map, road route,
straight-line distance, GPS history, packet sequence/drop counters).

## Folder hierarchy

```
```text
lora_tracker/
├── server.py                    # Flask server + serial reader + parser
├── requirements.txt
├── README.md
│
├── templates/
│   └── index.html               # Jinja2 template
│
├── static/
│   ├── style.css                # Dashboard CSS
│   └── app.js                   # Dashboard JavaScript
│
├── arduino/
│   ├── TX/
│   │   └── TX.ino               # Transmitter sketch
│   └── RX/
│       └── RX.ino               # Receiver sketch
│
└── tests/
    ├── __init__.py
    ├── test_parser.py           # Parser unit tests
    ├── test_routes.py           # Flask route tests (OSRM mocked)
    └── test_integration_serial.py  # Serial integration tests
```

# 🔌 Circuit Connections

# 📡 Transmitter Connections

## LoRa SX1278 → Arduino

| LoRa | Arduino UNO |
|---|---|
| VCC | 3.3V |
| GND | GND |
| SCK | D13 |
| MISO | D12 |
| MOSI | D11 |
| NSS | D10 |
| RST | D9 |
| DIO0 | D2 |

---

## GPS NEO-6M → Arduino

| GPS | Arduino UNO |
|---|---|
| VCC | 5V |
| GND | GND |
| TX | D4 |
| RX | D3 |

---

# 📟 Receiver Connections

## LoRa SX1278 → Arduino

| LoRa | Arduino UNO |
|---|---|
| VCC | 3.3V |
| GND | GND |
| SCK | D13 |
| MISO | D12 |
| MOSI | D11 |
| NSS | D10 |
| RST | D9 |
| DIO0 | D2 |

---

## OLED SSD1306 → Arduino

| OLED | Arduino UNO |
|---|---|
| VCC | 5V |
| GND | GND |
| SDA | A4 |
| SCL | A5 |

---

# 💻 Software Requirements

Install:

- Arduino IDE
- Python 3.x

---

# 📚 Arduino Libraries

Install these libraries from Arduino Library Manager:

```text
LoRa
TinyGPS++
Adafruit GFX
Adafruit SSD1306
SPI
Wire
SoftwareSerial
```

---

# 🐍 Python Libraries

Install required Python packages:

```bash
pip install -r requirements.txt
```

Or manually:

```bash
pip install flask pyserial requests
```

---

# ⚡ Upload Arduino Codes

---

# 1️⃣ Upload Transmitter Code

Open:

```text
arduino/transmitter/transmitter.ino
```

Select:

```text
Board  : Arduino UNO
Port   : COM Port of TX Arduino
```

Upload the code.

---

# 2️⃣ Upload Receiver Code

Open:

```text
arduino/receiver/receiver.ino
```

Select:

```text
Board  : Arduino UNO
Port   : COM Port of RX Arduino
```

Upload the code.

---

# ▶️ Run the Flask Server

Open terminal in project folder.

Run:

```bash
python server.py
```

You will see:

```text
LoRa Long Distance Tracker
Open http://localhost:5000
```

Open browser:

```text
http://localhost:5000
```

---

# 🌍 Dashboard Features

The dashboard shows:

- Live transmitter position
- Receiver fixed location
- Road route
- Straight-line distance
- GPS route history
- RSSI signal strength
- Emergency/status message
- Track point count

---

## 📡 Packet Format

The system supports both the **new packet format (with sequence numbers)** and the **legacy format (without sequence numbers)**.

### Over LoRa (TX → RX)

```text
<seq>,<lat>,<lng>,<message>
```

Example:

```text
42,17.385000,78.486700,Hello Trainee!
```

### Over USB Serial (RX → Python Server)

```text
DATA:<seq>,<lat>,<lng>,<message>,RSSI:<value>
```

Example:

```text
DATA:42,17.385000,78.486700,Hello Trainee!,RSSI:-87
```

### Legacy Packet Format

The server also accepts older packets that do not include a sequence number.

Legacy LoRa packet:

```text
<lat>,<lng>,<message>
```

Example:

```text
17.087741,82.068771,Hello Trainee!
```

Legacy receiver serial output:

```text
DATA:17.087741,82.068771,Hello,RSSI:-78
```
# 📷 Working Flow

## Step 1
📍 The GPS module acquires live latitude and longitude coordinates.

## Step 2
📡 The Arduino transmitter packages the GPS data and sends it over the LoRa network.

## Step 3
📥 The LoRa receiver receives the packet and displays the information on the OLED display.

## Step 4
💻 The receiver forwards the received data to the Python Flask server via USB serial.

## Step 5
🗺️ The Flask dashboard processes the data and displays the transmitter's location on an OpenStreetMap map.

---

# ▶️ Run the Server

```bash
pip install -r requirements.txt
python server.py
```

Open your browser and visit:

```text
http://localhost:5000
```

### Receiver Configuration

Set the receiver's fixed location near the top of `server.py`:

```python
RECEIVER_LAT = 17.xxxxxx
RECEIVER_LNG = 82.xxxxxx
```

These coordinates represent the receiver's permanent location and are used for distance calculations and map visualization.

# 📍 Technologies Used

## 🛠️ Embedded Systems
- Arduino C/C++
- SPI
- I2C
- SoftwareSerial

## 📡 RF Communication
- LoRa SX1278
- 433 MHz ISM Band

## 🛰️ GPS
- TinyGPS++
- NEO-6M GPS Module

## 🖥️ Backend
- Python 3
- Flask
- Threading
- PySerial

## 🌐 Frontend
- HTML5
- CSS3
- JavaScript
- Leaflet.js

## 🗺️ Mapping & Navigation
- OpenStreetMap
- OSRM Routing API
- Haversine Formula

---

# 🔒 Security Note

By default, the Flask server binds to **127.0.0.1 (localhost only)**, meaning only your computer can access the dashboard.

To access the dashboard from another device (such as your phone) on the same Wi-Fi network, start the server with:

### Linux/macOS

```bash
export FLASK_HOST=0.0.0.0
python server.py
```

### Windows

```cmd
set FLASK_HOST=0.0.0.0
python server.py
```

> **⚠️ Warning:** Running on `0.0.0.0` exposes your GPS coordinates and message data to other devices on the same local network. Only use this option on trusted networks.

---

# 🔌 Selecting the Serial Port

The server automatically scans available serial ports and attempts to connect to the LoRa receiver.

If multiple serial devices are connected, specify the correct port near the top of `server.py`:

```python
SERIAL_PORT = "COM5"        # Windows
# SERIAL_PORT = "/dev/ttyUSB0"   # Linux
# SERIAL_PORT = "/dev/tty.usbserial-XXXX"   # macOS
```

Replace the port name with the one assigned to your LoRa receiver.

# 📈 Future Improvements

- AES encryption
- Mesh networking
- Multi-node support
- Battery-powered portable node
- LoRa ACK packets
- Packet retransmission
- Sensor telemetry support
- Mobile application integration
- Cloud database logging

---
# ⚠️ Important Notes

- LoRa communication range depends on:
  - Antenna quality
  - Terrain
  - Obstacles
  - Spreading Factor (SF)

- The transmitter and receiver communicate **completely offline** using LoRa RF communication.

- **Internet is NOT required** for:
  - LoRa communication
  - GPS data transmission
  - OLED receiver display

- **Internet is ONLY required on the receiver-side computer** for:
  - Loading OpenStreetMap
  - OSRM road route calculation
  - Live Flask web dashboard
  - Visualizing the transmitter (victim) location on the map

- Even without an internet connection, the receiver can still:
  - Receive GPS coordinates
  - Display latitude and longitude on the OLED
  - Receive emergency/status messages
  - Measure RSSI signal strength

- With internet enabled on the receiver-side computer, the dashboard provides live map visualization and route tracking.

---

## 🔌 Selecting the Serial Port

The Flask server selects the serial port using the following priority:

### 1. `LORA_PORT` Environment Variable (Recommended)

**Linux/macOS**

```bash
export LORA_PORT=/dev/ttyUSB0
python server.py
```

**Windows**

```cmd
set LORA_PORT=COM11
python server.py
```

### 2. Automatic Detection

If `LORA_PORT` is not specified, the server automatically searches for common USB-to-Serial devices such as:

- Arduino
- CH340
- CP210x
- FTDI
- USB Serial
- ttyUSB
- ttyACM

### 3. No Compatible Device Found

If no matching serial device is detected:

- The server lists all available serial ports.
- The web dashboard continues running.
- The dashboard displays **"Waiting for LoRa data..."** until a receiver is connected.

This prevents the application from repeatedly trying to connect to a non-existent port (such as `COM11`).

---

# 🧪 Tested On

| Hardware / Platform | Status |
|---------------------|--------|
| Arduino UNO | ✅ |
| LoRa SX1278 (433 MHz) | ✅ |
| NEO-6M GPS Module | ✅ |
| SSD1306 OLED Display | ✅ |
| Windows 10 | ✅ |
| Windows 11 | ✅ |

## 🧪 Run the Tests

Install the project dependencies first:

```bash
pip install -r requirements.txt
```

Run all tests:

```bash
pytest
```

Run specific test files:

```bash
pytest tests/test_parser.py
pytest tests/test_routes.py
pytest tests/test_integration_serial.py
```

Run with verbose output:

```bash
pytest -v
```

Generate a coverage report (if `pytest-cov` is installed):

```bash
pytest --cov=. --cov-report=term-missing
```

# 👨‍💻 Author

## Challa Naveen Sai

B.Tech Electronics & Communication Engineering  
Aditya University

---

# ⭐ If You Like This Project

Give this repository a ⭐ on GitHub.

---

# 📜 License

This project is licensed under the MIT License.
