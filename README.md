[![KiCad 9](https://img.shields.io/badge/KiCad-9-blue)](https://kicad.org)
[![PCB: output_pcb](https://img.shields.io/badge/PCB-output__pcb-blue)](kicad/output_pcb.kicad_pcb)
[![Schematics](https://img.shields.io/badge/Sch-multiple-blueviolet)](kicad/output_pcb.kicad_sch)
[![PCBs: 1](https://img.shields.io/badge/PCBs-1-brightgreen)](kicad/output_pcb.kicad_pcb)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

# Output (KiCad project)

This repository contains a KiCad 9 project named `output_pcb` and several associated schematic sheets for audio-related modules. The main PCB is `output_pcb.kicad_pcb` and the project was generated with KiCad 9.

## Contents

- Overview
- Features
- Quick start (KiCad 9)
- Files
- Build & assembly notes
- Testing
- High-level BOM
- License & contributing

## Overview

The KiCad project collects multiple schematic sheets (amps, IO, meters) and a consolidated PCB layout. The top-level board title is "Output" and the project uses KiCad 9.

## Features

- Multi-sheet schematic setup (several module sheets).
- Main PCB file: `output_pcb.kicad_pcb` (KiCad 9 format).
- Mixed SMD and through-hole footprints likely used (3.5 mm jacks, headers, discrete parts).

## Quick start

1. Install KiCad 9 (this project was generated with KiCad 9).
2. Open the project: `kicad/output_pcb.kicad_pro`.
3. Inspect each schematic sheet and run ERC. Run PWR/CV checks before exporting fabrication files.

## Files

- `kicad/output_pcb.kicad_pro` — KiCad project file
- `kicad/output_pcb.kicad_sch` — top-level schematic (multi-sheet)
- `kicad/output_pcb.kicad_pcb` — PCB layout (KiCad 9)
- `kicad/output_pcb.kicad_prl` — PCB print/plot settings
- `kicad/hp_amp.kicad_sch` — high-pass / headphone amp (?) sheet
- `kicad/io_board.kicad_sch` — IO board sheet
- `kicad/line_amp.kicad_sch` — line amplifier sheet
- `kicad/rear_board.kicad_sch` — rear board / connector sheet
- `kicad/volume_meter.kicad_sch` — volume meter sheet

Note: open the `.kicad_sch` and `.kicad_pcb` files in KiCad to view full schematic hierarchy and footprints.

## Build & assembly notes

- Populate the PCB according to the schematic and footprint references. Observe polarized parts and IC orientations.
- Typical workflow: stencil/solder SMD parts first, then through-hole components (jacks, headers).
- Add decoupling capacitors close to op-amp or IC power pins; add bulk electrolytics on power rails if present.
- Verify connector/panel alignment (mounting holes, jack positions) before final assembly.

## Testing

1. With no inputs connected, apply power and verify rails at power pins (if applicable).
2. Apply known signals to input sections and confirm expected behaviour on outputs per schematic (audio/CV paths).
3. Use scope or audio probe to verify levels and check for noise or distortion.

## High-level BOM

This repository does not include a CSV BOM file. To generate a detailed BOM, open the project in KiCad and use the BOM generation/export plugin (CSV or custom script).

### Suggested quick BOM export

1. In KiCad Schematic Editor, run `Tools → Generate BOM` and choose your preferred BOM exporter.
2. Cross-check footprints in the PCB editor with the exported BOM.

## License & contributing

This project is distributed under the MIT license. See `LICENSE` for full text.

Contributions, issues, and pull requests are welcome. If you publish derived PCBs or panels, please credit the original author(s).

---
