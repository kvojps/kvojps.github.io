# 07: Contrair — renomear os tokens legados

**What to build:** Nada muda para o visitante. Esta fatia paga a dívida deliberada aberta no ticket
01: os nomes dos tokens voltam a dizer a verdade sobre o que carregam, para que quem for editar o
CSS depois não pinte de vermelho uma coisa chamada de verde.

É a metade **contrair** do expand–contract. Vem por último porque renomear enquanto outras fatias
editam o mesmo arquivo só gera conflito, e porque só agora se sabe quais tokens sobreviveram.

Ao final desta fatia o trabalho está pronto para José olhar, e o protocolo de verificação manual do
spec é executado por inteiro aqui.

**Blocked by:** 03 (Tipografia Archivo), 04 (Forma da marca), 05 (Orçamento de vermelho, verde e imagem), 06 (Assinatura e ativos de marca).

**Status:** ready-for-human

- [x] Nenhum nome de token legado sobrevive: cada nome descreve a cor ou o papel que realmente carrega.
- [x] Não restam aliases apontando de nome antigo para valor novo.
- [x] A página renderiza exatamente como antes da renomeação — esta é mudança de nome, não de valor.
- [ ] Servida localmente, a página foi conferida em 1440 px e em 390 px de largura.
- [ ] O console do navegador não reporta erro nem imagem falhando.
- [x] Os elementos vermelhos foram contados seção a seção contra a tabela de orçamento do spec, e batem.
- [ ] Emular a preferência de esquema escuro não altera a página.
- [ ] Emular a preferência de movimento reduzido faz as entradas por rolagem aparecerem sem transição.
- [ ] O indicador de foco continua visível em todos os alvos ao navegar por teclado.
- [x] O trabalho está na branch dedicada, sem push: o merge é decisão de José, depois de ver rodando.

Os cinco itens sem marca são o protocolo visual ao vivo, que precisa de navegador — a extensão do
Chrome não estava conectada nesta sessão. Ver `## Comments`: a fatia é rename byte a byte idêntico e
não pode regredir nenhum deles; a conferência ao vivo fecha junto com o critério 10, quando José
abrir rodando antes do merge.

## Comments

Implementado na branch `redesign-tinta`, sem push. Só `style.css` mudou; `index.html` intocado.

**A renomeação, valor a valor idêntica:**

- `--brand` → `--signal` (`#d6291e`), o vermelho da ação. Casa com `--on-signal`, que já
  pressupunha esse nome.
- `--brand-dark` → `--signal-dark` (`#a81f16`), o degrau escuro da rampa de sinal.
- `--brand-tint` **removido**, não renomeado. Era `#ede9e1`, byte a byte o mesmo valor de
  `--bg-alt`, e o comentário do ticket 01 já dizia "papel, não sinal". Único uso (`.service-icon`)
  agora aponta para `--bg-alt`. Um `--signal-tint` seria outro nome mentiroso; um token de papel à
  parte para um só campo de ícone seria generalização especulativa. O ponto único de definição
  torna trivial recriar um token de papel se surgir necessidade real.
- `--font-display` **removido**. Era `var(--font-body)` puro — um alias, exatamente o que o
  critério proíbe. A seam foi aberta no ticket 01 para ser resolvida aqui; fonte única é regra de
  marca (ADR 0001), o papel de título é peso 900, não família. As ~20 declarações
  `font-family: var(--font-body)` em títulos ficaram — redundantes com a herança do `body`, mas
  removê-las passaria do escopo "mudança de nome, não de valor".

Comentários do bloco `:root` reescritos para não ressuscitar os nomes mortos.

**Code review (Standards + Spec):** Standards sem violação. Spec sem item errado; registrou que a
fusão `--brand-tint`→`--bg-alt` é um passo além de um rename 1:1 — baixa severidade, defensável
pelos motivos acima, anotado aqui em vez de implícito.

**Verificação estática, exaustiva:**

- Nenhum `--brand`, `--brand-dark`, `--brand-tint`, `--font-display` ou `--accent*` sobrevive no
  CSS, nem em comentário.
- Todo `var(--…)` resolve para token definido; nenhum token órfão; chaves balanceadas (248/248).
- Nenhuma `box-shadow`/`text-shadow`/`drop-shadow`, nenhum `gradient`, nenhum `border-radius`
  não-nulo fora de `50%` e dos tokens `--radius-*` (todos zero).
- Nenhum bloco `prefers-color-scheme`; `color-scheme: light` no lugar.
- `@media (prefers-reduced-motion: reduce)` intacto, zerando a transição de `.reveal`.
- Nenhuma sobrescrita de `outline` — o anel de foco padrão do navegador segue intacto.
- Servida localmente (`python -m http.server`): `index.html`, `style.css`, `assets/avatar.png`,
  `assets/monograma.png` todos 200.

**Orçamento de vermelho, contado seção a seção contra a tabela do spec** (só `--signal` /
`--signal-dark` estáticos; hover não conta):

| Seção | Esperado | No código |
| --- | --- | --- |
| Cabeçalho | o botão de orçamento | `.nav-cta` / `.header-cta` bg ✓ |
| Primeira dobra | o botão primário | `.btn-primary` bg ✓ |
| Faixa de prova | nenhum | nenhum ✓ |
| Serviços | os números do processo | `.process-num` bg ✓ |
| Trabalhos | o botão da chamada intercalada | `.cta-inline .btn-primary` bg ✓ |
| Aplicativos | o filtro ativo | `.filter-btn.active` bg ✓ |
| Sobre | os números das estatísticas | `.about-stats dt` cor ✓ |
| Contato | o botão do cartão de contato | `.contact-card .btn-primary` bg ✓ |
| Rodapé | nenhum | nenhum ✓ |
| Modal | o botão de download | `.modal-footer .btn-download` bg ✓ |

**O que não deu para fazer:** a extensão do Chrome não estava conectada (mesma parede do ticket
01), então o protocolo visual ao vivo — abrir em 1440 px e 390 px, ler o console, emular esquema
escuro e movimento reduzido, navegar por teclado — não foi executado. Esta fatia é rename puro:
todo valor é byte a byte idêntico ao estado pós-ticket 06, `index.html` e o JS não foram tocados, e
nenhum seletor `@media`/`prefers-*` mudou — a renomeação não tem como alterar layout, console,
orçamento de vermelho, esquema escuro, movimento reduzido ou foco. A conferência ao vivo é a que o
José faz antes do merge (critério 10), e é onde esses cinco itens fecham.
