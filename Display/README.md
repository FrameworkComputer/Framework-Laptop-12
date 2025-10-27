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

## Firmware

The touchscreen IC presents as an I2C HID device at address 0x41.
Below the HID Report descriptor and details about some reports are documented.

### HID Report Descriptor

```
# 0x05, 0x0d,                    // Usage Page (Digitizers)             0
# 0x09, 0x04,                    // Usage (Touch Screen)                2
# 0xa1, 0x01,                    // Collection (Application)            4
# 0x85, 0x04,                    //  Report ID (4)                      6
# 0x05, 0x0d,                    //  Usage Page (Digitizers)            8
# 0x09, 0x22,                    //  Usage (Finger)                     10
# 0xa1, 0x02,                    //  Collection (Logical)               12
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           14
# 0x95, 0x01,                    //   Report Count (1)                  16
# 0x75, 0x06,                    //   Report Size (6)                   18
# 0x09, 0x51,                    //   Usage (Contact Id)                20
# 0x15, 0x00,                    //   Logical Minimum (0)               22
# 0x25, 0x3f,                    //   Logical Maximum (63)              24
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              26
# 0x09, 0x42,                    //   Usage (Tip Switch)                28
# 0x25, 0x01,                    //   Logical Maximum (1)               30
# 0x75, 0x01,                    //   Report Size (1)                   32
# 0x95, 0x01,                    //   Report Count (1)                  34
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              36
# 0x09, 0x47,                    //   Usage (Confidence)                38
# 0x75, 0x01,                    //   Report Size (1)                   40
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              42
# 0x05, 0x01,                    //   Usage Page (Generic Desktop)      44
# 0x75, 0x10,                    //   Report Size (16)                  46
# 0x55, 0x0e,                    //   Unit Exponent (-2)                48
# 0x65, 0x11,                    //   Unit (SILinear: cm)               50
# 0x09, 0x30,                    //   Usage (X)                         52
# 0x26, 0x00, 0x40,              //   Logical Maximum (16384)           54
# 0x35, 0x00,                    //   Physical Minimum (0)              57
# 0x46, 0x43, 0x0a,              //   Physical Maximum (2627)           59
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         62
# 0x09, 0x31,                    //   Usage (Y)                         64
# 0x26, 0x80, 0x25,              //   Logical Maximum (9600)            66
# 0x46, 0x6a, 0x06,              //   Physical Maximum (1642)           69
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         72
# 0x95, 0x01,                    //   Report Count (1)                  74
# 0x75, 0x08,                    //   Report Size (8)                   76
# 0x81, 0x03,                    //   Input (Cnst,Var,Abs)              78
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           80
# 0x26, 0xff, 0x7f,              //   Logical Maximum (32767)           82
# 0x09, 0x48,                    //   Usage (Width)                     85
# 0x75, 0x10,                    //   Report Size (16)                  87
# 0x95, 0x01,                    //   Report Count (1)                  89
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              91
# 0x09, 0x49,                    //   Usage (Height)                    93
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              95
# 0xc0,                          //  End Collection                     97
# 0x05, 0x0d,                    //  Usage Page (Digitizers)            98
# 0x09, 0x22,                    //  Usage (Finger)                     100
# 0xa1, 0x02,                    //  Collection (Logical)               102
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           104
# 0x95, 0x01,                    //   Report Count (1)                  106
# 0x75, 0x06,                    //   Report Size (6)                   108
# 0x09, 0x51,                    //   Usage (Contact Id)                110
# 0x15, 0x00,                    //   Logical Minimum (0)               112
# 0x25, 0x3f,                    //   Logical Maximum (63)              114
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              116
# 0x09, 0x42,                    //   Usage (Tip Switch)                118
# 0x25, 0x01,                    //   Logical Maximum (1)               120
# 0x75, 0x01,                    //   Report Size (1)                   122
# 0x95, 0x01,                    //   Report Count (1)                  124
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              126
# 0x09, 0x47,                    //   Usage (Confidence)                128
# 0x75, 0x01,                    //   Report Size (1)                   130
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              132
# 0x05, 0x01,                    //   Usage Page (Generic Desktop)      134
# 0x75, 0x10,                    //   Report Size (16)                  136
# 0x55, 0x0e,                    //   Unit Exponent (-2)                138
# 0x65, 0x11,                    //   Unit (SILinear: cm)               140
# 0x09, 0x30,                    //   Usage (X)                         142
# 0x26, 0x00, 0x40,              //   Logical Maximum (16384)           144
# 0x35, 0x00,                    //   Physical Minimum (0)              147
# 0x46, 0x43, 0x0a,              //   Physical Maximum (2627)           149
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         152
# 0x09, 0x31,                    //   Usage (Y)                         154
# 0x26, 0x80, 0x25,              //   Logical Maximum (9600)            156
# 0x46, 0x6a, 0x06,              //   Physical Maximum (1642)           159
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         162
# 0x95, 0x01,                    //   Report Count (1)                  164
# 0x75, 0x08,                    //   Report Size (8)                   166
# 0x81, 0x03,                    //   Input (Cnst,Var,Abs)              168
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           170
# 0x26, 0xff, 0x7f,              //   Logical Maximum (32767)           172
# 0x09, 0x48,                    //   Usage (Width)                     175
# 0x75, 0x10,                    //   Report Size (16)                  177
# 0x95, 0x01,                    //   Report Count (1)                  179
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              181
# 0x09, 0x49,                    //   Usage (Height)                    183
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              185
# 0xc0,                          //  End Collection                     187
# 0x05, 0x0d,                    //  Usage Page (Digitizers)            188
# 0x09, 0x22,                    //  Usage (Finger)                     190
# 0xa1, 0x02,                    //  Collection (Logical)               192
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           194
# 0x95, 0x01,                    //   Report Count (1)                  196
# 0x75, 0x06,                    //   Report Size (6)                   198
# 0x09, 0x51,                    //   Usage (Contact Id)                200
# 0x15, 0x00,                    //   Logical Minimum (0)               202
# 0x25, 0x3f,                    //   Logical Maximum (63)              204
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              206
# 0x09, 0x42,                    //   Usage (Tip Switch)                208
# 0x25, 0x01,                    //   Logical Maximum (1)               210
# 0x75, 0x01,                    //   Report Size (1)                   212
# 0x95, 0x01,                    //   Report Count (1)                  214
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              216
# 0x09, 0x47,                    //   Usage (Confidence)                218
# 0x75, 0x01,                    //   Report Size (1)                   220
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              222
# 0x05, 0x01,                    //   Usage Page (Generic Desktop)      224
# 0x75, 0x10,                    //   Report Size (16)                  226
# 0x55, 0x0e,                    //   Unit Exponent (-2)                228
# 0x65, 0x11,                    //   Unit (SILinear: cm)               230
# 0x09, 0x30,                    //   Usage (X)                         232
# 0x26, 0x00, 0x40,              //   Logical Maximum (16384)           234
# 0x35, 0x00,                    //   Physical Minimum (0)              237
# 0x46, 0x43, 0x0a,              //   Physical Maximum (2627)           239
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         242
# 0x09, 0x31,                    //   Usage (Y)                         244
# 0x26, 0x80, 0x25,              //   Logical Maximum (9600)            246
# 0x46, 0x6a, 0x06,              //   Physical Maximum (1642)           249
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         252
# 0x95, 0x01,                    //   Report Count (1)                  254
# 0x75, 0x08,                    //   Report Size (8)                   256
# 0x81, 0x03,                    //   Input (Cnst,Var,Abs)              258
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           260
# 0x26, 0xff, 0x7f,              //   Logical Maximum (32767)           262
# 0x09, 0x48,                    //   Usage (Width)                     265
# 0x75, 0x10,                    //   Report Size (16)                  267
# 0x95, 0x01,                    //   Report Count (1)                  269
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              271
# 0x09, 0x49,                    //   Usage (Height)                    273
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              275
# 0xc0,                          //  End Collection                     277
# 0x05, 0x0d,                    //  Usage Page (Digitizers)            278
# 0x09, 0x22,                    //  Usage (Finger)                     280
# 0xa1, 0x02,                    //  Collection (Logical)               282
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           284
# 0x95, 0x01,                    //   Report Count (1)                  286
# 0x75, 0x06,                    //   Report Size (6)                   288
# 0x09, 0x51,                    //   Usage (Contact Id)                290
# 0x15, 0x00,                    //   Logical Minimum (0)               292
# 0x25, 0x3f,                    //   Logical Maximum (63)              294
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              296
# 0x09, 0x42,                    //   Usage (Tip Switch)                298
# 0x25, 0x01,                    //   Logical Maximum (1)               300
# 0x75, 0x01,                    //   Report Size (1)                   302
# 0x95, 0x01,                    //   Report Count (1)                  304
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              306
# 0x09, 0x47,                    //   Usage (Confidence)                308
# 0x75, 0x01,                    //   Report Size (1)                   310
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              312
# 0x05, 0x01,                    //   Usage Page (Generic Desktop)      314
# 0x75, 0x10,                    //   Report Size (16)                  316
# 0x55, 0x0e,                    //   Unit Exponent (-2)                318
# 0x65, 0x11,                    //   Unit (SILinear: cm)               320
# 0x09, 0x30,                    //   Usage (X)                         322
# 0x26, 0x00, 0x40,              //   Logical Maximum (16384)           324
# 0x35, 0x00,                    //   Physical Minimum (0)              327
# 0x46, 0x43, 0x0a,              //   Physical Maximum (2627)           329
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         332
# 0x09, 0x31,                    //   Usage (Y)                         334
# 0x26, 0x80, 0x25,              //   Logical Maximum (9600)            336
# 0x46, 0x6a, 0x06,              //   Physical Maximum (1642)           339
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         342
# 0x95, 0x01,                    //   Report Count (1)                  344
# 0x75, 0x08,                    //   Report Size (8)                   346
# 0x81, 0x03,                    //   Input (Cnst,Var,Abs)              348
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           350
# 0x26, 0xff, 0x7f,              //   Logical Maximum (32767)           352
# 0x09, 0x48,                    //   Usage (Width)                     355
# 0x75, 0x10,                    //   Report Size (16)                  357
# 0x95, 0x01,                    //   Report Count (1)                  359
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              361
# 0x09, 0x49,                    //   Usage (Height)                    363
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              365
# 0xc0,                          //  End Collection                     367
# 0x05, 0x0d,                    //  Usage Page (Digitizers)            368
# 0x09, 0x22,                    //  Usage (Finger)                     370
# 0xa1, 0x02,                    //  Collection (Logical)               372
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           374
# 0x95, 0x01,                    //   Report Count (1)                  376
# 0x75, 0x06,                    //   Report Size (6)                   378
# 0x09, 0x51,                    //   Usage (Contact Id)                380
# 0x15, 0x00,                    //   Logical Minimum (0)               382
# 0x25, 0x3f,                    //   Logical Maximum (63)              384
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              386
# 0x09, 0x42,                    //   Usage (Tip Switch)                388
# 0x25, 0x01,                    //   Logical Maximum (1)               390
# 0x75, 0x01,                    //   Report Size (1)                   392
# 0x95, 0x01,                    //   Report Count (1)                  394
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              396
# 0x09, 0x47,                    //   Usage (Confidence)                398
# 0x75, 0x01,                    //   Report Size (1)                   400
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              402
# 0x05, 0x01,                    //   Usage Page (Generic Desktop)      404
# 0x75, 0x10,                    //   Report Size (16)                  406
# 0x55, 0x0e,                    //   Unit Exponent (-2)                408
# 0x65, 0x11,                    //   Unit (SILinear: cm)               410
# 0x09, 0x30,                    //   Usage (X)                         412
# 0x26, 0x00, 0x40,              //   Logical Maximum (16384)           414
# 0x35, 0x00,                    //   Physical Minimum (0)              417
# 0x46, 0x43, 0x0a,              //   Physical Maximum (2627)           419
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         422
# 0x09, 0x31,                    //   Usage (Y)                         424
# 0x26, 0x80, 0x25,              //   Logical Maximum (9600)            426
# 0x46, 0x6a, 0x06,              //   Physical Maximum (1642)           429
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         432
# 0x95, 0x01,                    //   Report Count (1)                  434
# 0x75, 0x08,                    //   Report Size (8)                   436
# 0x81, 0x03,                    //   Input (Cnst,Var,Abs)              438
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           440
# 0x26, 0xff, 0x7f,              //   Logical Maximum (32767)           442
# 0x09, 0x48,                    //   Usage (Width)                     445
# 0x75, 0x10,                    //   Report Size (16)                  447
# 0x95, 0x01,                    //   Report Count (1)                  449
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              451
# 0x09, 0x49,                    //   Usage (Height)                    453
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              455
# 0xc0,                          //  End Collection                     457
# 0x55, 0x0c,                    //  Unit Exponent (-4)                 458
# 0x66, 0x01, 0x10,              //  Unit (SILinear: s)                 460
# 0x35, 0x00,                    //  Physical Minimum (0)               463
# 0x47, 0xff, 0xff, 0x00, 0x00,  //  Physical Maximum (65535)           465
# 0x15, 0x00,                    //  Logical Minimum (0)                470
# 0x27, 0xff, 0xff, 0x00, 0x00,  //  Logical Maximum (65535)            472
# 0x75, 0x10,                    //  Report Size (16)                   477
# 0x95, 0x01,                    //  Report Count (1)                   479
# 0x05, 0x0d,                    //  Usage Page (Digitizers)            481
# 0x09, 0x56,                    //  Usage (Scan Time)                  483
# 0x81, 0x02,                    //  Input (Data,Var,Abs)               485
# 0x95, 0x08,                    //  Report Count (8)                   487
# 0x75, 0x08,                    //  Report Size (8)                    489
# 0x81, 0x03,                    //  Input (Cnst,Var,Abs)               491
# 0x05, 0x0d,                    //  Usage Page (Digitizers)            493
# 0x09, 0x54,                    //  Usage (Contact Count)              495
# 0x25, 0x7f,                    //  Logical Maximum (127)              497
# 0x95, 0x01,                    //  Report Count (1)                   499
# 0x75, 0x08,                    //  Report Size (8)                    501
# 0x81, 0x02,                    //  Input (Data,Var,Abs)               503
# 0x95, 0x02,                    //  Report Count (2)                   505
# 0x75, 0x08,                    //  Report Size (8)                    507
# 0x81, 0x03,                    //  Input (Cnst,Var,Abs)               509
# 0x85, 0x02,                    //  Report ID (2)                      511
# 0x09, 0x55,                    //  Usage (Contact Max)                513
# 0x25, 0x0a,                    //  Logical Maximum (10)               515
# 0x75, 0x08,                    //  Report Size (8)                    517
# 0x95, 0x01,                    //  Report Count (1)                   519
# 0xb1, 0x02,                    //  Feature (Data,Var,Abs)             521
# 0x06, 0x00, 0xff,              //  Usage Page (Vendor Defined Page 1) 523
# 0x09, 0xc5,                    //  Usage (Vendor Usage 0xc5)          526
# 0x85, 0x06,                    //  Report ID (6)                      528
# 0x15, 0x00,                    //  Logical Minimum (0)                530
# 0x26, 0xff, 0x00,              //  Logical Maximum (255)              532
# 0x75, 0x08,                    //  Report Size (8)                    535
# 0x96, 0x00, 0x01,              //  Report Count (256)                 537
# 0xb1, 0x02,                    //  Feature (Data,Var,Abs)             540
# 0xc0,                          // End Collection                      542
# 0x05, 0x0d,                    // Usage Page (Digitizers)             543
# 0x09, 0x02,                    // Usage (Pen)                         545
# 0xa1, 0x01,                    // Collection (Application)            547
# 0x85, 0x0d,                    //  Report ID (13)                     549
# 0x09, 0x20,                    //  Usage (Stylus)                     551
# 0xa1, 0x00,                    //  Collection (Physical)              553
# 0x09, 0x42,                    //   Usage (Tip Switch)                555
# 0x09, 0x44,                    //   Usage (Barrel Switch)             557
# 0x09, 0x45,                    //   Usage (Eraser)                    559
# 0x09, 0x3c,                    //   Usage (Invert)                    561
# 0x09, 0x32,                    //   Usage (In Range)                  563
# 0x09, 0x5a,                    //   Usage (Secondary Barrel Switch)   565
# 0x15, 0x00,                    //   Logical Minimum (0)               567
# 0x25, 0x01,                    //   Logical Maximum (1)               569
# 0x75, 0x01,                    //   Report Size (1)                   571
# 0x95, 0x06,                    //   Report Count (6)                  573
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              575
# 0x95, 0x02,                    //   Report Count (2)                  577
# 0x81, 0x03,                    //   Input (Cnst,Var,Abs)              579
# 0x05, 0x01,                    //   Usage Page (Generic Desktop)      581
# 0x09, 0x30,                    //   Usage (X)                         583
# 0x75, 0x10,                    //   Report Size (16)                  585
# 0x95, 0x01,                    //   Report Count (1)                  587
# 0xa4,                          //   Push                              589
# 0x55, 0x0e,                    //   Unit Exponent (-2)                590
# 0x65, 0x11,                    //   Unit (SILinear: cm)               592
# 0x35, 0x00,                    //   Physical Minimum (0)              594
# 0x46, 0x43, 0x0a,              //   Physical Maximum (2627)           596
# 0x26, 0x00, 0x40,              //   Logical Maximum (16384)           599
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              602
# 0x09, 0x31,                    //   Usage (Y)                         604
# 0x35, 0x00,                    //   Physical Minimum (0)              606
# 0x46, 0x6a, 0x06,              //   Physical Maximum (1642)           608
# 0x26, 0x80, 0x25,              //   Logical Maximum (9600)            611
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              614
# 0xb4,                          //   Pop                               616
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           617
# 0x09, 0x30,                    //   Usage (Tip Pressure)              619
# 0x26, 0xff, 0x0f,              //   Logical Maximum (4095)            621
# 0x75, 0x10,                    //   Report Size (16)                  624
# 0x95, 0x01,                    //   Report Count (1)                  626
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              628
# 0x09, 0x3d,                    //   Usage (X Tilt)                    630
# 0x55, 0x0e,                    //   Unit Exponent (-2)                632
# 0x65, 0x14,                    //   Unit (EnglishRotation: deg)       634
# 0x36, 0xd8, 0xdc,              //   Physical Minimum (-9000)          636
# 0x46, 0x28, 0x23,              //   Physical Maximum (9000)           639
# 0x16, 0xd8, 0xdc,              //   Logical Minimum (-9000)           642
# 0x26, 0x28, 0x23,              //   Logical Maximum (9000)            645
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              648
# 0x09, 0x3e,                    //   Usage (Y Tilt)                    650
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              652
# 0x09, 0x3b,                    //   Usage (Battery Strength)          654
# 0x75, 0x08,                    //   Report Size (8)                   656
# 0x95, 0x01,                    //   Report Count (1)                  658
# 0x15, 0x00,                    //   Logical Minimum (0)               660
# 0x25, 0x64,                    //   Logical Maximum (100)             662
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              664
# 0x55, 0x0c,                    //   Unit Exponent (-4)                666
# 0x66, 0x01, 0x10,              //   Unit (SILinear: s)                668
# 0x35, 0x00,                    //   Physical Minimum (0)              671
# 0x47, 0xff, 0xff, 0x00, 0x00,  //   Physical Maximum (65535)          673
# 0x15, 0x00,                    //   Logical Minimum (0)               678
# 0x27, 0xff, 0xff, 0x00, 0x00,  //   Logical Maximum (65535)           680
# 0x75, 0x10,                    //   Report Size (16)                  685
# 0x95, 0x01,                    //   Report Count (1)                  687
# 0x05, 0x0d,                    //   Usage Page (Digitizers)           689
# 0x09, 0x56,                    //   Usage (Scan Time)                 691
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              693
# 0xc0,                          //  End Collection                     695
# 0xc0,                          // End Collection                      696
# 0x06, 0x00, 0xff,              // Usage Page (Vendor Defined Page 1)  697
# 0x09, 0x01,                    // Usage (Vendor Usage 1)              700
# 0xa1, 0x01,                    // Collection (Application)            702
# 0x09, 0x01,                    //  Usage (Vendor Usage 1)             704
# 0x85, 0x03,                    //  Report ID (3)                      706
# 0x15, 0x00,                    //  Logical Minimum (0)                708
# 0x26, 0xff, 0x00,              //  Logical Maximum (255)              710
# 0x75, 0x08,                    //  Report Size (8)                    713
# 0x95, 0x3f,                    //  Report Count (63)                  715
# 0x81, 0x02,                    //  Input (Data,Var,Abs)               717
# 0x06, 0x00, 0xff,              //  Usage Page (Vendor Defined Page 1) 719
# 0x09, 0x01,                    //  Usage (Vendor Usage 1)             722
# 0x15, 0x00,                    //  Logical Minimum (0)                724
# 0x26, 0xff, 0x00,              //  Logical Maximum (255)              726
# 0x75, 0x08,                    //  Report Size (8)                    729
# 0x95, 0x3f,                    //  Report Count (63)                  731
# 0x91, 0x02,                    //  Output (Data,Var,Abs)              733
# 0x85, 0x0c,                    //  Report ID (12)                     735
# 0x09, 0x01,                    //  Usage (Vendor Usage 1)             737
# 0x81, 0x02,                    //  Input (Data,Var,Abs)               739
# 0x85, 0x07,                    //  Report ID (7)                      741
# 0x96, 0x06, 0x01,              //  Report Count (262)                 743
# 0x09, 0x01,                    //  Usage (Vendor Usage 1)             746
# 0xb1, 0x02,                    //  Feature (Data,Var,Abs)             748
# 0x85, 0x08,                    //  Report ID (8)                      750
# 0x96, 0x06, 0x04,              //  Report Count (1030)                752
# 0x09, 0x01,                    //  Usage (Vendor Usage 1)             755
# 0xb1, 0x02,                    //  Feature (Data,Var,Abs)             757
# 0x85, 0x09,                    //  Report ID (9)                      759
# 0x96, 0x06, 0x08,              //  Report Count (2054)                761
# 0x09, 0x01,                    //  Usage (Vendor Usage 1)             764
# 0xb1, 0x02,                    //  Feature (Data,Var,Abs)             766
# 0xc0,                          // End Collection                      768
# 0x05, 0x01,                    // Usage Page (Generic Desktop)        769
# 0x09, 0x02,                    // Usage (Mouse)                       771
# 0xa1, 0x01,                    // Collection (Application)            773
# 0x85, 0x05,                    //  Report ID (5)                      775
# 0x09, 0x01,                    //  Usage (Pointer)                    777
# 0xa1, 0x00,                    //  Collection (Physical)              779
# 0x05, 0x09,                    //   Usage Page (Button)               781
# 0x19, 0x01,                    //   Usage Minimum (1)                 783
# 0x29, 0x05,                    //   Usage Maximum (5)                 785
# 0x15, 0x00,                    //   Logical Minimum (0)               787
# 0x25, 0x01,                    //   Logical Maximum (1)               789
# 0x95, 0x05,                    //   Report Count (5)                  791
# 0x75, 0x01,                    //   Report Size (1)                   793
# 0x81, 0x02,                    //   Input (Data,Var,Abs)              795
# 0x95, 0x01,                    //   Report Count (1)                  797
# 0x75, 0x03,                    //   Report Size (3)                   799
# 0x81, 0x01,                    //   Input (Cnst,Arr,Abs)              801
# 0x05, 0x01,                    //   Usage Page (Generic Desktop)      803
# 0x75, 0x10,                    //   Report Size (16)                  805
# 0x95, 0x01,                    //   Report Count (1)                  807
# 0x55, 0x0e,                    //   Unit Exponent (-2)                809
# 0x65, 0x11,                    //   Unit (SILinear: cm)               811
# 0x09, 0x30,                    //   Usage (X)                         813
# 0x26, 0x00, 0x40,              //   Logical Maximum (16384)           815
# 0x35, 0x00,                    //   Physical Minimum (0)              818
# 0x46, 0x43, 0x0a,              //   Physical Maximum (2627)           820
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         823
# 0x09, 0x31,                    //   Usage (Y)                         825
# 0x26, 0x80, 0x25,              //   Logical Maximum (9600)            827
# 0x46, 0x6a, 0x06,              //   Physical Maximum (1642)           830
# 0x81, 0x42,                    //   Input (Data,Var,Abs,Null)         833
# 0xc0,                          //  End Collection                     835
# 0xc0,                          // End Collection                      836
```
