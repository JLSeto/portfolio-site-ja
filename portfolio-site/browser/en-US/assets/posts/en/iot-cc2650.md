# IoT Data Visualization with CC2650 SensorTag

*December 5, 2017*

<div class="tag-list">
  <span class="tag">#IoT</span>
  <span class="tag">#Texas Instruments CC2650</span>
  <span class="tag">#Nodejs</span>
  <span class="tag">#SensorData</span>
</div>

<p align="left">
  <img src="/assets/projects/cc2650/cc2650.jpg" alt="CC2650 sensor" style="max-width: 500px; width: 100%; height: auto; border-radius: 5px;" />
  <em style="display: block; margin-top: 6px; color: #666; font-size: 0.9rem;">Figure: Photo of my CC2650 sensor</em>
</p>

---

## Overview

Texas Instruments’ **CC2650 SensorTag** is a compact sensor platform that captures real-world data such as acceleration and temperature, enabling rapid prototyping for IoT applications. The SensorTag can easily connect to your smartphone via Bluetooth using the **TI SensorTag App**. The app not only displays sensor readings in real time but also allows you to forward that data to **IBM’s QuickStart platform** over Wi-Fi with the press of a button.

While IBM’s platform offers tools for analyzing data and hosting IoT applications, this project takes a different approach. Instead of building on IBM’s dashboard, it uses **Node-RED** and **WebSockets** to extract data from IBM’s cloud and forward it to a custom-built web interface. The diagram below illustrates the overall system architecture and highlights the parts built specifically for this demo:

<p align="center">
  <img src="/assets/projects/cc2650/cc2650_diagram.png" alt="System Architecture" style="max-width: 800px; width: 100%; height: auto;" />
</p>

---

## How It Works

The backend server is built with **Node.js**, which integrates **Node-RED**—a visual programming tool that simplifies data flow handling by allowing developers to connect logic blocks like a flowchart.

To retrieve data from IBM’s cloud, the `ibmiotapp` module in Node-RED is used. It subscribes to the SensorTag’s data stream. This data is then piped through Node-RED’s **WebSocket** node and sent to the Node.js server.

The server uses **WebSockets** to forward the data to the front-end webpage, where the raw values are displayed using **HTML**, **CSS**, and **JavaScript**. For better visualization, **Google Charts** is integrated to render real-time graphs of the SensorTag’s x, y, and z acceleration data.

<p align="center">
  <img src="/assets/projects/cc2650/middleware.png" alt="System Architecture" style="max-width: 800px; width: 100%; height: auto;" />
</p>

---

## Demo & Source Code

<a href="https://github.com/JLSeto/CC2650" style="text-decoration: none; color: #007acc; font-weight: bold;">📁 View Source on GitHub</a>

<div style="display: flex; flex-direction: column; align-items: center; width: 100%; max-width: 800px; margin: 0 auto;">
  <div style="position: relative; width: 100%; padding-bottom: 56.25%; overflow: hidden; border-radius: 12.5px; box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);">
    <iframe
      src="https://www.youtube.com/embed/2XyzMGU4GSo"
      frameborder="0"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
      allowfullscreen
      style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border-radius: 12.5px; border: 0; display: block;">
    </iframe>
  </div>
</div>

---
