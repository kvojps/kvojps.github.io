# Esteira na seção "Trabalhos"

Status: ready-for-agent

## Problem Statement

A seção `#trabalhos` (`index.html`) empilha os `article.case-card` num
`div.cases` (grid vertical). Cada case é um cartão largo, de duas colunas
(imagem | "O desafio / O que foi feito"); a cada novo projeto a seção cresce
mais um cartão de altura inteira.

O padrão para "uma coleção que não cabe empilhada" já existe neste site: a
**esteira** — faixa horizontal com encaixe de rolagem — usada na seção de
aplicativos (esforço `enxugar-conteudo`, ticket 04). O código já previa a
migração: o comentário `PRÓXIMO PASSO` em `#trabalhos` e o ADR 0001 dizem
"quando 'Trabalhos' passar de dois cases, adota a mesma esteira".

José quer antecipar isso: adotar a esteira agora, ainda com dois cases, para a
seção parar de crescer empilhada e para os dois usos de faixa horizontal do
site seguirem o mesmo padrão.

## Solution

A `div.cases` vira uma **esteira**, reusando o que já existe — a regra base
`.esteira`, o bloco `.esteira-controls`, os botões `.esteira-nav` e o helper JS
`setupOverflowNav`. Nenhum CSS ou JS de base é duplicado.

Formato escolhido (confirmado com José): **um case largo por vez**. O
`.case-card` mantém o layout interno de duas colunas; a esteira mostra um case
inteiro com uma prévia do próximo espiando na borda, e os controles
anterior/próximo avançam um case. É a mesma mecânica da esteira de apps, só com
a largura de card ajustada ao conteúdo mais largo dos cases.

Não há filtro de categoria em "Trabalhos", então a esteira entra sem a fiação
extra que a de apps tem para o filtro.

Ao final, "Trabalhos" percorre-se para o lado como "Aplicativos", os controles
seguem a TINTA (Fio, sem canto, sem sombra), e o glossário/ADR passam a
descrever a esteira como padrão de fato das duas seções.

## User Stories

### Visitante

1. Como visitante avaliando os trabalhos, quero percorrer os cases numa faixa
   horizontal, para ver os projetos sem rolar uma pilha de cartões altos.
2. Como visitante, quero ver um case inteiro por vez com uma prévia do próximo,
   para não perder o formato "O desafio / O que foi feito" que já conheço.
3. Como visitante que navega por teclado, quero alcançar e operar a esteira
   pelo Tab e pelas setas, para não depender do mouse.
4. Como visitante com movimento reduzido no sistema, quero que a esteira role
   sem animação suave, para navegar sem desconforto.
5. Como visitante, quero que os controles da esteira sigam a marca — em Fio,
   sem canto arredondado, sem sombra — para a página continuar parecendo um
   documento.
6. Como visitante no celular, quero um case por tela com a espia do próximo,
   para percorrer os projetos com o polegar.

### José (dono da marca)

7. Como dono da marca, quero que a esteira de "Trabalhos" não introduza
   nenhuma quinta cor nem sombra, para a paleta continuar fechada nas quatro do
   manual.
8. Como dono da marca, quero que os dois cases atuais fiquem intocados no
   conteúdo — texto, imagem, chips, botão — para este trabalho mexer só no
   invólucro.
9. Como dono da marca, quero ver a página rodando antes de aprovar, para julgar
   a mudança com meus próprios olhos.
10. Como dono da marca, quero que o trabalho fique numa branch até eu decidir
    publicar, para não expor uma versão pela metade.

### Quem mexer no código depois

11. Como pessoa que for somar um terceiro case, quero só duplicar um
    `<article class="case-card">` — a esteira cuida do resto — e uma nota
    dizendo isso no lugar da antiga instrução de "empilhe até o terceiro".
12. Como pessoa que abrir o repo depois, quero o glossário e o ADR dizendo que
    a esteira é o padrão das duas seções, para não achar que "Trabalhos" ainda
    empilha.

## Implementation Decisions

### Escopo e módulos tocados

- Uma branch nova a partir de `main`; sem push até José ver rodando.
- Módulos afetados:
  - `index.html` — marcação da seção `#trabalhos` (troca do container,
    inserção dos controles, atualização do comentário `PRÓXIMO PASSO`) e o
    bloco de script embutido (uma terceira instância de `setupOverflowNav`;
    `.case-card` sai do seletor do `IntersectionObserver` de reveal).
  - `style.css` — bloco "Client cases": remoção da regra morta `.cases` e
    entrada de um seletor de largura para `.esteira--cases > .case-card`.
  - `CONTEXT.md` e `docs/adr/0001-direcao-tinta.md` — a linha "quando
    'Trabalhos' passar de dois cases, adota a esteira" passa a registrar que a
    adoção foi feita.

### A esteira

- `div.cases` vira
  `<div class="esteira esteira--cases" id="works-esteira" role="group"
  aria-label="Esteira de trabalhos" tabindex="0">`. Os dois
  `article.case-card` seguem **intocados** dentro dela.
- Antes da faixa entra `div.esteira-controls#works-esteira-controls` com
  atributo `hidden`, contendo dois `button.esteira-nav` (`--prev` / `--next`),
  ids `works-esteira-prev` / `works-esteira-next`, `aria-label` "Trabalhos
  anteriores" / "Próximos trabalhos", com os mesmos SVGs de chevron da esteira
  de apps.
- CSS novo, só a largura do card (a base `.esteira` — flex, `overflow-x`,
  `scroll-snap`, `gap: 16px`, scrollbar oculta, `scroll-behavior: smooth` sob
  movimento não-reduzido — já serve):

  ```css
  .esteira--cases > .case-card {
    flex: 0 0 92%;            /* um case + prévia do próximo */
    scroll-snap-align: start;
  }
  @media (max-width: 800px) {
    .esteira--cases > .case-card { flex-basis: 88%; }
  }
  ```

