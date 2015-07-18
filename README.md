ArduinoTempLogger
=================

ArduinoTempLogger sketch will need following HW and SW libraries to work:

**HW**

* Arduino
* DS18B20 temperature sensor
* DS1307 RTC
* TX433N RF transmitter

**Libraries**

* DallasTemperature for DS18B20 temp sensor
* Wire for I2C communication
* OneWire for communication with DS18B20 sensos
* VirtualWire for RF communication
* RTClib for RTC functionality
* Narcoleptic for sleep functionality

**HW connections**

DS1307 RTC is connected to Arduino via I2C bus.
Temperature readings are read from DS18B20 digital temperature sensor via OneWire bus.
TX433N RF transmitter is connected to the Arduino via single GPIO pin.

This repository includes also breadboard and schematics pictures in PDF and Fritzing formats.

**Functionality of the sketch**

Sketch reads current time from the RTC clock and checks is it time to perform a temperature measurement function.
After the temperature is measured it will be added to the data string which is sent to Arduino based gateway which will
send the data to the MQTT server. So this sketch doesn't send temperature data directly to the MQTT server.

There is also a sleep function in main loop which will decrease overall power consumption.

It's possible to print amount of free RAM memory of Arduino via serial port by removing comment marks from `#define RAM_DEBUG` line