# Adequar a landing page ao design system TINTA

Status: ready-for-agent

## Problem Statement

José tem uma marca fechada — a direção **TINTA**, definida e aprovada no design system, com paleta,
tipografia, regras de uso e tom de voz. Ela já está no ar: o avatar, a bio e as capas de destaque do
perfil no Instagram seguem esse manual.

A landing page não segue. Ela foi construída antes de a marca existir e traz uma identidade
genérica de template: azul e verde como cores de marca, duas fontes que não são a da marca, cards
arredondados com sombra, degradê no bloco de contato, e um esquema escuro automático que a marca
nunca previu.

O resultado é que a pessoa que sai do perfil e clica no link encontra outra empresa. O trabalho de
fechar a marca não está rendendo no único lugar onde ela precisa converter — e cada peça nova que
José produzir vai aumentar a distância entre o que ele publica e o que o site mostra.

Há ainda uma pendência concreta: a imagem de logo do site foi apagada e as referências a ela
continuam no HTML. Hoje o site está publicado com favicon e imagem de compartilhamento quebrados.

## Solution

A landing page passa a ser a mesma marca que o perfil. Preto sobre papel, Archivo em toda parte,
tudo alinhado à esquerda, nenhum canto arredondado, nenhuma sombra, e o vermelho de sinal aparecendo
uma vez por seção — sempre apontando para a ação.

O logotipo em imagem some do cabeçalho e dá lugar à assinatura tipográfica da marca: o nome completo
com o descritor abaixo, exatamente como no manual. O monograma volta na aba do navegador e na
imagem de compartilhamento, usando o avatar vermelho já aprovado no design system.

As provas de trabalho — os screenshots dos projetos entregues — passam a aparecer em preto e branco,
ganhando cor quando o visitante interage com elas. As marcas dos aplicativos próprios ficam
coloridas: são logotipos de produto, não fotografia.

O texto do site não muda nesta rodada. É uma troca de pele, não de discurso.

Ao final, as regras da marca ficam escritas junto do código — um glossário e um registro de decisão
— para que ninguém as desfaça achando que são bug.

## User Stories

### Visitante

1. Como visitante que veio do perfil no Instagram, quero encontrar no site a mesma identidade visual
   do perfil, para não desconfiar de ter caído no lugar errado.
2. Como visitante, quero ler a página em uma única família tipográfica coerente, para que o texto
   pareça um documento e não uma colagem de templates.
3. Como visitante, quero que a página tenha fundo de papel claro e texto em tinta, para uma leitura
   sóbria e de alto contraste.
4. Como visitante, quero encontrar um único elemento vermelho por seção, para saber imediatamente
   onde está a ação daquele trecho.
5. Como visitante na primeira dobra, quero que o botão de orçamento seja a única coisa vermelha da
   tela, para não hesitar sobre o que fazer em seguida.
6. Como visitante, quero que os títulos tenham peso e aperto de cartaz, para reconhecer a hierarquia
   sem precisar ler.
7. Como visitante, quero que blocos sejam separados por fios nítidos, para entender a estrutura da
   página de relance.
8. Como visitante, quero ver os trabalhos entregues em preto e branco, para que as imagens formem um
   conjunto e não briguem entre si por atenção.
9. Como visitante interessado em um trabalho específico, quero que a imagem ganhe cor quando eu
   interajo com ela, para ver o projeto como ele realmente é.
10. Como visitante, quero que os ícones dos aplicativos apareçam coloridos, para distinguir um
    produto do outro.
11. Como visitante passando o mouse sobre um card, quero um retorno visual claro sem que o card se
    desloque, para não perder o alvo do clique.
12. Como visitante, quero que os screenshots continuem enquadrados como tela de aplicação, para
    entender que aquilo é software rodando e não uma foto qualquer.
13. Como visitante que usa o sistema em modo escuro, quero ver a mesma página que todo mundo vê,
    para receber a marca como ela foi desenhada.
