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

Fresh start from the v1.3 board (`Cart Adapter RTC 40 pin Header SMD CR1220.kicad_pcb`):

- **Kept exactly as v1.3:** card outline, ISA edge (ST1), J1 and the /ROM3, /ROM4 pads in their
  v1.3 positions, and your v1.3 routing between the ISA edge, J1 and the /ROM pads.
- **Removed:** the cartridge socket, the FMC-II RTC (Dallas socket, crystal, CR1220 holder), their
  silkscreen labels, and the v1.3 tracks that only went to them.
- **Added, not placed:** all 74 of TheHulk's parts (everything except its cartridge edge), with
  their nets, sitting below the card in TheHulk's own arrangement under the label
  "TheHulk parts - to be placed". No tracks.
- Net class: TheHulk's (0.2 mm tracks, 0.6/0.3 mm vias) with the clearance set to 0.1524 mm (6 mil),
  the clearance your v1.3 routing was laid out to. TheHulk's own layout also meets it.

## License

GPL-3.0 (see `LICENSE`), as TheHulk. TheHulk is by RetroLoft; GEMDRIVE is based on the
SidecarTridge Multi-device project by Diego Parrilla Santamaría (GOODDATA LABS SL).
