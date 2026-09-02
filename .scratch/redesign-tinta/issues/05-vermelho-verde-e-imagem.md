# 05: Orçamento de vermelho, fim do verde e provas de trabalho em preto e branco

**What to build:** O visitante encontra um único elemento vermelho por seção, sempre apontando para
a ação daquele trecho, e vê os trabalhos entregues como um conjunto em preto e branco em vez de seis
imagens brigando por atenção. Passar o mouse num card dá retorno claro sem que o card se desloque, e
devolve a cor à imagem para quem quiser ver o projeto como ele é.

As três coisas andam juntas porque todas definem o mesmo comportamento: onde o vermelho vive em
repouso, e o que acontece quando o visitante interage.

O verde é o ponto delicado. Ele carrega significado semântico hoje — disponibilidade, gratuidade,
confirmações, marcadores — e não tem para onde ir dentro de uma paleta de quatro cores. A decisão é
converter esse sinal de cromático para **tipográfico**: rótulo em caixa alta com fio, no lugar de
pílula colorida. Isso mantém a paleta fechada e libera o vermelho inteiro para a ação.

**Blocked by:** 03 (Tipografia Archivo em toda a página), 04 (Forma da marca).

**Status:** done

- [x] Cada seção da página exibe no máximo um elemento vermelho em repouso, conforme a tabela de orçamento do spec.
- [x] A primeira dobra gasta seu vermelho no botão primário; o trecho destacado dentro do título ficou em tinta.
- [x] A faixa de prova e o rodapé não têm nenhum vermelho.
- [x] Nenhuma cor verde sobrevive em parte alguma da página.
- [x] Os antigos sinais cromáticos de estado — disponibilidade, gratuidade, marcas de confirmação, marcadores de linha do tempo — agora são rótulos tipográficos com fio.
- [x] O hover de card não desloca o elemento nem produz sombra: a borda e o título vão ao sinal.
- [x] Screenshots dos trabalhos entregues e dos aplicativos aparecem dessaturados, com leve ganho de contraste.
- [x] Interagir com o card devolve a cor à imagem.
- [x] Os ícones dos aplicativos próprios permanecem coloridos em todos os lugares onde aparecem — são marcas de produto, não fotografia.
- [x] As animações de entrada por rolagem continuam funcionando, e continuam desligadas para quem pede movimento reduzido no sistema.

## Comments

Implementado na branch `redesign-tinta`. Sem push — o merge é decisão do José, depois de ver
rodando.

### Orçamento de vermelho

Cada seção passou a ter um único acento em repouso, na posição da tabela do spec. O que perdeu o
vermelho, e para onde foi:

- `.section-eyebrow` (todas as seções), `.service-icon` (4×), `.hero h1 .hl`, o link "Ver todos"
  da legenda do hero, `.text-link` (LinkedIn/GitHub), `.trajectory summary`, `.timeline-org` →
  **tinta**; os pontos de `.service-list`, `.modal-features` e o marcador de `.timeline-item` →
  **cinza/tinta**; `.case-detail dt` → **rótulo em cinza**.
- `.btn-download` era vermelho nos três lugares onde aparece (Trabalhos, Apps, Modal). Como o
  acento de Trabalhos é a chamada intercalada e o de Apps é o filtro ativo, o botão passou a
  **tinta cheia** em repouso, indo ao sinal só no hover. Dentro do modal ele **é** o acento da
  peça: `.modal-footer .btn-download` reintroduz o vermelho.
- Mantidos vermelhos (acentos sancionados): `.nav-cta`/`.header-cta` (cabeçalho), `.btn-primary`
  (primeira dobra, chamada intercalada, cartão de contato), `.process-num` (Serviços),
  `.filter-btn.active` (Apps), `.about-stats dt` (Sobre), `.modal-footer .btn-download` (Modal).
- Vermelho de hover (`:hover`/`:active` de botões, cards, filtros e da moldura do hero) é
  transitório e não conta contra o orçamento — como o spec registra.

### Fim do verde

