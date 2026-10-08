# Rev. A

## Target

Harbour Rev. A is a battery-powered groovebox and synthesizer.

Component BOM target: under JPY 10,000, excluding PCB fabrication, assembly, enclosure and packaging.

## Main hardware

- M5Stamp ESP32-P4
- Stamp-AddOn C6 for Wi-Fi
- 2.8 inch 320 x 240 SPI display
- microSD
- 1-cell LiPo battery

## Audio

- 48 kHz / 24-bit
- ES8388 codec
- mono microphone input
- mono line input
- stereo output
- microphone and line inputs available at the same time
- codec powered from a separate low-noise 3.3 V rail

The microphone uses one ADC channel and the line input uses the other. The two DAC channels are used for the stereo output.

## Controls

- 16 Kailh Choc performance keys
- 12 page keys
- 6 action / transport keys
- 6 push rotary encoders
- dedicated power button

The 40 switch inputs are read through five 74HC165 shift registers. Encoder A/B signals go directly to the ESP32-P4.

## LEDs

IS31FL3236A:

- 36 constant-current outputs
- independent 8-bit PWM
- 16 performance key LEDs
- 12 page LEDs
- 6 action LEDs
- 2 spare channels

## USB and MIDI

- USB-C: device, charging, USB MIDI and USB audio
- USB-A: host, mainly for MIDI controllers
- TRS MIDI Type A input
- TRS MIDI Type A output

USB host power is switched under firmware control.

## Power

- 1S LiPo, around 3000 to 4000 mAh
- IP5306 I2C power management
- physical power button connected to the PMIC
- switched 5 V rail for USB host
- protected battery pack suitable for sale in Japan

## Firmware

The firmware architecture is not decided yet.

Harbour may use a hardware-independent Felucca core, or it may become a separate Harbour OS while sharing DSP and other code with Felucca.
