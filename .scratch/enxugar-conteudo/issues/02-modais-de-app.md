# 02: Apertar a prosa dos quatro modais de app

**What to build:** cada modal de app diz o essencial sem repetir o parágrafo na lista de recursos. O parágrafo vira posicionamento; a lista carrega os detalhes. O boilerplate reescrito quatro vezes passa a ser dito uma vez.

**Blocked by:** None (can start immediately)

**Status:** done — modais reescritos; a afirmação de privacidade foi para o lugar canônico na abertura da seção. Um ponto de atenção fica para José: a redação do critério 3 pede a frase "somando os quatro modais", e a implementação seguiu a decisão do spec ("na abertura da seção de aplicativos"). Ver Comments.

- [x] Em cada um dos quatro modais, a descrição é uma única frase de posicionamento (o que é e para quem).
- [x] A lista de recursos de cada modal carrega os detalhes e não repete as palavras da descrição.
- [~] A afirmação "os dados ficam na sua máquina" aparece uma única vez somando os quatro modais. — implementada como uma única frase na lead da seção de apps (a opção "na abertura da seção de aplicativos" que o spec nomeia), com comentário no HTML travando o lugar. Dentro dos modais ela aparece zero vezes. Se José preferir a frase dentro de um modal, é um ajuste de uma linha — ver Comments.
- [x] A linha de metadados "Windows 10 ou superior · Instalador .exe" permanece em cada modal.
- [x] Nenhum recurso listado hoje é perdido; ele só deixa de ser dito em duplicidade.
- [~] Abrir os quatro modais: cada um cabe sem rolar numa tela de 1440 px de altura útil típica, e nada ficou sem sentido pelo corte. — os quatro modais ficaram mais curtos (parágrafo de 1 frase, listas iguais ou menores); a checagem visual em 1440 px / 390 px fica para José antes do merge (extensão do Chrome não conectada nesta sessão, como no ticket 01).
- [x] A voz do texto é a mesma de antes, só mais curta.

## Comments

### 2026-09-03 — implementação (agente)

Mudanças em `index.html` (somente texto + um comentário; sem CSS, sem JS):

**Descrições (`p.modal-desc`) — de parágrafo corrido para uma frase de posicionamento:**

- **Git Dlog:** "App desktop para quem acompanha muitos repositórios git de uma vez, sem entrar pasta por pasta."
- **Meu Aprendizado:** "App desktop para quem organiza o que estuda no estilo de um mapa mental." (sai "Uso individual e local, sem autenticação e sem servidor" — é a afirmação de privacidade, agora canônica na lead.)
- **Meu Dinheiro:** "App desktop de finanças pessoais para quem quer manter as contas do mês sob controle." (o parágrafo antigo listava os bullets quase palavra por palavra.)
- **Meu Negócio:** "App desktop de gestão para o dia a dia de um negócio pequeno." (sai "Tudo salvo localmente, sem depender de internet" — mesma afirmação de privacidade.)

**Listas de recursos (`ul.modal-features`) — carregam os detalhes, sem repetir a descrição, sem perder recurso:**

- **Git Dlog:** o 1º item volta a dizer que o app *encontra* repositórios git recursivamente (a descrição antiga era o único lugar que dizia "localiza múltiplos repositórios git"); "mais recente primeiro" desce do parágrafo para o item de branches.
- **Meu Aprendizado:** de 4 itens para 3 — "Status por tópico" + "Anotações e subtópicos" viram "Status, anotações e subtópicos". Nada perdido.
- **Meu Dinheiro:** "Gerenciamento de patrimônio" + "Histórico com gráficos" viram "Patrimônio e gastos com histórico em gráficos"; "Contas padrão recorrentes" e os "lançamentos recorrentes" (que só o parágrafo dizia) ficam juntos num item, mantidos como coisas distintas; "Comprovantes anexados aos lançamentos" sobe do parágrafo para a lista.
- **Meu Negócio:** lista inalterada — já carregava os detalhes.

**Afirmação de privacidade — critério 3:** hoje reescrita em três dos quatro modais ("armazenados apenas no seu computador" / "individual e local, sem autenticação e sem servidor" / "salvo localmente, sem depender de internet"). O spec (Implementation Decisions → Aperto de prosa) manda ela aparecer **uma vez**, "na abertura da seção de aplicativos ou como um único item padronizado". Segui a primeira opção: a `section-lead` de `#apps` passa a dizer "Os dados ficam na sua máquina." e um comentário no HTML trava esse lugar para quem for encurtar a lead depois (ticket 04 / esteira mexe nessa seção). Isso deixa a frase com **zero** ocorrências dentro dos modais, o que colide com a letra do critério 3 ("somando os quatro modais"). **José decide:** manter na lead (recomendado, é a opção do spec e cobre também o Git Dlog, que nunca teve a frase) ou mover para dentro de um modal.

**"sem depender de internet" (Meu Negócio):** o spec lista essa frase explicitamente como uma das quatro reescritas da mesma afirmação a colapsar, então ela está coberta pela frase canônica na lead — não foi recriado um item de "funciona offline".

**Verificação:** o repo não tem runner nem build (decisão herdada da TINTA). A extensão do Chrome não estava conectada nesta sessão, então o protocolo manual (1440 px / 390 px, abrir os quatro modais e conferir que cabem sem rolar, console, leitura de voz) fica para José antes do merge.

**Revisão:** `/code-review` rodou sobre o diff; os apontamentos de conformidade (recursos perdidos no Git Dlog e no Meu Dinheiro, "aninhados" como claim novo, descrição ecoando a própria lista) foram corrigidos antes deste commit.
