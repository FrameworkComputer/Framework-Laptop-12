# Mainboard

## License

Framework Laptop 12 © 2024 by Framework Computer Inc is licensed under CC BY 4.0.
To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/

## Pinouts

### Webcam Interface

This is the interface to the webcam module.
This module has not only the webcam but also an accelerometer and a dual-output Hall Sensor.

| Pin | Signal       | Notes                   |
|-----|----------    |-------------------------|
| 1   | 3VL_EC       |                         |
| 2   | TABLET_MODE# | Hall sensor tablet mode |
| 3   | LID_SW#      | Hall sensor lid closed  |
| 4   | ACC_INT      | G-Sensor interrupt      |
| 5   | GND          |                         |
| 6   | USB_DM       | Camera USB              |
| 7   | USB_DP       | Camera USB              |
| 8   | 3VS_CAM      |                         |
| 9   | CAM_SW       | Camera privacy switch   |
| 10  | DMIC_CLK     |                         |
| 11  | DMIC_DATA    |                         |
| 12  | MIC_SW       | Mic privacy switch      |
| 13  | ALS_INT#     | Reserved                |
| 14  | I2C_SCL      | Accelerometer I2C       |
| 15  | I2C_SDA      | Accelerometer I2C       |
| 16  | OS_DET_CAM   | Reserved, pullup        |
| 17  | GND          |                         |
| 18  | NC           |                         |
| 19  | NC           |                         |
| 20  | NC           |                         |

## Display Interface

IPEX 20879-030E connector used to interface to an eDP display.  Note that there are signals
defined for the I2C touchscreen. Note that pin 1 is on the left when looking at the receptacle on the Mainboard.

| Pin | Signal       | Notes                   |
|-----|----------    |-------------------------|
| 1   | PWR          | Backlight power         |
| 2   | PWR          |                         |
| 3   | PWR          |                         |
| 4   | NC           |                         |
| 5   | GND          |                         |
| 6   | GND          |                         |
| 7   | EDP_AUXN     |                         |
| 8   | EDP_AUXP     |                         |
| 9   | GND          |                         |
| 10  | EDP_TXP0     |                         |
| 11  | EDP_TXN0     |                         |
| 12  | GND          |                         |
| 13  | EDP_TXN1     |                         |
| 14  | EDP_TXP1     |                         |
| 15  | GND          |                         |
| 16  | EDP_HPD      | Hotplug                 |
| 17  | BLK_PWM_LCD  | Backlight PWM           |
| 18  | BKOFF#       | Backlight enable        |
| 19  | 3VS_EDP      |                         |
| 20  | 3VS_EDP      |                         |
| 21  | 3VS_EDP      |                         |
| 22  | 3VS_TS       |                         |
| 23  | 3VS_TS       |                         |
| 24  | TS_EN        |                         |
| 25  | TS_RST       |                         |
| 26  | TS_INT#      |                         |
| 27  | I2C_SDA      | Touch I2C               |
| 28  | I2C_SCL      | Touch I2C               |
| 29  | OS_DET_TS    | Reserved, pullup        |
| 30  | GND          |                         |

## Audio Daughterboard Interface

Pin 1 is top left, counting zigzag left, right, left, right downwards.

| Pin | Signal    |
|-----|-----------|
| 1   | SLEEVE    |
| 2   | HPOUT_R   |
| 3   | RING      |
| 4   | A_GND     |
| 5   | GND       |
| 6   | HPOUT_L   |
| 7   | JACK_PLUG |
| 8   | BOARD_ID  |
| 9   | SPK_L-    |
| 10  | SPK_R-    |
| 11  | SPK_L+    |
| 12  | SPK_R+    |

## Power Button Daughterboard Interface

| Pin | Signal   | Notes               |
|-----|----------|---------------------|
| 1   | USB_DP   | USB2.0 Reserved     |
| 2   | FP_CTRL  | Reserved            |
| 3   | USB_DM   | USB2.0 Reserved     |
| 4   | GND      |                     |
| 5   | 3V_FP    | 3V Reserved         |
| 6   | BTN#     | System Power Button |
| 7   | LED_PWM  |                     |
| 5   | 5V_LED   |                     |

## Battery 

Pin 1 is the left-most.

| Pin | Signal   | Notes  |
|-----|----------|--------|
| 1   | BAT+     | 13.5V  |
| 2   | BAT+     | 13.5V  |
| 3   | VRTC     |        |
| 4   | DAT_SMB  | SMBus  |
| 5   | CLK_SMB  | SMBus  |
| 6   | SYS_PRES |        |
| 7   | GND      |        |
| 8   | GND      |        |

## Input Cover Interface

Pin count from left to right.

| Conn | Pin | Signal     | Notes               |
|------|-----|------------|---------------------|
| JTP1 | 1   | 5VS_TP     |                     |
| JTP1 | 2   | KBL_P      |                     |
| JTP1 | 3   | 3VS_TP     |                     |
| JTP1 | 4   | TP_I2C_CLK | Touchpad I2C        |
| JTP1 | 5   | TP_I2C_SDA | Touchpad I2C        |
| JTP1 | 6   | TP_INT#    |                     |
| JTP1 | 7   | BOARD_ID   |                     |
| JTP1 | 8   | KB_I2C_SCL | Keyboard I2C        |
| JTP1 | 9   | KB_I2C_SDA |                     |
| JTP1 | 10  | KB_INT     |                     |
| JTP2 | 1   | KSI_03_IN  | Shorted to pin 2    |
| JTP2 | 2   | KSI_03_OUT | Shorted to pin 1    |
| JTP2 | 3   | KSI_02_IN  | Shorted to pin 4    |
| JTP2 | 4   | KSI_02_OUT | Shorted to pin 3    |
| JTP2 | 5   | KSI_00_IN  | Shorted to pin 6    |
| JTP2 | 6   | KSI_00_OUT | Shorted to pin 5    |
| JTP2 | 7   | GND        |                     |
| JTP2 | 8   | GND        |                     |
| JTP2 | 9   | GND        |                     |
| JTP2 | 10  | GND        |                     |

## Fan Interface

Hefeng AWA02-S04FIA-HF connector for the Fan.  Note that there are many other footprint
compatible 4-pin connectors that are likely compatible. This kind of connector is also known
as "JST SH", and has a 1.0 mm pitch. The same connector is used for the Speakers.

Pin 1 is further away from the speaker assembly.

| Pin | Signal    |
|-----|-----------|
| 1   | 5V        |
| 2   | FAN_SPEED |
| 3   | FAN_PWM   |
| 4   | GND       |

## RTC Battery Interface

NOTE: The mainboard will charge this battery, so a rechargable ML1220 battery must be used.
CR2032 is not okay because it cannot be charged.

Settings are kept alive by the normal system battery. The only case where an
RTC battery is needed, is when the system is used in standalone mode (without a battery).

Cvilux CVILU_CI4402M1HRC-NH connector for the RTC Battery.

| Pin | Signal    | Location |
|-----|-----------|----------|
| 1   | +RTCBATT  | Left     |
| 2   | GND       | Right    |
