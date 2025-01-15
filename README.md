# petlibro-esphome

A collection of esphome  firmwares for Petlibro devices.


# plwf105

An esphome firmware for [PLWF105](https://www.amazon.com/dp/B0BSFB2D37) automatic water bowl (also called the Dockstream or the PETLIBRO App Monitoring Cat Water Fountain with Wireless Pump) by Petlibro. 

## About

The default firmware, which is included in this respository requires use of the Petlibro application and must be cloud connected. Internally the firmware uses MQTT to communicate.

The esphome firmware included in this repository implements (almost) feature parity as the stock firmware without the need for the third party cloud, or any WAN connection for that matter.

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
4) At this point the board should be in programming mode.
5) Flash the firmware you created above.  You can use use https://web.esphome.io/ to do the flashing.

If you run into problems or otherwise need to revert, you can reflash back to stock firmware using the .bin file in this repo.

## Result

Here is how it looks in HomeAssistant:

![Result](https://github.com/user-attachments/assets/24344f14-f331-4fa7-b6bd-9aeaddb32a11)

## Calibration

1) The fountain will now be in calibration mode (slow flashing yellow light).
2) With the water a the min fill line and fully assembled, hit the "wifi" button (or enter the number yourself in the home assistant UI)
3) The light should flash fast now, with the water a the max fill line and fully assembled, hit the "wifi" button (or enter the number yourself in the home assistant UI)


# plwf108

An esphome firmware for [PLAF108](https://www.amazon.com/dp/B0CDC3WK46) automatic pet feeder (also called the Air feeder) by Petlibro.

## About

The default firmware, which is included in this respository requires use of the Petlibro application and must be cloud connected. Internally the firmware uses MQTT to communicate.

The esphome firmware included in this repository implements (almost) feature parity as the stock firmware without the need for the third party cloud, or any WAN connection for that matter.

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

I do not know what GPIO0 and GPIO1 are for. I think it's for the DC current sensor to maybe determine battery charge. But, that's a guess.

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
