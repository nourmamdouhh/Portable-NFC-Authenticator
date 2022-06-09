# Team Members: 
Adham Hegazy

Ahmed Ashraf 

Ahmed Wael 

Nourhan Nada


# GitHub Repository <span id="Github"><span>
https://github.com/AdhamHegazy/portable-nfc-authenticator


# Overview: 
The end goal of our project is to create an integrated portable NFC authentication system that could be utilized in environments where standard access portals are challenging to install. Our system will read user credentials from their access cards through a built-in NFC card reader, which would then be relayed - through the aid of an ESP32 Wi-Fi module - to a cloud server to perform the necessary authentication measures. The resolution of the process would then be displayed to the user through the 1602A LCD, which would be coupled with the triggering of the corresponding LED to indicate whether access was granted or not. 


# Hardware Components: 
* 1 Nucleo STM32 Board
* 2 LEDs

* 1 ESP32 Wi-Fi Module
<img src="https://i.ibb.co/ZfYLywb/Screen-Shot-2022-04-23-at-9-27-05-PM.png" width="500">


* 1 NFC RFID Reader/Writer 
<img src="https://i.ibb.co/hmzT8xT/Screen-Shot-2022-04-23-at-9-37-45-PM.png" width="500">

* 1 LCD Screen 
<img src="https://i.ibb.co/NVzncgn/LCD1602-RGB-Module-details-1.jpg" width="600">

# System Design: 

<img src="https://i.ibb.co/s585ndy/Block-diagram-1.png" width="1000">

# First Prototype
For this prototype, our main objective was to get the NFC reader working, as well as set the infrastructure for authentication. We used SPI3 connection with the NFC module in order to make sure that we are able to read the uid's of the NFC cards and tags that we have. We faced some problems with the initial configuration of the SPI3 channel communicating with the NFC module, but we solved them by fixing the Clock rate, Scaler, and bit-direction (LSB or MSB).

Currently, we check that there is an NFC module connected on SPIT3 (i.e. a successful connection), then we read the uid, and transmit it through UART to display it through TeraTerm. For the next prototypes, we would pass the uid to an authenticate function, which would use connections to a backend server.

Code can be found on [our github repository](https://github.com/AdhamHegazy/portable-nfc-authenticator)

## Connections
<img src="https://i.ibb.co/rv1rmGn/PXL-20220430-211711358.jpg" width="1000">

## Demo Video
https://youtu.be/rhVR1m4Tzeg


# Milestone 2

## Overview

For this milestone, we worked on connecting the ESP32 module with WiFi and sending GET requests to a web portal of our own creation (created using Flask for backend, HTML and Jinja for frontend, and MySQL for database).

We used the Arduino IDE to configure the ESP32 module and connect it to WiFi and send the GET request. Then, we made it communciate with the STM32 board using UART.

You can find the code for this milestone on our github repo on the MS2 branch.

Link: https://github.com/AdhamHegazy/portable-nfc-authenticator/tree/ms2

Link to Portal: https://portableauth.pythonanywhere.com/

## What's Next

Our main issue right now is that the physical connections of the wires are very shaky, and we spend a lot of time simply adjusting the cables. We need to find a way to stabilize the NFC reader on the breadboard so that we overcome this issue. We also need to integrate the LCD screen, but this should be simple enough.

## Demo
<img src="https://i.ibb.co/CQVXbQK/IMG-2026.jpg" width="1000">

## Portal
<img src="https://i.ibb.co/sPh7J9r/Capture.png" width="1000">

## Connections
<img src="https://i.ibb.co/wz1ccxH/IMG-2030.jpg" width="1000">

# Final Milestone

As a result of the physical connections being shaky from the second milestone, we had to weld pins to the headers of the NFC module and the LCD. 

For our final deliverable, we connected the LCD to the microcontroller using 7 GPIO pins to send the user status to the display.

In short, our system works as follows: 
- A user scans his/her ID. 
- The NFC module reads the ID and sends it to the ESP32 module. 
- The module connects to the WiFi and sends GET requests to our web portal, authenticating the ID. 
- A status is sent back to the microcontroller which then maps it to an output message onto the LCD.

Link to Project: https://github.com/AdhamHegazy/portable-nfc-authenticator/tree/ms3

Link to Portal: https://portableauth.pythonanywhere.com/

## Initial state
<img src="https://i.ibb.co/6NKNRpW/Whats-App-Image-2022-05-18-at-1-44-59-PM.jpg" width="1000">

## User Found
<img src="https://i.ibb.co/hWBCD7s/Whats-App-Image-2022-05-18-at-1-44-59-PM-1.jpg" width="1000">

## User Not Found
<img src="https://i.ibb.co/5B6MdqV/Whats-App-Image-2022-05-18-at-1-45-00-PM.jpg" width="1000">

## TeraTerm Output
<img src="https://i.ibb.co/4248f8z/TeraTerm.jpg" width="1000">

