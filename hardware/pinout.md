# LilyGO T-Embed CC1101 Plus — Pinout

> Based on official LilyGO documentation and source code.  
> Sources:  
> - https://wiki.lilygo.cc/products/t-embed-series/t-embed-cc1101/  
> - https://github.com/Xinyuan-LilyGO/T-Embed-CC1101  
> Note: This document covers the Plus variant (K268-01) with external antenna.

---

## Board Specifications

| Feature      | Specification                       |
|--------------|-------------------------------------|
| MCU          | ESP32-S3 dual-core LX7 @ 240 MHz   |
| Flash        | 16 MB                               |
| PSRAM        | 8 MB                                |
| Wi-Fi        | 2.4 GHz 802.11 b/g/n               |
| Bluetooth    | Bluetooth 5.0 LE                    |
| Sub-GHz      | CC1101                              |
| 2.4 GHz ISM  | nRF24L01 (Plus only)               |
| NFC          | PN532 (13.56 MHz)                  |
| Display      | 1.9-inch ST7789V IPS TFT (320×170) |
| RGB LED      | WS2812 × 8                         |
| Battery      | 3.7V 1300 mAh Li-Po                |
| Battery mgmt | BQ25896 + BQ27220                  |
| Storage      | TF card slot                        |
| USB          | USB Type-C                          |
| Expansion    | 2 × QWIIC (I2C)                    |
| Dimensions   | 97.5 × 39 × 31 mm                  |

---

## Pin Assignments

### LCD — ST7789V

| Signal | GPIO |
|--------|------|
| BL     | IO21 |
| DC     | IO16 |
| CS     | IO41 |
| CLK    | IO11 |
| MOSI   | IO09 |
| RST    | IO40 |

### CC1101 — Sub-GHz (SPI)

| Signal | GPIO |
|--------|------|
| CS     | IO12 |
| SCK    | IO11 |
| MOSI   | IO09 |
| MISO   | IO10 |
| GDO2   | IO38 |
| GDO0   | IO03 |
| SW1    | IO47 |
| SW0    | IO48 |

> ⚠️ CC1101 shares SPI bus (SCK/MOSI/MISO) with LCD. CS pins differentiate devices.

### NFC — PN532 (I2C)

| Signal   | GPIO |
|----------|------|
| SCL      | IO18 |
| SDA      | IO08 |
| IRQ      | IO17 |
| RF_RESET | IO45 |

> Note: PN532 I²C address depends on the addressing convention used by the library.

### nRF24L01 — 2.4 GHz ISM (Plus only)

> ⚠️ Pin assignments for the K268-01 (external antenna) variant are not yet
> publicly documented by LilyGO. Refer to the official repository for updates:
> https://github.com/Xinyuan-LilyGO/T-Embed-CC1101

### Encoder

| Signal | GPIO |
|--------|------|
| INA    | IO04 |
| INB    | IO05 |

### Buttons

| Signal              | GPIO |
|---------------------|------|
| KEY                 | IO06 |
| BOOT (encoder push) | IO00 |

### RGB LED — WS2812 × 8

| Signal | GPIO |
|--------|------|
| DATA   | IO14 |

### Infrared

| Signal | GPIO |
|--------|------|
| IR_EN  | IO02 |
| IR_RX  | IO01 |

### Microphone

| Signal | GPIO |
|--------|------|
| DATA   | IO42 |
| CLK    | IO39 |

### Speaker (I2S)

| Signal | GPIO |
|--------|------|
| BCLK   | IO46 |
| LRCLK  | IO40 |
| DIN    | IO07 |

> ⚠️ GPIO40 is shared between LCD_RST and I2S LRCLK according to the official schematic.

### Power & System

| Signal | GPIO |
|--------|------|
| PWR_EN | IO15 |

### Battery Management (I2C)

| IC      | I2C Address |
|---------|-------------|
| BQ27220 | 0x55        |
| BQ25896 | 0x6B        |

---

## Official Resources

- [Wiki](https://wiki.lilygo.cc/products/t-embed-series/t-embed-cc1101/)
- [GitHub Repository](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101)
- [Schematic V1.0](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/T-Embed-CC1101%20V1.0%2024-07-29.pdf)
- [CC1101 Datasheet](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/cc1101.pdf)
- [PN532 Datasheet](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/PN532_C1.pdf)
- [BQ25896 Datasheet](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/bq25896.pdf)
- [BQ27220 Datasheet](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/bq27220_datasheet.pdf)
