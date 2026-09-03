# Enxugar o conteúdo da landing page

Status: ready-for-agent

## Problem Statement

A landing page de José teve a identidade visual refeita no esforço `redesign-tinta`, que
**congelou a copy de propósito** — foi uma troca de pele, não de discurso. O texto ficou como
estava.

E como estava é verboso e repetido. O mesmo fato aparece em até quatro seções: "4 anos de
experiência", o trio de clientes Acer/Foxconn/Indorama, o bordão "da ideia à entrega" em quatro
variações, o Rótulo de disponibilidade em dois lugares, quatro chamadas de ação quase idênticas.
Os modais de app trazem um parágrafo corrido de 40 a 48 palavras e, logo abaixo, uma lista de
recursos que repete o mesmo parágrafo quase palavra por palavra. A seção "Sobre" fecha com um
bloco de três estatísticas cujos números já foram ditos na prosa ao lado. A seção de aplicativos
esconde metade dos cards atrás de um botão "Ver os N apps".

O visitante — que escaneia uma landing de serviço, não a lê linha a linha — rola mais do que
precisa e relê o que já sabe. José quer o texto mais curto e a página mais rápida de percorrer,
sem mudar o que ela diz nem o jeito de dizer.

## Solution

A página passa a dizer cada coisa uma vez. Cada fato repetido ganha um lugar canônico — o mais
forte — e some dos outros. Os parágrafos encolhem para no máximo duas frases, sem frase-parágrafo
corrida e sem floreio. Nos modais de app, o parágrafo vira uma frase de posicionamento e a lista
de recursos carrega os detalhes; a frase "os dados ficam na sua máquina", hoje reescrita nos
quatro modais, aparece uma vez só.

A seção de aplicativos troca a grade com botão de expandir por uma **esteira** horizontal com
encaixe de rolagem: os quatro cards visíveis numa faixa que se navega para o lado, com o filtro
de categoria mantido. A seção "Sobre" perde o bloco de estatísticas, e o Acento da seção — que
o orçamento da TINTA fixava nos números — passa para o controle que abre a trajetória.

"Sobre" ganha um par de parágrafos enxuto. Os cases contam o desafio em uma frase. A voz
continua a mesma de antes, só mais direta. Nenhuma seção, case ou app é adicionado ou removido;
nenhuma chamada de ação deixa de existir.

Ao final, a página tem a mesma informação e a mesma marca, em menos texto e menos rolagem.

## User Stories

### Visitante

1. Como visitante que escaneia a página, quero que cada informação apareça uma única vez, para
   não reler o mesmo fato em três seções.
2. Como visitante apressado, quero parágrafos de no máximo duas frases, para captar a ideia sem
   me perder numa frase corrida.
3. Como visitante no celular, quero uma página mais curta, para chegar ao contato com menos
   rolagem.
4. Como visitante interessado num app, quero que o modal diga o essencial sem repetir o
   parágrafo na lista de recursos, para entender o produto de relance.
5. Como visitante avaliando os aplicativos, quero vê-los numa esteira horizontal, para percorrer
   os quatro sem expandir uma grade.
6. Como visitante que procura um tipo específico de app, quero que o filtro de categoria
   continue funcionando na esteira, para chegar ao que me interessa.
7. Como visitante que navega por teclado, quero alcançar e operar a esteira pelo Tab e pelas
   setas, para não depender do mouse.
8. Como visitante com movimento reduzido no sistema, quero que a esteira role sem animação
   suave, para navegar sem desconforto.
9. Como visitante, quero que os controles da esteira sigam a marca — em Fio, sem canto
   arredondado, sem sombra — para a página continuar parecendo um documento.
10. Como visitante lendo "Sobre", quero um texto enxuto sobre quem faz o trabalho, sem um bloco
    de números que repete o que o parágrafo já disse.
11. Como visitante, quero que a proposta ("4 anos", os clientes, o prazo de resposta) apareça no
    lugar mais forte e só nele, para não sentir a página se repetindo.
