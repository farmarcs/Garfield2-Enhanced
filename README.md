![Garfield 2 Enhanced](assets/banner.png)

# Garfield 2 Enhanced

![Patch version](https://img.shields.io/badge/patch-v0.1-F28C28?style=flat-square) ![Platform](https://img.shields.io/badge/platform-PS2-3055A5?style=flat-square) ![Emulator](https://img.shields.io/badge/emulator-PCSX2-2677C9?style=flat-square) ![Region](https://img.shields.io/badge/region-PAL%20Europe-555555?style=flat-square) ![Experimental](https://img.shields.io/badge/status-experimental-B58105?style=flat-square) ![CRC](https://img.shields.io/badge/CRC-627B8252-555555?style=flat-square)

**Unofficial graphical improvements and reverse engineering for Garfield 2 on PlayStation 2.**

[**Download patch**](patches/SLES-54172_627B8252.pnach) · [Installation](docs/INSTALLATION.md) · [Technical notes](docs/TECHNICAL.md) · [Compatibility](docs/COMPATIBILITY.md) · [Changelog](CHANGELOG.md) · [Português (Brasil)](README.pt-BR.md)

## No Bloom — Experimental v0.1

The first working patch disables the targeted bloom effect, reducing distracting halos and apparent ghosting seen in the scenes tested by the project author. No gameplay issues were reported during those tests; other glow effects may be affected. This is an experimental patch, not an exhaustive compatibility guarantee.

| Compatibility | Value |
| --- | --- |
| Game | Garfield 2 (Europe) |
| Emulator | PCSX2, with per-game PNACH patch support |
| Serial | `SLES-54172` |
| CRC | `627B8252` |

## Download and installation

[Download the PNACH file](patches/SLES-54172_627B8252.pnach) (open the file and select Download raw file).

1. Check the game's serial and CRC in PCSX2 game properties.
2. Place the downloaded file in your configured PCSX2 `patches` directory. Keep the exact filename. If a local file with the same name already exists, back it up and merge only the missing No Bloom section instead of overwriting it.
3. Open the game's properties, select **Patches**, and enable **No Bloom - Experimental v0.1**.
4. Start the game from a fresh boot. To undo, disable the patch and restart the game.

See the [full installation guide](docs/INSTALLATION.md) for troubleshooting and backup instructions.

## Development roadmap

| Feature | Status |
| --- | --- |
| No Bloom v0.1 | Author-tested, experimental |
| Tail Animation Fix | Investigation planned |
| Extended Draw Distance | Investigation planned |
| Improved LOD and texture transitions | Investigation planned |

The 50 FPS patch is a separate modification and is not included here. Its interaction with the tail animation remains under investigation.

## Visual comparisons

Original and patched screenshots will be added after review of matched scenes. No demonstration images are included in this initial package.

## RetroAchievements

This project has not received official approval from RetroAchievements or PCSX2. Technical compatibility does not establish Hardcore eligibility. Do not use experimental patches for competitive achievement runs pending official guidance. See [compatibility notes](docs/COMPATIBILITY.md).

## Feedback and credits

Project maintainer: **farmarcs**. Original PNACH credit: **Garfield2 Lab (analise experimental)**. Report reproducible issues through GitHub Issues when the repository becomes public; include your PCSX2 version, renderer, serial/CRC, enabled patches and steps to reproduce.

Independent fan project. No game ISO, BIOS, original executable or extracted game assets are distributed. Licensing is pending maintainer review.
