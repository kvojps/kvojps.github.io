# kvojps.github.io

Landing page pessoal de José Ferreira. Este glossário fixa o vocabulário da marca — a direção TINTA
do design system — e nada além disso: cor, medida e decisão técnica moram no CSS e em `docs/adr/`.

## Language

### Paleta

**Tinta**:
A cor do texto e dos traços da marca: um quase-preto sobre papel.
_Avoid_: preto, carvão, foreground

**Papel**:
O fundo da marca: um branco quente, cor de papel — nunca branco puro, nunca fundo escuro.
_Avoid_: branco, fundo, background, off-white

**Sinal**:
O vermelho da marca, a única cor saturada da paleta. Existe para apontar a ação.
_Avoid_: destaque, cor de acento, brand red, CTA

**Cinza**:
O cinza da paleta: texto secundário, legendas e metadados — a informação de apoio que não compete
com a tinta.
_Avoid_: cinza-claro, muted, texto fraco

### Marca no cabeçalho

**Assinatura**:
O bloco de marca do cabeçalho: o monograma "JF/" travado ao nome completo, lado a lado. Sem
descritor — o que a pessoa faz aparece no título da página, não na assinatura.
_Avoid_: logo, logotipo, marca-d'água

**Monograma**:
O símbolo "JF/" em quadrado sinal — a única imagem da identidade. Vive em três lugares: à esquerda
do nome na assinatura, como favicon e como imagem de compartilhamento. Um só desenho em dois
arquivos: `monogram.png` no tamanho de ícone, `avatar.png` no tamanho de compartilhamento.
_Avoid_: logo, favicon, símbolo, ícone

### Elementos

**Rótulo**:
O papel visual que substitui as pílulas coloridas — disponibilidade, filtros, legendas: texto
tratado, não uma forma com fundo.
_Avoid_: pílula, tag, badge, etiqueta, chip

**Fio**:
A linha que separa blocos: o fio estrutural em tinta entre as seções, o fio de contorno nas
divisões internas. A marca não tem tracejado.
_Avoid_: borda, régua, divisória, separador

**Esteira**:
A faixa horizontal de cards que se percorre para o lado, um card encaixando por vez — o padrão para
uma coleção que não cabe empilhada. Distinta do carrossel, que neste site é só o transbordo dos
botões de filtro: a esteira move conteúdo, o carrossel move controles.
_Avoid_: carrossel, slider, grade, galeria

### Uso do vermelho

**Peça**:
Uma unidade de material da marca — um post, uma capa, um cartão. É a unidade contra a qual se conta
o acento.
_Avoid_: post, bloco, componente

**Acento**:
O único elemento em sinal dentro de uma peça: a marca gasta vermelho uma vez por peça, sempre sobre
a ação.
_Avoid_: destaque, CTA, botão vermelho
