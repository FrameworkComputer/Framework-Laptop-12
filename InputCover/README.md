# Input Cover

## License

Framework Laptop 12 © 2025 by Framework Computer Inc is licensed under CC BY 4.0.
To view a copy of this license, visit http://creativecommons.org/licenses/by/4.0/

## Layout

The input cover includes the touchpad and keyboard.
There is one main PCB, which we will call the touchpad PCB.
It includes the Pixart PCT2642QC (PLP239 Family) touchpad IC and IT8801 keyboard controler.

The keyboard matrix connects to the touchpad PCB through an FPC connector.

## Touchpad Module Details

For details about the touchpad module, including silkscreen and firmware,
please refer to [Touchpad.md].

## Pinouts

### Touchpad PCB to Mainboard

Connection is made through an FPC daughterboard that has pads for two sets of 10 pogo pins.
See the pinout for that on the mainboard README.md

Pinout for FPC connector on the touchpad PCB to the pogo pin daughterboard.
The `5VS_TP` and `KBL_P` pins are duplicated on this FPC connector, but not on the pogo pins.

KSI0, KSI3, and KSO2 are routed to the mainboard and back out for the possibility of letting a future mainboard scan the F1 and F2 keys directly, bypasing the keyboard controller IC.
On current hardware IN OUT pins are just shorted together on the mainboard.

| Pin | Signal     | Notes        |
|-----|------------|--------------|
| 1   | 5VS_TP     |              |
| 2   | 5VS_TP     |              |
| 3   | KBL_P      |              |
| 4   | KBL_P      |              |
| 5   | 3VS_TP     |              |
| 6   | TP_I2C_CLK | Touchpad I2C |
| 7   | TP_I2C_SDA | Touchpad I2C |
| 8   | TP_INT#    |              |
| 9   | BOARD_ID   |              |
| 10  | KB_I2C_SCL | Keyboard I2C |
| 11  | KB_I2C_SDA | Keyboard I2C |
| 12  | KB_INT     | Keyboard I2C |
| 13  | KSI_03_IN  |              |
| 14  | KSI_03_OUT |              |
| 15  | KSI_02_IN  |              |
| 16  | KSI_02_OUT |              |
| 17  | KSI_00_IN  |              |
| 18  | KSI_00_OUT |              |
| 19  | GND        |              |
| 20  | GND        |              |
| 21  | GND        |              |
| 22  | GND        |              |

### Touchpad to Keyboard

| Pin | Signal     |
|-----|------------|
| 1   | KSI_00_IN  |
| 2   | KSI1       |
| 3   | KSI2       |
| 4   | KSI_03_IN  |
| 5   | KSI4       |
| 6   | KSI5       |
| 7   | KSI6       |
| 8   | KSI7       |
| 9   | KSO0       |
| 10  | KSO1       |
| 11  | KSO_02_IN  |
| 12  | KSO3       |
| 13  | KSO4       |
| 14  | KSO5       |
| 15  | KSO6       |
| 16  | KSO7       |
| 17  | KSO8       |
| 18  | KSO9       |
| 19  | KSO10      |
| 20  | KSO11      |
| 21  | KSO12      |
| 22  | KSO13      |
| 23  | KSO14      |
| 24  | KSO15      |
| 25  | KSO16      |
| 26  | KSO17      |
| 27  | CAPS_P     |
| 28  | CAPS_N     |

## Keyboard

### Keyboard Matrix

ANSI layout:

