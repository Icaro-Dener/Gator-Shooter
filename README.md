# Gator Shooter

Jogo top-down em pixel art feito em HTML5 Canvas puro, num único arquivo, sem dependências nem build.

## Como jogar

Abra `index.html` no navegador.

| Controle | Ação |
|---|---|
| WASD | mover |
| Mouse | mirar |
| Clique esquerdo | atirar (shotgun) |
| Clique direito | faca (melee, recarga de 3 s) |
| R | recarregar (toque = 1 cartucho, segurar = continua) |
| M | liga/desliga o som |
| R (no game over) | recomeçar |
| ESC | voltar ao menu |

## Munição

- A escopeta tem 6 cartuchos, e a reserva começa com 12 (máximo de 30).
- Cada cartucho leva 0,25 s para recarregar e sai da reserva.
- Ao morrer, os inimigos podem derrubar caixas de munição: 12 cartuchos (2%), 6 (8%) ou 3 (18%). As caixas somem depois de 14 s.

## Modos

- **Campo de teste**: um inimigo parado (que reaparece), para testar o tiro e a faca.
- **Roguelike**: defenda a casa no centro. Os jacarés vêm das bordas, cada vez com mais frequência, e mordem a casa. Se a vida dela chegar a zero, você perde.

## Arquivos

Todos os sprites estão embutidos em `index.html` (base64). Os `.png` e `.gif` da pasta são as cópias originais, para referência e edição.
