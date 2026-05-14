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
```

---

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

# 📡 Packet Format

The transmitter sends data in CSV format:

```text
LATITUDE,LONGITUDE,MESSAGE
```

Example:

```text
17.087741,82.068771,Hello Trainee!
```

Receiver serial output:

```text
DATA:17.087741,82.068771,Hello,RSSI:-78
```

---

# 📷 Working Flow

## Step 1
GPS module gets live coordinates.

## Step 2
Arduino transmitter sends coordinates through LoRa.

## Step 3
Receiver gets packet and displays it on OLED.

## Step 4
Receiver sends data to Python Flask server.

## Step 5
Dashboard plots location on OpenStreetMap.

---

# 📍 Technologies Used

## Embedded Systems

- Arduino C/C++
- SPI
- I2C
- SoftwareSerial

## RF Communication

- LoRa SX1278
- 433 MHz ISM Band

## GPS

- TinyGPS++
- NEO-6M GPS Module

## Backend

- Python 3
- Flask
- Threading
- PySerial

## Frontend

- HTML5
- CSS3
- JavaScript
- Leaflet.js

## Mapping

- OpenStreetMap
- OSRM Routing API
- Haversine Formula

---

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

- LoRa range depends on:
  - antenna quality
  - terrain
  - obstacles
  - spreading factor

- The transmitter and receiver communicate completely offline using LoRa RF communication.

- Internet is NOT required for:
  - LoRa communication
  - GPS transmission
  - OLED receiver display

- Internet is ONLY required at the receiver-side computer for:
  - OpenStreetMap loading
  - OSRM road route calculation
  - Live web dashboard visualization
  - Viewing the victim/transmitter location on the map

- Even without internet, the receiver can still:
  - receive GPS coordinates
  - display latitude and longitude on the OLED
  - receive emergency/status messages
  - measure RSSI signal strength

- With internet enabled on the receiver side, the dashboard can visualize the live victim/transmitter location on the map interface.
# 🧪 Tested On

| Hardware | Status |
|---|---|
| Arduino UNO | ✅ |
| SX1278 433 MHz | ✅ |
| NEO-6M GPS | ✅ |
| SSD1306 OLED | ✅ |
| Windows 10/11 | ✅ |

---

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

See the [LICENSE](LICENSE) file for more details.
