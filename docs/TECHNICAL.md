# Technical notes / Notas técnicas

## Source and integrity

- Target: Garfield 2 Europe; `SLES-54172`; PCSX2 CRC `627B8252`.
- Original supplied file preserved byte-for-byte; only the duplicate-download suffix `(1)` was removed from its filename.
- SHA-256: `e3a24b54d4ed9b4af0e9cfdc13b71d29e9057f0ead999e15ff4919426e79cc51`

```ini
patch=2,EE,00348440,word,30420000
```

| Field | Value |
| --- | --- |
| CPU | Emotion Engine (EE) |
| Address | `0x00348440` |
| Replacement word | `0x30420000` |
| MIPS decode | `andi $v0, $v0, 0x0000` |

The replacement instruction zeros `$v0`. The original patch description identifies the target as a bloom routine in the Zouna engine. Previous author testing reports a reduction of bloom-related halos and apparent ghosting. The precise original instruction, surrounding control flow, and independent reproduction are not included in the supplied file and are not asserted here.

A análise anterior utilizou GS Dumps e o executável do jogo, conforme o relato do projeto. A instrução substituta zera `$v0`. O código original ao redor do endereço e a desmontagem completa deverão ser recuperados antes de afirmar o mecanismo exato de desativação do efeito.

## Validation still needed

- Record emulator build, renderer, resolution, enabled patches and tested scenes.
- Capture matched before/after screenshots, including bright and dark scenes.
- Confirm unrelated glow effects, transitions, menus and gameplay are not adversely affected.
- Review original disassembly and document exact control flow.
- Repeat independently before any official submission.
