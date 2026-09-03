# 01: Deduplicar a proposição repetida entre seções

**What to build:** cada fato da proposição aparece num único lugar canônico — o mais forte — e some dos outros. A página para de repetir a mesma informação de seção em seção. Somente texto; nenhuma estrutura, seção ou botão é removido.

**Blocked by:** None (can start immediately)

**Status:** done — os itens marcados `[~]` (2 e 6) dependem do corpo de "Sobre" e são concluídos pelo ticket 03, que está `Blocked by: 01`. Este ticket fixou os lugares canônicos e fez tudo o que seu escopo (só texto, "Sobre" congelado) permite.

- [x] O Rótulo "Disponível para novos projetos" aparece só na primeira dobra; o cartão de contato não o repete (José confirmou: remover do cartão — ver Comments).
- [~] "4 anos" de experiência e o trio de clientes Acer / Foxconn / Indorama aparecem só na faixa de prova. — faixa de prova fixada como lugar canônico; a `<meta>` foi encurtada e não diz mais "4 anos". A remoção da enumeração e do parêntese no corpo de "Sobre" fica para o 03 (corpo de "Sobre" congelado aqui).
- [x] "Respondo em até 1 dia útil" e "sem compromisso" aparecem só nos pontos da primeira dobra; o parágrafo de contato não os repete.
- [x] O bordão "da ideia à entrega" aparece numa única variação na página; as leads de "Trabalhos" e de "Aplicativos" não o repetem.
- [x] "rápido / bom no celular" aparece só no primeiro card de serviço; o "O que foi feito" do case CT Israel Dayan não o repete.
- [~] "código organizado / prazo realista" aparece só no bloco "Como funciona". — o alvo de remoção é o 2º parágrafo de "Sobre", congelado neste ticket; sai no 03. O bloco "Como funciona" já carrega o "como o trabalho é feito" e não recebeu copy nova.
- [x] As chamadas de ação usam texto alinhado, sem quatro variações quase iguais; a quantidade de botões não muda. (nav, header e primeira dobra passam a usar "Pedir orçamento"; "Falar sobre o seu projeto" e "Enviar e-mail" já eram distintas e ficam.)
- [x] A descrição da página e a de compartilhamento perdem a frase de enchimento e seguem idênticas entre si.
- [x] O corpo da seção "Sobre" não é alterado neste ticket (fica para o 03).
- [x] A voz do texto é a mesma de antes, só mais curta.

## Comments

### 2026-09-03 — implementação (agente)

Decisão de José (item 1): **remover** o Rótulo "Disponível para novos projetos" do cartão de contato. Fica só na primeira dobra.

Mudanças aplicadas em `index.html` (somente texto, sem CSS, sem JS):

- `<meta name="description">` e `<meta property="og:description">`: encurtadas e mantidas idênticas — sai "com 4 anos de experiência", sai a frase de enchimento "com acompanhamento direto"; "da ideia à entrega" fica na forma curta.
- Header CTA "Orçamento" e CTA da primeira dobra "Pedir um orçamento" → "Pedir orçamento", alinhando com a `nav-cta`.
- Lead de "Trabalhos" ("Do primeiro rascunho até a publicação.") removida — era só o bordão da primeira dobra repetido.
- Lead de "Apps": sai "— da ideia à instalação na máquina do usuário".
- Case CT Israel Dayan, "O que foi feito": sai "— rápida e feita para o celular, que é por onde o aluno chega" (fica no 1º card de serviço).
- Cartão de contato: removido o `span.badge-available`; o parágrafo perde "Respondo em até 1 dia útil, sem compromisso" (fica nos pontos da primeira dobra).

Itens marcados `[~]` dependem do corpo de "Sobre", que este ticket não toca (linha "O corpo da seção 'Sobre' não é alterado neste ticket"). São concluídos pelo 03, que está `Blocked by: 01` justamente para herdar os lugares canônicos fixados aqui.

Verificação: o repo não tem runner nem build (decisão herdada da TINTA — ver spec, "Testing Decisions"); a verificação é manual e é a leitura de José na página rodando. A extensão do Chrome não estava conectada nesta sessão, então o protocolo manual (1440 px / 390 px, console, contagem de vermelho, teclado) fica para José antes do merge.
