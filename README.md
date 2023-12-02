# About

Overall idea of the project is to build IoT Babysitter

## Requirements:
On any abnormal level of sound which mic is registering (baby starts to cry),
this portable device shall send SMS Text notification to group of people
(family members).

## Diagram:
```mermaid
sequenceDiagram
participant Mic
participant Device
participant AWS IoT
participant SNS Topic
participant Mobile Phone

Mic->>Device: registers noise level above the limit
Device->>AWS IoT: sends request with data (maybe dbs of sound or 1 to 10 level of noise) 
AWS IoT->>SNS Topic: sends data from request
SNS Topic->>Mobile Phone: sends text message to group saying "baby is crying"
```

## Hardware:
- ESP32 based WEMOS D1 mini (compact and has all what we need) [Documentation](https://www.wemos.cc/en/latest/d1/d1_mini.html) 
<img src="https://www.wemos.cc/en/latest/_static/boards/d1_mini_v4.0.0_1_16x16.png" width="200" height="200"/>
- Adafruit MAX9814 microphone with built in Amplifier 
<img src="https://cdn-shop.adafruit.com/970x728/1713-03.jpg width="200" height="200"/> 
- Some power (not sure yet maybe a battery, maybe some AC/DC converter to plug the device into socket)

## Software:
- AWS CDK IaC project to configure necessary permissions and setup (IoT Thing & SNS)
- Bash/Python script ( AWS Cli ) to grab necessary device certificates and store on github in this repo
- C++ code for ESP32 (also including reading and using ENV variables and Certificates before - maybe done by some python code)