12. Como visitante que chega pela prévia de um link, quero uma descrição curta e sem frase de
    enchimento, para saber do que se trata em uma linha.
13. Como visitante que já conhecia a página, quero reconhecer o mesmo tom, só mais direto, para
    sentir a mesma pessoa falando.
14. Como visitante lendo os cases, quero o desafio contado em uma frase, para chegar ao que foi
    feito sem uma narrativa longa.
15. Como visitante, quero que títulos, eyebrows e a moldura "O desafio / O que foi feito"
    continuem como estão, para não perder a estrutura que já conheço.
16. Como visitante na primeira dobra, quero encontrar ali o Rótulo de disponibilidade, para
    saber logo que dá para contratar.
17. Como visitante que passou pela primeira dobra, quero que a página não repita no rodapé de
    contato o que já me disse no topo, para não sentir que voltei ao início.

### José (dono da marca)

18. Como dono da marca, quero revisar identidade e discurso separadamente, para que este
    trabalho mexa só no volume do texto, não na voz.
19. Como dono da marca, quero aprovar caso a caso qualquer afirmação apagada por inteiro, para
    não perder um argumento de venda sem querer.
20. Como dono da marca, quero que o orçamento de Sinal continue com um Acento por Peça, para que
    a remoção do bloco de estatísticas não deixe "Sobre" sem ação marcada nem com duas.
21. Como dono da marca, quero que a reatribuição do Acento de "Sobre" fique registrada, para
    ninguém achar que foi um deslize.
22. Como dono da marca, quero que a esteira de aplicativos não introduza nenhuma quinta cor nem
    sombra, para a paleta continuar fechada nas quatro do manual.
23. Como dono da marca, quero que a contagem de botões de ação da página não mude, para o funil
    de contato continuar o mesmo.
24. Como dono da marca, quero ver a página rodando antes de aprovar, para julgar o corte com
    meus próprios olhos.
25. Como dono da marca, quero que o trabalho fique na branch de redesign até eu decidir
    publicar, para não expor uma versão pela metade.
26. Como dono da marca, quero que a esteira tenha nome próprio no vocabulário, para não
    confundir com o carrossel que já rola os botões de filtro.
27. Como dono da marca, quero que o texto do Descritor travado à Assinatura permaneça intocado,
    para a marca do cabeçalho não mudar de peça para peça.
28. Como dono da marca, quero que o resultado seja avaliado pela minha leitura da página, não
    por uma meta de contagem de palavras, para cortar pelo que soa bem e não pelo número.

### Quem mexer no código depois

29. Como pessoa que abrir este repo depois, quero a esteira de aplicativos descrita como padrão
    de interação, para não reinventar um carrossel diferente na próxima seção.
30. Como pessoa que for somar um terceiro case em "Trabalhos", quero uma nota dizendo para
    adotar a mesma esteira a partir daí, para a seção não crescer empilhada para sempre.
31. Como pessoa que for editar "Sobre", quero saber que o Acento da seção mudou de alvo, para
    não recolocar vermelho nos números.
32. Como agente implementando este spec, quero o protocolo de verificação manual escrito, para
    conferir o resultado sem inventar um método.
33. Como pessoa revisando o resultado, quero comparar a altura da página antes e depois, para
    medir o ganho de rolagem.

## Implementation Decisions

### Escopo e módulos tocados

- O trabalho é feito na branch `redesign-tinta`, sobre o resultado da TINTA. Não sai para o ar
  sem José ver rodando. Sem push.
- Módulos afetados: o documento único da página (nós de texto, os quatro modais de app, a marcação
  da seção de aplicativos, o bloco de estatísticas de "Sobre", a `<meta>` de descrição e a
  descrição de compartilhamento); a folha de estilo (layout e controles da esteira, remoção das
  regras do bloco de estatísticas e das regras de colapso da grade de apps); o bloco de script
  embutido (navegação da esteira, remoção da lógica de expandir/colapsar a grade).
