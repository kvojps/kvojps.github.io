# 04: Forma da marca — raio zero, fim das sombras, fios de dois níveis

**What to build:** A página ganha o caráter da direção escolhida: nada arredondado, nada com sombra,
e a estrutura legível de relance por fios nítidos. O visitante entende a organização da página pela
separação dos blocos, não por cards flutuando.

Sombra e fio andam juntos porque um substitui o outro: as sombras hoje fazem o trabalho de separar
blocos, e o fio assume esse papel no mesmo movimento.

**Blocked by:** 01 (Camada de tokens TINTA e fim do esquema escuro).

**Status:** done

- [x] Nenhum elemento da página tem canto arredondado. A única exceção são formas que são círculos por definição: os pontos de status e os pontos da barra da moldura.
- [x] Nenhuma sombra sobrevive na página, e os tokens de sombra foram **removidos**, não zerados — um token de sombra presente é convite a reintroduzir sombra.
- [x] Nenhum degradê e nenhum brilho sobrevivem em parte alguma.
- [x] Blocos estruturais — cabeçalho, separação entre seções, o box de processo e a linha do tempo — são separados por fio de 2 px em tinta.
- [x] Bordas de card e de campo usam fio de 1 px em divisor, para que dez cards simultâneos na tela não somem peso demais.
- [x] A borda tracejada da chamada intercalada virou fio sólido.
- [x] A moldura que enquadra os screenshots foi mantida — ela comunica "isto é software rodando" — agora com fio de tinta e canto reto.
- [x] As bolinhas de semáforo da moldura, cromaticamente alheias à paleta, viraram cinza.

## Comments

Implementado no commit `0c6c067`, na branch `redesign-tinta`. Sem push: o merge é decisão do
José, depois de ver rodando.

Decisões que se afastam da letra do checklist, registradas para o 05 e o 07 não tropeçarem:

- **`--radius-pill` foi removido, não renomeado.** O 01 deixou quatro degraus de raio; este
  ticket, que os liga às declarações, encontrou que `pill` carrega "pílula" — termo que o
  glossário manda evitar. Como os quatro degraus valem zero, os quatro usos (etiqueta de
  disponibilidade, filtro, chips) passaram a apontar para `--radius-sm` e o degrau `pill` saiu.
  Sobram três: `sm`, `md`, `lg`.
- **Os pontos decorativos de lista viraram quadrados.** `.service-list li::before`,
  `.timeline-item::before` e `.modal-features li::before` eram círculos de 6–8 px. O checklist
  fecha a exceção em dois itens — ponto de status e ponto da barra da moldura — e esses três não
  são nenhum dos dois. Ficaram quadrados. Sobrevivem redondos só o ponto da etiqueta de
  disponibilidade e as bolinhas da barra da moldura. `.process-num`, `.filter-nav` e
  `.modal-close`, que eram redondos por template e não são pontos, viraram retângulos de raio
  zero.
- **A moldura é o terceiro caso de fio.** O sistema tem dois níveis — estrutural 2 px em tinta,
  contorno 1 px em divisor —, mas o checklist pede a moldura "com fio de tinta". Ela ficou 1 px
  **em tinta**: combinação que o comentário do bloco de tokens agora registra como exceção
  explícita, não como fio solto.
- **A faixa de prova ficou fora do fio estrutural.** O checklist nomeia quatro blocos —
  cabeçalho, separação entre seções, box de processo, linha do tempo. A `.proof-strip` não está
  na lista e continua com contorno de 1 px em divisor. Se ela merece o fio de 2 px, é decisão do
  José ao ver rodando.

O verde semântico dos marcadores da linha do tempo e das listas **não foi tocado** — cor é do
05. Este ticket só mexeu na forma.

Verificação: só estática. A extensão do Chrome não estava conectada, então a página não foi
aberta nem os modos escuro/movimento-reduzido emulados — isso é o protocolo do 07. Conferido:
chaves balanceadas, nenhum token referenciado sem definição, nenhum `box-shadow`, `--shadow-*`,
`linear-gradient`, `radial-gradient` ou `dashed` no stylesheet, raio literal só nos dois pontos
declarados como exceção, e os dois arquivos servindo 200 em servidor local. `/code-review`
rodou nos dois eixos; os apontamentos viraram as quatro decisões acima.
