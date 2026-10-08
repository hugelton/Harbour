# Audio

Rev. A uses one ES8388.

## Format

- 48 kHz
- 24-bit I2S
- ESP32-P4 is I2S master
- MCLK: 12.288 MHz
- BCLK: 3.072 MHz
- LRCK: 48 kHz

## Inputs

The ADC channels are used separately.

- left ADC: microphone
- right ADC: line input

### Microphone

Use LIN1.

Basic input:

```
MIC jack -- 1 uF -- LIN1
```

A solder-selectable electret bias can be added with a 2.2 kOhm resistor from 3.3VA to the jack side of the coupling capacitor.

The ES8388 PGA provides the microphone gain. No external microphone amplifier is planned for Rev. A.

### Line input

Use RIN1.

The line input is attenuated before the codec so hot synth and headphone outputs do not clip the ADC.

```
LINE jack -- 22 kOhm --+-- 1 uF -- RIN1
                       |
                     10 kOhm
                       |
                      GND
```

The divider can be changed after input-level testing.

## Output

Use LOUT1 and ROUT1 for the main stereo output.

```
LOUT1 -- 47 uF -- 10 Ohm -- OUT L
ROUT1 -- 47 uF -- 10 Ohm -- OUT R
```

The larger coupling capacitors allow the same output to drive normal line inputs and low-impedance headphones for testing. No external headphone amplifier is planned.

LOUT2 and ROUT2 are unused in Rev. A.

## Codec support parts

Follow the ES8388 reference circuit around the codec.

- 100 nF at each supply pin
- 10 uF local bulk capacitance
- 10 uF at VMID
- 1 uF at ADCVREF
- 1 uF at VREF
- 33 Ohm series resistors on MCLK, BCLK, LRCK, DAC data and ADC data
- 10 kOhm I2C pull-ups if the system bus needs them

AVDD, HPVDD, DVDD and PVDD use the 3.3VA rail for Rev. A.

## I2C

ES8388 runs in 2-wire mode.

Tie AD0 low for address 0x10.
