# Gator Shooter

Jogo top-down em pixel art feito em HTML5 Canvas puro, num único arquivo, sem dependências nem build.

## Como jogar

Abra `index.html` no navegador.

| Controle | Ação |
|---|---|
| WASD | mover |
| Shift (segurar) | correr (60% mais rápido, sem limite). No começo da partida aparece uma dica de SHIFT e BOTÃO DIREITO, e o HUD tem os ícones de corrida e faca com a tecla escrita |
| Mouse | mirar |
| Clique esquerdo | atirar (shotgun) |
| Clique direito | faca (melee: dano 28, recarga de 0,85 s) |
| R | recarregar até encher (atirar interrompe) |
| 1 / 2 / 3 ou roda do mouse | trocar de arma (escopeta, uzi, revólveres — depois de comprar) |
| Q / F / C | dinamite / pimenta / cubo de gelo (consumíveis da loja) |
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
- **Roguelike**: defenda a casa no centro, wave após wave. A partida começa com o aviso grande "DEFENDA SUA CASA" e a casa contornada. Os jacarés vêm das bordas e mordem a casa; se a vida dela chegar a zero, você perde.
  - O jacaré básico é lento e frágil, com vida e velocidade fixas. O que cresce a cada wave é a quantidade: mais jacarés, chegando mais seguidos e em grupos maiores.
  - A cada 5 waves entra um inimigo novo, anunciado com "UMA NOVA AMEAÇA SURGE". Wave 5: **Tank** (maior que o básico, 300 de vida, bem lento, mordida de 20 na casa contra 5 do básico, quase não é empurrado). A partir daí aparecem tanks misturados na horda, um a mais a cada 2 waves. Wave 10: **Range**, um gavial armado (90 de vida). Ele não chega perto da casa: fica rondando em volta da clareira, sempre virado para ela, para, abre o olho para mirar e atira de longe (bala branca grande, 10 de dano). 15% dos ranges vêm com **dois revólveres** (atiram duas vezes seguidas) e 5% com **escopeta** (5 chumbos de 6). Aparecem 3 ranges na wave 10, um a mais a cada wave, até no máximo 5 por wave. A mira deles erra bastante no começo e vai ficando mais precisa a cada wave. Wave 15: **Rusher**, uma jacarezinha de lacinho que corre muito (175 contra 60 do básico) e tem pouca vida (12). A mordida dela é fraca (2), mas vem a cada 0,3 s (o básico morde a cada 1 s). São 4 na wave 15 e +2 por wave, até 12. Wave 20: **Healer**, um jacaré curandeiro com uma chama verde na mão, que brilha bastante (de dia e de noite). Ele não ataca e nunca se aproxima da casa: anda num anel em volta da clareira, puxando para o lado onde há jacarés machucados, e a cada 1,2 s solta uma onda de cura que cura todos os machucados num raio de 340 px (14 + 5% da vida máxima de cada um), com raios verdes e os curados brilhando verde. Tem 70 de vida. É 1 na wave 20, +1 a cada 2 waves, até 4.
  - Para testar uma wave específica, abra o jogo com `?wave=N` no fim do endereço (ex.: `index.html?wave=10`).
  - **Dentes** são o dinheiro do jogo. Há quatro: pequeno (vale 1), grande (5), prata (10) e ouro (25). Quanto mais longe na partida, maior a chance dos valiosos: o grande começa em 7% e vai até 28%, o prata aparece a partir da wave 8 (até 12%) e o ouro a partir da wave 15 (até 5%). O básico solta 1 dente 20% das vezes, a rusher 25%, o range 1–2 (80%), o healer 1–2 (90%) e o tank sempre 2–3. Os dentes **não somem**: ficam no chão até você pegar e, no fim de cada wave, todos os que sobraram voam até você. O total fica no canto inferior esquerdo.
  - **Velho Bill**: depois das waves 5, 10, 15… (antes de virar dia ou noite) um jacaré velho mercador chega correndo pela direita com o carrinho de loja e estaciona do lado direito da casa; ao ir embora dá meia-volta e sai pela direita. Na primeira vez rola uma cutscene em que ele se apresenta. Chegue perto do carrinho e aperte **E** para abrir a loja (o jogo para enquanto ela está aberta). A visita dura 45 s com a loja fechada, ou aperte **Enter** para dispensar o Bill e seguir para a próxima wave.
  - Loja com 3 abas (1/2/3 trocam de aba). Cada nível custa mais que o anterior; tudo vale só para a partida atual.
    - **Armas**: Escopeta (+1 cartucho por nível, de 6 até 12), **Uzi** (tiros rápidos, dano 7, bom contra grupos; 3 níveis) e **Revólveres** (dois revólveres que atiram um de cada vez, dano 20, precisos e atravessam 3 inimigos; 3 níveis). A escopeta usa cartuchos (caixa verde). A Uzi (pente 30) e os revólveres (pente 12) usam a mesma munição de 9 mm (caixa azul, reserva até 150). Caixas de 9 mm só caem dos jacarés e só aparecem no fim da wave se você tiver uma dessas armas.
    - **Defesa**: Cabana (+10% de defesa da casa contra mordidas e tiros por nível, até 50%), Mina terrestre (+1 mina plantada perto da casa a cada wave, até 6; explode quando um jacaré passa) e Primo Antony (jacaré aliado que fica na frente da casa atirando nos inimigos; 3 níveis, no último espalha 3 tiros). Ele tem vida (120, +40 por nível, recupera 30% a cada wave): jacarés que passam perto mordem ele e os tiros dos ranges acertam ele no caminho. Se morrer, só volta comprando de novo (do nível 1) na próxima loja do Bill.
    - **Consumíveis** (ficam na mochila): Dinamite (Q, arremessa na mira e explode em área), Pimenta dedo-de-moça (F, por 15 s os tiros incendeiam: os inimigos pegam fogo e levam dano por 3 s) e Cubo de gelo (C, arremessa na mira e congela os inimigos em área por 4 s).
  - Ao fim de cada wave aparecem na frente da porta uma caixa de munição (12 + 4 por wave) e um curativo que recupera 20% da vida da casa. Somem em 5 s; com a casa em 100%, o curativo some na hora.
  - Entre uma wave e outra há uma pausa de 4 s.
  - Ao fim de cada wave o jogo congela e aparecem 3 cartas de upgrade; escolha 1 (clique ou teclas 1/2/3). Os upgrades acumulam durante a partida:
    crítico +5%, vampirismo +2% (o dano causado cura a casa), velocidade de ataque +10%, dano +10%, velocidade de recarga +10% (estas três e Calibre Maior valem para todas as armas), vida máxima da casa +15%, recarga da faca −10%, dano da faca +10, balas 10% maiores, +2 projéteis, empurrão da faca +15%, alcance da faca +5%, Arrancador (+5% de chance dos inimigos dropar dentes) e Pernas Ligeiras (+5% de velocidade de movimento).
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
