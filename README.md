[![KiCad 9](https://img.shields.io/badge/KiCad-9-blue)](https://kicad.org)
[![Schematic v1.0](https://img.shields.io/badge/Sch-v1.1-blueviolet)](kicad/buffer-module.kicad_sch)
[![PCB v1.0](https://img.shields.io/badge/PCB-v1.0-blue)](kicad/buffer-module.kicad_pcb)
[![PCBs: 3](https://img.shields.io/badge/PCBs-3-brightgreen)](kicad/buffer-module.kicad_pcb)
[![Format: Eurorack](https://img.shields.io/badge/Format-Eurorack-0093ff)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)
[![Instagram](https://img.shields.io/badge/Instagram-@moonsofmercury-E4405F?logo=instagram&logoColor=white)](https://www.instagram.com/moonsofmercury/)

# Output (KiCad 9)

Multi-sheet KiCad 9 project providing schematics and PCB for audio output / amplifier modules.

## Table of contents
- Overview
- Features
- Project layout
- Quick start
- Build & assembly notes
- Testing
- BOM
- Contributing
- License

## Overview
This repository contains the KiCad 9 project `output_pcb`. It includes multiple schematic sheets (HP amp, line amp, IO, volume meter, etc.) and a single PCB layout. All design files live under `kicad/`.

## Features
- Multi-sheet schematic architecture for modular subsystems.
- Single PCB layout in KiCad 9 format: `kicad/output_pcb.kicad_pcb`.
- Mix of through-hole and SMD parts (jacks, headers, op-amps, passives).

## Project layout
Project files:
- `kicad/output_pcb.kicad_pro` — KiCad project file
- `kicad/output_pcb.kicad_sch` — top-level schematic (hierarchical)
- `kicad/output_pcb.kicad_pcb` — PCB layout
- `kicad/output_pcb.kicad_prl` — plot/print settings

- `output/` — generated zipped gerbers and other fabrication outputs

Schematic sheets:
- `kicad/hp_amp.kicad_sch` — HP / amp sheet
- `kicad/line_amp.kicad_sch` — line amp sheet
- `kicad/io_board.kicad_sch` — IO / connectors
- `kicad/rear_board.kicad_sch` — rear panel / connectors
- `kicad/volume_meter.kicad_sch` — meter sheet

## Quick start
1. Install KiCad 9.
2. Open `kicad/output_pcb.kicad_pro`.
3. In Schematic Editor: run ERC and review results.
4. In PCB Editor: update PCB from schematic, then run DRC.
5. Generate fabrication outputs (Gerbers, drill, BOM, pick-and-place) as needed.

## Build & assembly notes
- Follow footprints and polarity/orientation markings (IC notches, electrolytics, LEDs, diodes).
- Suggested assembly order: SMD (reflow/paste) → THT (jacks, headers, pots) → mechanical fixtures.
- Decoupling: place 100 nF capacitors close to each op-amp’s power pins; use bulk electrolytics on rails where appropriate.
- Verify mechanical alignment (jack positions, mounting holes) against your panel/enclosure before final tightening.

## Testing
1. Power: apply power with no signal inputs; verify rail voltages and polarity at key ICs/connectors.
2. Signal: inject known signals; verify outputs with an oscilloscope or audio probe.
3. Mechanics: confirm jack seating, connector fit, and pot operation.

## BOM
The BOM is user-maintained in `BOM.md`. A KiCad-exported CSV can be generated from the schematic if you prefer a machine-readable BOM.

<details>
  <summary><strong>Detailed BOM</strong></summary>

### Bill of Materials

Please verify against the schematic before procurement.

Sanity-check totals (deduplicated):
- Capacitors (C): 34
- Diodes/LEDs (D): 12
- Mounting holes (H): 4
- Connectors/Jacks/Headers (J): 13
- Resistors (R): 48
- Pots (RV): 2
- ICs (U): 12
- Total line-item quantity: 125

Cleanup notes:
- Removed duplicate single entries for `C1` and `C2` (the combined `C1, C2` entry already covers them).
- `U2, U7, U10–U12`: datasheet link points to TL071 (not TL074). Consider updating the URL.
- `J12, J22`: footprint name contains repeated `P2.54mm`; confirm it matches your library.

### BOM table

| Designator(s) | Qty | Value / Part | Footprint | Vendor / URL | Notes |
|---|---:|---|---|---|---|
| C1, C2 | 2 | 150 nF | Capacitor_THT:C_Disc_D4.7mm_W2.5mm_P5.00mm | https://www.taydaelectronics.com/10-x-0-15uf-50v-ceramic-disc-capacitor-pkg-of-10.html | |
| C5–C28 | 24 | 100 nF | Capacitor_THT:C_Disc_D4.7mm_W2.5mm_P5.00mm | https://www.taydaelectronics.com/a-553-0-1uf-50v-ceramic-disc-capacitor-pkg-of-10.html | |
| C29, C30, C33, C34 | 4 | 100 pF | Capacitor_THT:C_Disc_D4.7mm_W2.5mm_P5.00mm | https://www.taydaelectronics.com/10-x-100pf-50v-ceramic-disc-capacitor-pkg-of-10.html | |
| C31, C32, C39, C40 | 4 | 10 µF | Capacitor_THT:CP_Radial_D4.0mm_P1.50mm | https://www.taydaelectronics.com/datasheets/files/A-3931.PDF | |
| D1, D2 | 2 | 1N4148 | Diode_THT:D_A-405_P7.62mm_Horizontal | https://www.taydaelectronics.com/datasheets/files/A-157.PDF | |
| D3, D8 | 2 | LED (RED) 3mm | LED_THT:LED_D3.0mm_Clear | https://www.taydaelectronics.com/led-3mm-red-water-clear-ultra-bright.html | |
| D4, D9 | 2 | LED (AMBER) 3mm | LED_THT:LED_D3.0mm_Clear | https://www.taydaelectronics.com/led-3mm-orange-water-clear.html | |
| D5–D7, D10–D12 | 6 | LED (GREEN) 3mm | LED_THT:LED_D3.0mm_Clear | https://www.taydaelectronics.com/led-3mm-green-water-clear-super-bright.html | |
| H1–H4 | 4 | Mounting Hole 2.7mm | MountingHole:MountingHole_2.7mm_M2.5 | — | |
| J1, J2 | 2 | 3.5 mm Audio Jack (switching) | Eurorack:Jack_3.5mm_QingPu_WQP-PJ398SM_Vertical | https://www.taydaelectronics.com/datasheets/files/w-qp-518ma_drawings.pdf | |
| J3–J5 | 3 | 6.35 mm Audio Jack | Eurorack:Jack_6.35mm_PJ_629HAN_slots | https://www.taydaelectronics.com/datasheets/files/A-1121.pdf | |
| J6 | 1 | 2x5 Eurorack power header | Connector_IDC:IDC-Header_2x05_P2.54mm_Vertical | https://www.taydaelectronics.com/datasheets/files/A-2939.pdf | |
| J7 | 1 | 1x3 Pin Socket | Connector_PinHeader_2.54mm:PinHeader_1x03_P2.54mm_Vertical | https://www.taydaelectronics.com/datasheets/files/FH411.pdf | |
| J11, J13, J21, J23 | 4 | 1x10 Pin Header | Connector_PinHeader_2.54mm:PinHeader_1x10_P2.54mm_Vertical | https://www.taydaelectronics.com/datasheets/files/A-197.pdf | |
| J12, J22 | 2 | 1x10 Pin Socket | Connector_PinHeader_2.54mm:PinHeader_1x10_P2.54mm_P2.54mm_Vertical | https://www.taydaelectronics.com/datasheets/files/FH411.pdf | |
| R1, R2 | 2 | 100 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | reichelt | |
| R3, R11, R19, R20 | 4 | 20 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | https://www.taydaelectronics.com/datasheets/files/royalohmprecisionmetalmf.pdf | |
| R4–R6, R12–R14, R21–R26, R39–R48 | 22 | 10 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | https://www.taydaelectronics.com/datasheets/files/royalohmprecisionmetalmf.pdf | |
| R7–R10, R15–R18 | 8 | 10 Ω | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_P10.16mm_Horizontal | reichelt | footprint string differs; verify |
| R27–R30 | 4 | 100 Ω | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | reichelt | |
| R31, R32 | 2 | 22 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | reichelt | |
| R33 | 1 | 33 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | reichelt | |
| R34 | 1 | 2.2 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | reichelt | |
| R35 | 1 | 1.5 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | https://www.taydaelectronics.com/datasheets/files/royalohmprecisionmetalmf.pdf | |
| R36 | 1 | 2.4 kΩ | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | https://www.taydaelectronics.com/datasheets/files/royalohmprecisionmetalmf.pdf | |
| R37 | 1 | 820 Ω | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | https://www.taydaelectronics.com/datasheets/files/royalohmprecisionmetalmf.pdf | |
| R38 | 1 | 470 Ω | Resistor_THT:R_Axial_DIN0207_L6.3mm_D2.5mm_P10.16mm_Horizontal | reichelt | |
| RV1, RV2 | 2 | 50 kΩ B (potentiometer) | Eurorack:Potentiometer_Alpha_RD902F-40-00D_Dual_Vertical_CircularHoles_centered | https://www.taydaelectronics.com/datasheets/files/A-5440.pdf | |
| U1 | 1 | TL072 (dual op-amp) | Package_DIP:DIP-8_W7.62mm | reichelt | |
| U2, U7, U10–U12 | 5 | TL074 (quad op-amp) | Package_DIP:DIP-14_W7.62mm | http://www.ti.com/lit/ds/symlink/tl071.pdf | datasheet link likely for TL074 |
| U3–U6, U8, U9 | 6 | NE5532 (dual op-amp) | Package_DIP:DIP-8_W7.62mm | https://www.taydaelectronics.com/ne5532-5532-ic-dual-low-noise-op-amp.html | |

</details>

## Contributing
Issues and PRs welcome. If you change schematics/PCB, include updated BOM and any relevant build/test notes.

## License
MIT — see `LICENSE`.