14. Como visitante que reduz movimento no sistema operacional, quero que as animações de entrada
    sejam desligadas, para navegar sem desconforto.
15. Como visitante no celular, quero a mesma identidade e a mesma legibilidade do desktop, para não
    receber uma versão de segunda classe.
16. Como visitante, quero que o cabeçalho traga o nome completo e o que a pessoa faz, para saber de
    quem é o site antes de rolar.
17. Como visitante com muitas abas abertas, quero reconhecer o site pelo ícone da aba, para voltar
    a ele sem procurar.
18. Como visitante que recebeu o link em uma conversa, quero ver uma prévia com a marca correta,
    para confiar no link antes de abrir.
19. Como visitante que usa leitor de tela ou navega por teclado, quero que o foco continue visível
    e as marcações semânticas intactas, para navegar sem depender da cor.
20. Como visitante, quero que a página continue carregando rápido, para não pagar pela troca de
    identidade com tempo de espera.

### José (dono da marca)

21. Como dono da marca, quero que o site obedeça à proporção de uso da paleta, para que o vermelho
    não perca força por excesso.
22. Como dono da marca, quero que o site use somente as quatro cores do manual, para que nenhuma cor
    órfã sobreviva de decisões antigas.
23. Como dono da marca, quero que a página nunca centralize título ou texto, para manter a assinatura
    de composição da marca.
24. Como dono da marca, quero que nenhum canto seja arredondado, para preservar o caráter da direção
    escolhida.
25. Como dono da marca, quero que nenhuma sombra, degradê ou brilho sobreviva, para que a página
    pareça trabalho e não anúncio.
26. Como dono da marca, quero que o cabeçalho use a assinatura tipográfica em vez de uma imagem, para
    que a marca fique nítida em qualquer tela e não dependa de um arquivo.
27. Como dono da marca, quero que o monograma apareça apenas como avatar e ícone, respeitando a
    restrição do manual.
28. Como dono da marca, quero reaproveitar o avatar já aprovado no design system, para não ter duas
    versões do mesmo símbolo circulando.
29. Como dono da marca, quero que o descritor de serviço apareça travado à assinatura, para que ele
    nunca mude de peça para peça.
30. Como dono da marca, quero que o texto atual da página seja preservado nesta rodada, para revisar
    identidade e discurso separadamente.
31. Como dono da marca, quero ver a página rodando antes de publicar, para aprovar a troca com meus
    próprios olhos.
32. Como dono da marca, quero que o site publicado continue no ar intacto enquanto o trabalho
    acontece, para não expor uma versão pela metade.

### Quem mexer no código depois

33. Como pessoa que abrir este repo daqui a seis meses, quero encontrar um glossário da marca, para
    usar os termos certos em vez de inventar sinônimos.
34. Como pessoa que abrir este repo, quero encontrar registrado por que a direção TINTA foi escolhida
    e a outra rejeitada, para não reabrir uma decisão já tomada.
35. Como pessoa que abrir este repo, quero entender que o raio zero e a fonte única são regra de
    marca, para não "consertar" o que está certo.
36. Como pessoa que for editar o CSS, quero que os nomes dos tokens digam a cor que realmente
    carregam, para não pintar de vermelho uma coisa chamada de verde.
37. Como pessoa que for adicionar uma seção nova, quero saber quanto vermelho aquela seção pode
    gastar, para não estourar a proporção da paleta.
38. Como agente trabalhando neste repo, quero que a configuração de tracker e glossário já esteja
    escrita, para publicar spec e tickets sem precisar perguntar.

## Implementation Decisions

### Camada de tokens

- O vocabulário de tokens legado (uma cor "de marca" azul e uma cor "de acento" verde) é
  **substituído**, não aliasado, pelo vocabulário do design system: papel, superfície, tinta, sinal,
  divisor, mais as rampas neutra e de acento. Aliasar deixaria nomes mentirosos — um token chamado
  de acento verde carregando tinta preta — e é exatamente o tipo de armadilha que a próxima pessoa
  cai.
