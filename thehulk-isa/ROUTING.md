# Layout status

KiCad 9.0.3, `kicad-cli pcb drc --schematic-parity`:

| Check | Result |
|---|---|
| Schematic parity | 0 issues |
| Unrouted connections | 303: TheHulk's parts are not placed yet |
| Clearance | 3, all inside the v1.3 routing (A13 near J1 pad 11, D14 near J1 pad 2), same as the v1.3 board |
| Invalid outline | 11: the v1.3 outline as it is (ST1's built-in edge lines overlap the board's own edge lines, one small gap at x = 229.1 mm, y = 71.1 mm, one stray line at x = 207.6 mm); the v1.3 board shows the same in KiCad 9 |
| Silkscreen / footprint library notes | cosmetic, or TheHulk's footprints vs. stock KiCad 9 libraries |

## Done

- v1.3 ISA edge to J1 and /ROM pad routing: complete for every signal (D0-D15, A1-A15, /UDS, /LDS,
  /ROM3, /ROM4).

## To do

- Place TheHulk's parts on the card. USB (J3), microSD (Card1), MODE button (SW1) and the status
  LED (D6) go on the tab through the bracket if they need to be reached from outside the case.
- Route TheHulk. Its bus side connects to the same nets as J1, so it can join your v1.3 tracks or
  J1's pads.
- GND and +5V between ISA fingers (B1, B10, B29, B31, A11, C2-C5, D16, D18) are not routed, as on
  v1.3. A GND pour plus a +5V track would close them.
- Add a GND pour if wanted.
