# 01: Camada de tokens TINTA e fim do esquema escuro

**What to build:** A landing page inteira passa a ser papel e tinta. Quem abrir o site vê a paleta
da marca em toda parte — fundo de papel claro, texto em tinta, vermelho de sinal onde antes havia
azul — em vez da identidade genérica de template.

Esta é a fatia de **expansão**: como toda cor da página já vem de token, redefinir os valores no
ponto único de definição recolore tudo de uma vez, sem varredura. Os nomes dos tokens continuam os
antigos e passam a mentir sobre o que carregam — dívida deliberada, paga no ticket 07.

Um detalhe que não pode esperar: o cartão de contato é pintado com um degradê entre as duas cores
de marca. Redefinir os tokens sem tocar nele produziria um campo vermelho cheio, que o manual
proíbe explicitamente. O degradê sai nesta fatia.

**Blocked by:** None (can start immediately).

**Status:** ready-for-agent

- [ ] O trabalho acontece numa branch dedicada; a branch principal permanece intocada e o site publicado continua no ar.
- [ ] Os quatro valores da paleta — papel, tinta, sinal e cinza — e as rampas derivadas estão declarados como token no ponto único de definição.
- [ ] A página inteira renderiza sobre papel claro com texto em tinta; nenhum azul ou verde vindo de token sobrevive.
- [ ] O esquema de cor escuro automático foi removido por inteiro: emular a preferência de esquema escuro não altera nada na página.
- [ ] A declaração de esquema de cor da página anuncia apenas claro, para que controles nativos do navegador acompanhem.
- [ ] Nenhum valor de cor escrito literalmente sobrevive no stylesheet — brancos puros, transparências, o verde-menta do ponto de status e o azul-claro de hover viraram token.
- [ ] O degradê do cartão de contato foi removido e substituído por campo de papel; em nenhum ponto da página existe campo vermelho cheio.
- [ ] Existem tokens de raio, valendo zero em todos os degraus.
- [ ] O espaçamento não foi tocado: o ritmo atual continua igual e a página segue respondendo à largura da tela.
