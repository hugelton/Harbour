# Power

Rev. A uses a single-cell LiPo and a standard IP5306.

## Power tree

```
USB-C VBUS
    |
  IP5306 ---- LiPo
    |
   5 V
    +---- Stamp-P4
    +---- C6 add-on
    +---- LCD / backlight
    +---- USB host load switch
    |
 AP2112K-3.3
    |
  ES8388
```

## USB-C input

The USB-C device connector is also the charge input.

- 5.1 kOhm from CC1 to GND
- 5.1 kOhm from CC2 to GND
- VBUS to IP5306 VIN
- USB 2.0 data to the Stamp-P4 HS USB pins
- ESD protection on D+ and D-

No USB-PD controller is required. Harbour is a 5 V sink.

## IP5306

Use the common 4.20 V IP5306, not the I2C variant.

- 1 uH shielded inductor
- 10 uF at VIN
- 22 uF at BAT
- 4 x 22 uF at VOUT for the first revision
- KEY to a dedicated momentary power button

The output capacitor count can be reduced later if the 5 V rail stays clean under CPU, display and USB host load.

## Battery

Use a protected 1S pack with a nominal capacity around 3000 to 4000 mAh.

Battery voltage is measured on GPIO50 through a high-value divider:

- 1 MOhm from BAT to GPIO50
- 330 kOhm from GPIO50 to GND
- 100 nF from GPIO50 to GND

This keeps the battery monitor independent of the PMIC.

## USB host power

USB-A VBUS is supplied from the 5 V rail through a current-limited load switch.

Current choice: SY6280.

GPIO41 controls the load switch. Host power is off when it is not needed.

## Audio rail

The ES8388 is powered from a separate 3.3 V LDO.

Current choice: AP2112K-3.3.

- 4.7 uF at LDO input
- 4.7 uF at LDO output

Keep the codec, LDO and audio ground return away from the IP5306 switching node and the C6 antenna area.
