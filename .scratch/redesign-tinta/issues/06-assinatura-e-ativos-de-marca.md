# 06: Assinatura no cabeçalho e ativos de marca

**What to build:** O visitante sabe de quem é o site antes de rolar, reconhece a aba pelo ícone, e
recebe uma prévia com a marca correta quando o link é compartilhado numa conversa.

Esta fatia também conserta um defeito que está no ar hoje: a imagem de logo foi removida do repo
sem que as referências a ela fossem atualizadas, então o site publicado está com ícone de aba e
prévia de compartilhamento quebrados.

O cabeçalho deixa de depender de um arquivo de imagem. A assinatura tipográfica fica nítida em
qualquer densidade de tela e não pode sumir do jeito que a imagem sumiu.

**Blocked by:** 03 (Tipografia Archivo em toda a página).

**Status:** ready-for-agent

- [ ] O cabeçalho exibe a assinatura tipográfica — nome completo com o descritor de serviço abaixo — sem nenhuma imagem.
- [ ] O descritor aparece travado à assinatura, no papel visual de rótulo.
- [ ] Nenhuma referência à imagem de logo removida sobrevive na página.
- [ ] O ícone da aba do navegador mostra o monograma, e é reconhecível em tamanho pequeno.
- [ ] A prévia de compartilhamento aponta para o avatar em resolução plena e carrega sem erro.
- [ ] O ativo de origem é o avatar vermelho já aprovado no design system, obtido do projeto de design — não uma recriação nova do símbolo.
- [ ] O monograma não aparece em nenhum outro lugar da página: o manual o restringe a avatar e capa.
- [ ] O console do navegador não reporta nenhuma imagem falhando ao carregar.
