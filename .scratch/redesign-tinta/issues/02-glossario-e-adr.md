# 02: Glossário da marca e registro de decisão

**What to build:** As regras da marca passam a estar escritas junto do código. Quem abrir este repo
daqui a seis meses encontra o vocabulário certo e entende por que a página é como é — em vez de
"consertar" o raio zero achando que é bug.

Vem cedo de propósito: fixa o vocabulário que as fatias seguintes usam nos seus próprios títulos e
descrições.

**Blocked by:** None (can start immediately).

**Status:** done

- [x] Existe um glossário na raiz do repo definindo os termos da marca: Tinta, Papel, Sinal, Cinza, Assinatura, Monograma, Descritor, Rótulo, Fio, Peça e Acento.
- [x] O glossário contém apenas definições de termo — nenhum detalhe de implementação, nenhuma decisão técnica, nenhum valor de cor como especificação.
- [x] Existe um registro de decisão explicando por que a direção TINTA foi escolhida e por que a direção alternativa foi rejeitada.
- [x] O registro lista as consequências difíceis de reverter: raio zero, fonte única, alinhamento à esquerda sempre, e o orçamento de 5% de vermelho.
- [x] O registro deixa explícito que essas restrições são regra de marca, não defeito de implementação.
- [x] A tradução de "um só elemento vermelho por peça" para "um acento por seção" está registrada como interpretação desta adaptação, não como regra do manual.

## Comments

Implementado na branch `redesign-tinta`, sem push.

- **O glossário nasceu como `CONTEXT.md` na raiz, não como um arquivo novo chamado "glossário".**
  `AGENTS.md` e `docs/agents/domain.md` já definem o glossário deste repo como `CONTEXT.md` na
  raiz; criar um `GLOSSARIO.md` à parte forkaria a convenção e deixaria duas fontes de vocabulário.
  O critério pede "um glossário na raiz" — é o que `CONTEXT.md` é.
- **O registro de decisão é `docs/adr/0001-direcao-tinta.md`**, seguindo a estrutura de ADR do
  repo (numeração sequencial, corpo curto). Primeiro ADR do projeto — `docs/adr/` nasce aqui.
- **A alternativa rejeitada foi lida como "manter a identidade de template do site".** O spec
  fala em "direção alternativa" mas o bakeoff que escolheu TINTA aconteceu dentro do design
  system, que é externo a este repo e não documentado aqui. O que este ADR pode honestamente
  registrar é a decisão que é deste repo: trocar a pele para TINTA em vez de deixar o site na
  identidade genérica com que nasceu. Não inventei detalhes de um comparativo que não tenho.
- **A tabela de orçamento seção a seção não foi copiada para o ADR.** Ela vive no spec
  (`.scratch/redesign-tinta/spec.md`); o ADR só registra que a leitura "peça = seção" é
  interpretação desta adaptação, não regra do manual, e aponta para onde a tabela está.

Verificação: os dois arquivos são prosa em markdown. Conferido que os 11 termos estão definidos em
`CONTEXT.md`, que não há literal de cor (`#…`) nem medida (`…px`) no glossário, e que o ADR cobre
as quatro consequências nomeadas no critério 4. Sem teste automatizado — o repo não tem
infraestrutura de teste e este ticket não produz código.

O code review (eixos Standards + Spec) rodou e apontou detalhe de implementação vazando para o
glossário mesmo sem hex nem px — tratamento tipográfico em `Assinatura`, `Rótulo` e `Fio`, e a
regra de hover em `Acento`. Corrigido: as definições foram enxugadas para dizer o que o termo é, o
intro caiu para duas frases, e a frase do hover ficou só no ADR (era duplicada nos dois arquivos).
No ADR: `preto` trocado por `tinta` (estava no `_Avoid_` de Tinta), a seção `## Status: Aceito`
removida (o formato do repo pede frontmatter com enum, não um `##` para um primeiro ADR recém-aceito),
e a seção de alternativa agora diz explicitamente que o comparativo entre direções de marca é do
design system e não deste repo.
