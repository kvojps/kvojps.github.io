# Adoção da direção TINTA na landing page

## Contexto e decisão

A marca pessoal de José está fechada no design system sob a direção **TINTA**: tinta sobre papel,
uma só família tipográfica (Archivo), composição sempre alinhada à esquerda, nenhum canto
arredondado, nenhuma sombra ou degradê, e o vermelho de sinal limitado a cerca de 5% do uso da
paleta. O perfil no Instagram já segue esse manual. A landing page, construída antes de a marca
existir, ainda carrega a identidade genérica do template de origem — azul e verde como cores de
marca, duas fontes fora do manual, cards arredondados com sombra, degradê no bloco de contato e
esquema escuro automático.

Decidimos **trocar a pele da página inteira para TINTA**. O texto não muda nesta rodada: é troca de
identidade visual, não de discurso.

## Alternativa rejeitada

A escolha de TINTA sobre outras direções de marca aconteceu dentro do design system e não está
registrada neste repo. O que este registro documenta é a decisão que é deste repo: **manter a
identidade de template do site** — azul/verde, duas fontes, cards com sombra, degradê, modo escuro —
que não custava trabalho nenhum. Rejeitada porque o esforço de fechar a marca não rende se o site
não a segue: quem sai do perfil e clica no link encontra outra empresa, e cada peça nova que José
publicar aumenta a distância entre o que ele posta e o que o site mostra. O custo zero de não fazer
nada é pago em desconfiança do visitante, no único lugar onde a marca precisa converter.

## Consequências difíceis de reverter

Estas quatro restrições vêm do manual da marca. São **regra de marca, não defeito de
implementação** — quem for editar o CSS ou o HTML depois não deve "consertá-las":

- **Raio zero.** Nenhum canto arredondado em toda a página. Única exceção: formas que são círculos
  por definição, como pontos de status. O token de raio continua existindo e vale zero em todos os
  degraus, para haver um ponto único de retomada caso a marca um dia mude de ideia.
- **Fonte única.** Archivo em toda a página, em três pesos. Nenhuma segunda família tipográfica.
- **Alinhamento à esquerda sempre.** Nenhum título ou bloco de texto centralizado. A única
  centralização que sobra no CSS é uma regra de mobile, herdada.
- **Orçamento de 5% de vermelho.** O sinal ocupa cerca de 5% do uso da paleta — proporção do
  manual. O vermelho de hover é transitório e não conta contra ela.

## Interpretação desta adaptação

O manual diz "um só elemento vermelho por peça", e "peça" ali é um post do Instagram. **A tradução
para uma página que rola — uma peça é uma seção, um acento por seção — é interpretação desta
adaptação, não regra do manual.** Fica registrada aqui para ser contestável em vez de implícita. A
tabela que fixa qual é o acento de cada seção acompanha o trabalho de adaptação, não este registro.

## Padrões de interação nomeados

Este ADR trata de efeito estático — sombra, degradê, brilho, raio. Movimento não é regra de marca
aqui. Ainda assim, um padrão de navegação ganha nome próprio para a próxima pessoa não reinventar
outro:

- **Esteira** (esforço `enxugar-conteudo`, ticket 04): faixa horizontal de cards com encaixe de
  rolagem, usada na seção de aplicativos no lugar de uma grade com botão de expandir. Nome distinto
  do **carrossel**, que neste repo é só o transbordo dos botões de filtro. A rolagem suave da
  esteira respeita a preferência de movimento reduzido. A seção "Trabalhos" também adota a esteira
  (esforço `esteira-trabalhos`), um case largo por vez — antecipada ainda com dois cases, para a
  seção parar de crescer empilhada.

  **A esteira de "Trabalhos" vale só a partir de 800px** (esforço de responsividade mobile). Abaixo
  disso os cases empilham. A esteira resolve escassez de espaço horizontal, que é problema de
  desktop; no celular o card de case vira coluna única e passa de 600px de altura, e um card assim
  dentro de uma faixa com encaixe obrigatório troca rolagem vertical por swipe acidental, com os
  controles ‹ › parados lá no topo, fora de vista. **Esteira serve card curto; card alto empilha** —
  é essa regra, e não a seção, que decide: os cards de app têm ~350px e continuam em esteira nas duas
  larguras. Quem for mexer nisto depois não deve "restaurar" a esteira no mobile.
