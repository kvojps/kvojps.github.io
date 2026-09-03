# 01: Esteira de trabalhos

**What to build:** a seção "Trabalhos" mostra os cases numa esteira horizontal
navegável para o lado — um case largo por vez, com prévia do próximo —,
reusando o padrão `.esteira` / `.esteira-controls` / `setupOverflowNav` da
seção de aplicativos, dentro das regras da TINTA.

**Blocked by:** None (can start immediately)

**Status:** done

## Acceptance criteria

- [x] `div.cases` vira
      `<div class="esteira esteira--cases" id="works-esteira" role="group"
      aria-label="Esteira de trabalhos" tabindex="0">`; os dois
      `article.case-card` ficam intocados dentro dela.
- [x] Antes da faixa entra `div.esteira-controls#works-esteira-controls`
      (`hidden`) com dois `button.esteira-nav` (`--prev` / `--next`), ids
      `works-esteira-prev` / `works-esteira-next`, `aria-label` "Trabalhos
      anteriores" / "Próximos trabalhos", com os SVGs de chevron da esteira de
      apps.
- [x] CSS novo só para a largura do card:
      `.esteira--cases > .case-card { flex: 0 0 92%; scroll-snap-align: start }`
      e `@media (max-width: 800px) { .esteira--cases > .case-card { flex-basis:
      88% } }`. A regra morta `.cases { display: grid; gap: 24px }` sai.
- [x] `.case-card` (grid interno de 2 colunas), `.case-card:hover`, a
      alternância `.case-card:nth-child(even)` e o media query de 800px que
      colapsa o card em 1 coluna permanecem.
- [x] Nenhum bloco de `.esteira-controls` / `.esteira-nav` é copiado — os
      seletores genéricos já servem. Nenhum `:focus`/`outline` próprio.
- [x] No script, uma terceira instância de `setupOverflowNav` (após a da
      esteira de apps), guardada por `if (worksEsteira)`: `step()` = largura do
      primeiro `.case-card` visível `+ 16`, fallback `clientWidth`;
      `toggle(on)` = `worksControls.hidden = !on`; `smooth()` =
      `!reduceMotion.matches`. Sem integração de filtro.
- [x] `.case-card` sai do seletor do `IntersectionObserver` de reveal
      (`"main > section, .service-card, .case-card"` →
      `"main > section, .service-card"`); o comentário do observer passa a
      citar `.app-card` e `.case-card`. A `<section id="trabalhos">` continua
      revelando via `main > section`.
- [x] O comentário `PRÓXIMO PASSO` em `#trabalhos` perde a instrução "a partir
      do terceiro case, adote a esteira" e mantém só: duplicar um
      `<article class="case-card">` por projeto, alternância de lado
      automática, dica do `<dt>O resultado</dt>`.
