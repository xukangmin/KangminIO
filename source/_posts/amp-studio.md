---
title: Amp Studio - A current measurement tool
date: 2021-08-08 19:47:35
tags: diy, current measurement
---

# Current Measurement tool

Current measurement is extremely helpful for IoT device battery optimization. 

Features:
- USB Type C PD Input with user selectable power source, 3.3V, 5V, 9V, 12V and 20V.
- On board screen to view the current trend in live
- ESP32 with WiFi capability for remote monitoring current chart on PC or phone
- Measure A, mA, nA with 3 different current shunt
- Using USB Type C source or User input power source

Key components:
- [INA3221](https://www.ti.com/amplifiers/ina3221), 3 channels current measurement
- [ESP32](https://www.espressif.com/en/products/socs/esp32), Main MCU for communication
- [UPD350](https://www.digikey.com/en/products/detail/microchip-technology/UPD350CT-I-Q8X/8639020), USB PD 3.0
- [FUSB302](https://www.digikey.com/en/products/detail/onsemi/FUSB302TMPX/7356101), USB PD 3.0
- [STUSB4500](https://www.st.com/en/interfaces-and-transceivers/stusb4500.html), USB PD 3.0

