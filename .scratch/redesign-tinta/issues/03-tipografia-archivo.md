# 03: Tipografia Archivo em toda a página

**What to build:** O visitante lê a página inteira numa única família tipográfica, com títulos que
têm peso e aperto de cartaz. O texto passa a parecer um documento coerente em vez de uma colagem de
templates, e a hierarquia fica reconhecível sem precisar ler.

Esta fatia também estabelece o **papel visual de rótulo** — peso máximo, caixa alta, tracking largo
— que as fatias seguintes usam para substituir as pílulas coloridas por sinal tipográfico.

**Blocked by:** 01 (Camada de tokens TINTA e fim do esquema escuro).

**Status:** done

- [x] A página carrega uma única família tipográfica, em três pesos, reaproveitando a origem externa de fontes já usada — nenhuma nova dependência de rede.
- [x] As duas famílias tipográficas anteriores não são mais requisitadas nem referenciadas em lugar nenhum.
- [x] Títulos usam o peso máximo, com tracking de −3,5% e entrelinha apertada.
- [x] O corpo de texto lê 15 px sobre 1,55.
- [x] Existe um papel visual de rótulo — peso máximo, 13 px, caixa alta, tracking 8% — disponível para as fatias seguintes.
- [x] Os tamanhos de meio-passo herdados foram encaixados na escala do manual.
- [x] Títulos continuam respondendo à largura da tela; a página permanece legível e sem quebra no celular.
- [x] Nenhum título ou bloco de texto está centralizado.

## Comments

Implementado na branch `redesign-tinta`. Sem push.

O que mudou:

- **Fonte única.** `index.html` troca `Space Grotesk` + `Inter` por `Archivo:wght@400;600;900`
  na mesma origem (`fonts.googleapis.com` / `fonts.gstatic.com`, preconnects intactos) — a URL
  do Google devolve exatamente três `@font-face`, nenhuma nova dependência de rede. `--font-body`
  passa a `'Archivo'`; `--font-display` deixa de ser uma segunda família e vira alias de
  `--font-body`, mantido como seam do papel de título até o ticket 07 (mesma lógica dos degraus
  de raio no ticket 01).
- **Três pesos, e só três.** As declarações que usavam `500` e `700` foram encaixadas em `600`
  (intermediário) e `900` (título/rótulo). `body` declara `font-weight: 400` explícito. O CSS
  agora referencia apenas 400/600/900.
- **Títulos.** Todo heading em `--font-display` usa `font-weight: 900`,
  `letter-spacing: var(--tracking-tight)` e `line-height: var(--leading-tight)`. Os dois valores
  nasceram como token no ponto único de definição — `--tracking-tight: -0.035em` (o −3,5% do
  manual, não o −1,5% do arquivo de tokens; ver Further Notes do spec) e `--leading-tight: 1.1`
  — porque o aperto se repetia em ~12 regras e a próxima re-afinação seria uma varredura.
- **Corpo.** `body { font-size: 15px; line-height: 1.55 }`.
- **Rótulo.** Nova classe `.label` (900 / 13px / caixa alta / `letter-spacing: 0.08em`), no
  bloco compartilhado com `.section-eyebrow`. Fica disponível para as fatias 05/06 aplicarem no
  lugar das pílulas — ainda não há marcação que a consuma, é hook semeado de propósito.
- **Meio-passos.** 13,5 → 13 · 14,5 → 14 · 15,5 → 15 · 18,5 → 18 · 11,5 → 12. Cada meio-passo
  colapsa para o degrau inteiro mais próximo da escala; 11,5 sobe para o piso 12. Nenhum `N.5px`
  sobrou.
- **Fluidez e centralização.** Os quatro `clamp()` de título permanecem (só o teto 18,5 do
  `hero-lead` virou 18). Nenhum `text-align: center` novo; o único que existe segue sendo a regra
  de mobile do `.contact-mail`, que o ADR 0001 registra explicitamente como aceita.

Fora de escopo, revertido após o code review: o restyle do `.brand` do cabeçalho (assinatura é
o ticket 06) e a aplicação do papel de rótulo ao `.case-detail dt` (Trabalhos é o ticket 05).
Ambos voltaram ao peso `600` para não referenciar o `700` que saiu da folha.

Verificação: estática. A extensão do Chrome não estava conectada, então a página não foi aberta
em 1440/390 px, nem conferidos console, ícone da aba e quebra de título no celular — isso fica
para o José ver rodando, como no ticket 01. Conferido: chaves balanceadas; nenhum `Inter` /
`Space Grotesk` em HTML ou CSS; nenhum `N.5px`; pesos só em 400/600/900; a folha do Google
servindo as três faces de `fonts.gstatic.com`; os dois arquivos em 200 no servidor local.

Code review em dois eixos rodado antes do commit. Standards: sem violação de constraint
documentada; apontou o número mágico repetido (`-0.035em` / `1.1`) — endereçado com os tokens
`--tracking-tight` / `--leading-tight`. Spec: sem critério faltando; apontou os dois pontos de
escopo acima, revertidos.
