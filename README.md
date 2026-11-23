# Gator Shooter

Jogo top-down em pixel art feito em HTML5 Canvas puro, num único arquivo, sem dependências nem build.

## Como jogar

Abra `index.html` no navegador.

| Controle | Ação |
|---|---|
| WASD | mover |
| Shift (segurar) | correr (60% mais rápido, sem limite) |
| Mouse | mirar |
| Clique esquerdo | atirar (shotgun) |
| Clique direito | faca (melee, recarga de 1 s) |
| R | recarregar até encher (atirar interrompe) |
| M | liga/desliga o som |
| Ctrl | mostra/esconde os stats |
| 1 / 2 / 3 | escolher carta de upgrade |
| ESC / P | pausar (continuar, recomeçar, voltar ao menu e ajustar o volume da música) |
| R (no game over) | recomeçar |
| ESC (no game over) | voltar ao menu |

## Munição

- A escopeta tem 6 cartuchos, e a reserva começa com 12 (máximo de 30; no modo horda o máximo cresce +5 por wave).
- Cada cartucho leva 0,25 s para recarregar e sai da reserva.
- Ao morrer, os inimigos raramente derrubam caixas de munição: 12 cartuchos (0,5%), 6 (2,5%) ou 3 (7%). Todos os drops somem depois de 5 s. A fonte principal de munição é a caixa do fim de cada wave.

## Modos

- **Campo de treino**: três jacarés parados em coluna à direita (que reaparecem) e a casa só de enfeite, para treinar o tiro e a faca. Se a munição acabar de vez, aparece uma caixa ao lado da casa.
- **Roguelike**: defenda a casa no centro, wave após wave. Os jacarés vêm das bordas e mordem a casa; se a vida dela chegar a zero, você perde.
  - O jacaré básico é lento e frágil, com vida e velocidade fixas. O que cresce a cada wave é a quantidade: mais jacarés, chegando mais seguidos e em grupos maiores.
  - A cada 5 waves entra um inimigo novo, anunciado com "UMA NOVA AMEAÇA SURGE". Wave 5: **Tank** (maior que o básico, 300 de vida, bem lento, mordida de 20 na casa contra 5 do básico, quase não é empurrado). A partir daí aparecem tanks misturados na horda, um a mais a cada 2 waves. Wave 10: **Range**, um gavial armado (90 de vida). Ele não chega perto da casa: fica rondando em volta da clareira, sempre virado para ela, para, abre o olho para mirar e atira de longe (bala branca grande, 10 de dano). 15% dos ranges vêm com **dois revólveres** (atiram duas vezes seguidas) e 5% com **escopeta** (5 chumbos de 6). Aparecem 3 ranges na wave 10, um a mais a cada wave, até no máximo 5 por wave. A mira deles erra bastante no começo e vai ficando mais precisa a cada wave.
  - Para testar uma wave específica, abra o jogo com `?wave=N` no fim do endereço (ex.: `index.html?wave=10`).
  - **Dentes** são o dinheiro do jogo. Há dois dentes: o pequeno vale 1 e o grande (que brilha) vale 5. Os jacarés deixam cair dentes de vez em quando: o básico raramente (12%, vale 1), o range quase sempre (70%, vale 1–2) e o tank sempre (vale 2–6, às vezes um dente grande). Os dentes quicam no chão, voam até você quando chega perto e somem depois de 14 s. O total fica no canto inferior esquerdo.
  - **Velho Bill**: depois das waves 5, 10, 15… (antes de virar dia ou noite) um jacaré velho mercador chega correndo pela direita com o carrinho de loja e estaciona do lado direito da casa; ao ir embora dá meia-volta e sai pela direita. Na primeira vez rola uma cutscene em que ele se apresenta. Chegue perto do carrinho e aperte **E** para abrir a loja (o jogo para enquanto ela está aberta). A visita dura 45 s com a loja fechada, ou aperte **Enter** para dispensar o Bill e seguir para a próxima wave.
  - Itens da loja: caixa de cartuchos (+15, 4 dentes), kit de reparo (40% da casa, 6), carta misteriosa (escolhe 1 de 3 upgrades; 10, +5 a cada compra), botas de corrida (+10% de velocidade andando e correndo, até 3 níveis; 8/13/18) e ímã de dentes (puxa os dentes de mais longe, até 2 níveis; 6/12).
  - Ao fim de cada wave aparecem na frente da porta uma caixa de munição (12 + 4 por wave) e um curativo que recupera 20% da vida da casa. Somem em 5 s; com a casa em 100%, o curativo some na hora.
  - Entre uma wave e outra há uma pausa de 4 s.
  - Ao fim de cada wave o jogo congela e aparecem 3 cartas de upgrade; escolha 1 (clique ou teclas 1/2/3). Os upgrades acumulam durante a partida:
    crítico +5%, vampirismo +2% (o dano causado cura a casa), velocidade de ataque +10%, dano da escopeta +10%, velocidade de recarga +10%, vida máxima da casa +15%, recarga da faca −10%, dano da faca +10, balas 10% maiores, +2 projéteis, empurrão da faca +15% e alcance da faca +5%.
  - Os stats aparecem discretos à esquerda da tela e mudam em tempo real (Ctrl mostra/esconde).

