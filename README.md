# MineMap  
A real world GPS powered Minecraft style map device built with Raspberry Pi. Generates live tiled maps, applies Minecraft textures, and displays your actual position on screen.

---

## ⭐ Features

- 🟩 **Real GPS position tracking**
- 🧭 **9-axis orientation (heading) tracking** 
- 🗺️ **Tile-based map rendering**
- 🌍 **Square 7.6” 800×800 display** 
- 🔋 **Fully portable with internal battery (disassembled power bank)**  
- 🖥️ **Runs smoothly on Raspberry Pi 5**  
- 🔌 USB-C charging, Wi-Fi hotspot support  
- 📝 Easy configuration 

---

## 📦 Hardware Requirements

### 💻 Main Board  
- **Raspberry Pi 5 8g**  
- **Pi 5 Official Slim Cooler**

### 🖥️ Display  
- **7.6” 800×800 IPS Square Panel (BOE)**  
- **HDMI → MIPI Driver Board (approx. 48×48mm)**  
- Short HDMI cable (15–20cm)

### 📡 Navigation & Orientation  
- **GPS Module** — Ublox NEO-M8N / M10N / USB GPS  
- **IMU (Compass + Gyro + Accelerometer)**  
  - Recommended: **BNO055** or **BNO080**

### 🔋 Power (Internal Battery)  
- Disassembled **5000–10000 mAh power bank**  
  - Built-in BMS  
  - Output: 5V 2–3A  
- Short USB-C→USB-C cable for internal routing

### 🧩 Optional  
- Copper/aluminum shielding foil  
- RGB LED indicators  
- Buzzer/alert module  
- Extra USB board for expansion

---

## 🛠️ Software Setup

### 1. Flash Raspberry Pi OS (64-bit)
Use Raspberry Pi Imager →  
**Raspberry Pi OS (64-bit) – Bookworm/Bullseye**

### 2. Install dependencies
```bash
sudo apt update
sudo apt install python3-pip python3-pygame python3-requests python3-smbus
pip install pyserial adafruit-circuitpython-bno055 pillow
````

### 3. Clone the repository

```bash
git clone https://github.com/YourUser/MineMap.git
cd MineMap
```

### 4. Configure your device

Edit `config.py`:

```python
API_KEY = "YOUR_GOOGLE_MAPS_KEY"
GPS_PORT = "/dev/ttyACM0"
IMU_I2C_ADDRESS = 0x28  # BNO055 default
MAP_TILE_PROVIDER = "google"  # or "osm"
```

---

## ▶️ Running MineMap

### Start the tile renderer

```bash
python3 map.py
```

### Start the display renderer (fullscreen)

```bash
python3 display.py
```

---

## 📁 Project Structure

```
MineMap/
│── display.py       # Renders fullscreen map & cursor on the 7.6" display
│── map.py           # Fetches map tiles, merges them, handles GPS updates
│── imu.py           # IMU heading reader (BNO055/BNO080)
│── gps.py           # GPS data parser and NMEA reader
│── config.py        # API keys, device settings, ports
│── assets/
│    └── cursor.png  # Minecraft-style cursor graphics
│── 3d/
│    ├── MineMap_Front.stl
│    ├── MineMap_Back.stl
│    └── MineMap_InternalFrame.stl
│── README.md
```

---

## 🧭 IMU / Orientation Support

MineMap uses:

* **Gyroscope** → rotation speed
* **Accelerometer** → tilt compensation
* **Magnetometer** → true north heading
* **Sensor fusion** → stable real-time orientation

The map rotates **as you rotate the device** — just like a real in-game map.

---

## 🧱 3D Printed Case

### Features

* Pixel-style edges
* Minecraft inspired ventilation pattern (small round holes, 3–3.5mm)
* Internal mounts for:

  * Display & driver board
  * Pi 5
  * GPS module
  * IMU sensor (central placement)
  * Internal battery pack
* Right-side USB-C port for charging
* Space for optional RGB indicator LEDs

### Recommended Print Settings

```
Material: PLA / PETG  
Infill: 15–20%  
Layer Height: 0.2mm  
Supports: Only for screen frame  
```

---

## 🌐 Map Providers

MineMap supports:

| Provider     | Works | Notes                               |
| ------------ | ----- | ----------------------------------- |
| Google Maps  | ✔     | Requires API key                    |
| OSM          | ✔     | Free                                |
| Custom Tiles | ✔     | Minecraft texture overlays possible |

---

## 🧪 Future Features

* Offline tile caching
* Compass calibration UI
* Custom Minecraft biome texture mode
* Animation smoothing
* Joystick/button control support

---

## 🤝 Contributing

Pull Requests welcome!
If you build a custom enclosure or add features, submit them and I’ll showcase them.

---

## 📜 License

Shield: [![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg

---

## 🧱 Screenshots

Coming Soon

---

## ⭐ Star the repo if you like MineMap!
