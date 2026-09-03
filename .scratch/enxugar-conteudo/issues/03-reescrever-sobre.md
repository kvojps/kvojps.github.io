# 03: Reescrever a seção "Sobre"

**What to build:** "Sobre" fica enxuta — um par de parágrafos direto, trajetória curta, sem o bloco de números que a prosa ao lado já diz — e continua com um Acento por Peça, agora no controle da trajetória.

**Blocked by:** 01 (Deduplicar a proposição repetida entre seções) — o 01 fixa onde "4 anos" e o trio de clientes moram antes de "Sobre" deixar de dizê-los.

**Status:** done — "Sobre" reescrita, bloco de estatísticas e suas regras removidos, trajetória de 7 para 3 linhas, Acento reatribuído ao controle da trajetória e a reatribuição registrada no spec e no ticket 05 da TINTA. Verificação visual (1440/390 px, console, contagem de vermelho, teclado) fica para José antes do merge — extensão do Chrome não conectada nesta sessão, como nos tickets 01 e 02. Ver Comments.

- [x] Os dois parágrafos viram um par enxuto: o primeiro diz o que José faz e onde; o segundo, o que isso rende num projeto pequeno e a formação.
- [x] A enumeração de clientes e o parêntese "(que monta os iPhones da Apple)" saem do parágrafo.
- [x] A trajetória completa cai de sete linhas para cerca de três, agrupando a progressão de cargos na Fitec num intervalo único.
- [x] O bloco de estatísticas (anos / apps / formação) é removido, e suas regras de estilo saem junto.
- [x] O Acento da seção passa para o controle que abre a trajetória; "Sobre" tem exatamente um elemento em Sinal, contado contra a tabela de orçamento da TINTA.
- [x] A linha "Sobre" da tabela de orçamento de vermelho no spec da `redesign-tinta` é atualizada.
- [x] A reatribuição do Acento fica registrada — comentário no ticket de vermelho da TINTA ou linha no registro de decisão.
- [x] A voz do texto é a mesma de antes, só mais curta.

## Comments

### 2026-09-03 — implementação (agente)

Mudanças em `index.html` (seção `#sobre`) e `style.css` (bloco `/* About */`), mais o registro
da consequência de marca no esforço `redesign-tinta`.

**Parágrafos — de dois blocos para um par enxuto:**

- 1º: "Trabalho na Fitec em projetos de e-commerce, testes de hardware e processamento de dados."
  Uma frase, o que faz e onde. Sai "Há 4 anos" (lugar canônico: faixa de prova, fixado no
  ticket 01) e sai a enumeração "Acer, Foxconn (que monta os iPhones da Apple) e Indorama",
  junto com os `<strong>` que a marcavam (lugar canônico: faixa de prova).
- 2º: "Trago essa bagagem para projetos pequenos: um sistema que continua funcionando depois da
  entrega. Formado e mestre em Engenharia pela UPE." Sai "código organizado, prazo realista"
  (lugar canônico: bloco "Como funciona", fixado no ticket 01 — item marcado `[~]` lá, concluído
  aqui). O que rende num projeto pequeno + a formação, como pede o critério.

**Trajetória — de 7 itens para 3:** os cinco cargos da Fitec (Bolsista → Estagiário →
Assistente Jr → Especialista SW Jr → Especialista SW Pl) viram uma linha única
"Ago 2022 – o momento · De Bolsista a Especialista em Desenvolvimento de SW Pl · Fitec". Os dois
diplomas da UPE (Bacharel, Mestre) ficam como linhas próprias — são formações distintas, não
progressão de cargo. Ordem cronológica por início: Bacharel, Fitec, Mestre.

**Bloco de estatísticas:** o `<dl class="about-stats">` inteiro (anos / apps / formação) saiu do
HTML. No CSS saíram `.about-stats`, `.stat`, `.about-stats dt`, `.about-stats dd`. O
`.about-grid` era grade de duas colunas só para acomodar as estatísticas ao lado; sem a segunda
coluna, os dois `<div>` aninhados (`about-grid` > `about-main`) viraram um só,
`<div class="about-copy">`, com `max-width: 62ch` (a mesma medida em caracteres que
`.section-lead` já usa). A media query `@media (max-width: 860px)`, que só empilhava a grade,
foi removida. A estrutura que a seção depende — a seção, o `<details>`, a timeline — não muda.

**Acento reatribuído:** `.trajectory summary` ("Ver trajetória completa") passou de
`color: var(--text)` para `color: var(--signal)` — é o único elemento de ação da seção e agora
o único em sinal. O chevron `::after` segue por `currentColor`. Comentário no CSS explica a
escolha e aponta para o orçamento.

**Registro da consequência de marca (`redesign-tinta`):**

- `spec.md`: linha "Sobre" da tabela de orçamento de vermelho passou de "os números das
  estatísticas" para "o controle que abre a trajetória completa", com nota de rodapé datada
  explicando a reatribuição e a alternativa não escolhida (deixar "Sobre" sem Acento).
- `issues/05-vermelho-verde-e-imagem.md`: comentário datado com a decisão, a mudança de CSS e a
  alternativa registrada.

**Verificação:** o repo não tem runner nem build (decisão herdada da TINTA — ver spec, "Testing
Decisions"). Chaves do CSS balanceadas (241/241); nenhuma referência pendente a `about-stats` /
`.stat`. A extensão do Chrome não estava conectada nesta sessão, então o protocolo manual do
spec (servir em 1440 px / 390 px, console sem erro, contar o vermelho seção a seção — "Sobre"
deve ter exatamente um: o controle da trajetória —, emular esquema escuro e movimento reduzido,
navegar por teclado conferindo o foco, comparar a altura antes/depois) fica para José antes do
merge, como nos tickets 01 e 02.
