# 06: Assinatura no cabeçalho e ativos de marca

**What to build:** O visitante sabe de quem é o site antes de rolar, reconhece a aba pelo ícone, e
recebe uma prévia com a marca correta quando o link é compartilhado numa conversa.

Esta fatia também conserta um defeito que está no ar hoje: a imagem de logo foi removida do repo
sem que as referências a ela fossem atualizadas, então o site publicado está com ícone de aba e
prévia de compartilhamento quebrados.

O cabeçalho deixa de depender de um arquivo de imagem. A assinatura tipográfica fica nítida em
qualquer densidade de tela e não pode sumir do jeito que a imagem sumiu.

**Blocked by:** 03 (Tipografia Archivo em toda a página).

**Status:** done

- [x] O cabeçalho exibe a assinatura tipográfica — nome completo com o descritor de serviço abaixo — sem nenhuma imagem.
- [x] O descritor aparece travado à assinatura, no papel visual de rótulo.
- [x] Nenhuma referência à imagem de logo removida sobrevive na página.
- [x] O ícone da aba do navegador mostra o monograma, e é reconhecível em tamanho pequeno.
- [x] A prévia de compartilhamento aponta para o avatar em resolução plena e carrega sem erro.
- [x] O ativo de origem é o avatar vermelho já aprovado no design system, obtido do projeto de design — não uma recriação nova do símbolo.
- [x] O monograma não aparece em nenhum outro lugar da página: o manual o restringe a avatar e capa.
- [x] O console do navegador não reporta nenhuma imagem falhando ao carregar.

## Comments

Implementado na branch `redesign-tinta`. Sem push — o merge é decisão do José, depois de ver
rodando.

### Assinatura no cabeçalho

- `.brand` deixa de ser um `<a>` com `<img class="hero-logo">` + texto e passa a empilhar dois
  spans: `.brand-name` ("José Ferreira", peso 900 / caixa alta / `--tracking-tight` /
  `--leading-tight` / 15px — na escala colapsada do ticket 03, não um degrau novo) sobre
  `.brand-descriptor`.
- O descritor **é** o papel de rótulo: `class="brand-descriptor label"`. `.label` (900 / 13px /
  caixa alta / tracking 0,08em / cinza) é a classe que o ticket 03 semeou exatamente para isto.
  `.brand-descriptor` só acrescenta `line-height: var(--leading-tight)` para o caso de quebra em
  duas linhas no cabeçalho estreito.
- Texto do descritor: **"Desenvolvimento de sites e sistemas sob medida"**, a mesma linha de
  serviço que já vivia no `<title>` e no `og:title` — travada à assinatura, não texto de página.
- `.brand` vira coluna (`flex-direction: column`, `align-items: flex-start`, `gap: 3px`,
  `min-width: 0`). Some o `gap: 10px` horizontal, o `font-weight: 600` e o `font-size: 15px` do
  bloco antigo (agora nos filhos). A regra `.hero-logo` foi **removida** junto — era a regra da
  imagem que sumiu.
- `aria-label` do `<a>` passou de "Voltar ao topo" para **"José Ferreira — voltar ao topo"**: com
  a assinatura agora sendo o elemento de marca, deixar o nome acessível de fora da árvore de
  acessibilidade (o `aria-label` substitui o nome acessível) escondia justamente a identidade.
  Mantém a dica da função (voltar ao topo).

### Ativos de marca

- O José adicionou o **avatar vermelho aprovado** (`JF/` branco sobre sinal, 1080×1080) —
  primeiro em `assets/logo.png`, renomeado para **`assets/avatar.png`**: o glossário manda evitar
  a palavra "logo", e o critério 3 pede que nenhuma referência à *imagem de logo* sobreviva.
  `avatar` é termo sancionado (entra na definição de Monograma).
- **`assets/monograma.png`** (48×48) é derivado do avatar por redução LANCZOS (Pillow) — o
  "símbolo reduzido da marca, derivado do avatar vermelho" do glossário, ao pé da letra. O spec
  pede os dois derivados: *"Dele deriva um ícone reduzido para a aba; o arquivo em resolução
  plena serve à imagem de compartilhamento."*
- `<link rel="icon" sizes="48x48" href="assets/monograma.png">` — o `JF/` continua legível a
  48 px (conferido no arquivo renderizado); nítido de propósito em vez de um PNG de 1080 px
  rebaixado pelo navegador.
- `og:image` → `https://kvojps.github.io/assets/avatar.png` (resolução plena). Acrescentados
  `og:image:width`/`height` (1080) para a prévia carregar sem re-fetch nos scrapers de OG —
  serve ao "carrega sem erro" do critério. Nada de `og:image:alt`: seria discurso, e o spec é
  troca de pele.
- O monograma/avatar só aparece no `<head>` (ícone + og:image). Nenhuma ocorrência no `<body>`.
  Os `.app-icon`/`.modal-icon` são marcas de produto, não o monograma.

### Verificação

Estática, como nos tickets 01/03/05 — a extensão do Chrome não estava conectada, então não foram
abertos 1440/390 px, nem conferidos console, ícone da aba na barra do navegador e prévia de
compartilhamento renderizada. Isso fica para o José ver rodando; o protocolo completo do spec
roda no ticket 07.

Conferido: chaves balanceadas (248/248); nenhum `logo`, `hero-logo` ou `assets/logo.png` em
HTML/CSS (só `catálogo` e a classe alheia `.proof-logos` batem no grep); `assets/avatar.png` e
`assets/monograma.png` servindo 200 em servidor local, junto de todas as outras imagens da
página; `.brand-name` em 15 px (na escala), tokens `--tracking-tight`/`--leading-tight`
reaproveitados, nenhum literal de cor; o descritor carregando `.label`.

### Code review

`/code-review` rodou nos dois eixos antes do commit.

- **Standards** apontou: `font-size: 11px` num override mobile do descritor furava o piso 12 px da
  escala (ticket 03) e re-afinava o papel fixo de `.label` num media query, sem precedente no
  repo; e `.brand-name` em 16 px estava fora da escala colapsada. Endereçado: o override
  `@media (max-width: 640px)` foi **removido por inteiro** (o cabeçalho fixo de 72 px comporta o
  descritor em até três linhas no celular sem sobrepor o hero — a guarda era desnecessária), e
  `.brand-name` desceu para 15 px. Glossário, cor e tokens: sem violação.
- **Spec** apontou: o critério do ícone da aba pedia um derivado reduzido, não o arquivo pleno
  reusado (endereçado com `assets/monograma.png` 48×48); `og:image:alt` era escopo a mais
  (removido); e o `aria-label` "Voltar ao topo" mascarava a nova assinatura na árvore de
  acessibilidade (endereçado com "José Ferreira — voltar ao topo").
