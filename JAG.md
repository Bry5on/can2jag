# can2jag — GS450H / Jaguar cluster fork

Defaults for the V2 board on this fork:

| Pin | Function |
|---|---|
| Coil RPM | tach-ammeter (`0x0AA` byte 6 × 20 = amps × 10 as RPM) |
| Speed Square | mph from `0x0AA` byte 1 / 2 |
| EML | coolant PWM (`0x0AA` byte 3, °C) |
| EPC | stator PWM (`0x0AA` byte 2, °C) |

There is **no peg-at-warning**. Duty comes from the calibration curve. With an empty curve the firmware maps 0–120 °C → 0–1023 so the needle moves immediately; capture points in Calibration Builder to match the Jag.

## UI / EEPROM
- `coolantOutput` default `EML`
- `statorOutput` default `EPC` (refuses the same pin as coolant)
- `useGs450h` default on
- PWM carrier default **200 Hz** (same as the Lingenfelter calibrate that moved the needle)

Enable **ECU RPM** in Speed/RPM if the coil tach should follow the ammeter mapping.

## Build
PlatformIO project under `PlatformIO/`. Flash firmware + `data/` LittleFS.
