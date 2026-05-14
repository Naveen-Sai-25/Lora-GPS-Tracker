<<<<<<< HEAD
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
lora_tracker/
├── server.py                    # Flask server + serial reader + parser
├── requirements.txt
├── README.md
│
├── templates/
│   └── index.html               # Jinja2 template (extracted from server.py)
│
├── static/
│   ├── style.css                # extracted CSS
│   └── app.js                   # extracted dashboard JS (seq/drop tracking)
│
├── arduino/
│   ├── TX/
│   │   └── TX.ino               # transmitter sketch — adds sequence number
│   └── RX/
│       └── RX.ino               # receiver sketch — emits documented format
│
└── tests/
    ├── __init__.py
    ├── test_parser.py           # unit tests for is_valid() / parse_packet()
    ├── test_routes.py           # Flask endpoint tests (OSRM mocked)
    └── test_integration_serial.py  # serial loopback integration tests
>>>>>>> 6ff8ed8 (Updated README, images, and added MIT license)
```

## Packet format

<<<<<<< HEAD
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
=======
Over LoRa (TX → RX):
```
<seq>,<lat>,<lng>,<message>
```

Over USB serial (RX → Python server):
```
DATA:<seq>,<lat>,<lng>,<message>,RSSI:<value>
>>>>>>> 6ff8ed8 (Updated README, images, and added MIT license)
```

Example:

```text
17.087741,82.068771,Hello Trainee!
```
<<<<<<< HEAD

Receiver serial output:

```text
DATA:17.087741,82.068771,Hello,RSSI:-78
=======
DATA:42,17.385000,78.486700,Hello Trainee!,RSSI:-87
>>>>>>> 6ff8ed8 (Updated README, images, and added MIT license)
```

The server also accepts legacy packets without a sequence number.

<<<<<<< HEAD
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
=======
## Run the server

```bash
pip install -r requirements.txt
python server.py
# open http://localhost:5000
```
>>>>>>> 6ff8ed8 (Updated README, images, and added MIT license)

Set `RECEIVER_LAT` / `RECEIVER_LNG` near the top of `server.py` to your
fixed receiver location.

<<<<<<< HEAD
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
=======
### Security note

By default, the server binds to `127.0.0.1` (localhost only) so only
your computer can access the dashboard. If you want to view it from
another device on the same WiFi (e.g., your phone), set:

```bash
# Linux/macOS
export FLASK_HOST=0.0.0.0
python server.py

# Windows
set FLASK_HOST=0.0.0.0
python server.py
```

**Warning:** This exposes GPS coordinates and message content to anyone
on your local network without authentication. Only use this in trusted
networks.
>>>>>>> 6ff8ed8 (Updated README, images, and added MIT license)

### Selecting the serial port

<<<<<<< HEAD
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
=======
The server picks the port in this order:

1. **`LORA_PORT` environment variable** — explicit override:
   ```bash
   # Linux/macOS
   export LORA_PORT=/dev/ttyUSB0
   # Windows
   set LORA_PORT=COM11
   ```
2. **Auto-detection** by USB descriptor keyword (Arduino, CH340, CP210,
   FTDI, USB Serial, ttyUSB, ttyACM).
3. If neither finds a port, the server prints a clear error listing
   available ports and the dashboard keeps running with
   "Waiting for LoRa data...". No more silent infinite retries on a
   non-existent `COM11`.
>>>>>>> 6ff8ed8 (Updated README, images, and added MIT license)

## Run the tests

<<<<<<< HEAD
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
=======
```bash
# everything
python -m unittest discover -s tests -v

# or with pytest
pip install pytest
pytest tests/ -v

# individual files
python -m unittest tests.test_parser -v
python -m unittest tests.test_routes -v
python -m unittest tests.test_integration_serial -v
```

The tests do **not** need an Arduino plugged in. The integration tests
patch `serial.Serial` with a `FakeSerial` that streams pre-recorded
lines, simulating a loopback device. OSRM is mocked with
`unittest.mock`.

## What changed (vs. the original)

1. **Template extracted.** The 200-line HTML string is now
   `templates/index.html`, with CSS in `static/style.css` and JS in
   `static/app.js`. `server.py` uses `render_template` instead of
   `render_template_string`. Easier to maintain and supports template
   inheritance.

2. **Tests added.**
   - `test_parser.py` — 25+ cases for `is_valid()` / `parse_packet()`:
     valid new/legacy formats, out-of-range coords, missing fields,
     non-string input, empty messages, truncated lines, etc.
   - `test_routes.py` — Flask `/data`, `/history`, and every `/route`
     error path (no GPS, invalid cache, timeout, connection error,
     HTTP error, invalid JSON, NoRoute, malformed payload, success).
   - `test_integration_serial.py` — patches `serial.Serial` with
     `FakeSerial` to feed a real byte stream through `read_serial()`,
     plus direct `_ingest_line` tests for dropped-packet detection
     and history cap. Includes port-resolution tests.

3. **Consistent packet format.**
   - `RX.ino` now prints `,RSSI:<value>` (comma before `RSSI:`)
     matching the documented `DATA:<…>,RSSI:<value>` format, with
     improved sequence number detection (validates length 1-10 digits).
   - `TX.ino` prepends a monotonically increasing `<seq>` field and
     checks `gps.location.age() < 2000` to avoid transmitting stale
     coordinates after GPS signal loss.
   - The server tracks `seq` and `dropped` in `latest_data`, and the
     dashboard shows both as cards. Drops are detected by gaps in the
     sequence number.

4. **Port detection fixed.** No more silent `COM11` fallback. Priority:
   `LORA_PORT` env var → auto-detection (Arduino/CH340/CP210/FTDI/
   ttyUSB/ttyACM) → clear error listing available ports.

5. **Security improved.** Server binds to `127.0.0.1` (localhost only)
   by default instead of `0.0.0.0`. Set `FLASK_HOST=0.0.0.0` if you
   need LAN access (dashboard accessible from phone on same WiFi).

6. **Route recalculation optimized.** Dashboard now only fetches a new
   OSRM route when the transmitter moves >5 meters (instead of every 15
   seconds regardless), reducing bandwidth and avoiding rate limits.

7. **TX.ino warns about comma replacement.** When updating the message
   via Serial Monitor, if the user's text contains commas, TX now prints
   a warning explaining they were replaced with spaces to protect the
   CSV packet format.

8. **Offline map tile fallback.** Dashboard displays a warning banner when
   OpenStreetMap tiles are unreachable (no internet), allowing markers and
   routes to continue working without the map background.

9. **Serial auto-reconnect with periodic retry.** If no Arduino is detected
   at startup, server now polls every 10 seconds instead of exiting,
   automatically connecting when the Arduino is plugged in.

10. **RX.ino comment corrected.** Updated "1-10 digits" to "0-10 digits
    (including zero)" to match the actual sequence number validation logic.

11. **Performance: collections.deque for gps_history.** Replaced list with
    `deque(maxlen=500)` for O(1) append operations instead of O(n) pop(0).

12. **Unified haversine function in app.js.** Merged `haversineMeters()` and
    `haversineKm()` into single `haversine(lat1, lng1, lat2, lng2, unit)`
    function to eliminate code duplication.

13. **OLED error handling in RX.ino.** If display.begin() fails, receiver
    continues operating without display and periodically retries
    initialization every 30 seconds instead of hanging forever.

14. **uint32_t wrap behavior documented.** Added comment in TX.ino noting
    that sequence wraps to 0 after 4,294,967,295 (~136 years at 2-second
    intervals), which is expected behavior.
>>>>>>> 6ff8ed8 (Updated README, images, and added MIT license)
