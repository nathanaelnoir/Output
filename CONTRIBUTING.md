# Contributing

Thanks for your interest in contributing to this KiCad project.

Please follow these guidelines to make collaboration smooth:

## Reporting issues
- Open an issue with a clear title and description of the problem.
- Include steps to reproduce, KiCad version (KiCad 9 preferred), and relevant screenshots or exported files.

## Pull requests
- Fork the repo and create a branch for your change.
- Keep each PR focused (one logical change per PR).
- Describe what you changed and why; include screenshots or exported outputs if relevant.
- Update `BOM.md` or documentation when parts, footprints, or board changes are made.

## Working with KiCad files
- This project uses KiCad 9. Open files under the `kicad/` directory in KiCad 9.
- Avoid unrelated reformatting of KiCad files. When editing schematics or PCB, explain the reason in the PR.
- Generated fabrication outputs (Gerbers, drill files) live in the `output/` folder — do not edit generated files by hand; regenerate them from the PCB when needed.

## Code style & commits
- Use small, atomic commits with descriptive messages.
- Do not change licensing or author attribution without agreement from maintainers.

## Testing
- Open the project in KiCad 9, run ERC on schematics and DRC on the PCB before submitting changes.

## License
By contributing you agree that your contributions will be licensed under the repository's MIT license.

If you're unsure about a change, open an issue first to discuss it.

Thank you — contributions are welcome!
