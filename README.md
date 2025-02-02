# petlibro-esphome

A collection of alternative DIY open-source [ESPHome firmware](https://esphome.io) for [Petlibro](https://petlibro.com) series of smart cat/dog food feeders and water fountains devices.

Petlibro makes WiFi-connected pet food feeders and water fountains based on ESP8266/ESP32 microcontrollers from Espressif. Their default firmware requires that you use their Petlibro mobile application to create an account and it must via that be connected to their cloud (but use MQTT to communicate internally). 

This ESPHome firmware implements local LAN support with almost feature-parity as stock firmware without need for cloud/WAN connection.

# Dockstream Smart Fountain (PLWF105)

An esphome firmware for PLWF105 automatic water bowl (also called the Dockstream Smart Fountain or the PETLIBRO App Monitoring Cat Water Fountain with Wireless Pump) by Petlibro. 

PLWF105 is available in either white-colored variant or black-colored variant of the same model:

* https://petlibro.com/products/dockstream-app-monitoring-water-fountain
  * https://www.amazon.com/dp/B0BSFB2D37

## About this ESPHome firmware for plwf105

This ESPHome firmware for plwf105 implements (almost) feature parity as the stock firmware but supports only local connections (instead of requiring cloud connection).

### Supported Features

- Turn pump on or off
- Red LED
- Yellow LED
- Scale (used to determine water level)
- Pump error indicator
- water consumption tracking
- water reporting in oz and ml
- configurable pump intervals
- integrated calibration process

## Flashing prereqs

If you carefully open the water bowl "base" you will see a PCB holding a `ESP32-C3-WROOM-03`, a `HX7111` and a voltage regulator. There is also one more chip on the board but I am unable to identify it.
![PCB](https://github.com/user-attachments/assets/cf67e89f-4cc1-4773-8e06-78d1bb700e36)

The PCB very conveniently contains 3 pins that we can use to flash our firmware. `GND`, `TX`, and `RX`.
The PC has a `VCC` pin that can be used to power to program, but your USB-Serial converter needs to be able to supply enough current. I suggest using the USB plug to power while programing.
The PCB also has two pads on the lower right corner labled `B` and `G`. These pads can be shorted to put the ESP chip in programmer mode.

## Flashing

0) You will need to generate a firmware .bin file from ESPHome based on the .yaml file in this repo.  

1) Plug the USB to serial converter into your computer and hook up to the pin holes as described below. Do NOT power the board/fountain yet.


`GND` -> `GND`

`TX`  -> `RX`

`RX`  -> `TX`

You don't even need to solder anything most likely. I was able to hold the pins in place with just tension.

2) Take a small wire and hold it on the `B` and `G` pads described above.
3) While still holding the wire in place, plug in the pumps USB cable.
4) At this point the board should be in programming mode.  If you left the top panel connected, the light should be a steady white.  If it's slowly flashing white you did not enter programming mode.
5) Flash the firmware you created above.  You can use use https://web.esphome.io/ to do the flashing.

If you run into problems or otherwise need to revert, you can reflash back to stock firmware using the .bin file in this repo.

## Result

Here is how it looks in HomeAssistant:

![Result](https://github.com/user-attachments/assets/24344f14-f331-4fa7-b6bd-9aeaddb32a11)

## Calibration

1) The fountain will now be in calibration mode (slow flashing yellow light).
2) With the water a the min fill line and fully assembled, hit the "wifi" button (or enter the number yourself in the home assistant UI)
3) The light should flash fast now, with the water a the max fill line and fully assembled, hit the "wifi" button (or enter the number yourself in the home assistant UI)


# Petlibro Air Smart Feeder (PLAF108 model)

An ESPHome firmware for PLAF108 automatic pet feeder (also called the Air Smart Feeder) by Petlibro.

PLAF108 is available in either white-colored variant or black-colored variant of the same model:

* https://petlibro.com/products/air-wifi-feeder
  * https://www.amazon.com/dp/B0CDC3WK46

## About this ESPHome firmware for PLAF108

This ESPHome firmware for PLAF108 implements (almost) feature parity as the stock firmware but supports only local connections (instead of requiring cloud connection).

### Supported Features

- Alarm Red LED
- Sensor for showing if feeder is on battery power
- Sensor for showing if battery is plugged in
- Sensor to enable the "Food Detection" sensor
- Sensor for showing if mains connected
- Switch to turn motor left
- Switch to turn motor right
- Sensor to show when the motor has done a quarter turn

### Unknowns

I do not know what GPIO0 and GPIO1 are for. I think it's for the DC-power current sensor to maybe determine battery charge. But, that's a guess.

## Flashing prereqs

The PCB very conveniently contains 4 pins that we can use to flash our firmware. `GND`, `TX`, `RX`, and `VCC`. The PCB also has two unlabled pin holes. These holes can be connected to each other put the ESP chip in programmer mode.

## Flashing

1) Plug the USB to serial converter into your computer and hook up to the pin holes as described below. Do NOT plugin the board yet.


`GND` -> `GND`

`TX`  -> `RX`

`RX`  -> `TX`

You don't even need to solder anything most likely. I was able to hold the pins in place with just tension.

2) Take a small wire and hold place it in the unmarked pin holes described above
3) While still holding the wire in place, plug in the board.
4) At this point the board should be in programming mode.
5) Flash the firmware in this repo.