- [x] `CONTEXT.md` (### Elementos, verbete Esteira) e
      `docs/adr/0001-direcao-tinta.md` (## Padrões de interação nomeados): a
      frase "quando 'Trabalhos' passar de dois cases, adota a esteira" passa a
      registrar que a adoção foi feita.
- [x] Os controles seguem a TINTA: Fio, raio zero, sem sombra; nenhuma quinta
      cor entra na paleta.
- [x] Console do navegador sem erros; nenhuma imagem falhando ao carregar. —
      verificação manual delegada ao José (ver protocolo no `spec.md`).

## Verification

Protocolo de verificação manual completo em `../spec.md` (seção "Testing
Decisions"). Em resumo: servir em 1440 px e 390 px; a esteira rola e encaixa um
case por vez com a prévia do próximo; controles por teclado com foco visível;
movimento reduzido pula a rolagem suave; abaixo de 800 px o case colapsa em 1
coluna; esquema escuro não muda nada; contagem de vermelho da seção inalterada;
regressão da esteira de apps, do carrossel de filtros e do modal.

`node --check` no script embutido; chaves do CSS balanceadas; nenhuma
referência pendente a `.cases`; os dois arquivos servindo 200 em servidor
local.

## Comments

Implementado na branch `feat/esteira-trabalhos`, sem push.

**HTML (`index.html`).** A `<div class="cases">` virou
`<div class="esteira esteira--cases" id="works-esteira" role="group"
aria-label="Esteira de trabalhos" tabindex="0">`; os dois `<article
class="case-card">` seguem intocados dentro dela e o `</div>` de fechamento é o
mesmo. Antes da faixa entrou `<div class="esteira-controls"
id="works-esteira-controls" hidden>` com dois `<button class="esteira-nav">`
(`#works-esteira-prev` / `#works-esteira-next`, `--prev` / `--next`), reusando
os mesmos SVGs de chevron da esteira de apps. O comentário `PRÓXIMO PASSO`
perdeu o parágrafo "a partir do terceiro case, pare de empilhar: adote a
esteira" (já não se aplica) e passou a dizer que o `case-card` é filho direto da
`.esteira`.

**CSS (`style.css`).** Saiu a regra morta `.cases { display: grid; gap: 24px }`.
Entrou só a largura do card: `.esteira--cases > .case-card { flex: 0 0 92%;
scroll-snap-align: start }` e, em `@media (max-width: 800px)`, `flex-basis: 88%`.
A base `.esteira` (flex, `overflow-x: auto`, `scroll-snap-type: x mandatory`,
`gap: 16px`, scrollbar oculta, `scroll-behavior: smooth` sob movimento
não-reduzido) e os blocos genéricos `.esteira-controls` / `.esteira-nav` (este
compartilhado com `.filter-nav` na seção "Filter bar") já serviam — nada
copiado. `.case-card` (grid interno de 2 colunas), `:hover`, `nth-child(even)` e
o media query de 800px que colapsa em 1 coluna ficaram como estavam. Nenhum
`:focus`/`outline` próprio, como no ticket 04.

**Script (`index.html`).** Terceira instância de `setupOverflowNav`, logo após a
da esteira de apps, guardada por `if (worksEsteira)`: `scroller`
`#works-esteira`; `step()` mede a largura do primeiro `.case-card` visível `+
16` (o `gap`), com `clientWidth` de fallback; `toggle(on)` faz
`worksControls.hidden = !on`; `smooth()` é `!reduceMotion.matches`. Sem filtro
de categoria em "Trabalhos", então nenhuma fiação extra (ao contrário da esteira
de apps). `.case-card` saiu do seletor do `IntersectionObserver` de reveal
(`"main > section, .service-card, .case-card"` → `"main > section,
.service-card"`) — mesmo motivo do `.app-card` no ticket 04: numa faixa
horizontal os cards nascem fora do viewport e ficariam presos em `opacity: 0`. A
`<section id="trabalhos">` continua no seletor via `main > section`, então o
fade da seção inteira ao rolar é preservado; o comentário do observer passou a
citar os dois.

**Glossário e registro.** `CONTEXT.md` (verbete **Esteira**) ganhou "Usada nas
seções de aplicativos e de trabalhos". `docs/adr/0001-direcao-tinta.md` (##
Padrões de interação nomeados): a frase condicional "quando 'Trabalhos' passar
de dois cases, adota a esteira" virou o registro de que "Trabalhos" já a adota
(esforço `esteira-trabalhos`), um case largo por vez, antecipada ainda com dois
cases.

**Verificação.** O repo não tem runner nem build. `node --check` no script
embutido passa; chaves do CSS balanceadas (242/242); aninhamento de tags do
`index.html` balanceado (parser `html.parser`); nenhuma referência pendente à
classe `.cases`. A extensão do Chrome não estava conectada nesta sessão, então o
protocolo manual do `spec.md` — servir em 1440 px e 390 px, console sem erro,
esteira rolando e encaixando um case por vez com a espia do próximo, controles
por teclado com foco visível, movimento reduzido pulando a rolagem suave,
colapso em 1 coluna abaixo de 800 px, esquema escuro inalterado, contagem de
vermelho da seção, e a regressão da esteira de apps / carrossel de filtros /
modal — fica para o José antes do merge, como nos tickets 01–04.
