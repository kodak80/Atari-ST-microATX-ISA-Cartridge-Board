# TheHulk ISA card

[TheHulk](https://github.com/RetroLoft/thehulk) (RetroLoft's network and SD card storage cartridge for
the Atari ST, ESP32-S3 + iCE40UP5K) moved onto the Atari ST mATX ISA cartridge board in the parent
folder. The cartridge bus reaches the card through the ISA edge (same pinout as the v1.3 board) or
the internal 40-pin header J1. The /ROM3 and /ROM4 pads are kept for the flying wires from the
motherboard.

KiCad 9 project, based on TheHulk `hardware/prod-v2` (commit `c8f1c73`).

## What changed from TheHulk prod-v2

- **Cartridge edge removed.** The 40-pin cartridge connector `CON1` is now `J1`, a 2×20 IDC header
  (`isa_card:IDC-Header_2x20_P2.54mm_Vertical_kodak80`). Its pins are numbered exactly like the cartridge
  port, so nothing else in TheHulk's circuit changed.
- **ISA edge added** (`ST1`, `isa_card:ISA_16bit_Edge` / `isa_card:IBM16BIT`) on the same nets as
  v1.3: D0–D15, A1–A15, /UDS, /LDS, +5V, GND. The ISA pins v1.3 had but the cartridge port doesn't
  (A16–A19, RDY2, VRES, MEMRD/MEMWR, ±12V) are marked no-connect.
- **/ROM3 and /ROM4 wire pads** (`ROM3`, `ROM4`), as on v1.3.
- **FMC-II RTC socket and the passthrough cartridge socket are gone.**
- Everything else is TheHulk prod-v2 unchanged: same parts, same nets, same FPGA and ESP32 pins, so
  TheHulk's gateware and firmware should run as they are.

## PCB

- Card outline from v1.3, with two changes:
  - the sloping top edge now starts further left (top-left corner at x = 176.4 mm instead of
    207.6 mm) to make room for TheHulk's core. Check this against the case.
  - the tab that goes through the bracket is 6 mm longer (edge at x = 248.8 mm instead of
    242.8 mm), so the whole microSD socket sits outside the bracket. The tab now sticks out about
    18.3 mm behind the bracket.
- TheHulk's routed core sits in the tall section next to the bracket, rotated 90°. Its routing is
  kept as RetroLoft laid it out. The ESP32-S3 antenna overhangs the top edge as it overhangs the
  cartridge PCB on TheHulk: 106.1 mm above the bottom of the ISA edge, inside the ISA full-height
  limit of 106.7 mm.
- The old gold-finger tracks of TheHulk fan out straight into J1. The pin order follows the fingers,
  so there are no crossings.
- User-facing parts are on the tab that goes through the bracket (where v1.3 had the cartridge
  socket): USB (J3), status LED (D6), MODE button (SW1) and microSD socket (Card1). The SD card goes
  in from outside the case.
- GND pour on both layers over the whole card, kept off the gold fingers.

## Status

See `ROUTING.md` for what is routed and what is left. The board passes the KiCad 9 schematic
parity check. Remaining DRC items are listed there too.

## License

GPL-3.0 (see `LICENSE`), as TheHulk. TheHulk is by RetroLoft; GEMDRIVE is based on the
SidecarTridge Multi-device project by Diego Parrilla Santamaría (GOODDATA LABS SL).
