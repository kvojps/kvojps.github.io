# 04: Esteira de aplicativos

**What to build:** a seção de aplicativos mostra os quatro apps numa esteira horizontal navegável para o lado, sem o botão de expandir, com o filtro de categoria intacto e dentro das regras da TINTA.

**Blocked by:** None (can start immediately)

**Status:** done

- [x] Os quatro cards de app ficam numa faixa horizontal com encaixe de rolagem; o botão "Ver os N apps" e sua lógica de expandir/colapsar saem do script.
- [x] Controles anterior/próximo rolam a esteira por uma largura de card; são alcançáveis por teclado e mantêm o foco visível.
- [x] Os controles são tratados como Fio (contorno em divisor ou tinta), sem canto arredondado e sem sombra; nenhuma quinta cor entra na paleta.
- [x] O filtro de categoria continua mostrando e escondendo os cards certos dentro da esteira e segue sendo o Acento da seção.
- [x] A navegação de transbordo dos botões de filtro (o "carrossel" que já existe) continua funcionando, sem mudança.
- [x] A rolagem suave da esteira só ocorre sob preferência de movimento não-reduzido.
- [x] No desktop aparecem cerca de 2,5 cards; no mobile cerca de 1,15 (espia o próximo).
- [x] "esteira" entra no glossário, distinta de "carrossel"; o padrão ganha uma linha no registro de decisão da TINTA.
- [x] Console do navegador sem erros; nenhuma imagem falhando ao carregar. — verificação manual delegada ao José (ver Comments).

## Comments

Implementado na branch `redesign-tinta`, sem push.

**HTML (`index.html`).** A `<div class="apps-grid" id="apps-grid">` virou
`<div class="esteira" id="apps-esteira" role="group" aria-label="Esteira de aplicativos"
tabindex="0">`; os quatro `<article class="app-card">` seguem intocados dentro dela. O
`<button class="apps-more" id="apps-more">` ("Ver os 4 apps") saiu por completo. Antes da
esteira entrou `<div class="esteira-controls" id="apps-esteira-controls" hidden>` com dois
`<button class="esteira-nav">` (`#apps-esteira-prev` / `#apps-esteira-next`), reusando os mesmos
SVGs de chevron do carrossel de filtros. A nota de código da seção "Trabalhos" ganhou a linha
mandando adotar a esteira a partir do terceiro case.

**CSS (`style.css`).** Saíram `.apps-grid` (+ media 1040), `.apps-more` (base + todo o bloco
`@media (max-width: 560px)` com `.apps-grid.is-collapsed`) e as três regras de
`transition-delay` em `.apps-grid > .app-card:nth-child(...)` (as de `.services-grid`
permanecem). Entraram `.esteira` (flex, `overflow-x: auto`, `scroll-snap-type: x mandatory`,
scrollbar oculta), `.esteira > .app-card` com `flex-basis` por breakpoint — `~2,5` cards
acima de 1040 px, `~1,8` até 1040, `87%` (≈1,15, espia o próximo) até 560 —, e `.esteira-controls`.
Os controles `.esteira-nav` **entraram nos próprios seletores de `.filter-nav`** (bloco base,
`:hover`, `:disabled`, `svg`) em vez de um bloco copiado — mesmo tratamento de Fio (`border: 1px
solid var(--border)`, `border-radius: var(--radius-sm)` = 0, sem sombra, hover transitório ao
sinal). `.esteira-nav:active` entrou na lista de touch feedback. A rolagem suave fica em
`@media (prefers-reduced-motion: no-preference) { .esteira { scroll-behavior: smooth } }`.

**Script (`index.html`).** Removidos `appsGrid`, `appsMore`, `expandApps()` e o bloco
`if (cards.length > 2) { ... }`. O carrossel de filtros e a esteira agora compartilham um
`setupOverflowNav({ scroller, prev, next, step, toggle, smooth })` — a lógica de transbordo /
`disabled` nas pontas / fiação de eventos, que estava duplicada, virou uma função; cada uso passa
seu `step()` (dois botões vs. uma largura de card), seu `toggle()` (esconder as duas setas vs.
esconder `#apps-esteira-controls` em bloco) e seu `smooth()` (`true` no filtro, `!reduceMotion`
na esteira). O comportamento do carrossel de filtros é bit-a-bit o de antes — só saiu de
`stepFilters` / `updateFilterNav` nomeados para a fábrica. O handler de filtro ganhou
`esteira.scrollTo({ left: 0, behavior: "auto" })` (reset instantâneo, sem herdar o
`scroll-behavior: smooth` do CSS) e a chamada ao `update` devolvido pela fábrica. `.app-card`
saiu do seletor do `IntersectionObserver` de reveal — na esteira os cards nascem fora do viewport
na horizontal e ficariam presos em `opacity: 0`; o antigo `expandApps` já forçava `is-visible`
pelo mesmo motivo.

**Glossário e registro.** `CONTEXT.md` ganhou o termo **Esteira** em "### Elementos", com a
distinção explícita do carrossel ("a esteira move conteúdo, o carrossel move controles"), sem
literal de cor nem medida. `docs/adr/0001-direcao-tinta.md` ganhou a seção "## Padrões de
interação nomeados" registrando a esteira, o nome escolhido e a orientação de "Trabalhos"
adotá-la a partir do terceiro case.

**Code review (Standards + Spec).** Rodou nos dois eixos. Sem violação dura. Aplicado: (1) o
bloco CSS `.esteira-nav` era cópia verbatim de `.filter-nav` → virou seletor compartilhado; (2)
`updateEsteiraNav`/`stepEsteira` eram a mesma forma de `updateFilterNav`/`stepFilters`, e o spec
pede "reaproveita o padrão de navegação" → extraído `setupOverflowNav` que serve os dois; (3)
mistura de registro `apps-track` (EN) × `esteira-*` (PT) → o trilho virou `.esteira` /
`#apps-esteira`, ids namespaced `apps-esteira-*`; (4) `scrollTo` sem `behavior` no reset de
filtro animava sob movimento normal → fixado para `"auto"`. Não aplicado, por decisão: nenhum
`:focus`/`outline` próprio para `.esteira-nav` nem para o `.esteira[tabindex]` — o repo inteiro
depende do anel de foco padrão do navegador (não há `outline: none` em lugar nenhum), e um estilo
de foco só para a esteira quebraria a consistência com `.filter-nav`. A linha na nota de
"Trabalhos" e a seção no ADR foram lidas como escopo deste ticket (critério 8 pede a linha no
registro; o spec-pai pede a nota de "Trabalhos" em US30).

**Verificação.** O repo não tem runner nem build (decisão herdada da TINTA). `node --check` no
script embutido passa; chaves do CSS balanceadas (241/241); nenhuma referência pendente a
`apps-grid` / `apps-more` / `is-collapsed` / `apps-track`; os dois arquivos servem 200 em
servidor local. A
extensão do Chrome não estava conectada nesta sessão, então o protocolo manual do spec — servir
em 1440 px e 390 px, console sem erro e sem imagem falhando, a esteira rolando e encaixando, o
filtro mostrando os cards certos, os controles por teclado com foco visível, movimento reduzido
pulando a rolagem suave, contagem de vermelho seção a seção, altura antes/depois — fica para o
José antes do merge, como nos tickets 01–03.
