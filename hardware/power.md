# Power & Shutdown — BQ25896 PMIC

> Based on Texas Instruments BQ25896 documentation and the LilyGO T-Embed CC1101 schematic.
> Source: https://www.ti.com/lit/ds/symlink/bq25896.pdf

---

## Overview

The BQ25896 (I2C `0x6B`) is the power-path/charger IC. It gates the battery to
the system rail through an internal **BATFET**. `PWR_EN` (IO15) is only a
soft-power latch — it does **not** cut the rail on its own.

---

## Power-on

Driving `PWR_EN` (IO15) HIGH latches the board on and keeps it powered after the
button is released.

---

## Shutdown

Releasing the `PWR_EN` latch is not enough; the BATFET keeps the rail alive.
To power the board down, disable the BATFET over I2C:

| Register | Bit | Field        | Action              |
|----------|-----|--------------|---------------------|
| `0x09`   | 5   | `BATFET_DIS` | Set to 1 to shut off |

This must be a **read-modify-write** — read `REG09`, set bit 5, write it back —
so the other control bits are preserved.

> ⚠️ On USB power the board stays alive even with the BATFET disabled, because
> VBUS still feeds the system rail. Shutdown only powers the board off on
> battery.

---

## Gotcha — encoder push is a strapping pin

The encoder push button is on **IO00** (BOOT), an ESP32-S3 strapping pin. If it
is held LOW at power-on or reset, the boot ROM enters serial download mode
instead of running the firmware, and the board appears dead. This is decided in
ROM and cannot be worked around in software — avoid holding the encoder while
powering on.

---

## Official Resources

- [BQ25896 Datasheet (PDF)](https://www.ti.com/lit/ds/symlink/bq25896.pdf)
- [BQ27220 Datasheet (PDF)](https://www.ti.com/lit/ds/symlink/bq27220.pdf)
