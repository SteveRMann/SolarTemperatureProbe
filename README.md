# SolarTemperatureProbe
Project experimenting with solar floodlight from Lowes.
The original solar sensor was replaced with a charge controller which charges the battery during the day.
The DS18B20 sensor was wired to a Wemos D1 Mini.

Inside the case is a magnet switch. A magnet on the outside of the case will reset the processor.
If the MQTT topic solar/ota_mode with a message of "OFF", then the module will enter a sleep mode to save battery
If the message is "ON", sleep mode is bypassed.

mqtt:
  broker: '192.168.1.124'
  discovery: false
  discovery_retain: false
  birth_message:
  will_message:
  on_message:
    #ota on = turn off deep sleep
    - topic: solar/ota_mode
      payload: 'ON'
      then:
        - deep_sleep.prevent: deep_sleep_1
    #ota off = turn on deep sleep
    - topic: solar/ota_mode
      payload: 'OFF'
      then:
        - deep_sleep.enter: deep_sleep_1
