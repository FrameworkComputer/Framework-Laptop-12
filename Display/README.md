# Display

## Mechanical

A 2D drawing of the Display Module for use in creating screen protectors.
Note that the cutout for the webcam is needed, but the LED can shine through
most types of screen protector materials.

## Electrical

### Connectors

Display eDP

| Pin | Signal       | Notes                   |
|-----|--------------|-------------------------|
| 1   | NC           |                         |
| 2   | GND          |                         |
| 3   | EDP_TXN1     | eDP Lane 1              |
| 4   | EDP_TXP1     | eDP Lane 1              |
| 5   | H_GND        |                         |
| 61  | EDP_TXN0     | eDP Lane 0              |
| 70  | EDP_TXP0     | eDP Lane 0              |
| 7   | H_GND        |                         |
| 9   | EDP_AUXP     | eDP Auxiliary Channel   |
| 10  | EDP_AUXN     | eDP Auxiliary Channel   |
| 11  | H_GND        |                         |
| 12  | 3VS_EDP      | 3VS                     |
| 13  | 3VS_EDP      | 3VS                     |
| 14  | NC           |                         |
| 15  | H_GND        |                         |
| 16  | H_GND        |                         |
| 17  | EDP_HPD      | Hotplug                 |
| 18  | BL_GND       |                         |
| 19  | BL_GND       |                         |
| 10  | BL_GND       |                         |
| 21  | BL_GND       |                         |
| 22  | BKOFF#       | Backlight enable        |
| 23  | BLK_PWM_LCD  | Backlight PWM           |
| 24  | NC           |                         |
| 25  | NC           |                         |
| 26  | BL_POWER     |                         |
| 27  | BL_POWER     | Touch I2C               |
| 28  | BL_POWER     | Touch I2C               |
| 29  | BL_POWER     | Reserved, pullup        |
| 30  | NC           |                         |

Touch

| Pin | Signal       | Notes                   |
|-----|----------    |-------------------------|
|  1  | 3VS_TS       |                         |
|  2  | TS_EN        |                         |
|  3  | TS_RST       |                         |
|  4  | TS_INT#      |                         |
|  5  | I2C_SDA      | Touch I2C               |
|  6  | I2C_SCL      | Touch I2C               |
|  7  | OS_DET_TS    | Reserved, pullup        |
|  8  | GND          |                         |

### Silkscreen

| Label  | Type      | Description       |
|--------|-----------|-------------------|
| OS_DET | Testpoint | Reserved          |
| SCL    | Testpoint | I2C SCL           |
| SDA    | Testpoint | I2C SDA           |
| INT    | Testpoint | I2C Interrupt     |
| RST    | Testpoint | Touch IC Reset    |
| TPEN   | Testpoint | Touch Enable      |
| VDD33  | Testpoint | 3.3V              |
| GND    | Testpoint | Ground            |
