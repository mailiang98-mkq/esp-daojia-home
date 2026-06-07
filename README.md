#  navo Home App

<div align="center">
<p align="center">
  <img src="src/assets/images/logo.png" alt="navo Home App" width="200"/>
</p>
</div>


<div align="center">

[![License: Apache-2.0](https://img.shields.io/badge/License-Apache_2.0-yellow.svg)](https://opensource.org/licenses/Apache-2.0)
[![React Native](https://img.shields.io/badge/React%20Native-v0.76.9-blue.svg)](https://reactnative.dev/)
[![Expo](https://img.shields.io/badge/Expo-SDK%2052-black.svg)](https://expo.dev/)

</div>

<div align="center">
Brief: A powerful React Native application built with Expo for managing IoT ecosystem.
Control your smart devices, manage rooms, and automate your home with ease.
</div>

## Project introduction
This project consists of three parts: a mobile application, hardware firmware and a closed-source backend. This document mainly describes the mobile application. For detailed functions, please refer to the key feature section.

The sample hardware firmware for remote OCR meter reading is available here: [camera_ocr](https://github.com/mailiang98-mkq/camera_ocr.git).
The firmware is developed based on Espressif IDF. It supports manual button meter reading and scheduled monthly meter reading on the 1st day of each month. The collected data will be uploaded to a public image hosting service (cloud OCR is not implemented currently).

Based on ESP-IDF and FreeRTOS for ESP32 series SoCs, the firmware provides C APIs including device agent, BLE/SoftAP device provisioning, OTA updates and MQTT local/cloud connectivity. The core IoT capabilities are encapsulated by the official SDK, developers only need to implement custom business logic.

The backend service is closed-source, built on AWS serverless stack (Lambda, DynamoDB, S3) deployed via SAM templates. It adopts Go as the main development language, uses MQTT over TLS for device communication and RESTful APIs for client interaction.

### Key Features
- Device Provisioning via QR code, BLE, and SoftAP
- Matter Device Commissioning
- Home & Room Management
- Local and Cloud Device Dual Control
- User Authentication via AWS Cognito and OAuth (Google, Apple)
- Real-time device state synchronization
- Scenes, Schedules, and Intelligent Automations
- AI Agent for natural language device control
- System Push Notifications
- Cross-platform support (Android & iOS)
- Multi-language localization (English, Chinese)
- Dynamic feature flags via environment variables
- UI automated testing with Appium and Pytest-BDD

## AI Coding Platform
| Item       | Cursor             | Antigravity        | DeepSeek-Coder          |
|------------|--------------------|--------------------|-------------------------|
| Type       | AI Code Editor     | Coding Agent Tool  | Open-source Code LLM    |
| Runtime    | Desktop App        | Desktop App        | Local / API Server      |
| Core Use   | Daily coding edit  | Generate full proj | Base code model         |
| Cost       | Subscription based | Free+API cost      | Open-source free to use |

## 🏗️ App Technology Stack & Architecture
### App Technology Stack
| Category           | Technologies                              |
|--------------------|-------------------------------------------|
| Core Framework     | React Native                               |
| Network Request    | Axios, MQTT over WebSocket, RESTful API    |
| Development Tools  | Node.js, Android Studio, Expo CLI          |
| Target Platforms   | Android, iOS                               |

### Architecture

```
┌──────────────────────────────────────────────────────┐
│                   React UI (features/)               │
├──────────────────────────────────────────────────────┤
│              CDF Store (src/store/)                  │
│  MobX stores · Entities · Synchronizers · Registry  │
├──────────────────────────────────────────────────────┤
│           SDK Adaptor (src/sdk-adaptors/)            │
│         ESPRMBaseSDKAdaptor + Transformers           │
├──────────────────────────────────────────────────────┤
│        ESP RainMaker Base SDK / Matter SDK           │
├──────────────────────────────────────────────────────┤
│        Native Adaptors (src/native-adaptors/)        │
│  Prov · LocalControl · Discovery · OAuth · Matter…  │
└──────────────────────────────────────────────────────┘
```

## Run & Build method

> If you already have a React Native development environment set up with Node.js 22+, Android Studio/Xcode configured, you can jump straight into the Quick Start section below. 

```bash
# Prerequisites: Node.js 22+, Android Studio or Xcode
git clone https://github.com/mailiang98-mkq/esp-daojia-home.git
cd esp-daojia-home
nvm use 22
npm install

# Configure environment
cp .env.example .env
# Edit .env if needed, then sync to native projects
npm run prebuild

# Development Build

# For Android
npm run android

# For iOS (macOS only)
npm run ios -- --device
```
## Runtime Screenshots（demo video）

<p align="center">
  <video width="400" controls>
    <source src="https://github.com/mailiang98-mkq/esp-daojia-home/releases/download/demo-video/20260607_181939.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <br>
  <a href="https://github.com/mailiang98-mkq/esp-daojia-home/releases/download/demo-video/20260607_181939.mp4">View Demo Video</a>
</p>