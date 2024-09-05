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

## Flashing prereqs

If you carefully open the water bowl "base" you will see a PCB holding a `ESP32-C3-WROOM-03`, a `HX7111` and a voltage regulator. There is also one more chip on the board but I am unable to identify it.

The PCB very conveniently contains 3 pins that we can use to flash our firmware. `GND`, `TX`, and `RX`.
The PC has a `VCC` pin that can be used to power to program, but your USB-Serial converter needs to be able to supply enough current. I suggest using the USB plug to power while programing.
The PCB also has two pads on the lower right corner labled `B` and `G`. These pads can be shorted to put the ESP chip in programmer mode.

## Flashing

1) Plug the USB to serial converter into your computer and hook up to the pin holes as described below. Do NOT power the board/fountain yet.


`GND` -> `GND`

`TX`  -> `RX`

`RX`  -> `TX`

You don't even need to solder anything most likely. I was able to hold the pins in place with just tension.

2) Take a small wire and hold it on the `B` and `G` pads described above.
3) While still holding the wire in place, plug in the pumps USB cable.
4) At this point the board should be in programming mode.
5) Flash the firmware in this repo.

## Result

Here is how it looks in HomeAssistant:

![result](https://snaps.screensnapr.io/87e1c594199be79458be93003644f0)