- Os tokens de sombra **deixam de existir**. Não são zerados: são removidos, junto de todos os seus
  usos. Um token de sombra presente é um convite a reintroduzir sombra.
- Raio existe como token e vale zero em todos os degraus. Manter o token (em vez de apagar a
  propriedade) preserva o ponto único de retomada caso a marca um dia mude de ideia.
- O esquema de cor escuro automático é **removido por inteiro**. A marca tem uma paleta só. A
  declaração de esquema de cor da página passa a anunciar apenas claro, para que controles nativos
  do navegador acompanhem.
- Espaçamento **não** é tokenizado nesta rodada. O ritmo atual já é responsivo e funciona; trocá-lo
  significaria reescrever o CSS inteiro e arriscar o layout em nove pontos de quebra, sem ganho
  visível para o visitante.

### Cor

- A paleta é fechada em quatro valores: papel, tinta, sinal e cinza, mais as rampas derivadas para
  estados intermediários.
- O verde que hoje carrega significado semântico ("disponível", "grátis", marcas de confirmação,
  marcadores de linha do tempo) **não é traduzido para outra cor**: vira tinta e cinza. Onde ele
  sinalizava estado, o sinal passa a ser tipográfico — rótulo em caixa alta com fio — em vez de
  cromático. Isso mantém a paleta fechada e libera o vermelho inteiro para a ação.
- Todo valor de cor escrito literalmente no CSS (brancos puros, transparências, um verde-menta de
  ponto de status, um azul-claro de hover) é convertido para token. Nenhum literal de cor sobrevive.

### Orçamento de vermelho

Contrato de uma linha por seção. "Um só elemento vermelho por peça" é regra de post; numa página que
rola, a peça é a seção.

| Seção | O acento vermelho |
| --- | --- |
| Cabeçalho | o botão de orçamento |
| Primeira dobra | o botão primário |
| Faixa de prova | nenhum |
| Serviços | os números do processo |
| Trabalhos | o botão da chamada intercalada |
| Aplicativos | o filtro ativo |
| Sobre | o controle que abre a trajetória completa |
| Contato | o botão do cartão de contato |
| Rodapé | nenhum |
| Modal | o botão de download |

O vermelho de hover é transitório e **não conta** contra o orçamento estático da seção.

> **Atualização (2026-09-03, esforço `enxugar-conteudo`, ticket 03):** a linha "Sobre"
> era "os números das estatísticas". O bloco de estatísticas foi removido de "Sobre"
> (cada número já vivia na prosa ao lado ou na faixa de prova), então o Acento passou
> para **o controle que abre a trajetória completa** — o único elemento de ação da
> seção. Alternativa registrada e não escolhida: deixar "Sobre" sem Acento, como a
> faixa de prova e o rodapé. Ver `.scratch/enxugar-conteudo/issues/03-reescrever-sobre.md`
> e o comentário no ticket 05 deste esforço.

### Tipografia

- Fonte única: Archivo, em três pesos (corpo, intermediário, título). As duas famílias atuais saem,
  e a origem externa de fontes já usada é reaproveitada — nenhuma nova dependência de rede.
- Título: peso máximo, tracking **−3,5%**, entrelinha apertada.
- Corpo: 15 px sobre 1,55.
- Rótulo: peso máximo, 13 px, caixa alta, tracking 8%. Esse é o novo papel visual de tudo que hoje é
  pílula colorida — etiqueta de disponibilidade, marcador de gratuito, filtros, legendas.
- Os tamanhos de meio-passo herdados (13,5 / 14,5 / 15,5 / 18,5) são encaixados na escala do manual.
- Títulos fluidos permanecem fluidos: a escala continua respondendo à largura da tela, apenas
  re-afinada em torno dos valores do manual. Fixar os tamanhos quebraria o mobile.

### Forma e fio