```
┌─────┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬────┐
│ Esc │F1 │F2 │F3 │F4 │F5 │F6 │F7 │F8 │F9 │F10│F11│F12│ Del│
├───┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴────┤
│ ` │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 0 │ - │ = │Backsp│
├───┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬────┤
│ Tab │ Q │ W │ E │ R │ T │ Y │ U │ I │ O │ P │ [ │ ] │ \  │
├─────┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴────┤
│ Caps │ A │ S │ D │ F │ G │ H │ J │ K │ L │ ; │ ' │ Enter │
├──────┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴───────┤
│ Shift  │ Z │ X │ C │ V │ B │ N │ M │ , │ . │ / │  Shift  │
├────┬───┼───┼───┼───┴───┴───┴───┴───┼───┼───┼───┴┬───┬────┤
│    │   │   │   │                   │   │   │    │ ↑ │    │
│Ctrl│FN │WIN│Alt│                   │Alt│Ctl│ ←  ├───┤  → │
│    │   │   │   │                   │   │   │    │ ↓ │    │
└────┴───┴───┴───┴───────────────────┴───┴───┴────┴───┴────┘
|     |Col 0|Col 1|Col 2|Col 3|Col 4|Col 5|Col 6|Col 7|Col 8|Col 9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|Row 0|     | F11 | F1  | B   | F10 | N   |     |     | =   |     |RAlt |     |     |     |     |     | FN  |     |
|Row 1|     | ESC | F4  | G   | F7  | F12 | H   |     | '   | F9  |     | Bsp |     |     |LCtrl|     |     |     |
|Row 2|     | TAB | F3  | T   | F6  | ]   | Y   |     | [   | Del |     | F8  |     |     |     |     |     |     |
|Row 3| WIN | `   | F2  | 5   | S   |     | -   |     | 6   |     |     | \   |     |     |RCtrl|     |     |     |
|Row 4|     | A   | D   | F   | F5  | K   | J   |     | ;   | L   |     |Enter|     |     |     |     |     |     |
|Row 5|     | 1   | ,   | >   | /   | C   |Space|LShft| X   | V   |     | M   |     |     |     |     |     |     |
|Row 6|     | Z   | 3   | 4   | 2   | 8   | 0   |     | 7   | 9   |     | Down|Left |LAlt |     |CapsL|     |     |
|Row 7|     | U   | I   | O   | P   | Q   | W   |RShft| E   | R   |     | Up  |Right|     |     |     |     |     |
```

ISO Layout:

```
┌─────┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬────┐
│ Esc │F1 │F2 │F3 │F4 │F5 │F6 │F7 │F8 │F9 │F10│F11│F12│ Del│
├───┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴────┤
│ ` │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 0 │ - │ = │Backsp│
├───┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬────┤
│ Tab │ Q │ W │ E │ R │ T │ Y │ U │ I │ O │ P │ [ │ ] │Entr│
├─────┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┬──┴┐   │
│ Caps │ A │ S │ D │ F │ G │ H │ J │ K │ L │ ; │ ' │ # │   │
├────┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴─┬─┴───┴───┤
│Shft│ \ │ Z │ X │ C │ V │ B │ N │ M │ , │ . │ / │  Shift  │
├────┼───┼───┼───┼───┴───┴───┴───┴───┼───┼───┼───┴┬───┬────┤
│    │   │   │   │                   │   │   │    │ ↑ │    │
│Ctrl│FN │WIN│Alt│                   │Alt│Ctl│ ←  ├───┤  → │
│    │   │   │   │                   │   │   │    │ ↓ │    │
└────┴───┴───┴───┴───────────────────┴───┴───┴────┴───┴────┘
|     |Col 0|Col 1|Col 2|Col 3|Col 4|Col 5|Col 6|Col 7|Col 8|Col 9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|
|Row 0|     | F11 | F1  | B   | F10 | N   |     |     | =   |     |RAlt |     |     |     |     |     | FN  |     |
|Row 1|     | ESC | F4  | G   | F7  | F12 | H   |     | '   | F9  |     | Bsp |     |     |LCtrl|     |     |     |
|Row 2|     | TAB | F3  | T   | F6  | ]   | Y   |     | [   | Del |     | F8  |     |     |     |     |     |     |
|Row 3| WIN | `   | F2  | 5   | S   |     | -   |     | 6   |     |     |     |     |     |RCtrl|     |     |     |
|Row 4|     | A   | D   | F   | F5  | K   | J   |     | ;   | L   |     |Enter|     |     |     |     |     |     |
|Row 5|     | 1   | ,   | >   | /   | C   |Space|LShft| X   | V   |     | M   |     |     |     |     |     |     |
|Row 6|     | Z   | 3   | 4   | 2   | 8   | 0   |     | 7   | 9   |     | Down|Left |LAlt |     |CapsL|     | #   |
|Row 7|     | U   | I   | O   | P   | Q   | W   |RShft| E   | R   |     | Up  |Right|     |     |     |     | \   |
```

### Rollover

Like most laptop keyboards, the Framework Laptop 12 and Laptop 13 do not support full n-key rollover.
That means the system recognizes only a limited number of keys pressed at the same time.

The limitation is in hardware - the key switches would have to have diodes or other mechanisms to avoid ghosting.
See: https://en.wikipedia.org/wiki/Key_rollover#Key_jamming_and_ghosting

Framework Laptop 16 was with gaming in mind, where you need to press many keys at the same time.
It has resistors on each key and uses analog scanning to detect which keys are
pressed and achieves almost full n-key rollover.

Framework Laptop 12 and 13 do not have any special mechanism.
They do have a matrix that is optimized to avoid issues with the most common
key combinations when typing and using shortcuts.
So while at minimum two, in most cases many more keys, up to 12 keys can be registered at the same time.
Keys that are commonly used with others are not placed in the same row or column as each other.

See that the control, shift, alt keys, as well as fn, left/right, windows are
placed in their own column each and not in the same rows.

However, since n-key rollover is not supported and the matrix is a limited size, some combinations are not possible.
As explained in the linked Wikipedia article, this happens if three keys share the same two rows and same two columns.
The firmware is not able to determine if three or four keys are pressed - to avoid "ghost keys", it ignores both.

One example of those combinations is: Left/Right Shift + W + Space

```
|       |Col 6|Col 7|
| Row 5 |Space|LShft|
| Row 7 | W   |RShft|
```

Why we chose this matrix. The Framework Laptop 13 has a custom matrix. When we
made the Framework Laptop 13 ChromeOS Edition, we had to make a separate
version of the keyboard and input deck to meet the ChromeOS requirements.
ChromeOS didn't have a Windows/Linux compatible matrix at that time - now they
do, so with compatibility in mind, we picked their new standard
["Straus" Keyboard](https://chromium.googlesource.com/chromiumos/platform/ec/+/HEAD/common/keyboard_strauss.c).
