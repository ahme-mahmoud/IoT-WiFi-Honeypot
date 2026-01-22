# IoT-WiFi-Honeypot
<p align="center">
  <img 
    src="assets/logo.png"
    alt="IoT Wi-Fi Honeypot"
    width="600"
  />
</p>

<h1 align="center">IoT Wi-Fi Honeypot (Evil Twin Behavioral Analysis)</h1>

<p align="center">
  <strong>
    IoT Security • Wi-Fi Behavioral Analysis • Evil Twin Detection
  </strong>
</p>

---

# 🚨 IoT Wi-Fi Honeypot (Honey Bot)

## 📌 Project Overview

This project implements an **IoT Wi-Fi Honeypot** designed to analyze the **reconnection behavior** of IoT devices when exposed to **Fake Access Point (Evil Twin)** scenarios.

Instead of performing active exploitation, the system focuses on **behavioral analysis**, observing how an ESP32-based IoT device reconnects to Wi-Fi networks based solely on SSID trust.

---

## 🎯 Problem Statement

Many IoT devices automatically reconnect to previously known Wi-Fi networks **without validating the authenticity of the Access Point**.

This behavior exposes IoT environments to:
- Evil Twin attacks
- Traffic interception
- Man-in-the-Middle (MitM)
- Data manipulation

---

## 💡 Solution Approach

The project is implemented in **two phases**:

### 1️⃣ Phase 1 – Normal Operation
- ESP32 connects to a legitimate Wi-Fi network
- Reads sensor data (LDR)
- Sends periodic HTTP requests to a logging server
- Confirms connectivity using LED feedback

### 2️⃣ Phase 2 – Evil Twin Scenario
- Legitimate Access Point is disabled
- A Fake Access Point with the same SSID is introduced
- ESP32 attempts to reconnect automatically
- Reconnection behavior is analyzed and classified

No firmware changes are made between phases.

---

## 🧠 Behavioral Analysis

The system analyzes:
- Wi-Fi disconnection events
- Wi-Fi reconnection timing
- Phase transitions
- Request frequency
- Source IP address

Based on these indicators, the behavior is classified as:
- **Normal**
- **Evil Twin Suspected**
- **Evil Twin Confirmed**

---

## 🏗️ System Architecture

<p align="center">
  <img 
    src="assets/architecture.png"
    alt="System Architecture"
    width="750"
  />
</p>

```text
[ ESP32 IoT Device ]
        ↓
 Wi-Fi Disconnection
        ↓
[ Fake Access Point ]
        ↓
[ Honeypot Server ]
        ↓
[ Dashboard & Logs ]
