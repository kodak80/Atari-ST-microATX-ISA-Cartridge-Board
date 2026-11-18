# Routing status

KiCad 9.0.3, `kicad-cli pcb drc --schematic-parity`:

| Check | Result |
|---|---|
| Schematic parity | 0 issues |
| Copper clearance, shorts, board edge, outline | 0 errors |
| Unrouted connections | 61 |
| Silkscreen overlaps / silk over copper / silk to edge | 14 / 3 / 8 (cosmetic) |
| Footprint differs from library | 60: TheHulk's footprints vs. the stock KiCad 9 libraries, as upstream |

## Routed

- TheHulk's whole core, exactly as RetroLoft routed it (rotated 90°).
- The fan-out from TheHulk's old gold-finger tracks to J1 (pin order matches, no crossings;
  even pins on B.Cu to the upper row, odd pins on F.Cu between the upper-row pads to the lower row).
- GND pour on both layers (refill after routing: press B).

## Still to route (61)

| Group | Count | Notes |
|---|---|---|
| ISA edge ST1 to J1 | 45 | D0–D15, A1–A15, /UDS, /LDS, +5V_CART, GND fingers. The ISA pin order is not the cartridge order, so this needs real routing. No tracks along or between the gold fingers, no vias in the finger keep-out (rule area above the fingers). GND fingers only need a short track and a via into the pour. |
| Tab parts | 14 | USB J3 (VBUS, D+, D-), microSD Card1 (SCLK, MOSI, MISO, SD_CS, CD, +3V3_ESP), MODE button SW1 (BTN1), status LED D6 (+5V_SYS, DIN from D5). The tracks that went to these parts on TheHulk were removed when the parts moved to the tab. Keep USB D+/D- as a pair. |
| /ROM3, /ROM4 pads | 2 | To J1 pins 31 and 33. |

Suggested widths: +5V_CART and +5V_SYS 0.5 mm or more, signals 0.25 mm (TheHulk's default netclass:
0.2 mm track, 0.2 mm clearance).
