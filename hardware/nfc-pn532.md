# PN532 — NFC Controller

> Based on official NXP Semiconductors documentation.  
> Source: https://www.nxp.com/docs/en/nxp/data-sheets/PN532_C1.pdf

---

## Overview

The PN532 is a highly integrated NFC controller manufactured by NXP Semiconductors, based on an 80C51 microcontroller core. It operates at 13.56 MHz and supports multiple contactless communication standards.

---

## Key Specifications

| Parameter           | Value                        |
|---------------------|------------------------------|
| Operating frequency | 13.56 MHz                    |
| Max transfer speed  | 424 kbps                     |
| Host interfaces     | I2C, SPI, UART (HSU)        |
| I2C address         | Typically 0x24 (7-bit)      |
| Supply voltage      | 2.7 – 5.5 V                 |
| Core                | 80C51 — 40 KB ROM, 1 KB RAM |

> Note: PN532 I²C addressing is sometimes documented using 8-bit notation (0x48) and sometimes using 7-bit notation (0x24). Verify against the library in use.

---

## Supported Operating Modes

| Mode                         | Description                                    |
|------------------------------|------------------------------------------------|
| ISO/IEC 14443A Reader/Writer | MIFARE and compatible cards                   |
| ISO/IEC 14443B Reader/Writer | ISO B cards (layers 2 and 3)                  |
| FeliCa Reader/Writer         | Sony FeliCa protocol — 212 kbps and 424 kbps  |
| MIFARE Classic emulation     | 1K and 4K card emulation                      |
| NFCIP-1 (P2P)               | Active and passive peer-to-peer mode           |

---

## Supported Card Types

- MIFARE Classic 1K / 4K
- MIFARE Ultralight
- MIFARE DESFire
- ISO/IEC 14443-4 cards
- FeliCa (RCS_860, RCS_854)
- Innovision Jewel / Topaz

---

## Key Features

- Complete ISO/IEC 14443A framing and error detection (parity and CRC)
- Hardware support for anticollision
- Integrated analog circuitry for demodulation and decoding
- Buffered output drivers for direct antenna connection
- IRQ pin for interrupt-driven communication
- Low power modes available

---

## Typical Applications

- NFC tag reading
- Access control systems
- Smart locks
- NFC-based authentication
- Card emulation
- Peer-to-peer NFC communication
- MIFARE and DESFire projects

---

## Notes

- The PN532 does **not** support 125 kHz (low-frequency) RFID cards
- The PN532 does **not** bypass or crack card security mechanisms
- Authentication and higher-level protocols must be implemented by the host software
- Only one host interface (I2C, SPI, or UART) can be active at a time
- Communication distance is typically 5–7 cm depending on antenna design

---

## Official Resources

- [PN532 Datasheet (PDF)](https://www.nxp.com/docs/en/nxp/data-sheets/PN532_C1.pdf)
- [PN532 User Manual (PDF)](https://www.nxp.com/docs/en/user-guide/141520.pdf)