## Dev mode

No campo de treino, digite **0806** para abrir o painel de testes (digite de novo ou clique no × para fechar). Nele dá para:

- mudar o nível de cada upgrade (passe o mouse no nome para ver o que ele faz);
- adicionar jacarés, tanks e ranges, que atacam a casa do campo de treino (ela ganha vida enquanto houver inimigos de teste);
- ligar munição infinita, casa invencível e noite, encher a munição e curar a casa;
- chamar o velho Bill, ganhar 20 dentes e rever a cutscene do primeiro encontro.

## Cenário

A partida acontece numa clareira cercada de mata, num mapa maior que a tela: a câmera acompanha o jacaré com zoom (puxando um pouco na direção da mira), e quanto mais longe da casa, mais densa fica a mata. Quando a casa sai da tela, uma seta na borda aponta para ela e fica vermelha quando ela está sendo atacada. Jacarés escondidos atrás da casa aparecem como uma silhueta vermelha por cima dela (só a parte encoberta). Os tiros passam por trás das copas e troncos das árvores que estão na frente deles (só no desenho; o tiro continua igual). As árvores balançam com o vento, soltam folhas e tremem quando um jacaré passa por elas. As bordas ficam na sombra das árvores, o centro tem luz de sol, e alguns vagalumes piscam perto da mata. O jacaré anima as pernas ao andar e pisca de vez em quando.

**Dia e noite (modo horda):** 5 waves de dia, 5 de noite, e assim por diante (noite nas waves 6–10, 16–20…). A noite cai aos poucos no intervalo antes da wave 6 e o banner avisa ("A NOITE CAIU" / "AMANHECEU"). Uma coruja pia quando começa a anoitecer e o galo canta quando começa a amanhecer. À noite tudo fica escuro e azulado (a clareira da casa fica um pouco mais clara, como se recebesse a luz da lua de cima), aparecem muitos vagalumes, o jogador ilumina em volta, os tiros (seus e dos ranges) iluminam o caminho com luz amarelada, a casa acende as janelas (luz amarelada) e os jacarés ficam com um ponto vermelho brilhando nos olhos.

## Música

- **Gator Shooter Theme** toca no menu e no campo de treino; **Swamp Attack** toca no modo horda (roguelike); **Old Bill Shop** toca enquanto o velho Bill está na área com a loja (depois a horda volta de onde parou).
- O volume abaixa na pausa e na escolha de cartas. O volume da música é ajustado no menu de pausa (botões − / +, ou setas). M silencia música e efeitos.

## Arquivos

Todos os sprites estão embutidos em `index.html` (base64). Os `.png` e `.gif` da pasta são as cópias originais, para referência e edição. Os sons da coruja e do galo também estão embutidos (originais em `sons/`). As músicas ficam em `musica/` e são carregadas pelo `index.html`, então a pasta precisa ir junto.