- Não são módulos deste spec, mas recebem um registro por consequência: a tabela de orçamento de
  vermelho no spec da TINTA (linha de "Sobre") e o registro de decisão da TINTA.

### Deduplicação — um lugar canônico por fato

Cada fato repetido fica no lugar indicado e sai dos demais. José confirma os casos marcados.

| Fato | Lugar canônico | O que sai |
| --- | --- | --- |
| "4 anos de experiência" | a faixa de prova | o bloco de estatísticas (removido de qualquer modo); a menção na meta é encurtada |
| Clientes Acer / Foxconn / Indorama | a faixa de prova | a enumeração no primeiro parágrafo de "Sobre" e o parêntese "(que monta os iPhones da Apple)" |
| Rótulo "Disponível para novos projetos" | a primeira dobra | a repetição no cartão de contato — *confirmar com José* |
| "Respondo em até 1 dia útil" + "sem compromisso" | os pontos da primeira dobra | a repetição no parágrafo de contato |
| Bordão "da ideia à entrega" (quatro variações) | a lead da primeira dobra | a lead de "Trabalhos" e a menção no lead de "Aplicativos"; a meta mantém uma forma curta |
| "rápido / bom no celular" | o primeiro card de serviço | a repetição no "O que foi feito" do case CT Israel Dayan |
| "código organizado / prazo realista" | o bloco "Como funciona" | a repetição no segundo parágrafo de "Sobre" |
| Bordão "sob medida" | o Descritor (travado pela TINTA) e o `<title>` | opcional: variar o H1 — baixa prioridade |
| Texto das chamadas de ação | todos os botões ficam | apenas alinhar: navegação e primeira dobra passam a usar a mesma frase; as outras duas já são distintas |

### Aperto de prosa

- Diretriz, não porta rígida: no máximo duas frases por parágrafo; nada de frase-parágrafo
  corrida; sem floreio ("Fique à vontade para testar", o parêntese da Apple).
- **Modais de app** (maior alvo): o parágrafo de descrição vira **uma frase** de posicionamento
  (o que é e para quem); a lista de recursos carrega os detalhes, sem repetir as palavras do
  parágrafo. A frase "os dados ficam na sua máquina", hoje reescrita nos quatro modais, aparece
  **uma vez** — na abertura da seção de aplicativos ou como um único item padronizado. A linha
  de metadados "Windows 10 ou superior · Instalador .exe", idêntica nos quatro, permanece.
- Primeira dobra: a lead perde a última oração ("sem intermediário e sem jargão"); o ponto
  "Você fala direto comigo" já cobre isso.
- Lead da seção de aplicativos: reduzida a uma frase.
- Case Inácio Móveis: o "O desafio" (narrativa de ~28 palavras) cai para uma frase.
- Cards de serviço: mantêm parágrafo e lista, mas o parágrafo vira gancho curto e a lista não
  repete as palavras dele.
- "Sobre": os dois parágrafos são fundidos num par enxuto — o primeiro diz o que faz e onde, o
  segundo diz o que isso rende num projeto pequeno e a formação.
- Trajetória (dentro do bloco recolhido): a progressão de cargos na Fitec é agrupada num
  intervalo único, reduzindo de sete para cerca de três linhas. Prioridade menor.
- Descrição da página e descrição de compartilhamento: a segunda frase de enchimento sai; as
  duas continuam idênticas entre si.
- A voz não muda. O manual traz tom de voz e bios prontas, mas isso não está no repo e não entra.

### Esteira de aplicativos

- A grade de cards e o botão "Ver os N apps" dão lugar a uma **esteira**: faixa horizontal com
  encaixe de rolagem, cada card alinhando no início. O botão de expandir e sua lógica de
  colapso saem.
