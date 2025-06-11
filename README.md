# ESP32-Web-Server
Host a web server on your ESP32-CAM using a mobile hotspot! Perfect for remote or offline setups where traditional Wi-Fi isn’t available.  📦 No external server, cloud required.   Great starting point for offline IoT logging, remote image storage, or embedded camera apps.

## 📷 ESP32-CAM Web Server with SD Card Upload via Mobile Hotspot

This project demonstrates how to use an **ESP32-CAM** to:

* 📡 Connect to a **mobile hotspot** via Wi-Fi
* 🌐 Host a web server accessible from other devices on the hotspot
* 📁 Allow **image uploads via web interface**
* 💾 Save the uploaded images to a **microSD card**



### 📲 Requirements

* **ESP32-CAM** board (with built-in microSD slot)
* **Formatted microSD card** (FAT32, ≤16GB recommended)
* **Mobile hotspot** (e.g., your phone's Wi-Fi)
* **Arduino IDE** with the following libraries:

  * `WiFi.h`
  * `WebServer.h`
  * `FS.h`
  * `SD_MMC.h`



### 🔌 Pin Configuration

#### SD\_MMC Interface (Used for microSD card):

| Signal | GPIO    |
| ------ | ------- |
| CS     | GPIO 5  |
| MOSI   | GPIO 15 |
| MISO   | GPIO 2  |
| SCK    | GPIO 14 |

> ⚠️ The `SD_MMC.begin()` method uses default pins internally. No manual SPI configuration is required.



### 📡 Wi-Fi Interface

* The ESP32’s Wi-Fi uses its **internal radio hardware**, **not standard GPIO pins**.
* It can **coexist with SD\_MMC** as they do not conflict directly.
* Ensure a **stable power supply** (5V/1A or better) to prevent brownouts during Wi-Fi activity.



### 📂 File Upload System

* Access the ESP32 web page via your mobile hotspot IP (shown in Serial Monitor).
* Upload files using a basic HTML form hosted at `/`.
* Uploaded images are saved to the **root directory of the SD card**.
* Files are named according to the original filename.



### 🧪 How to Run

```bash
# 1. Replace the following placeholders in the sketch:
#    const char* ssid = "Your_Hotspot_SSID";
#    const char* password = "Your_Hotspot_Password";

# 2. Upload the sketch to your ESP32-CAM via Arduino IDE

# 3. Open Serial Monitor (115200 baud) and watch for:
#    - Wi-Fi connection success
#    - Assigned IP address
#    - SD card status

# 4. Connect your phone/laptop to the same hotspot

# 5. Open browser and navigate to:
#    http://<ESP32_IP_Address>
```

---

### ⚠️ Tips & Troubleshooting

* Format the SD card as **FAT32**, not exFAT.
* Make sure your **hotspot supports 2.4GHz Wi-Fi** (ESP32 does **not support 5GHz**).
* If uploads fail:

  * Check SD card is properly inserted and mounted.
  * Use smaller image files (<5MB recommended).
  * Verify browser is on the same hotspot.







