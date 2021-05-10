# IOT based WATER MONITORING SYSTEM USING ESP8266-nodeMCU-microcontroller & WATER FLOW SENSOR:
## Overview: IoT Water Flow Meter using ESP8266 & Water Flow Sensor
 

In this project we will learn how to make IoT Based Water Flow Meter using ESP8266 & Water Flow Sensor. We will interface YFS201 Hall Effect Water Flow Sensor with NodeMCU ESP8266 Board. We will display the water flow rate & Total Volume in 0.96″ OLED Display. We will then integrate the hardware with cloud based IoT Server. For IoT Server, we will use Thingspeak App. The water flow rate & volume data can be uploaded to Thingspeak Server & can be viewed/monitored from any part of the world.

 Water Management System is an important part of City Management. Water management involves supplying water according to the real requirement & without wasting Water. Therefore it is very important to measure water flow rate and volume. Without measuring these parameters, Water Management is almost impossible. Also monitoring the Water Volume, Flow Rate & Water Quality remotely using Internet Connectivity has become very essential. Therefore there is a need for Monitoring Water Management System Online.

 There are so many Water Flow Sensors available in the market but are too expensive to use and afford. As a result, a low-cost water flow meter is required. So we will use YFS201 Hall Effect Water Flow Sensor with ESP8266 & design simple IoT Based Water Flow Meter.
 
 ## Table of Contents :

- 1 Overview: IoT Water Flow Meter using ESP8266 & Water Flow Sensor
- 2 YF-S201 Hall-Effect Water Flow Sensor
- 3 IoT Water Flow Meter using ESP8266 & Water Flow Sensor
- 4 Mathematical Calculation to Measure Flow Rate & Volume
- 5 Setting up Thingspeak
- 6 Source Code/Program
- 7 Monitoring Water Flow Rate & Volume and output graph

# YF-S201 Hall-Effect Water Flow Sensor
![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/YF-S201-Hall-Effect-Water-Flow-Sensor.jpg)

This is an image of the YF-S201 Hall-Effect Water Flow Sensor. This sensor can be connected to the waterline as it has both inlet and outlet. Inside the sensor, there is a pinwheel that measures how much liquid has moved through it. There’s an integrated magnetic hall effect sensor that outputs an electrical pulse with every revolution.
The sensor comes with three wires:
- 1. Red (5-24VDC power)
- 2. Black (ground)
- 3. Yellow (Hall effect pulse output)

 

The water flow rate can be calculated by counting the pulses from the output of the sensor. Each pulse is approximately 2.25 milliliters. This Sensor is cheaper and best but not the accurate one as flow rate/volume varies a bit depending on the flow rate, fluid pressure, and sensor orientation. To get better precision of more than 10%, a lot of calibration is required. You can make a basic IoT Based Water Flow Meter using this Sensor.

The pulse signal is a simple square wave so its quite easy to log and convert into liters per minute using the following formula.

 > 1	Pulse frequency (Hz) / 7.5 = flow rate in L/min
 
 # IoT Water Flow Meter using ESP8266 & Water Flow Sensor
 
 Water Flow Sensor is a digital Sensor, so we can connect its output pin to any of the digital pins of ESP8266. In my case, I connected to GPIO2, i.e D4. The sensor works at 5V & can be connected to Vin of ESP8266. Similarly, I2C OLED Display SDA & SCL pins are connected to D2 & D1 of ESP8266 respectively. The OLED Display works at 3.3V so it can be connected to 3.3V pin of Nodemcu.
 ![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/Water-Flow-Sensor-ESP8266-Node%20Mcu%20Circuit%20Diagram.jpg)
 I have assembled the circuit on Breadboard. You can use the PCB for making the small Water Flow Meter board and you can also use ARDUINO UNO set up for connecting  YF-S201 Hall-Effect Water Flow Sensor with LED display.

 let us see the IoT Water Flow Meter Circuit Diagram & Connection with Arduino Uno .
 
 ![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/Circuit-Diagram%20with%20ARDUINO%20UNO.jpg)
 
 # Mathematical Calculation to Measure Flow Rate & Volume

> Sensor Frequency (Hz) = 7.5 * Q (Liters/min)

> Litres = Q * time elapsed (seconds) / 60 (seconds/minute)

> Litres = (Frequency (Pulses/second) / 7.5) * time elapsed (seconds) / 60

> Litres = Pulses / (7.5 * 60)

 # Setting up Thingspeak

Now we need to setup the Thingspeak Account. To set up Thingspeak follow the following Steps:
 ![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/thingspeak.png)
 
 - Step 1: Visit https://thingspeak.com/ and create your account by filling up the details.
 - ![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/waterflow_channel.png)
 - Step 2: Create a New Channel by Clicking on “Channel” & fill up the following details as shown in the image below.
 - ![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/waterflowAPI.png)
 - Step 3: Click on API Key, you will see the “Write API Key“. Copy the API Key. This is very important, it will be required in Code Part.
 - Step 4: You can click on the “Private View” & customize the display window as you want.

 So, that’s all from the Thingspeak Setup Part. Now let us move to the programming Part.

 # Source Code/Program
 
Now Let us see ESP8266 Water Flow Sensor Code using Arduino IDE. The code can be directly uploaded to the NodeMCU Board. But before that we need few Libraries for OLED Display. So download the Library first and add it to the Arduino IDE.

 

> Download SSD1306 Library

> Download Adafruit GFX Library 

 
> 1.String apiKey = “I4T8HSIGTOLPHUPE”;

> const char *ssid = “Water_Monitor”; 

> const char *pass = “YF-2019”;
 

Change the Thingspeak API Key, Wifi SSID & Password from the line above.

Now go through the source code given: https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/Water%20Flow%20reading%20code.c


# Monitoring Water Flow Rate & Volume In ThingSpeak
 

Once the Code is uploaded the OLED Display will start working and will show the flow rate and volume. Initially the flow rate will be 0 liter/minute(L/M). Also Total Volume shown will be 0 Liter(L).
![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/Iot-Water-Flow-Meter-SETUP.jpg)
 

Once the motor is turned ON & Water Starts flowing, you can see the OLED Display displaying the Flow Rate (F) & Volume(V).

## OUTPUT GRAPH

![Alt Text](https://github.com/AbhishekSarewar1911/IOT-basedWater-Monitoring-System-using-waterflow-yf-s201-sensor-and-8266-nodeMCU-microcontroller-/blob/main/Water-Flow-Sensor-Thingspeak2.jpg)

### thankyou!
