# plwf105

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
