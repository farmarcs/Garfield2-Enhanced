# Installation / Instalação

## English

**Requirements:** your own game dump of Garfield 2 Europe (`SLES-54172`, `627B8252`), and a PCSX2 build supporting labeled per-game PNACH patches.

1. Stop the emulation. In the game list, right-click Garfield 2 and open Properties. Check the serial and CRC; do not install on a different revision.
2. Download [the PNACH file](../patches/SLES-54172_627B8252.pnach) using the raw download option. The name must be `SLES-54172_627B8252.pnach`, without `.txt` or a duplicate-download suffix.
3. Locate the configured `patches` folder in your PCSX2 data directory (check Settings > Folders if available). On a typical Windows setup it may be under `Documents\PCSX2\patches`; portable installations and customized paths differ.
4. If a local PNACH with the same name exists, back it up. Append the entire labeled No Bloom section (from `[No Bloom - Experimental v0.1]` onward) only if it is not already present. Otherwise copy the supplied file into the folder. Do not edit the built-in `resources/patches.zip`.
5. Open the game's Properties > Patches and enable the labeled No Bloom patch. Reopen properties or restart PCSX2 if the label is missing. Boot the game normally rather than loading a savestate.
6. Compare an affected scene with the patch disabled and enabled, keeping renderer and settings constant.

**Rollback:** stop emulation, uncheck No Bloom and boot again. If removing the file, restore any previous local file from backup or remove only the inserted section. Keep your other patches intact.

**Troubleshooting:** verify serial/CRC, the real patches directory, filename extension and the patch checkbox. Other patches may conflict. Test No Bloom alone, with achievements disabled for experiments. If unexpected glow or gameplay changes occur, disable it and report the scene and settings.

## Português (Brasil)

**Requisitos:** sua própria cópia de Garfield 2 Europa (`SLES-54172`, `627B8252`) e uma versão do PCSX2 compatível com patches PNACH identificados por nome.

1. Encerre a emulação. Na lista de jogos, clique com o botão direito em Garfield 2, abra Propriedades e confirme serial e CRC. Não instale em outra revisão.
2. Baixe [o PNACH](../patches/SLES-54172_627B8252.pnach) pela opção de download do arquivo bruto. O nome precisa ser exatamente `SLES-54172_627B8252.pnach`, sem `.txt` ou sufixo de download duplicado.
3. Localize a pasta `patches` configurada no PCSX2 (verifique Configurações > Pastas, se disponível). No Windows, pode ficar em `Documents\PCSX2\patches`; instalações portáteis e caminhos personalizados podem ser diferentes.
4. Se já houver um PNACH local com o mesmo nome, faça backup. Acrescente a seção completa do No Bloom (a partir de `[No Bloom - Experimental v0.1]`) somente se ela ainda não existir. Caso contrário, copie o arquivo fornecido para a pasta. Não altere `resources/patches.zip`.
5. Abra Propriedades do jogo > Patches e marque No Bloom. Se não aparecer, reabra as propriedades ou reinicie o PCSX2. Inicie o jogo normalmente, sem carregar save state.
6. Compare uma cena afetada com o patch desligado e ligado, mantendo renderizador e demais configurações iguais.

**Desinstalação:** encerre a emulação, desmarque No Bloom e inicie novamente. Se remover o arquivo, restaure o backup ou remova somente a seção acrescentada, preservando os outros patches.

**Problemas:** confira o serial/CRC, pasta real, extensão do arquivo e ativação. Teste o No Bloom isoladamente e sem conquistas ativas durante os experimentos. Desative caso surjam alterações indesejadas e informe a cena e configurações usadas.

Reference / Referência: [PCSX2 — Writing Patches](https://pcsx2.net/docs/advanced/writing-patches/).
