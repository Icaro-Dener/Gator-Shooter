# Gator Shooter

Jogo top-down em pixel art feito em HTML5 Canvas puro, num único arquivo, sem dependências nem build.

## Como jogar

Abra `index.html` no navegador.

| Controle | Ação |
|---|---|
| WASD | mover |
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
  - Ao fim de cada wave aparecem na frente da porta uma caixa de munição (12 + 4 por wave) e um curativo que recupera 20% da vida da casa. Somem em 5 s; com a casa em 100%, o curativo some na hora.
  - Entre uma wave e outra há uma pausa de 4 s.
  - Ao fim de cada wave o jogo congela e aparecem 3 cartas de upgrade; escolha 1 (clique ou teclas 1/2/3). Os upgrades acumulam durante a partida:
    crítico +5%, vampirismo +2% (o dano causado cura a casa), velocidade de ataque +10%, dano da escopeta +10%, velocidade de recarga +10%, vida máxima da casa +15%, recarga da faca −10%, dano da faca +10, balas 10% maiores, +2 projéteis, empurrão da faca +15% e alcance da faca +5%.
  - Os stats aparecem discretos à esquerda da tela e mudam em tempo real (Ctrl mostra/esconde).

## Dev mode

No campo de treino, digite **0806** para abrir o painel de testes (digite de novo ou clique no × para fechar). Nele dá para:

- mudar o nível de cada upgrade (passe o mouse no nome para ver o que ele faz);
- adicionar jacarés, tanks e ranges, que atacam a casa do campo de treino (ela ganha vida enquanto houver inimigos de teste);
- ligar munição infinita e casa invencível, encher a munição e curar a casa.

## Cenário

A partida acontece numa clareira cercada de mata. As árvores balançam com o vento, soltam folhas e tremem quando um jacaré passa por elas. As bordas ficam na sombra das árvores, o centro tem luz de sol, e alguns vagalumes piscam perto da mata. O jacaré anima as pernas ao andar e pisca de vez em quando.

## Música

- **Gator Shooter Theme** toca no menu e no campo de treino; **Swamp Attack** toca no modo horda (roguelike).
- O volume abaixa na pausa e na escolha de cartas. O volume da música é ajustado no menu de pausa (botões − / +, ou setas). M silencia música e efeitos.

## Arquivos

Todos os sprites estão embutidos em `index.html` (base64). Os `.png` e `.gif` da pasta são as cópias originais, para referência e edição. As músicas ficam em `musica/` e são carregadas pelo `index.html`, então a pasta precisa ir junto.