- A barra de filtro de categoria permanece, com sua navegação de transbordo atual (que rola os
  **botões de filtro**, não os cards — intocada). Filtrar passa a mostrar e esconder cards
  dentro da esteira.
- Script mínimo novo: controles anterior/próximo que rolam a esteira por uma largura de card, e
  um indicador de posição opcional. Reaproveita o padrão de navegação que o script já tem para o
  transbordo dos filtros.
- Conformidade com a TINTA: os controles da esteira são tratados como Fio (contorno de 1 px em
  divisor, ou 2 px em tinta), raio zero, sem sombra. O Acento da seção continua sendo **o filtro
  ativo** — o filtro sobrevive, então o orçamento não muda aqui. As bolinhas da moldura já são
  cinza pela TINTA.
- Rolagem suave só sob preferência de movimento não-reduzido.
- Desktop: cerca de 2,5 cards visíveis. Mobile: cerca de 1,15 (espia o próximo).
- **Vocabulário:** a faixa de cards é a **esteira**; "carrossel" continua sendo só o transbordo
  dos botões de filtro. Vale uma entrada no glossário e/ou uma linha no registro de decisão.
- Ganho esperado: menos um clique e os quatro produtos visíveis de uma vez; altura parecida com
  a da grade colapsada de hoje. É remoção de interação, não grande economia de rolagem.

### Remoção do bloco de estatísticas em "Sobre"

- O bloco de três estatísticas (anos, apps, formação) sai — cada número já está na prosa ao lado
  ou na faixa de prova.
- **Consequência de marca:** o orçamento de vermelho da TINTA fixa "os números das estatísticas"
  como o Acento da seção "Sobre". Com o bloco fora, o Acento passa para o **controle que abre a
  trajetória completa**, o único elemento de ação da seção. Alternativa registrada: deixar
  "Sobre" sem Acento (o orçamento já admite seções assim — a faixa de prova e o rodapé).
- A reatribuição é registrada por José: nota nos comentários do ticket de vermelho da TINTA ou
  uma linha nova no registro de decisão.

### "Trabalhos" permanece empilhado

- Com apenas dois cases, "Trabalhos" **não** vira esteira: o custo de script não se paga e
  esconderia metade do conteúdo atrás de interação, contra o objetivo de escaneabilidade. Os
  cards seguem empilhados, com o lado da imagem alternando como hoje.
- A copy encurtada já reduz a altura dos cards. A nota de código que orienta somar um terceiro
  case ganha uma linha: a partir do terceiro, adotar a mesma esteira.

## Testing Decisions

**Decisão: nenhuma seam automatizada é introduzida. A verificação é manual.** Herdado da TINTA e
pela mesma razão: o repo não tem gerenciador de pacotes, runner nem integração contínua — o site
inteiro são dois arquivos servidos estaticamente. Qualquer seam seria nova, e a mais barata ainda
traria um ecossistema de dependências para um projeto que não tem nenhuma.

**O que seria um bom teste aqui.** Comportamento externo, não texto de arquivo: o que o navegador
desenhou e o que o visitante consegue fazer — a esteira rola e encaixa, o filtro mostra os cards
certos, os controles respondem ao teclado, a seção "Sobre" tem exatamente um elemento vermelho,
a página ficou mais curta. Uma varredura textual sobre o HTML ou o CSS seria uma seam mais baixa
e enganosa: passaria com o layout quebrado.

**Módulos verificados:** a esteira de aplicativos (rolagem, encaixe, filtro, controles, teclado,
movimento reduzido), a seção "Sobre" (bloco removido, Acento reatribuído, contagem de vermelho),
e a página inteira (altura antes/depois, ausência de fato repetido entre seções, voz preservada).

**Prova de arte anterior:** o "Protocolo de verificação manual" do spec da `redesign-tinta` — a
mesma abordagem de servir a página em duas larguras, checar o console, contar o vermelho seção a
seção, emular esquema escuro e movimento reduzido, e navegar por teclado conferindo o foco.

