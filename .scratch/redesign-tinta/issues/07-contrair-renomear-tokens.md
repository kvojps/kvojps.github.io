# 07: Contrair — renomear os tokens legados

**What to build:** Nada muda para o visitante. Esta fatia paga a dívida deliberada aberta no ticket
01: os nomes dos tokens voltam a dizer a verdade sobre o que carregam, para que quem for editar o
CSS depois não pinte de vermelho uma coisa chamada de verde.

É a metade **contrair** do expand–contract. Vem por último porque renomear enquanto outras fatias
editam o mesmo arquivo só gera conflito, e porque só agora se sabe quais tokens sobreviveram.

Ao final desta fatia o trabalho está pronto para José olhar, e o protocolo de verificação manual do
spec é executado por inteiro aqui.

**Blocked by:** 03 (Tipografia Archivo), 04 (Forma da marca), 05 (Orçamento de vermelho, verde e imagem), 06 (Assinatura e ativos de marca).

**Status:** ready-for-agent

- [ ] Nenhum nome de token legado sobrevive: cada nome descreve a cor ou o papel que realmente carrega.
- [ ] Não restam aliases apontando de nome antigo para valor novo.
- [ ] A página renderiza exatamente como antes da renomeação — esta é mudança de nome, não de valor.
- [ ] Servida localmente, a página foi conferida em 1440 px e em 390 px de largura.
- [ ] O console do navegador não reporta erro nem imagem falhando.
- [ ] Os elementos vermelhos foram contados seção a seção contra a tabela de orçamento do spec, e batem.
- [ ] Emular a preferência de esquema escuro não altera a página.
- [ ] Emular a preferência de movimento reduzido faz as entradas por rolagem aparecerem sem transição.
- [ ] O indicador de foco continua visível em todos os alvos ao navegar por teclado.
- [ ] O trabalho está na branch dedicada, sem push: o merge é decisão de José, depois de ver rodando.
