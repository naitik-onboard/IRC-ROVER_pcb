# 24-Pin Header (TS-124-G-AA) – Pin Naming Changes

This document tracks the progressive changes made to the **24-pin header symbol (TS-124-G-AA)** that connects to the left-hand side of the **Teensy 4.1 (DEV-16771)** in the schematic.

The header went from a generic, numbered symbol (`01`–`24`) to a symbol where the **pin numbers are removed** and every pin carries its **Teensy 4.1 pin-out name**.

---

## 1. Summary of Changes

| Item | Before | After |
|------|--------|-------|
| Pin labels | Generic numbers only (`01`, `02`, … `24`), same style as the other TS-10x headers on the sheet | Signal / pin-out names (`GND`, `RX1/CS1/CRX2`, … `OUT1B`) |
| GPIO numbers | Teensy GPIO number used to identify the pin | GPIO number dropped from the label; only the function names remain |
| Header position order | 1 → 24 | Unchanged (pin 1 → pin 24) |
| Footprint / part | TS-124-G-AA, 1 × 24 | Unchanged |

Only the **labelling** changed. The physical header, its pin count and its pin order are the same.

---

## 2. Progressive Changes

### Revision 1 – Generic header
- Symbol placed as TS-124-G-AA with pins numbered `01`–`24`.
- No signal names, so the header could not be read against the Teensy without a pin map.

### Revision 2 – Numbers removed
- Generic pin numbers / GPIO numbers removed from the pin labels.
- Pin names now describe the function instead of the position.

### Revision 3 – Pin-out names applied (current)
- Every pin renamed to match the Teensy 4.1 left-side pin-out (see table below).
- Alternate functions are listed with `/` (e.g. `A10/TX6/SCL2`).
- Power and ground pins are named explicitly (`GND`, `3.3V`).

> Edit the revision list above to match your actual commit history.

---

## 3. Current Pin-Out (Pins 1 – 24)

| Header Pin | Teensy 4.1 GPIO (removed from label) | New Pin Name | Function Group |
|:---:|:---:|---|---|
| 1  | –  | `GND` | Power |
| 2  | 0  | `RX1/CS1/CRX2` | UART1 RX / SPI1 CS / CAN2 RX |
| 3  | 1  | `TX1/MISO1/CTX2` | UART1 TX / SPI1 MISO / CAN2 TX |
| 4  | 2  | `OUT2` | Audio out |
| 5  | 3  | `LRCLK2` | Audio I2S |
| 6  | 4  | `BCLK2` | Audio I2S |
| 7  | 5  | `IN2` | Audio in |
| 8  | 6  | `OUT1D` | Audio out |
| 9  | 7  | `RX2/OUT1D` * | UART2 RX / Audio out |
| 10 | 8  | `TX2/IN1` | UART2 TX / Audio in |
| 11 | 9  | `OUT1C` | Audio out |
| 12 | 10 | `CS/MQSR` | SPI CS / MQS right |
| 13 | 11 | `MOSI/CTX1` | SPI MOSI / CAN1 TX |
| 14 | 12 | `MISO/MQSL` | SPI MISO / MQS left |
| 15 | –  | `3.3V` | Power |
| 16 | 24 | `A10/TX6/SCL2` | ADC / UART6 TX / I2C2 SCL |
| 17 | 25 | `A11/RX6/SDA2` | ADC / UART6 RX / I2C2 SDA |
| 18 | 26 | `A12/MOSI1` | ADC / SPI1 MOSI |
| 19 | 27 | `A13/SCK1` | ADC / SPI1 SCK |
| 20 | 28 | `RX7` | UART7 RX |
| 21 | 29 | `TX7` | UART7 TX |
| 22 | 30 | `CRX3` | CAN3 RX |
| 23 | 31 | `CTX3` | CAN3 TX |
| 24 | 32 | `OUT1B` | Audio out |

\* See "Points to Verify" below.

---

## 4. Points to Verify

1. **Pin 8 vs Pin 9** – both are labelled `OUT1D` (pin 8 `OUT1D`, pin 9 `RX2/OUT1D`). On the Teensy 4.1, GPIO 7 is normally `RX2/OUT1A`, so pin 9 is probably meant to read `RX2/OUT1A`.
2. **Header size** – the part is a single-row 1 × 24 header (TS-124-G-AA), not a 12-pin one. Check the footprint if a 2 × 12 layout was intended.
3. **Net names** – confirm the net labels on the Teensy symbol (`U?`) match the new header names so ERC/DRC stays clean.

---

## 5. Notes

- Pins 25–48 (the second TS-124-G-AA header) follow the same naming scheme and can be documented in the same way.
- Tool: Altium Designer schematic (`.SchDoc`).
