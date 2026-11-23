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

- A escopeta tem 6 cartuchos, e a reserva começa com 12 (máximo de 30).
- Cada cartucho leva 0,25 s para recarregar e sai da reserva.
- Ao morrer, os inimigos raramente derrubam caixas de munição: 12 cartuchos (0,5%), 6 (2,5%) ou 3 (7%). Todos os drops somem depois de 5 s. A fonte principal de munição é a caixa do fim de cada wave.

## Modos

- **Campo de treino**: três jacarés parados em coluna à direita (que reaparecem) e a casa só de enfeite, para treinar o tiro e a faca. Se a munição acabar de vez, aparece uma caixa ao lado da casa.
- **Roguelike**: defenda a casa no centro, wave após wave. Os jacarés vêm das bordas e mordem a casa; se a vida dela chegar a zero, você perde.
  - O jacaré básico é lento e frágil, com vida e velocidade fixas. O que cresce a cada wave é a quantidade: mais jacarés, chegando mais seguidos e em grupos maiores.
  - Ao fim de cada wave aparecem na frente da porta uma caixa de munição (12 + 4 por wave) e um curativo que recupera 20% da vida da casa. Somem em 5 s; com a casa em 100%, o curativo some na hora.
  - Entre uma wave e outra há uma pausa de 4 s.
  - Ao fim de cada wave o jogo congela e aparecem 3 cartas de upgrade; escolha 1 (clique ou teclas 1/2/3). Os upgrades acumulam durante a partida:
    crítico +5%, vampirismo +2% (o dano causado cura a casa), velocidade de ataque +10%, dano da escopeta +10%, velocidade de recarga +10%, vida máxima da casa +15%, recarga da faca −10%, dano da faca +10, balas 10% maiores, +3 projéteis, empurrão da faca +15% e alcance da faca +5%.
  - Os stats aparecem discretos à esquerda da tela e mudam em tempo real (Ctrl mostra/esconde).

## Cenário

A partida acontece numa clareira cercada de mata. As árvores balançam com o vento, soltam folhas e tremem quando um jacaré passa por elas. As bordas ficam na sombra das árvores, o centro tem luz de sol, e alguns vagalumes piscam perto da mata. O jacaré anima as pernas ao andar e pisca de vez em quando.

## Música

- **Gator Shooter Theme** toca no menu e no campo de treino; **Swamp Attack** toca no modo horda (roguelike).
- O volume abaixa na pausa e na escolha de cartas. O volume da música é ajustado no menu de pausa (botões − / +, ou setas). M silencia música e efeitos.

## Arquivos

Todos os sprites estão embutidos em `index.html` (base64). Os `.png` e `.gif` da pasta são as cópias originais, para referência e edição. As músicas ficam em `musica/` e são carregadas pelo `index.html`, então a pasta precisa ir junto.
