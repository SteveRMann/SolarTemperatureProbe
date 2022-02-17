# SolarTemperatureProbe
Project experimenting with solar floodlight from Lowes.
The original solar sensor was replaced with a charge controller which charges the battery during the day.
The DS18B20 sensor was wired to a Wemos D1 Mini.

Inside the case is a magnet switch. A magnet on the outside of the case will reset the processor.
If the MQTT topic solartp/cmnd with a message of "ON", then the module will enter a sleep mode to save battery
If the message is "OFF", sleep mode is bypassed.
