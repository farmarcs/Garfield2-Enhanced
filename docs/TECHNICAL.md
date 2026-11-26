# Technical notes / Notas técnicas

[English](#english) · [Português (Brasil)](#português-brasil)

## English

### Target and integrity

- Garfield 2 (Europe), serial `SLES-54172`, PCSX2 CRC `627B8252`.
- File: [SLES-54172_627B8252.pnach](../patches/SLES-54172_627B8252.pnach), 339 bytes.
- SHA-256: `e3a24b54d4ed9b4af0e9cfdc13b71d29e9057f0ead999e15ff4919426e79cc51` (recomputed from the repository file on 2026-11-26).
- The original supplied file remains unchanged in content. Only its duplicate-download filename suffix was removed at initial import.

```ini
patch=2,EE,00348440,word,30420000
```

In PCSX2's PNACH syntax, placement 2 combines startup and continuous application; EE identifies the Emotion Engine and word specifies a 32-bit write.

### Observed original control flow

The project author's PCSX2 EE debugger capture (2026-11-26) showed the following instructions before enabling the patch. Register names are normalized here for readability.

```asm
0034843C  8E220754  lw    v0,0x754(s1)
00348440  30420800  andi  v0,v0,0x0800
00348444  10400004  beq   v0,zero,0x00348458
00348448  00000000  nop
0034844C  0220202D  daddu a0,s1,zero
00348450  0C0D2E08  jal   0x0034B820
00348454  0200282D  daddu a1,s0,zero
```

| State | EE address | Word | Decoded instruction |
| --- | --- | --- | --- |
| Original | `00348440` | `30420800` | `andi v0,v0,0x0800` |
| No Bloom | `00348440` | `30420000` | `andi v0,v0,0x0000` |

The original instruction tests bit 11 of the word loaded from offset 0x754. The replacement always produces zero in v0, so the conditional branch is taken (after the nop delay slot), skipping the call at 0x00348450. The call's association with the targeted bloom effect is supported by the observed visual changes. This does not establish the complete semantics of the callee or the exact internal bloom algorithm.

### Author validation — 2026-11-26

| Item | Observation |
| --- | --- |
| Environment | Windows; PCSX2 v2.9.196 |
| Renderer | Direct3D 12; 3x internal resolution shown in gameplay captures |
| Manual debugger test | Original word restored and patched word applied reversibly during one emulation session |
| External test | PINE IPC read/write of the same EE address; matching serial/CRC; visual toggling reported successful |
| Visual evidence | Three gameplay comparison pairs: castle staircase, armour hall and locked door |
| Frame rate | 50 FPS and 100% emulation speed visible in separate live-toggle test captures; not a performance benchmark |

See the [visual gallery](../README.md#visual-comparisons). The author also reported successful PNACH testing across multiple scenes. The external testing tool is separate and is neither distributed nor required here.

### Limits and further validation

- Only the specified game revision and the author-tested environment are documented.
- The comparisons are gameplay frames, not identical animation frames.
- Some luminous effects remain visible; unrelated effects may also be affected.
- Full-game coverage, independent reproduction, other renderers/builds, and comprehensive combined-patch tests remain pending.
- The patch is experimental, not an official PCSX2 or RetroAchievements submission or approval. Test offline with achievements disabled.

---

## Português (Brasil)

### Alvo e integridade

- Garfield 2 (Europa), serial `SLES-54172`, CRC do PCSX2 `627B8252`.
- Arquivo: [SLES-54172_627B8252.pnach](../patches/SLES-54172_627B8252.pnach), 339 bytes.
- SHA-256: `e3a24b54d4ed9b4af0e9cfdc13b71d29e9057f0ead999e15ff4919426e79cc51` (recalculado a partir do arquivo do repositório em 26/11/2026).
- O conteúdo do PNACH original permanece intacto. Na importação inicial, foi removido apenas o sufixo de download duplicado do nome do arquivo.

```ini
patch=2,EE,00348440,word,30420000
```

Na sintaxe PNACH do PCSX2, o tipo de aplicação 2 combina a inicialização e a aplicação contínua; EE identifica o Emotion Engine e word indica uma escrita de 32 bits.

### Fluxo de controle observado

A captura do depurador EE do PCSX2 feita pelo autor em 26/11/2026 mostrou as instruções originais reproduzidas na seção em inglês.

| Estado | Endereço EE | Palavra | Instrução decodificada |
| --- | --- | --- | --- |
| Original | `00348440` | `30420800` | `andi v0,v0,0x0800` |
| No Bloom | `00348440` | `30420000` | `andi v0,v0,0x0000` |

A instrução original testa o bit 11 da palavra carregada a partir do deslocamento 0x754. A substituição força v0 a zero, fazendo com que o desvio condicional seja tomado (após a instrução nop no delay slot) e a chamada em 0x00348450 seja ignorada. A associação dessa chamada ao bloom investigado é sustentada pelas alterações visuais observadas. Isso não comprova toda a semântica da função chamada nem o algoritmo interno do bloom.

### Validação do autor — 26/11/2026

| Item | Observação |
| --- | --- |
| Ambiente | Windows; PCSX2 v2.9.196 |
| Renderizador | Direct3D 12; resolução interna 3x exibida nas capturas de gameplay |
| Teste manual | Aplicação e restauração reversíveis da instrução pelo depurador na mesma sessão |
| Teste externo | Leitura e escrita no mesmo endereço EE via PINE IPC, com serial/CRC conferidos; alternância visual confirmada pelo autor |
| Evidência visual | Três pares comparativos: escadaria, salão das armaduras e porta com cadeado |
| Taxa de quadros | 50 FPS e velocidade de emulação de 100% visíveis em capturas separadas do teste ao vivo; não constituem benchmark |

Consulte a [galeria visual](../README.pt-BR.md#comparações-visuais). O autor também relatou testes bem-sucedidos do PNACH em diversas cenas. A ferramenta externa de testes é independente, não está distribuída aqui e não é necessária para o patch.

### Limitações e validação adicional

- Somente a revisão indicada e o ambiente testado pelo autor estão documentados.
- As capturas são quadros de gameplay, não quadros idênticos de animação.
- Alguns efeitos luminosos permanecem visíveis; outros efeitos podem ser afetados.
- Cobertura integral do jogo, reprodução independente, outros renderizadores/versões e testes abrangentes com patches combinados permanecem pendentes.
- Patch experimental, sem submissão ou aprovação oficial do PCSX2 ou RetroAchievements. Teste offline e com conquistas desativadas.

---

References / Referências: [PCSX2 — Writing Patches](https://pcsx2.net/docs/advanced/writing-patches/) · [PCSX2 — Patch definitions](https://github.com/PCSX2/pcsx2/blob/master/pcsx2/Patch.h) · [Compatibility / Compatibilidade](COMPATIBILITY.md).
