# Real-Time IoT Data Visualization with Arduino 101 and MEAN Stack

*August 8, 2021*

<div class="tag-list">
  <span class="tag">IoT</span>
  <span class="tag">BLE</span>
  <span class="tag">Arduino101</span>
  <span class="tag">Intel Edison</span>
  <span class="tag">MEANstack</span>
  <span class="tag">Nodejs</span>
  <span class="tag">WebSockets</span>
  <span class="tag">SensorData</span>
  <span class="tag">RealTimeVisualization</span>
</div>

<p align="left">
  <img src="/assets/projects/iot-mean-app/arduino101.jpg" alt="arduino101" style="max-width: 500px; width: 100%; height: auto; border-radius: 5px;" />
  <em style="display: block; margin-top: 6px; color: #666; font-size: 0.9rem;">Figure: Photo of my Arduino101</em>
</p>

---

## Overview

This project showcases a real-time IoT system integrating an **Arduino 101** (based on the **Intel Curie module**) with a **MEAN stack** (MongoDB, Express, AngularJS, Node.js) RESTful API server. The Arduino 101 collects motion data — specifically acceleration and gyroscope readings — and broadcasts it over **Bluetooth Low Energy (BLE)**.

A client device connects to the Arduino 101 via BLE, retrieves the advertised data, and forwards it over Wi-Fi to a Node.js server. The server stores the data in **MongoDB** and simultaneously pushes it to a web frontend, where the data is visualized in real time. From this webpage, users can remotely adjust the Arduino 101's **sampling frequency**, with changes reflected almost instantly (accounting for the combined latency of BLE transmission, Wi-Fi transfer, and the Arduino’s processing loop) both in the data flow and visualizations.

The diagram below illustrates the system architecture:

<p align="center">
  <img src="/assets/projects/iot-mean-app/arduino101_diagram_db.png" alt="System Architecture" style="max-width: 800px; width: 100%; height: auto;" />
</p>

---

## How It Works

### Arduino 101

The Arduino 101 firmware is written using standard Arduino code with the `CurieBLE` and `CurieIMU` libraries. The board acts as a BLE peripheral, exposing one service with **seven characteristics**:

- **Six read-only characteristics**: acceleration (`ax`, `ay`, `az`) and gyroscope (`gx`, `gy`, `gz`) data  
- **One writable characteristic**: sampling frequency (`ts`)

Each characteristic is assigned a **UUID**, allowing the client to subscribe, read, write, or receive notifications.

---

### Client Device

A Node.js script on the client device uses the **Noble** library to discover and connect to the Arduino 101 over BLE. Once connected, it subscribes to the service and enables notifications for all seven characteristics.

Using **Socket.io**, the client streams sensor data and sampling frequency changes to the Node.js server in real time.

> **Why Socket.io instead of WebSockets?**  
> Socket.io was chosen for its simplified multiplexing capabilities. Unlike vanilla WebSockets, Socket.io allows multiple event streams over a single connection with less overhead and an easier API.

---

### Server & Web Interface

The server, built with **Node.js** and **Express**, receives sensor data via Socket.io and stores it in **MongoDB**. It also uses Socket.io to broadcast updates to the web frontend.

The webpage is built with **AngularJS** and styled using **Bootstrap**. Sensor data is visualized with **Google Charts**, providing real-time graphs of accelerometer and gyroscope values. Users can interact with the interface to change the Arduino 101's sampling frequency. These changes propagate back instantly through the same pipeline and are immediately reflected in the incoming data stream.

---

## Demo & Source Code

<a href="https://github.com/JLSeto/Arduino101" target="__blank" style="text-decoration: none; color: #007acc; font-weight: bold;">📁 View Source on GitHub</a>

<div style="display: flex; flex-direction: column; align-items: center; width: 100%; max-width: 800px; margin: 0 auto;">
  <div style="position: relative; width: 100%; padding-bottom: 56.25%; overflow: hidden; border-radius: 12.5px; box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);">
    <iframe
      src="https://www.youtube.com/embed/x961tXPIoRY"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border-radius: 12.5px; border: 0; display: block;">
    </iframe>
  </div>
</div>

---