- Nenhum canto arredondado. Única exceção: formas que são círculos por definição — pontos de status
  e os pontos da barra da moldura. Um ponto é forma, não canto.
- Dois níveis de fio: **estrutural** de 2 px em tinta, separando cabeçalho, seções, o box de
  processo e a linha do tempo; e **de contorno** de 1 px em divisor, nas bordas de card e campo. Fio
  de 2 px em tudo somaria peso demais com dez cards simultâneos na tela.
- A borda tracejada da chamada intercalada vira fio sólido: o manual não tem tracejado.
- A moldura de navegador que enquadra os screenshots é **mantida** — ela comunica "isto é software
  rodando" — mas passa a fio de tinta com canto reto, e as bolinhas de semáforo, cromaticamente
  alheias à paleta, viram cinza.

### Interação

- O padrão de hover atual (deslocamento vertical mais sombra) é substituído por **inversão de fio**:
  a borda vai ao sinal e o título do card vai ao sinal. Sem deslocamento, sem sombra. Coerente com
  "o vermelho marca onde importa".
- As animações de entrada por rolagem são **mantidas**. As proibições do manual — degradê, sombra,
  brilho — são todas de efeito estático; movimento não é mencionado. A preferência de movimento
  reduzido do sistema já é respeitada e continua sendo.

### Imagem

- Provas de trabalho (screenshots de projetos entregues e dos aplicativos) recebem dessaturação
  total com leve ganho de contraste, e voltam à cor quando o visitante interage com o card. O
  utilitário de dessaturação do design system é usado como está.
- Marcas de produto (os ícones dos aplicativos próprios, nos cards e nos modais) ficam **isentas**.
  A regra do manual fala de foto; um logotipo de produto não é foto, e dessaturá-lo apagaria a
  identidade de cada aplicativo.

### Marca no site

- O cabeçalho troca a imagem de logo pela **assinatura tipográfica**: o nome completo em caixa alta
  com peso de título sobre o descritor em rótulo. Sem imagem — a marca fica nítida em qualquer
  densidade de tela e deixa de depender de um arquivo que pode sumir (como sumiu).
- O monograma volta apenas onde o manual permite: ícone da aba e imagem de compartilhamento.
- O ativo de origem é o **avatar vermelho** já aprovado no design system, obtido diretamente do
  projeto de design. O manual o marca como recomendado por não desbotar sob compressão. Dele deriva
  um ícone reduzido para a aba; o arquivo em resolução plena serve à imagem de compartilhamento.
- A imagem de logo antiga permanece removida, e suas referências pendentes no HTML são resolvidas —
  o que também conserta o favicon e a prévia de compartilhamento, hoje quebrados no site publicado.

### Documentação

- Nasce um **glossário** na raiz com os termos da marca: Tinta, Papel, Sinal, Cinza, Assinatura,
  Monograma, Descritor, Rótulo, Fio, Peça, Acento. Só glossário — nenhum detalhe de implementação.
- Nasce **um registro de decisão** cobrindo a escolha da direção TINTA sobre a direção alternativa,
  e as consequências difíceis de reverter: raio zero, fonte única, alinhamento à esquerda sempre,
  orçamento de 5% de vermelho. Sem esse registro, as regras parecem defeito.

### Entrega

- O trabalho acontece em uma branch dedicada. A branch principal publica direto para o ar; uma
  mudança desta dimensão não vai a público sem José ver rodando. Sem push.

## Testing Decisions

**Decisão: nenhuma seam automatizada será introduzida.** Verificação é manual.

O contexto que leva a isso: o repo tem zero infraestrutura de teste. Não há gerenciador de pacotes,
runner, nem integração contínua — o site inteiro são dois arquivos servidos estaticamente. Não
existe seam prévia para preferir, então qualquer seam seria nova, e a mais barata delas ainda traria
um ecossistema de dependências inteiro para um projeto que hoje não tem nenhuma.

