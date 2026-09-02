# 03: Tipografia Archivo em toda a página

**What to build:** O visitante lê a página inteira numa única família tipográfica, com títulos que
têm peso e aperto de cartaz. O texto passa a parecer um documento coerente em vez de uma colagem de
templates, e a hierarquia fica reconhecível sem precisar ler.

Esta fatia também estabelece o **papel visual de rótulo** — peso máximo, caixa alta, tracking largo
— que as fatias seguintes usam para substituir as pílulas coloridas por sinal tipográfico.

**Blocked by:** 01 (Camada de tokens TINTA e fim do esquema escuro).

**Status:** ready-for-agent

- [ ] A página carrega uma única família tipográfica, em três pesos, reaproveitando a origem externa de fontes já usada — nenhuma nova dependência de rede.
- [ ] As duas famílias tipográficas anteriores não são mais requisitadas nem referenciadas em lugar nenhum.
- [ ] Títulos usam o peso máximo, com tracking de −3,5% e entrelinha apertada.
- [ ] O corpo de texto lê 15 px sobre 1,55.
- [ ] Existe um papel visual de rótulo — peso máximo, 13 px, caixa alta, tracking 8% — disponível para as fatias seguintes.
- [ ] Os tamanhos de meio-passo herdados foram encaixados na escala do manual.
- [ ] Títulos continuam respondendo à largura da tela; a página permanece legível e sem quebra no celular.
- [ ] Nenhum título ou bloco de texto está centralizado.
