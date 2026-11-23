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
| ESC / P | pausar (continuar, recomeçar ou voltar ao menu) |
| R (no game over) | recomeçar |
| ESC (no game over) | voltar ao menu |

## Munição

- A escopeta tem 6 cartuchos, e a reserva começa com 12 (máximo de 30).
- Cada cartucho leva 0,25 s para recarregar e sai da reserva.
- Ao morrer, os inimigos podem derrubar caixas de munição: 12 cartuchos (2%), 6 (8%) ou 3 (18%). Todos os drops somem depois de 5 s.

## Modos

- **Campo de treino**: três jacarés parados em coluna à direita (que reaparecem) e a casa só de enfeite, para treinar o tiro e a faca. Se a munição acabar de vez, aparece uma caixa ao lado da casa.
- **Roguelike**: defenda a casa no centro, wave após wave. Os jacarés vêm das bordas e mordem a casa; se a vida dela chegar a zero, você perde.
  - Cada wave tem mais jacarés, que chegam mais rápido, em grupos maiores, mais velozes e com mais vida.
  - Ao fim de cada wave aparecem na frente da porta uma caixa de munição (+12) e um curativo que recupera 20% da vida da casa. Somem em 5 s; com a casa em 100%, o curativo some na hora.
  - Entre uma wave e outra há uma pausa de 4 s.

## Cenário

A partida acontece numa clareira cercada de mata. As árvores balançam com o vento, soltam folhas e tremem quando um jacaré passa por elas. As bordas ficam na sombra das árvores, o centro tem luz de sol, e alguns vagalumes piscam perto da mata. O jacaré anima as pernas ao andar e pisca de vez em quando.

## Arquivos

Todos os sprites estão embutidos em `index.html` (base64). Os `.png` e `.gif` da pasta são as cópias originais, para referência e edição.