Um bom teste aqui verificaria **comportamento externo**: o que o navegador desenhou, não o que o
arquivo de estilo diz. A seam alta e única que atenderia isso seria ler os estilos computados do DOM
da página servida e afirmar as regras da marca — nenhum raio não-nulo fora dos círculos declarados,
nenhuma sombra, toda família tipográfica sendo Archivo, toda cor pertencendo à paleta, um acento
vermelho por seção, nenhum texto centralizado. Uma varredura textual sobre o CSS seria uma seam mais
baixa e enganosa: passaria com o layout quebrado.

Fica **registrado como opção rejeitada por ora**, não como esquecimento. Se a página crescer ou
passar a ter mais de uma pessoa editando, essa é a seam a abrir, e é uma só.

**Prova de arte anterior: nenhuma.** Não há testes de qualquer tipo neste repo.

### Protocolo de verificação manual

1. Servir a página localmente e abrir em 1440 px e em 390 px de largura.
2. Console do navegador sem erros; nenhuma imagem falhando ao carregar.
3. Confirmar que nenhum token ou nome legado sobreviveu no CSS, e que não restam sombras, raios
   não-nulos fora dos círculos declarados, nem referências às fontes antigas.
4. Contar os elementos vermelhos seção a seção contra a tabela de orçamento acima.
5. Emular preferência de esquema escuro: a página não pode mudar.
6. Emular preferência de movimento reduzido: as entradas por rolagem devem aparecer sem transição.
7. Conferir o ícone na aba do navegador e a prévia de compartilhamento.
8. Navegar por teclado: o indicador de foco continua visível em todos os alvos.

## Out of Scope

- **Reescrita de copy.** O manual traz tom de voz e quatro versões de bio prontas; nada disso entra.
  A única exceção é o descritor que acompanha a assinatura no cabeçalho, que é parte do bloco de
  marca, não texto de página.
- **Tokenização de espaçamento.** O ritmo atual permanece.
- **Conteúdo novo.** Nenhuma seção, projeto, caso ou aplicativo é adicionado.
- **Teste automatizado e integração contínua.** Decidido acima.
- **Instalar ferramenta de linha de comando de issue tracker.** O tracker deste repo é markdown local.
- **Publicar.** O trabalho fica em branch, sem push. O merge é decisão de José, depois de ver rodando.
- **Peças fora do site** — capas de destaque, posts, cartão. São trabalho de design, não deste repo.
- **Modo escuro em qualquer forma.** Removido, não reimplementado.

## Further Notes

- **Contradição resolvida dentro do próprio design system.** O manual visual especifica tracking de
  −3,5% em títulos, enquanto o arquivo de tokens do sistema aplica −1,5%. Vale o manual: é o que
  José viu renderizado e aprovou nas peças. O arquivo de tokens carrega o default genérico do
  template de onde o sistema nasceu.
- **"Um só elemento vermelho por peça" é regra de post do Instagram.** A tradução para uma página
  que rola — uma peça é uma seção — é interpretação desta especificação, não do manual. Está na
  tabela acima para ser contestável em vez de implícita.
- **O verde era a única cor semântica sem destino.** O azul de marca mapeia limpo para o sinal
  vermelho; o verde não tinha para onde ir dentro de uma paleta de quatro cores. Convertê-lo em
  sinal tipográfico em vez de cromático é a decisão menos óbvia deste spec e a mais provável de ser
  questionada depois.
- **O site publicado está hoje com favicon e prévia de compartilhamento quebrados**, por causa da
  imagem de logo removida sem que as referências fossem atualizadas. Este trabalho conserta isso de
  passagem; se ele for adiado, vale consertar em separado.
- **A página já é alinhada à esquerda.** Existe um único texto centralizado em todo o CSS, e é uma
  regra de mobile. A proibição mais estrutural do manual já estava praticamente cumprida por acaso.
- **O glossário e o registro de decisão nascem deste trabalho.** Não existiam quando o spec foi
  escrito, então este spec não pôde consumi-los — ele os produz.
