# 04: Forma da marca — raio zero, fim das sombras, fios de dois níveis

**What to build:** A página ganha o caráter da direção escolhida: nada arredondado, nada com sombra,
e a estrutura legível de relance por fios nítidos. O visitante entende a organização da página pela
separação dos blocos, não por cards flutuando.

Sombra e fio andam juntos porque um substitui o outro: as sombras hoje fazem o trabalho de separar
blocos, e o fio assume esse papel no mesmo movimento.

**Blocked by:** 01 (Camada de tokens TINTA e fim do esquema escuro).

**Status:** ready-for-agent

- [ ] Nenhum elemento da página tem canto arredondado. A única exceção são formas que são círculos por definição: os pontos de status e os pontos da barra da moldura.
- [ ] Nenhuma sombra sobrevive na página, e os tokens de sombra foram **removidos**, não zerados — um token de sombra presente é convite a reintroduzir sombra.
- [ ] Nenhum degradê e nenhum brilho sobrevivem em parte alguma.
- [ ] Blocos estruturais — cabeçalho, separação entre seções, o box de processo e a linha do tempo — são separados por fio de 2 px em tinta.
- [ ] Bordas de card e de campo usam fio de 1 px em divisor, para que dez cards simultâneos na tela não somem peso demais.
- [ ] A borda tracejada da chamada intercalada virou fio sólido.
- [ ] A moldura que enquadra os screenshots foi mantida — ela comunica "isto é software rodando" — agora com fio de tinta e canto reto.
- [ ] As bolinhas de semáforo da moldura, cromaticamente alheias à paleta, viraram cinza.
