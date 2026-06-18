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

## The Schematic
> The number of sensors can be increased or decreased depending on the requirements. 
<img width="1159" height="604" alt="Sig (1)" src="https://github.com/user-attachments/assets/41e85c58-c2e1-4b84-b1a9-ff46e8834755" />





