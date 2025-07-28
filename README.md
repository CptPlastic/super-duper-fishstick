# super-duper-fishstick 🐟✨

This repository contains OTA-enabled ESP32 firmware and tools for peer discovery, versioning, and web-based management. It is designed for use with both ESP32 WROOM and Nano boards.

## Features 🚀

- 🛰️ **Peer Discovery**: Devices broadcast their MAC and IP over UDP, auto-detecting peers on the same network.
- 🖥️ **Modern Web UI**: Responsive, dark-themed web interface at `http://<device-ip>:8080/` with device info, discovered peers, and OTA update status.
- 🔄 **OTA Updates**: One-click firmware update from the web UI, with version checking against a remote server.
- 🧑‍💻 **REST API**: JSON endpoint at `/rest` with device, firmware, and peer info.

## Project Structure 📁

- `esp32-IO/peer_discovery/wroom_esp32_peer_discovery/wroom_esp32_peer_discovery.ino` — ESP32 WROOM firmware
- `esp32-IO/peer_discovery/nano_esp32_peer_discovery/nano_esp32_peer_discovery.ino` — ESP32 Nano firmware
- `esp32-IO/latest_version.txt` and `esp32-IO/nano_latest_version.txt` — Remote version files (hosted on your server)

## Quick Start ⚡️

1. ✏️ Edit WiFi credentials in the `.ino` file.
2. 🔌 Flash the firmware to your ESP32 board.
3. 📶 Connect to the same WiFi network.
4. 🌐 Access the web UI at `http://<device-ip>:8080/`.
5. ⬆️ Use the **Update Firmware** button if a new version is available.
6. 👀 View discovered peers and device info in the web UI or via `/rest`.

## REST API Example 🛠️

`GET http://<device-ip>:8080/rest`

Returns:

```json
{
  "board": "ESP32 WROOM or Nano",
  "firmware": "1.x.x",
  "latest": "1.x.x",
  "updateAvailable": true,
  "mac": "...",
  "ip": "...",
  "rssi": -60,
  "channel": 6,
  "devices": [
    { "mac": "...", "ip": "...", "lastSeen": 2 }
  ]
}
```

## OTA Update Hosting 🗂️

- 🌍 Host your firmware binaries and version files on a web server (see URLs in the `.ino` files).
- 📝 Update the version file and binary to trigger OTA updates.

## Board Differences 🧩

- **WROOM**: Uses onboard LED, board name in UI is "ESP32 WROOM". 💡
- **Nano**: Uses RGB LED, board name in UI is "ESP32 Nano". 🌈

---

For questions or improvements, open an issue or PR. 🙌
