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
<p align="center">
  Brief:A powerful React Native application built with Expo for managing  IoT ecosystem. 
  Control your smart devices, manage rooms, and automate your home with ease.
</p>
</div>
##Project introduction
This project consists of three parts: a mobile application, a backend, and hardware firmware. This project is the mobile application part，For detailed information of this project, please refer to the key feature item.

The sample hardware firmware code (remote OCR meter reading) can be found at the following link: [(https://github.com/mailiang98-mkq/camera_ocr.git)]. The firmware is built using the Espressif IDF framework and mainly implements: local button-based meter reading, meter reading on the 1st of each month, and sending the meter reading data to a cloud image hosting service (currently using a public image hosting service; cloud OCR is not implemented). This firmware is built on ESP-IDF with C APIs for device agent, provisioning (BLE/SoftAP), OTA updates, MQTT cloud connectivity, and local control. It supports ESP32 series SoCs using FreeRTOS. The open-source SDK handles core IoT functions while developers only implement application logic. 

The backend is closed-source and built using Amazon AWS's serverless technology stack: ESP RainMaker backend utilizes AWS serverless architecture (Lambda, DynamoDB, S3) deployed via SAM templates. It is primarily implemented in Go, using MQTT over TLS for device communication and REST APIs for client interactions.
### Key  Features

- Device Provisioning via QR code, BLE, and SoftAP
- Matter Device Commissioning
- Home & Room Management
- Local and Cloud Device Control
- Authentication with AWS Cognito and OAuth (Google, Apple)
- Real-time Device State Sync
- Scenes, Schedules, and Automations
- AI Agent for natural language device control
- Push Notifications
- Cross-platform (iOS and Android)
- Localization (English, Chinese)
- Feature Flags via environment variables
- UI Test Automation with Appium and Pytest-BDD 

## AI coding plaform

| Item       | Cursor             | Antigravity        | DeepSeek-Coder          |
|------------|--------------------|--------------------|-------------------------|
| Type       | AI Code Editor     | Coding Agent Tool  | Open-source Code LLM    |
| Runtime    | Desktop App        | Desktop App        | Local / API Server      |
| Core Use   | Daily coding edit  | Generate full proj | Base code model         |
| Cost       | Subscription based | Free+API cost      | Open-source free to use |






## 🏗️ App Technology Stack & architectrue
###App Technology Stack
| Category           | Technologies                              |
|--------------------|-------------------------------------------|
| Core Framework     | React Native                               |
| Network Request    | Axios, MQTT over WebSocket, RESTful API    |
| Development Tools  | Node.js, Android Studio, Expo CLI          |
| Target Platforms   | Android, iOS                               |



###architectrue
┌──────────────────────────────────────────────────────┐
│                   React UI (features/)               │
├──────────────────────────────────────────────────────┤
│              CDF Store (src/store/)                  │
│  MobX stores · Entities · Synchronizers · Registry   │
├──────────────────────────────────────────────────────┤
│           SDK Adaptor (src/sdk-adaptors/)            │
│         ESPRMBaseSDKAdaptor + Transformers           │
├──────────────────────────────────────────────────────┤
│        ESP RainMaker Base SDK / Matter SDK           │
├──────────────────────────────────────────────────────┤
│        Native Adaptors (src/native-adaptors/)        │
│  Prov · LocalControl · Discovery · OAuth · Matter…   │
└──────────────────────────────────────────────────────┘


## ⚡Run & Build method

> If you already have a React Native development environment set up with Node.js 22+, Android Studio/Xcode configured, you can jump straight into the Quick Start section below. 

**TL;DR - Get running in 5 minutes:**

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
##Runtime Screenshots（demo video）

<p align="center">
  <video width="400" controls>
    <source src="https://github.com/mailiang98-mkq/esp-daojia-home/releases/download/demo-video/20260607_181939.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <br>
  <a href="https://github.com/mailiang98-mkq/esp-daojia-home/releases/download/demo-video/20260607_181939.mp4">View Demo Video</a>
</p>