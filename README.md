# CarPlay for Android

[![Latest Release](https://img.shields.io/github/v/release/Marshmellow31/CarPlay-for-Android?color=blue)](https://github.com/Marshmellow31/CarPlay-for-Android/releases)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![Android](https://img.shields.io/badge/Android-7.1%2B%20(API%2025%2B)-brightgreen.svg)](https://developer.android.com)
[![iOS](https://img.shields.io/badge/iOS-12.0%2B-black.svg)](https://apple.com)

**Turn any Android phone, tablet, or secondary device into a dedicated, standalone Apple CarPlay display.**

[⬇️ **Download Latest APK (v1.1.0)**](https://github.com/Marshmellow31/CarPlay-for-Android/releases/latest/download/CarPlay-1.1.0.apk) · [All Releases](https://github.com/Marshmellow31/CarPlay-for-Android/releases)

Supports both **Wired (USB)** and **Wireless (Wi-Fi / Hotspot)** CarPlay with zero dongles, no cloud accounts, and no jailbreak required. Calibrated specifically for high-density Android phone and tablet screens so icons, text, and touch buttons are large, sharp, and easy to use daily.

---

## Why This Project?

Most existing Android CarPlay receiver apps (like DiPlay or Carlinkit software) are hardcoded for massive **10–15 inch car head units** with low pixel density (150–200 DPI). 

When you install those apps on an Android phone (typically 5.5–6.7 inches with high density like 400+ DPI):
- iOS assumes it is connected to a 12-inch car dashboard.
- It shrinks all icons, dock tiles, and buttons down to microscopic sizes (~6 mm), making them nearly impossible to tap while driving or when mounted on a dashboard phone mount.
- Aspect ratios are often distorted with black bars on modern tall screens (19.5:9 / 20:9).

**CarPlay for Android solves this:**
- **Phone-Calibrated Screen Dimensions (`widthPhysicalMm`)**: Informs iOS of the phone's true handheld/mount dimensions, triggering iOS to render large, finger-friendly icons and buttons (~17 mm).
- **Edge-to-Edge 20:9 & Widescreen Layout**: Automatically adapts to modern smartphone aspect ratios without letterboxing.
- **Granular Button & UI Sizing**: Includes presets (`Large`, `Medium`, `Small`) and a 5 mm fine-tuning slider to dial in the exact touch size you prefer.
- **Standalone Offline MFi Authentication**: Local on-device handshake—no external Carlinkit dongle or external MFi server needed.

---

## Perfect Use Cases

* 🚗 **Secondary Phone as Car Dashboard Screen**: Repurpose an older Android phone or tablet into a permanent, high-resolution CarPlay navigation and music console for any car lacking built-in CarPlay.
* 🏍️ **Motorcycle / Bike Navigation**: Mount a waterproof Android phone to handlebars and stream Apple Maps, Google Maps, and music directly from your iPhone in your pocket or backpack.
* 📱 **Portable CarPlay Display**: Carry a lightweight 7–10 inch Android tablet in rental cars or older family vehicles for an instant Apple CarPlay experience.
* 🔌 **Dongle-Free Head Unit Receiver**: Run native CarPlay on aftermarket Android head units without bulky USB adapters.

---

## Features

- **Wired & Wireless CarPlay**:
  - **Wired USB**: Plug in your iPhone via USB-C or Lightning cable (USB OTG supported).
  - **Wireless Hotspot & Wi-Fi Direct**: Seamless automatic wireless connection via the phone's hotspot or shared Wi-Fi network.
- **Touch & Gesture Optimized**:
  - Full multi-touch support mapped accurately to CarPlay coordinates regardless of screen scale.
  - Fullscreen immersive mode hiding Android status and navigation bars.
- **Audio & Siri Integration**:
  - High-fidelity stereo media playback (Spotify, Apple Music, Podcasts).
  - Smooth navigation audio ducking (turn-by-turn prompts).
  - Voice routing for hands-free Siri and phone calls with software Opus encoder fallback.
- **Customizable Video Engine**:
  - Smooth 60 FPS hardware-accelerated H.264 decoding.
  - Adjustable resolution scaling (30% to 160%) for optimal balance of sharpness and low battery draw.
- **Brand Agnostic**:
  - Default OEM home icon labeled `CarPlay` (no car-brand lock-in).

---

## Quick Start & Setup

### Requirements
* **iPhone**: iOS 12.0 or newer (iPhone 5s and up).
* **Android Device**: Android 7.1 (API 25) or newer (phones, tablets, or head units).
* **Wi-Fi & Bluetooth**: For wireless connection, or a USB cable for wired connection.

### How to Connect

#### Option A: Wireless (Hotspot)
1. Turn on the **Personal Hotspot** on your Android device (or connect both iPhone and Android device to the same Wi-Fi network).
2. Connect your iPhone's Wi-Fi to the Android device's hotspot.
3. Open the **CarPlay** app on Android.
4. On your iPhone, go to **Settings → General → CarPlay** or accept the CarPlay connection prompt on your screen.

#### Option B: Wired (USB Cable)
1. Connect your iPhone to your Android device using an OTG cable / USB-C to Lightning / USB-C to USB-C cable.
2. Grant USB device permission when prompted on Android.
3. CarPlay starts automatically.

---

## Fine-Tuning Button Size & Display

If you want larger or smaller buttons:
1. Open **Settings → Display** inside the CarPlay app.
2. Under **CarPlay size**, choose your preferred preset:
   - **Large (`120 mm`)** *(Default)*: Extra-large, easy-to-tap buttons—ideal for car phone mounts.
   - **Medium (`145 mm`)**: Balanced mobile scale matching standard phone dimensions.
   - **Small (`180 mm`)**: Compact layout displaying more map and content area.
3. During an active CarPlay session, swipe down or tap the menu to use the **Physical Length Slider** to adjust button scale in **5 mm increments**.

---

## Building from Source

### Prerequisites
* JDK 21 or JDK 25
* Android SDK (API 37) and Build-Tools 36.0.0
* Android NDK 28.2.13676358

### Build Command
Clone the repository and build the main application:

```bash
git clone https://github.com/Marshmellow31/CarPlay-for-Android.git
cd CarPlay-for-Android

# Build debug APK
./gradlew :mobile:assembleDebug
```

The resulting APK will be generated at:
```
mobile/build/outputs/apk/debug/mobile-debug.apk
```

To install directly to a connected device via ADB:
```bash
adb install -r mobile/build/outputs/apk/debug/mobile-debug.apk
```

---

## Architecture & Credits

This project is built upon open research and community contributions:
- Based on [DiPlay](https://github.com/shihabal3amri/DiPlay) by Shihab Al-Amri.
- Inherited protocol implementation from [xcertplay](https://github.com/shilapi/xcertplay) by shilapi (GPLv3).
- Home and settings interface adapted from [DiAuto](https://github.com/shihabal3amri/DiAuto) (AGPLv3).
- Protocol reverse engineering and Wi-Fi research credited to [LIVI](https://github.com/f-io/LIVI) and [Showcase](https://github.com/amineross/showcase).

### License & Legal Disclaimer
* **License**: Licensed under the GNU General Public License v3.0 ([GPL-3.0](LICENSE)).
* **Disclaimer**: This is an independent open-source project. Apple, CarPlay, iPhone, and iOS are trademarks of Apple Inc. This software is not endorsed by, affiliated with, or certified by Apple Inc.
