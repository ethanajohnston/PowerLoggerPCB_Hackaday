# PowerLoggerPCB_Hackaday
Working code for ESP32 3-Channel Power Logger Hackaday Project

This is much better code written for the power logger here: https://hackaday.io/project/187504-esp32-3-channel-power-logger

The repo is a **PlatformIO** project. I fixed most issues with the source code and also some in the INA3221 library.

## Changes:
- Disabled Wifi and Time Server. (This is usually not needed but can easily be uncommented back in. By default was programmed to wait until wifi is connected before doing anything else which I found annoying.)
- Better deboucing and button responsiveness.
- Very fast loading time.
- Changed INA3221 lib and source code functions to provide info in the advertised units.
- I have a 50Ohm shunt on Ch1, 33.33Ohm on Ch2 and 100Ohm shunt on ch3. I will likely change all channels to 33.33Ohm so it can measure up to 4.9A. With the default 100Ohm shunt, the max measurable current per channel is 1.628A.
- Fixed bugs with text not being cleared when changing between some screens.

## Changing Shunt Resistor Value:
- Change resistor values here:
https://github.com/ethanajohnston/PowerLoggerPCB_Hackaday/blob/9f3d30193f948ed65e8873540991e1f779342dbb/src/main.cpp#L802
- Change the displayed current rating per channel here(other channels are below in code):
https://github.com/ethanajohnston/PowerLoggerPCB_Hackaday/blob/9f3d30193f948ed65e8873540991e1f779342dbb/src/main.cpp#L399
- Change the Warning and Critical set points:
https://github.com/ethanajohnston/PowerLoggerPCB_Hackaday/blob/9f3d30193f948ed65e8873540991e1f779342dbb/src/main.cpp#L285C1-L296C13

## Notes:
- Probably don't put more than 5A through the traces that connect to the shunt.
- Make sure your shunt resistor is rated for the MAX amount of dissipated power. 
