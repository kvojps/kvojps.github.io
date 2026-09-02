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

**Status:** ready-for-agent

- [ ] Cada seção da página exibe no máximo um elemento vermelho em repouso, conforme a tabela de orçamento do spec.
- [ ] A primeira dobra gasta seu vermelho no botão primário; o trecho destacado dentro do título ficou em tinta.
- [ ] A faixa de prova e o rodapé não têm nenhum vermelho.
- [ ] Nenhuma cor verde sobrevive em parte alguma da página.
- [ ] Os antigos sinais cromáticos de estado — disponibilidade, gratuidade, marcas de confirmação, marcadores de linha do tempo — agora são rótulos tipográficos com fio.
- [ ] O hover de card não desloca o elemento nem produz sombra: a borda e o título vão ao sinal.
- [ ] Screenshots dos trabalhos entregues e dos aplicativos aparecem dessaturados, com leve ganho de contraste.
- [ ] Interagir com o card devolve a cor à imagem.
- [ ] Os ícones dos aplicativos próprios permanecem coloridos em todos os lugares onde aparecem — são marcas de produto, não fotografia.
- [ ] As animações de entrada por rolagem continuam funcionando, e continuam desligadas para quem pede movimento reduzido no sistema.
