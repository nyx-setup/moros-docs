# ESP32-S3 Capabilities

> Based on official Espressif documentation.  
> Source: https://www.espressif.com/en/products/socs/esp32-s3

---

## Processor

- Dual-core Xtensa LX7 @ up to 240 MHz
- 512 KB internal SRAM
- 384 KB ROM
- ULP coprocessor (RISC-V + FSM) for low-power operation
- Vector instructions that accelerate DSP and TinyML workloads

## Wireless

- Wi-Fi 802.11 b/g/n (2.4 GHz), 40 MHz bandwidth
- Bluetooth 5 LE (no Classic Bluetooth)
  - Long range via Coded PHY
  - Advertisement extension
  - Up to 2 Mbps PHY

## Peripherals

- Up to 45 GPIOs (availability depends on module/board)
- 14 capacitive touch GPIOs
- SPI, I2S, I2C, UART, PWM, RMT, ADC
- USB 1.1 OTG (native, no external chip needed)
- SD/MMC host
- TWAI (Two-Wire Automotive Interface / CAN bus compatible)

## Security

- AES-XTS flash encryption
- RSA-based secure boot
- Digital signature and HMAC
- 4 Kbit eFuse storage
- World Controller — hardware privilege isolation allowing separation between trusted and untrusted execution contexts

## Power

- Multiple sleep modes via ULP coprocessor
- 12-bit SAR ADC (20 channels) usable in sleep mode
