# Water-Leakage-Detection-Based-on-IoT
-- Water leakage in water distribution networks is a significant issue that leads to problems, so here is the small prototype to get the leakage notifactions --

First of all, try to understand the concept first in  [my article](https://www.atlantis-press.com/proceedings/ictrops-24/126011947).

## What-we-need
1. Microcontroller NodeMCU ESP32
2. Flow Sensor 
3. Pressure Sensor
4. ADS1115 (optional, read the [specific details](https://github.com/smandini/Pressure-Sensor-with-ESP32) first)

### Monitoring & Notification
The concept focuses on monitoring water distribution within the pipeline and sending notifications if a leak occurs. The monitoring website utilizes [Thinger.io](https://thinger.io/), while [Telegram](https://web.telegram.org/a/) handles the notification messages.

Since we use Thinger.io and its Data Buckets to store historical and time series data from connected devices, we need to understand that the server may not be designed to handle frequent device reconnections or unstable network connections. For example, we configure the microcontroller to collect sensor data every five minutes. However, if a reconnection occurs; even for a very brief period, such as a few milliseconds before the next five minutes interval is reached, the system may initiate a synchronization process from the last recorded connection. As a result, this behavior could cause inconsistencies in the data collection intervals recorded in the Data Buckets.

If Thinger.io fails to connect while the device still has an active internet connection, the issue is likely related to the code implementation rather than the network itself. In such cases, pay close attention to the program flow and verify which functions or processes need to be executed first. An incorrect execution order may prevent the Thinger.io from establishing or maintaining a connection.

It is important to note that Telegram Group IDs has negative values. Therefore, they must be stored using a 64-bit integer (int64). In this system, we use the CTBot library for Telegram Bot integration and ArduinoJson version 6.19.4, which is the supported version for the current implementation. 

## Calibration & Signal Related
Many sensor characteristics are not specified by the manufacturer or supplier. Therefore, understanding and evaluating the sensor's output value is very important to ensure reliable performance and accurate measurements. A sensor can be considered to be in good condition if it meets the required precision and resolution specifications. In addition, do not forget to evaluate the linearity of each sensor using mathematics equation, as this directly affects measurement accuracy. Verifying precision, resolution, and linearity helps ensure that the sensor provides reliable and accurate data.

With some sensors, there is a tendency for the output value of the sensor to drift when used for a long time. The temporal stability of the sensor signal seems to be important in order not to increase the measurement error of the sensor.

**The most important things are ensuring that the system receives a sufficient voltage supply and that the ground connections are properly paired for each component or sensor. During system testing, a slight decrease in the resolution and precision of the output is generally considered normal, provided that the deviation remains within an acceptable range and does not significantly affect the system's performance.**

In partial testing or individual sensor testing, sensors may only be evaluated under static response conditions. However, when integrated into the complete system, the sensors are required to respond to dynamic operating conditions. These dynamic conditions can introduce deviations, response delays, or non linearities that may not be observed during individual sensor testing.

## The Schematic
**The number of sensors can be increased or decreased depending on the requirements.** 
The addition of multiple analog inputs necessitates accurate calculation of the system’s power (voltage and current) requirements, as the system typically depends on the external power supply.

According to the ADS1115 datasheet,
> The resistor and capacitor are needed. When the ADS1115 is converting data, it draws current in short spikes. The 0.1μF bypass capacitor supplies the momentary bursts of extra current needed from the supply. On the I2C interface, the bus wires are pulled high by pull-up resistors.
<img width="1159" height="604" alt="Sig (1)" src="https://github.com/user-attachments/assets/41e85c58-c2e1-4b84-b1a9-ff46e8834755" />





