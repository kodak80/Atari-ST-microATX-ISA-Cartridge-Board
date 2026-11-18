# Atari ST microATX ISA Cartridge Board

ISA board to allow the original Atari ST cartridge socket on a card. It brings
the ST cartridge port out to an ISA (16-bit) card outline and an internal
40-pin IDC header, so the cartridge bus can be used inside a microATX case
build. Board silkscreen: *Atari ST ATX Cartridge Port ISA Adapter v1.3 —
kodak80 (2022)*.

## Board

- Two-layer PCB in an ISA 16-bit card outline (`ST1`)
- Atari ST cartridge port connection (`U$1`) with ROM3/ROM4 select lines
- Internal 40-pin IDC header (`J1`) carrying the cartridge bus
- DIP-16 socket (`J2`) for a Dallas-style RTC ("FMC-II RTC"), with crystal
  (`Y1`) and CR1220 coin-cell holder (`BT1`)
- Jumper option on the board (`JP`)

## Files

| File | Contents |
|------|----------|
| `Cart Adapter RTC 40 pin Header SMD CR1220.kicad_pro` | KiCad project |
| `Cart Adapter RTC 40 pin Header SMD CR1220.kicad_sch` | Schematic |
| `Cart Adapter RTC 40 pin Header SMD CR1220.kicad_pcb` | PCB layout |
| `IDC-Header_2x20_P2.54mm_Vertical_kodak80.kicad_mod` | Custom 2×20 IDC header footprint |
| `empty.kicad_wks` | Drawing sheet |

Created in KiCad 6; opens in later versions (they will offer to upgrade the
file format on save). The schematic was originally imported from Eagle, so
several symbols live in the embedded `Cart Adapter-eagle-import` library.

## Revision

v1.3

## TheHulk ISA card (branch `thehulk-isa`)

[`thehulk-isa/`](thehulk-isa/) merges RetroLoft's [TheHulk](https://github.com/RetroLoft/thehulk)
network/SD storage cartridge onto this card: schematic done, PCB is this v1.3 board with the socket
and RTC removed and TheHulk's parts added, ready to be placed. KiCad 9, GPL-3.0. See
[`thehulk-isa/ROUTING.md`](thehulk-isa/ROUTING.md).
