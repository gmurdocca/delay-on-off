## What does it do?

This circuit was designed to add power-on-after-AC-resume support to a device that needs someone to press a momentary-action push button to turn the device on.

This repo contains KiCad design files for building a monostable multivibrator high-low pulse circuit that provides delayed on-off momentary action switch actuation.

![Alt text](http://i.imgur.com/IZ11wSL.png "Delay-On-Off circuit board")

## Why?

Any device that doesn't support power-on-after-AC-resume will stay off if AC is temporarily lost. This is bad if you need the device to be powered on as often as possible. This circuit solves this problem by implementing an electronic switch that presses the power button automatically.

## Requirements and installation

Open the files in KiCad, create gerber files and a drill file and send them to a fabricator (eg. http://dirtypcbs.com/)

This circuit will auto-power-on devices when AC is restored if:

* the device has a simple 2-pin connector behind a momentary action power button that, when shorted, will power the device on
* has a 5-12 volt DC rail that is permanently up when AC is restored (this is used to power the circuit and start the timer)
* the device's power button needs to be pressed and released a short time after AC power is restored

## Typical Installation

* If the device is powered by a standard ATX PSU:
  * connect the +5v stand-by terminal (purple lead) on the PSU to the positive power-in header
  * connect any ground terminal (any black lead) on the PSU to the negative power-in header
  * connect the positive side of your device's push-button contact to the positive side of the output header
  * connect the negative side of your device's push-button contact to the negative side ot the output header

## Config

Stock components as shown on the schematic will cause the circuit to "press" the power button on the target device ~2 seconds after AC resume, and "release" the power button ~1 second after that. The power button will stay "released" permanently until the next AC power cycle.

The target device's power button will function as normal. After automatic power on, this circuit will remain dormant until AC is cycled.

Changing the values of C1 and R1 will extend the time before power button is pressed. Changing the values of C2 and R2 will extend the time that the power button is pressed (before it is released). These values should be changed as per standard 555 timer monostable multivibrator circuits which are well documented.