### Protocolo de verificação manual

1. Servir a página localmente e abrir em 1440 px e em 390 px de largura.
2. Console do navegador sem erros; nenhuma imagem falhando ao carregar.
3. Rolar a página inteira conferindo a tabela de deduplicação: nenhum fato aparece em duas
   seções. Comparar a altura total contra a versão anterior (guardar as mudanças e medir).
4. Seção de aplicativos: o filtro mostra e esconde os cards certos; a esteira rola e encaixa;
   os controles anterior/próximo funcionam; são alcançáveis e operáveis por teclado; o foco
   fica visível; sob movimento reduzido a esteira pula sem rolagem suave; no mobile aparece um
   card e a espia do próximo.
5. "Sobre": o bloco de estatísticas sumiu; o único elemento vermelho da seção é o controle da
   trajetória. Contar os elementos vermelhos seção a seção contra a tabela de orçamento da TINTA.
6. Emular preferência de esquema escuro: a página não muda.
7. Emular preferência de movimento reduzido: as entradas por rolagem aparecem sem transição.
8. Navegar por teclado do topo ao rodapé: o indicador de foco continua visível em todos os
   alvos, incluindo os novos controles da esteira.
9. Ler cada string alterada: a voz é a mesma de antes, apenas mais curta.

## Out of Scope

- **Mudança de voz ou de tom.** O manual traz tom de voz e quatro versões de bio prontas; nada
  disso está no repo e nada disso entra. Este trabalho encurta o texto que já existe, no jeito em
  que já é dito.
- **Conteúdo novo ou removido em bloco.** Nenhuma seção, case ou app é adicionado. Apagar uma
  afirmação inteira só acontece com o aval de José, caso a caso.
- **Esteira em "Trabalhos".** Enquanto forem dois cases, a seção segue empilhada.
- **Alteração do Descritor.** O texto travado à Assinatura no cabeçalho não muda.
- **Tokenização de espaçamento.** O ritmo atual permanece.
- **Teste automatizado e integração contínua.** Decidido acima.
- **Metas numéricas de compactação.** Sem alvo de porcentagem ou de contagem de palavras; o
  aceite é a leitura de José na página rodando.
- **Publicar.** O trabalho fica na branch `redesign-tinta`. O merge é decisão de José, depois de
  ver rodando.
- **Peças fora do site.** Não se aplicam.

## Further Notes

- **O guia de tom de voz e as bios não estão no repositório.** Vivem só no projeto de design
  externo. Por isso a voz é preservada como está: não há material no repo para reescrever contra.
- **A esteira é um padrão de interação que o registro de decisão da TINTA não cobre.** O ADR
  trata de efeito estático (sombra, degradê, brilho); movimento não é mencionado, e as entradas
  por rolagem já foram mantidas na TINTA pela mesma leitura. Ainda assim, vale uma linha no
  registro documentando a esteira e o nome escolhido, para a próxima pessoa não criar um
  carrossel diferente.
- **A remoção do bloco de estatísticas edita um contrato documentado** — a tabela de orçamento
  de vermelho da TINTA. Não é um efeito colateral silencioso: a linha de "Sobre" é reescrita e a
  reatribuição do Acento é registrada.
- **O ganho de "Trabalhos" vem só da copy.** Sem esteira e sem cortar um case, o que encurta a
  seção é a frase única no "O desafio" e o alinhamento das leads. Quando entrar um terceiro case,
  a esteira passa a valer.
- **"Disponível para novos projetos" no cartão de contato é o único item de deduplicação com
  dúvida real.** O cartão é o ponto de conversão; um lembrete fresco de disponibilidade ali tem
  valor. Fica marcado para José decidir.
- **A altura da grade de aplicativos hoje já é curta** por causa do colapso em dois cards. A
  esteira não encurta muito — ela tira o clique e mostra os quatro. O ganho de rolagem maior
  vem da deduplicação e do aperto de prosa, não da esteira.
