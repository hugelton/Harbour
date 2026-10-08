# Rev. A pin map

Provisional pin assignment for the M5Stamp ESP32-P4.

GPIO34 to GPIO38 are left unused because they are strapping pins. GPIO24 and GPIO25 are kept for USB Serial/JTAG.

## Fixed interfaces

| Function | Pin |
| --- | --- |
| USB HS device D- / D+ | dedicated USB HS pins |
| USB FS host D- | GPIO26 |
| USB FS host D+ | GPIO27 |
| C6 SDIO reset | GPIO42 |
| C6 SDIO clock | GPIO43 |
| C6 SDIO command | GPIO44 |
| C6 SDIO D0 | GPIO45 |
| C6 SDIO D1 | GPIO46 |
| C6 SDIO D2 | GPIO47 |
| C6 SDIO D3 | GPIO48 |

The C6 pins are on the Stamp-P4 BTB connector.

## System I2C

| Function | Pin |
| --- | --- |
| SDA | GPIO9 |
| SCL | GPIO10 |

The bus is shared by the ES8388 and IS31FL3236A.

## Audio

| Function | Pin |
| --- | --- |
| I2S MCLK | GPIO16 |
| I2S BCLK | GPIO17 |
| I2S LRCK | GPIO18 |
| I2S DAC data | GPIO19 |
| I2S ADC data | GPIO20 |

## MIDI

| Function | Pin |
| --- | --- |
| MIDI IN UART RX | GPIO21 |
| MIDI OUT UART TX | GPIO22 |

## Display and microSD

SPI is shared by the display and microSD.

| Function | Pin |
| --- | --- |
| LCD CS | GPIO28 |
| SPI MOSI | GPIO29 |
| SPI SCK | GPIO30 |
| SPI MISO | GPIO31 |
| microSD CS | GPIO32 |
| LCD D/C | GPIO33 |
| LCD reset | GPIO39 |
| LCD backlight PWM | GPIO49 |

The LCD does not need MISO.

## Panel input

Five cascaded 74HC165 devices read the 40 switches.

| Function | Pin |
| --- | --- |
| 74HC165 /PL | GPIO12 |
| 74HC165 clock | GPIO13 |
| 74HC165 data | GPIO14 |

The 40 inputs are:

- 16 performance keys
- 12 page keys
- 6 action / transport keys
- 6 encoder push switches

Encoder A/B signals are connected directly.

| Encoder | A | B |
| --- | --- | --- |
| 1 | GPIO0 | GPIO1 |
| 2 | GPIO2 | GPIO3 |
| 3 | GPIO4 | GPIO5 |
| 4 | GPIO6 | GPIO7 |
| 5 | GPIO8 | GPIO11 |
| 6 | GPIO15 | GPIO23 |

## Power

| Function | Pin |
| --- | --- |
| USB host 5 V enable | GPIO41 |
| Battery voltage sense | GPIO50 |

The main power button is connected directly to the IP5306 KEY pin.

## Reserved

| Pins | Use |
| --- | --- |
| GPIO24, GPIO25 | USB Serial/JTAG |
| GPIO34 - GPIO38 | ESP32-P4 strapping pins |
| GPIO52 | spare |

This map is provisional until the first schematic is complete.