- `.case-card` (layout interno de duas colunas), `.case-card:hover`, a
  alternância `.case-card:nth-child(even)` e o media query de 800px que colapsa
  o card em uma coluna **permanecem**.
- `.esteira-controls` e `.esteira-nav` são genéricos e não mudam. Nenhum
  `:focus`/`outline` próprio — o site inteiro depende do anel de foco padrão do
  navegador, como decidido no ticket 04.

### O script

- Terceira instância de `setupOverflowNav`, logo após a da esteira de apps,
  guardada por `if (worksEsteira)`:
  - `scroller`: `#works-esteira`; `prev`/`next`: `#works-esteira-prev` /
    `#works-esteira-next`.
  - `step()`: largura do primeiro `.case-card` visível `+ 16` (o `gap`), com
    `worksEsteira.clientWidth` como fallback — mesma forma da esteira de apps.
  - `toggle(on)`: `worksControls.hidden = !on`.
  - `smooth()`: `!reduceMotion.matches`.
- Sem filtro de categoria em "Trabalhos" → nenhuma integração extra, nenhum
  `updateEsteiraNav()` para rechamar.
- `.case-card` sai do seletor do `IntersectionObserver` de reveal
  (`"main > section, .service-card, .case-card"` →
  `"main > section, .service-card"`). Mesmo motivo pelo qual `.app-card` já
  ficou de fora no ticket 04: numa faixa horizontal os cards fora do viewport
  nunca disparariam o observer e ficariam presos em `opacity: 0`. A
  `<section id="trabalhos">` continua no seletor via `main > section`, então o
  fade da seção inteira ao rolar é preservado. O comentário do observer passa a
  citar `.app-card` e `.case-card`.

### "Trabalhos" com dois cases

- A esteira entra mesmo com só dois cases. Com `flex-basis: 92%`, dois cases
  transbordam o container, então os controles aparecem já agora. Se em algum
  breakpoint não houver transbordo, `setupOverflowNav` esconde o bloco de
  controles sozinho — a seção fica visualmente como hoje.
- O comentário `PRÓXIMO PASSO` perde a instrução "a partir do terceiro case,
  pare de empilhar: adote a esteira" (já não se aplica) e mantém só: duplicar
  um `<article class="case-card">` por projeto, a alternância de lado
  automática, e a dica do `<dt>O resultado</dt>`.
- A linha do ADR 0001 e a do glossário que condicionavam a esteira ao terceiro
  case passam a dizer que "Trabalhos" já a adota.

## Testing Decisions

**Nenhuma seam automatizada é introduzida. A verificação é manual.** Herdado da
TINTA e do ticket 04, pela mesma razão: o repo não tem gerenciador de pacotes,
runner nem CI — o site são dois arquivos servidos estaticamente.

**O que importa verificar:** comportamento externo — a esteira rola e encaixa,
os controles respondem ao teclado com foco visível, o movimento reduzido pula a
rolagem suave, e a esteira de apps / o carrossel de filtros / o modal seguem
intactos. Uma varredura textual sobre HTML/CSS passaria com o layout quebrado.

### Protocolo de verificação manual

1. Servir a página localmente e abrir em 1440 px e em 390 px de largura.
2. Console do navegador sem erros; nenhuma imagem falhando ao carregar.
3. "Trabalhos": a esteira rola para o lado e encaixa um case por vez; a prévia
   do próximo aparece na borda. Os controles anterior/próximo rolam um case;
   "anterior" fica desabilitado no início e "próximo" no fim.
4. Alcançar a esteira e os controles por Tab; rolar pelas setas do teclado; o
   indicador de foco fica visível em todos os alvos.
5. Emular movimento reduzido: a esteira rola sem animação suave e as entradas
   por rolagem aparecem sem transição.
6. Abaixo de 800 px: cada case colapsa em uma coluna e a faixa mostra ~um case
   com a espia do próximo.
7. Emular esquema escuro: a página não muda.
8. Contar os elementos vermelhos da seção contra a tabela de orçamento da
   TINTA — a esteira não acrescentou nenhum.
9. Regressão: a esteira de apps (`#apps-esteira`), o carrossel dos botões de
   filtro e o modal de detalhes continuam funcionando.

## Out of Scope

- **Conteúdo dos cases.** Texto, imagem, chips e botão "Visitar site" dos dois
  cases atuais não mudam.
- **Redesenhar o `.case-card` num formato compacto.** O card fica largo, um por
  tela; a alternativa "cards estilo apps, ~2 por tela" foi descartada por José.
- **Formato "O desafio / O que foi feito"** e o `<dt>O resultado</dt>` sugerido
  — seguem como estão.
- **Teste automatizado e CI.** Decidido acima.
- **Publicar.** O trabalho fica na branch. O merge para `main` — que publica no
  ar — é decisão de José depois de ver rodando.
- **`aside.cta-inline`** ao fim da seção — fica como está.

## Further Notes

- A esteira já é padrão nomeado no repo (CONTEXT.md "### Elementos", ADR 0001
  "## Padrões de interação nomeados"). Este trabalho não cria um padrão novo —
  aplica o existente e corrige as duas linhas que ainda diziam "Trabalhos vai
  adotar quando passar de dois cases".
- O ganho não é de rolagem enorme com dois cases — é tirar o crescimento
  empilhado e unificar a interação das duas seções. O ganho real aparece quando
  entrar o terceiro case.
- O número mágico `+ 16` no `step()` do JS depende de a esteira usar
  `gap: 16px` (o valor da base `.esteira`). Se algum dia a esteira de trabalhos
  usar outro `gap`, ajustar o `step()`.