`--accent` (#111) e `--accent-tint` (#ede9e1) eram o par legado do antigo verde semântico. Depois
de reconvertidos os usos, sobraram zero referências, então **os dois tokens foram removidos** — não
há o que o ticket 07 renomeie. `--brand*` continua legado e é problema do 07; o comentário do bloco
de tokens foi ajustado para dizer isso.

### Sinais de estado → rótulo com fio

- `.badge-available`: era pílula com ponto de status. Virou rótulo em caixa alta (peso 900, 13 px,
  tracking 8%) com fio estrutural de 2 px em tinta à esquerda. O `<span class="dot">` saiu do HTML
  nas duas ocorrências (hero e cartão de contato).
- `.chip-free` "Grátis": rótulo com o mesmo fio à esquerda. `.chip-category` compartilhava a regra
  e virou rótulo também — sem fundo, sem borda: o glossário manda evitar "pílula/tag/badge", e
  deixar categoria como pílula ao lado de um "Grátis" sem fundo ficaria incoerente.
- `.hero-points`: os tiques viraram um fio curto de 2 px em tinta e o texto virou rótulo.
- Marcador de `.timeline-item`: o fio é a régua de 2 px do próprio item; o ponto ficou em tinta.

### Hover de card

Removido o `translateY(-2px)`/`translateY(-4px)` de `.service-card`, `.case-card`, `.app-card` e
`.hero-shot`. No lugar: a borda vai ao sinal e o `h3` do card vai ao sinal (na moldura do hero, o
fio da `.shot-frame` vai ao sinal). **Sem transição**: a classe `.reveal`, que o script de entrada
por rolagem aplica de forma permanente a todos os cards, governa o `transition` deles e venceria
qualquer `transition` próprio por ordem de cascata — então a inversão de fio é instantânea, o que
também serve ao objetivo do critério (retorno claro sem perder o alvo do clique). O apontamento do
`/code-review` sobre `transition` morto foi endereçado assim: as declarações inertes saíram.

### Imagem em preto e branco

`.app-shot` entra com `filter: grayscale(1) contrast(1.05)` e volta à cor em
`:hover`/`:focus-within`/`:active` do card (ou da âncora do hero), e dentro de `.modal-body`. Os
ícones de produto (`.app-icon`/`.modal-icon`) não têm filtro — são marca, não foto. O `:active`
cobre o toque, onde não há hover: pressionar um botão do card (Detalhes / Visitar site) propaga
`:active` ao card e devolve a cor enquanto o dedo está sobre ele. **Ponto para o José ver rodando:**
no celular, o card de trabalho entregue não tem modal e seu único filho focável é um link externo,
então a cor só volta durante o toque no botão, não de forma persistente. Se isso não bastar, o
caminho é envolver o screenshot num link para o projeto (como já é no hero) — ficou fora desta
rodada por ser mudança de estrutura, não de pele.

### Verificação

Estática. A extensão do Chrome não estava conectada — a página não foi aberta em 1440/390 px, nem
emulados esquema escuro e movimento reduzido, nem conferido o console. Isso fica para o José, e o
protocolo completo do spec roda no ticket 07. Conferido: chaves balanceadas (247/247); nenhum
`--accent`, `Inter`/`Space Grotesk`, `box-shadow`, `linear-gradient`, `dashed` ou
`prefers-color-scheme` no CSS/HTML; raio literal só nos dois círculos declarados (barra da moldura
e — agora sem o ponto de disponibilidade); bloco de `prefers-reduced-motion` e observador de
`.reveal` intactos; os dois arquivos servindo 200 em servidor local; contagem de vermelhos seção a
seção contra a tabela do orçamento.

`/code-review` rodou nos dois eixos antes do commit. Quatro apontamentos, todos endereçados:
`transition` de card morto por causa do `.reveal` (declarações removidas, hover agora é
instantâneo); sem caminho de cor no toque (`:active` adicionado ao grupo de reveal); `transition:
color` inútil em `.service-card` (removido); `:focus-visible` do hero divergindo do `:focus-within`
dos cards (hero passou a `:focus-within`).
