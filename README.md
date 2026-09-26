# ESP8266-RELAY

Browser-based firmware flashing portal for the **NodeMCU 1.0 (ESP-12E Module)** using **ESP Web Tools** and **GitHub Pages**.

Created by **rakabhai**.

---

## Features

* Browser-based ESP8266 firmware installation
* No Arduino IDE required for end users
* No desktop flashing application required
* Uses ESP Web Tools and Web Serial
* GitHub Pages hosting
* Responsive lightweight interface
* Direct firmware download from the project repository
* Supports NodeMCU 1.0 (ESP-12E Module)
* ESP8266 firmware image at flash offset `0x00000`

---

## Project Information

| Item             | Value                        |
| ---------------- | ---------------------------- |
| Project          | ESP8266-RELAY                |
| Creator          | rakabhai                     |
| Board            | NodeMCU 1.0 (ESP-12E Module) |
| Chip Family      | ESP8266                      |
| Firmware         | `2GTracker.ino.bin`          |
| Flash Offset     | `0x00000`                    |
| Firmware Version | 1.0.0                        |
| Flashing Method  | ESP Web Tools                |
| Hosting          | GitHub Pages                 |

---

## Repository Structure

The repository should have exactly this structure:

```text
ESP8266-RELAY/
│
├── index.html
├── manifest.json
├── README.md
│
└── firmware/
    └── 2GTracker.ino.bin
```

### Important

The firmware filename must match exactly:

```text
2GTracker.ino.bin
```

The path is:

```text
firmware/2GTracker.ino.bin
```

Do not rename the file unless you also update `manifest.json`.

---

# Browser Firmware Installation

## 1. Connect the ESP8266

Connect your NodeMCU ESP-12E board to your computer using a USB **data** cable.

A charging-only USB cable will not work.

---

## 2. Use a supported browser

Use a desktop browser with Web Serial support.

Recommended:

* Google Chrome
* Microsoft Edge

The browser must be able to access the Web Serial API.

The firmware installer must be opened through HTTPS.

GitHub Pages provides HTTPS automatically.

---

## 3. Close other serial programs

Before flashing, close programs that may already be using the ESP8266 serial port.

Examples:

* Arduino Serial Monitor
* Arduino Serial Plotter
* PlatformIO Serial Monitor
* PuTTY
* Other serial terminal applications

Only the browser firmware installer should use the serial port during flashing.

---

## 4. Open the firmware portal

Your GitHub Pages URL will normally look like:

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/
```

Replace:

```text
YOUR_USERNAME
```

with your GitHub username.

---

## 5. Press Flash Firmware

Click:

```text
Flash Firmware
```

The ESP Web Tools interface will open the browser serial-port selection dialog.

Select the serial device belonging to your ESP8266.

---

## 6. Start installation

After selecting the board, follow the ESP Web Tools installation dialog.

The firmware file used by this project is:

```text
2GTracker.ino.bin
```

The firmware is written at:

```text
0x00000
```

---

# Firmware Manifest

The project uses:

```text
manifest.json
```

The production manifest is:

```json
{
  "name": "ESP8266-RELAY",
  "version": "1.0.0",
  "builds": [
    {
      "chipFamily": "ESP8266",
      "parts": [
        {
          "path": "firmware/2GTracker.ino.bin",
          "offset": 0
        }
      ]
    }
  ]
}
```

The numeric offset:

```json
"offset": 0
```

represents the ESP8266 flash address:

```text
0x00000
```

---

# Verify the Manifest

After GitHub Pages is enabled, open:

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/manifest.json
```

The browser should display the JSON contents.

If you receive:

```text
404 Not Found
```

the GitHub Pages configuration or file path needs to be checked.

---

# Verify the Firmware

Open:

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/firmware/2GTracker.ino.bin
```

The browser may download the BIN file instead of displaying it.

That is normal.

The important point is that the URL must not return:

```text
404 Not Found
```

---

# GitHub Pages Setup

## Step 1 — Create the repository

Create a GitHub repository named:

```text
ESP8266-RELAY
```

---

## Step 2 — Upload the files

Upload:

```text
index.html
manifest.json
README.md
```

Then create:

```text
firmware
```

and upload:

```text
2GTracker.ino.bin
```

---

## Step 3 — Enable GitHub Pages

Open:

```text
Repository
→ Settings
→ Pages
```

Under **Build and deployment**, select:

```text
Source:
Deploy from a branch
```

Select:

```text
Branch:
main
```

Select:

```text
Folder:
/ (root)
```

Click:

```text
Save
```

Wait for the GitHub Pages deployment to finish.

---

# Expected Website URL

The final website should normally be:

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/
```

The important URLs are:

### Website

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/
```

### Manifest

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/manifest.json
```

### Firmware

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/firmware/2GTracker.ino.bin
```

---

# Troubleshooting

## Failed to download manifest

If ESP Web Tools reports:

```text
Failed to download manifest
```

first open the manifest URL directly:

```text
https://YOUR_USERNAME.github.io/ESP8266-RELAY/manifest.json
```

Check that the JSON is accessible.

Also check:

* `manifest.json` is in the repository root
* GitHub Pages is enabled
* the GitHub Pages URL is correct
* HTTPS is being used
* the manifest filename is exactly `manifest.json`

---

## GitHub Pages 404

If the website returns 404:

1. Open repository Settings.
2. Open Pages.
3. Confirm deployment from `main`.
4. Confirm the folder is `/ (root)`.
5. Confirm `index.html` is in the repository root.
6. Wait for GitHub Pages deployment to complete.
7. Refresh the page.

The repository should contain:

```text
index.html
manifest.json
README.md
firmware/
```

---

## Firmware 404

If the firmware cannot be downloaded, verify:

```text
firmware/2GTracker.ino.bin
```

The manifest must contain:

```json
"path": "firmware/2GTracker.ino.bin"
```

GitHub filenames are case-sensitive.

For example:

```text
2GTracker.ino.bin
```

is different from:

```text
2gtracker.ino.bin
```

---

## Flashing connection failure

Try the following:

1. Disconnect the ESP8266.
2. Reconnect USB.
3. Try another USB cable.
4. Try another USB port.
5. Close Serial Monitor.
6. Close other serial programs.
7. Try Chrome or Edge.
8. Select the correct serial device.
9. Try manual bootloader mode.

---

# Manual ESP8266 Bootloader Mode

Some NodeMCU boards automatically enter bootloader mode.

I
