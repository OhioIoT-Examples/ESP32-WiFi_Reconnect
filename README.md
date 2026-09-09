# ESP32 WiFi: Reconnect The Right Way <a href="https://www.ohioiot.com"><img src="https://www.ohioiot.com/logo_150.jpg" width="40" ></a>


## Overview
This code serves is an output from the YouTube video [ESP32 WiFi - Reconnect The Right Way](https://youtu.be/Ie_zWN5bujE), part of a video series marching toward your next-level WiFi library for ESP32 IoT developers.  👉 Subscribe to the [OhioIoT YouTube Channel](https://www.youtube.com/@OhioIoT?sub_confirmation=1) for more on All Things IoT: hardware, firmware, connectivity, cloud computing, and dev toolkit.



## Getting Started
```
git clone https://github.com/OhioIoT-ESP32-WiFi-Examples/Reconnect-The-Right-Way.git
```


### Getting Started - PlatformIO
- Set your wifi credentials in ***src/main.cpp***
- Compile and run


### Getting Started - Arduino IDE 
- Open ***wifi_lab.ino*** in the ***wifi_lab/*** folder.  That sketch directly links all three files in the ***lib/wifi_tools*** directory. 
- Add your wifi credentials in ***wifi_lab.ino***.
- When you are satisfied that it works:
  - copy the ***wifi_tools*** folder to your Arduino shared ***libraries/*** folder
  - change your include in ***wifi_lab.ino*** to be `#include "wifi_tools.h"`

## Updates
- 09-15-2025: Re-inserted `WiFi.reconnect()` as the reconnect function in the event handler.  `wifi_tools.reconnect()` is only calling `WiFi.reconnect()` after the timer exceeds he threshold.  This works if we are constantly polling this function in the loop whenever `!wifi_tools.is_connected`. Events happen when they happen.  If your disconnected event happens before the timer is exceeded - no reconnect. 
- 09-19-2025: My observation thus far was that a disconnect event is called every time you call WiFi.begin() and fail to connect.  That doesn't mean it's always the case.  Until it is confirmed, we need to keep checking the reconnect() function in the loop whenever it is the case that we are not connected.  See more at the 13:38 mark of [ESP32 WiFi - Final Checklist](https://youtu.be/He9YtNsHtYU).


<br>


*OhioIoT is an IoT platform designed for small-scale IoT projects (https://www.ohioiot.com).*
