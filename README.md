# Security-System-with-ESP32
A home security system using the ESP32 and getting notified with Home Assistant, oled and buzzer.

We use two ESP32 boards: one as a transmitter and one as a receiver.
The transmitter has a PIR sensor that detects motion. When motion is detected, a connected LED turns on.
The receiver collects this data and also has a light sensor with a laser pointer. When the laser beam is interrupted, the sensor state changes.
All data is sent to Home Assistant via MQTT. When motion or light interruption is detected, a buzzer is activated.

We suugest the following steps in order to make it work.
1. download the image from the following oficial site: https://www.home-assistant.io/installation/windows/
2. We currently use Oracle VM box. We suggest it.
3. When you set up the image it will automaticly generate a static ip. Use this ip on ESP reciever code.
4. On reicever code change the wifi with your own in order to connect to the internet. It's higly suggested to use the same wifi as home assistant
5. Download and use file explorer on home assistant menu and search for config.yaml file
6. Download and set up the MQTT broker.
7. On this file create the IDs you wanna use. Those are the ones we use:
  binary_sensor:
    - name: "Laser Sensor"
      state_topic: "home/sensor/light"
      payload_on: "ON"
      payload_off: "OFF"
      device_class: light
      unique_id: "laser_sensor_123"
8.You are ready to go!



