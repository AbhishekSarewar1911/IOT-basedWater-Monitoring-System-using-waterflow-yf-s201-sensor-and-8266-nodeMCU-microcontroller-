# IOT based WATER MONITORING SYSTEM USING ESP8266-nodeMCU-microcontroller & WATER FLOW SENSOR:
## Overview: IoT Water Flow Meter using ESP8266 & Water Flow Sensor
 

In this project we will learn how to make IoT Based Water Flow Meter using ESP8266 & Water Flow Sensor. We will interface YFS201 Hall Effect Water Flow Sensor with NodeMCU ESP8266 Board. We will display the water flow rate & Total Volume in 0.96″ OLED Display. We will then integrate the hardware with cloud based IoT Server. For IoT Server, we will use Thingspeak App. The water flow rate & volume data can be uploaded to Thingspeak Server & can be viewed/monitored from any part of the world.

 Water Management System is an important part of City Management. Water management involves supplying water according to the real requirement & without wasting Water. Therefore it is very important to measure water flow rate and volume. Without measuring these parameters, Water Management is almost impossible. Also monitoring the Water Volume, Flow Rate & Water Quality remotely using Internet Connectivity has become very essential. Therefore there is a need for Monitoring Water Management System Online.

 There are so many Water Flow Sensors available in the market but are too expensive to use and afford. As a result, a low-cost water flow meter is required. So we will use YFS201 Hall Effect Water Flow Sensor with ESP8266 & design simple IoT Based Water Flow Meter.
 
 ## Table of Contents :

- 1 Overview: IoT Water Flow Meter using ESP8266 & Water Flow Sensor
- 3 YF-S201 Hall-Effect Water Flow Sensor
- 4 IoT Water Flow Meter using ESP8266 & Water Flow Sensor
- 6 Mathematical Calculation to Measure Flow Rate & Volume
- 7 Setting up Thingspeak
- 8 Source Code/Program
- 9 Monitoring Water Flow Rate & Volume and output graph

# YF-S201 Hall-Effect Water Flow Sensor
![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/YF-S201-Hall-Effect-Water-Flow-Sensor.jpg)

This is an image of the YF-S201 Hall-Effect Water Flow Sensor. This sensor can be connected to the waterline as it has both inlet and outlet. Inside the sensor, there is a pinwheel that measures how much liquid has moved through it. There’s an integrated magnetic hall effect sensor that outputs an electrical pulse with every revolution.
The sensor comes with three wires:
-1. Red (5-24VDC power)
-2. Black (ground)
-3. Yellow (Hall effect pulse output)

 

The water flow rate can be calculated by counting the pulses from the output of the sensor. Each pulse is approximately 2.25 milliliters. This Sensor is cheaper and best but not the accurate one as flow rate/volume varies a bit depending on the flow rate, fluid pressure, and sensor orientation. To get better precision of more than 10%, a lot of calibration is required. You can make a basic IoT Based Water Flow Meter using this Sensor.

The pulse signal is a simple square wave so its quite easy to log and convert into liters per minute using the following formula.

 `<addr>` 1	Pulse frequency (Hz) / 7.5 = flow rate in L/min
