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

- [x] O trabalho acontece numa branch dedicada; a branch principal permanece intocada e o site publicado continua no ar.
- [x] Os quatro valores da paleta — papel, tinta, sinal e cinza — e as rampas derivadas estão declarados como token no ponto único de definição.
- [x] A página inteira renderiza sobre papel claro com texto em tinta; nenhum azul ou verde vindo de token sobrevive.
- [x] O esquema de cor escuro automático foi removido por inteiro: emular a preferência de esquema escuro não altera nada na página.
- [x] A declaração de esquema de cor da página anuncia apenas claro, para que controles nativos do navegador acompanhem.
- [x] Nenhum valor de cor escrito literalmente sobrevive no stylesheet — brancos puros, transparências, o verde-menta do ponto de status e o azul-claro de hover viraram token.
- [x] O degradê do cartão de contato foi removido e substituído por campo de papel; em nenhum ponto da página existe campo vermelho cheio.
- [x] Existem tokens de raio, valendo zero em todos os degraus.
- [x] O espaçamento não foi tocado: o ritmo atual continua igual e a página segue respondendo à largura da tela.

## Comments

Implementado no commit `899a912`, na branch `redesign-tinta`. Sem push: o merge é decisão do
José, depois de ver rodando.

Duas decisões que se afastam da letra do checklist e ficam registradas para o 07 não tropeçar:

- **O verde-menta do ponto de status e o azul-claro de hover foram removidos, não tokenizados.**
  Os dois só existiam dentro de sobrescritas do cartão de contato — `.contact-card .badge-available
  .dot` e `.contact-card .btn-primary:hover` — que existiam apenas para o conteúdo sobreviver sobre
  o campo vermelho. Com o degradê fora, o cartão é papel e o estilo padrão da página se aplica: as
  cinco sobrescritas saíram inteiras. Tokenizar uma regra morta seria pior. O critério "nenhum valor
  literal sobrevive" continua valendo.
- **`--scrim` nasceu unificado e foi desfeito.** A primeira versão colapsava as duas opacidades de
  véu (0.45 da gaveta do menu, 0.5 do modal) em um valor só. O code review apontou que isso é
  mudança de comportamento pegando carona num ticket de cor, e a correção virou `--scrim-nav` e
  `--scrim-modal` nas opacidades originais.

Duas observações que o code review levantou e que ficaram como estão de propósito:

- Os quatro degraus de raio não são referenciados por nenhuma declaração — é a metade *expandir*
  desta fatia. Quem liga é o ticket 04.
- `--brand` carrega sinal e `--accent` carrega tinta. Dívida declarada, paga no 07.

Verificação: só estática. A extensão do Chrome não estava conectada, então a página não foi aberta
nem o esquema escuro emulado. Conferido que não há literal de cor fora do bloco de tokens, nenhum
bloco `prefers-color-scheme`, nenhum token referenciado sem definição, chaves balanceadas, e os dois
arquivos servindo 200 em servidor local. O protocolo visual completo é do ticket 07.

Os valores da paleta foram escolhidos com o José nesta sessão: o design system é externo ao repo e
não traz hex nenhum. Papel `#f5f2ec` / `#ede9e1`, tinta `#111111`, sinal `#d6291e`, cinza `#6e6a63`,
divisor `#d8d3c9`.
