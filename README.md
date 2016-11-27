# delay-on-off
Monostable multivibrator high-low for delayed on-off momentary action switch actuation

## What does it do?

This circuit adds an electronic power-on-after-AC-resume function to a device that:

* Doesn't support it
* Needs someone to press a momentary-action push-button to turn the device on

## Why?

Any device that doesn't support power-on-after-AC-resume will stay off if AC is temporarily lost. This is bad if you need the device to be turned on as often as possible. This circuit solves this problem by implementing an electronic switch that "presses the power button" automatically.

## Requirements and installation

This circuit will auto-power-on devices when AC is restored if:

* the device has a simple 2-pin connector on behind the momentary actionpower button that, when shorted, will power the device on
* has a 5-12 volt DC rail that is permanently up when AC is restored (this is used to power the circuit)
* the device's power button needs to be pressed and released momentarily after AC power is restored

## Typical Installation

* If the device is powered by a standard ATX PSU:
  * connect the +5v stand-by terminal (purple lead) to the positive power-in header
  * connect any ground terminal (any black lead) to the negative power-in header
  * connect the positive side of the push-button contact to the positive side of the output header
  * connect the negative side of the push-button contact to the negative side ot the output header

## Config

Stock components will cause the circuit to "press" the power button on the target device ~2 seconds after AC resume, and "release" the power button ~0.5 seconds after that.

It will stay "released" permanently until the next AC power cycle.

The target device's power button will function as normal after that. The target device will not auto-power on unless AC is disconnected and reconnected.

Changing the values of C1 and R1 will extend the time before power button is pressed.

Changing the values of C2 and R2 will extend the time that the power button is pressed (before it is released).

The values should be changed exactly as per standard 555 monostable multivibrator circuits.

