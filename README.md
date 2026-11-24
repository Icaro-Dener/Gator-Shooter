# Gator Shooter

Jogo top-down em pixel art feito em HTML5 Canvas puro, num único arquivo, sem dependências nem build.

## Como jogar

Abra `index.html` no navegador.

| Controle | Ação |
|---|---|
| WASD | mover |
| Shift (segurar) | correr (60% mais rápido) gastando **fôlego**: dá uns 3 s de corrida, a barra fica dentro do ícone da corrida (direita); se esgotar (barra vermelha piscando) só volta a correr com 30% de fôlego. No começo da partida aparece uma dica de SHIFT e BOTÃO DIREITO, e o HUD tem os ícones de corrida e faca com a tecla escrita |
| Mouse | mirar |
| Clique esquerdo | atirar (shotgun) |
| Clique direito | faca (melee: dano 28, recarga de 0,85 s) |
| R | recarregar até encher (atirar interrompe) |
| 1 / 2 / 3 ou roda do mouse | trocar de arma (escopeta, uzi, revólveres — depois de comprar) |
| Q / F / C | dinamite / pimenta / cubo de gelo (consumíveis da loja) |
| M | liga/desliga o som |
| Ctrl | mostra/esconde os stats |
| 1 / 2 / 3 | escolher carta de upgrade |
| ESC / P | pausar (continuar, configurações, recomeçar, voltar ao menu) |
| R (no game over) | recomeçar |
| ESC (no game over) | voltar ao menu |

## Munição

- Os chumbos da escopeta (e do Primo Antony) usam o sprite do tiro do revólver, um pouco maior e mais esbranquiçado; com a carta Calibre Maior a partir de +50% eles viram o tiro da uzi.
- A escopeta tem 6 cartuchos, e a reserva começa com só 6 (máximo de 30; no modo horda começa em 24 e cresce +2 por wave, até 60). A munição é escassa de propósito: a faca é a arma para economizar cartuchos.
- Cada cartucho leva 0,25 s para recarregar e sai da reserva.
- Ao morrer, os inimigos raramente derrubam caixas de munição: 8 cartuchos (0,4%), 4 (1,5%) ou 2 (4,3%). Todos os drops somem depois de 5 s. A fonte principal de munição é a caixa do fim de cada wave.

## Modos

- **Campo de treino**: dois espantalhos no gramado, em cima à direita da casa, entre as árvores, e a casa só de enfeite, para treinar o tiro e a faca. Os espantalhos não morrem e não machucam (por isso o treino não mostra os corações): balançam quando levam tiro e mostram o dano. Um deles tem chapéu de palha, que voa longe no primeiro tiro (e não volta). Se a munição acabar de vez, aparece uma caixa ao lado da casa.
- **Chapéus**: 5% dos jacarés nascem de chapéu (palha, marrom, preto ou boné, sorteado). Ao morrer, o chapéu cai no chão e some como os itens (5 s, piscando no fim); chegue perto e aperte o **botão direito** para pegar (perto de um chapéu o botão direito pega em vez de dar facada), e o seu jacaré passa a usar o chapéu até o fim da partida. Só dá para usar um por vez: pegar outro troca, e o antigo cai no chão. O chapéu do espantalho também dá para pegar. Sprites em `sprites/treino/espantalho.png` e `sprites/chapeus/`.
- **Roguelike**: defenda a casa no centro, wave após wave. A partida começa com uma cutscene: o jacaré sai de dentro de casa pela porta e reclama "os vizinhos não me dão um dia de folga" (clique ou E pula/continua). Depois vem o aviso grande "DEFENDA SUA CASA" com a casa contornada, e só então a horda começa. Os jacarés vêm das bordas e mordem a casa; se a vida dela chegar a zero, você perde.
  - O jacaré básico é lento e frágil, com vida e velocidade fixas. O que cresce a cada wave é a quantidade: mais jacarés, chegando mais seguidos e em grupos maiores. A cada 5 waves **só o jacaré básico** fica 8% mais rápido (waves 6–10: +8%, 11–15: +16%… até +40% na wave 26); os outros inimigos mantêm a velocidade, e o banner da wave avisa.
  - A cada 5 waves entra um inimigo novo, anunciado com "UMA NOVA AMEAÇA SURGE". Wave 5: **Tank** (maior que o básico, 300 de vida, lento (50, o básico anda a 70), mordida de 20 na casa contra 5 do básico, quase não é empurrado). A partir daí aparecem tanks misturados na horda, um a mais a cada 2 waves. Wave 10: **Range**, um gavial armado (90 de vida). Ele não chega perto da casa: fica rondando em volta da clareira, sempre virado para ela, para, abre o olho para mirar e atira de longe (bala branca grande, 10 de dano). 15% dos ranges vêm com **dois revólveres** (atiram duas vezes seguidas) e 5% com **escopeta** (5 chumbos de 6). Aparecem 3 ranges na wave 10, um a mais a cada wave, até no máximo 5 por wave. A mira deles erra bastante no começo e vai ficando mais precisa a cada wave. Wave 15: **Rusher**, uma jacarezinha de lacinho que corre muito (175 contra 60 do básico) e tem pouca vida (12). A mordida dela é fraca (2), mas vem a cada 0,3 s (o básico morde a cada 1 s). São 4 na wave 15 e +2 por wave, até 12. Wave 20: **Healer**, um jacaré curandeiro com uma chama verde na mão, que brilha bastante (de dia e de noite). Ele não ataca e nunca se aproxima da casa: anda num anel em volta da clareira, puxando para o lado onde há jacarés machucados, e a cada 1,2 s solta uma onda de cura que cura todos os machucados num raio de 340 px (14 + 5% da vida máxima de cada um), com raios verdes e os curados brilhando verde. Tem 70 de vida. É 1 na wave 20, +1 a cada 2 waves, até 4.
  - **Inimigos evoluem** desde a wave em que aparecem: o **tank** ganha +8% de vida a cada wave (300 na wave 5, 900 na 30) e **segura as balas** (não atravessam ele para acertar quem está atrás); o **range** fica mais preciso a cada 5 waves (mira e leque da escopeta mais fechados); o **rusher** fica 8% mais rápido a cada 5 waves; o **healer** cura e dá escudo 8% a mais a cada 5 waves e anda **atrás dos tanks** (sem tank, atrás do jacaré mais próximo), do lado de fora, usando eles de escudo.
  - Para testar uma wave específica, abra o jogo com `?wave=N` no fim do endereço (ex.: `index.html?wave=10`).
  - **Dentes** são o dinheiro do jogo. Há quatro: pequeno (vale 1), grande (5), prata (10) e ouro (25). Quanto mais longe na partida, maior a chance dos valiosos: o grande começa em 7% e vai até 20%, o prata aparece a partir da wave 9 (até 8%) e o ouro a partir da wave 16 (até 3%). Como as waves têm cada vez mais jacarés, a chance de cada um soltar dente cai aos poucos (÷ (1 + 6% por wave)), para a renda crescer de forma gradual. Na wave 1, o básico solta 1 dente 25% das vezes, a rusher 25%, o range 1–2 (80%), o healer 1–2 (90%) e o tank sempre 2–3. Os dentes **não somem**: ficam no chão até você pegar e, no fim de cada wave, todos os que sobraram voam até você. O total fica no canto inferior esquerdo.
  - **Velho Bill**: depois das waves 5, 10, 15… (antes de virar dia ou noite) um jacaré velho mercador chega correndo pela direita com o carrinho de loja e estaciona do lado direito da casa; ao ir embora dá meia-volta e sai pela direita. Na primeira vez rola uma cutscene em que ele se apresenta. Chegue perto do carrinho e aperte **E** para abrir a loja (o jogo para enquanto ela está aberta). A visita dura 45 s com a loja fechada, ou aperte **Enter** para dispensar o Bill e seguir para a próxima wave.
  - A loja é uma janela grande, quase tela cheia, com tema de madeira rústica (`sprites/interface/madeira.png`, ampliada inteira, sem repetir). Os cards são de madeira clara com texto escuro, e a frase de cada item fica justificada e ajusta o tamanho da fonte para preencher o card. À esquerda fica o Bill com o balão de fala e os **serviços**; à direita, 3 abas (1/2/3) com os itens em cards: nome, ícone grande, frase, o que o próximo nível faz (em verde), os níveis em quadrados (os comprados ficam verdes, maiores e brilhando) e o botão de compra (verde = dá para comprar, vermelho = falta dente, cinza = indisponível). Cada nível custa bem mais que o anterior, e a cada visita o Bill traz **só um nível de cada upgrade**. Tudo vale só para a partida atual. Perto do carrinho aparece só a tecla **E** e o carrinho ganha um contorno branco pulsando.
  - Em cada aba os itens ficam do **mais barato ao mais caro** (o que está no nível máximo ou esgotado vai para o fim); a ordem é tirada ao abrir a loja e não muda enquanto você compra e aparecem **3 por vez**: as setas nas laterais, a roda do mouse ou ←/→ (A/D) rolam para os lados, e as bolinhas embaixo mostram quais estão à mostra.
    - **Armas**: Escopeta (+1 cartucho por nível, de 6 até 12), **Uzi** (tiros rápidos, dano 7, balas bem grandes, recarga de 0,9 s; 5 níveis de dano e velocidade e, no nível 6, por 600 dentes, **DUAS UZIS**: uma em cada mão, atirando alternado, pente de 60; bom contra grupos; 3 níveis) e **Revólveres** (dois revólveres que atiram um de cada vez, cada um dando seu próprio coice, dano 20, balas grandes, precisos e atravessam 3 inimigos; 3 níveis). A escopeta usa cartuchos (caixa verde). A Uzi (pente 30) e os revólveres (pente 12) usam a mesma munição de 9 mm (caixa azul, reserva até 150). Caixas de 9 mm só caem dos jacarés e só aparecem no fim da wave se você tiver uma dessas armas.
    - **Defesa**: **Cabana** ("Instala barras de metal…": diminuição de dano de 10% por nível, até 50%), **Minas terrestres** ("CUIDADO! Quem pisar…": +1 mina por nível, até 8, sempre 2 de cada lado da casa; a ponta vermelha de cada mina armada acende num brilho a cada ~2 s; sprites `sprites/itens/mina.png` e `medkit.png`), **Para-raio** (25 dentes): fica em cima do telhado e puxa para si os raios que cairiam na casa, no Antony ou no jogador; aguenta 10 raios (luzinhas no poste) e quebra com um estalo; dá para recarregar; sprite `sprites/itens/para-raio.png`, **Primo Antony** ("Certeza que ele aparece…": +Dano +Vida, 3 níveis; se morrer, os upgrades resetam e o card mostra **RESSUSCITAR**, que o traz de volta no nível 1) e **Cercado** (abaixo). Antony e Cercado têm dois botões separados no mesmo card.
    - **Serviços do Bill** (fora das abas, embaixo do retrato): **REABASTECER** (tecla 4) enche toda a munição e **CURAR CASA** (tecla 5) deixa a casa em 100%. Cada um uma vez por visita; ficam mais caros com o avanço da partida e com os upgrades (armas no reabastecer; Tábuas Extras e Cabana no curar).
    - **Cercado** ("Melhor maneira de impor limites.", aba DEFESA, 5 níveis): no nível 1 (100 dentes) o Bill monta uma cerca em toda a borda da terra (42 cercas; preços 115/175/255/345/460), deixando a casa, as minas e as armadilhas do lado de dentro. Os upgrades deixam cada cerca mais forte: vida 60 / 100 / 150 / 220 / 300, por 100 / 150 / 220 / 300 / 400 dentes (um nível por visita). O botão **CONSERTAR** do mesmo card refaz as quebradas e conserta as danificadas; o preço é proporcional ao estrago e sobe com o nível da cerca (2 a 8 dentes por cerca quebrada). As cercas não são vendidas avulsas. Os jacarés que vão até a casa param e mordem a cerca até quebrar, e ela também segura os tiros dos ranges; o jogador e os tiros dele passam por cima. Quando o velho Bill chega, as cercas da vaga e do caminho dele abaixam como um portão e voltam quando ele vai embora.
    - **Consumíveis** (ficam na mochila): Dinamite (Q, arremessa na mira e explode em área), Pimenta dedo-de-moça (F, por 15 s os tiros incendeiam: os inimigos pegam fogo e levam dano por 3 s) e Cubo de gelo (C, arremessa na mira e congela os inimigos em área por 4 s).
  - **Healer**: cura a cada 0,9 s num raio grande e dá um **escudo verde** (hexágono) de 25% da vida máxima por 4 s a quem cura, que absorve tiros, faca e explosões. Ao morrer solta uma última onda que cura 30% de quem está perto. Para se destacar, tem um anel tracejado girando em volta dele no chão e quatro formas verdes (losango, triângulo, quadrado e X) girando em órbita; quem está com escudo ganha o hexágono verde em volta e um ícone de escudo em cima da cabeça, e a cura solta cruzes verdes subindo. Os efeitos vêm de `sprites/inimigos/healer/healer-efeitos.png`.
  - **Números de dano**: cada acerto mostra o dano causado em cima do inimigo (os chumbos de um mesmo tiro somam num número só). Quanto maior o dano, maior e mais vermelho o número (branco, laranja, vermelho a partir de 80). No crítico aparece "CRIT" com o número em amarelo. Os números ficam por cima de tudo, inclusive à noite.
  - **Tiros do Range**: balas redondas vermelhas grandes, todas do mesmo tamanho (48 px), girando devagar, lentas (300 px/s, dá para ver e desviar) e com um brilho vermelho pulsando em volta; à noite iluminam o caminho.
  - **Recarga automática** (ligada por padrão, dá para desligar em Configurações): quando o pente ou a escopeta esvazia e há reserva, a arma recarrega sozinha; atirar interrompe. R continua recarregando na hora, mesmo com balas no pente. Desligada, só recarrega com R.
  - **Dano na casa**: cada mordida e cada tiro que acerta a casa mostra o dano em vermelho ("-5", "-20"...), já com o desconto da Cabana.
  - **Chuva**: a partir da wave 3, cada wave tem 22% de chance de começar a chover ("COMEÇOU A CHOVER" no banner). Dura 2 waves e depois fica pelo menos 3 waves sem chover. Na chuva: céu fechado, gotas e respingos, som de chuva; os jacarés andam 15% mais rápido; o chão escorrega (o jogador demora a frear e a virar); o fogo da pimenta apaga entre 1 e 2 s; a dinamite tem 25% de chance de molhar e falhar; o cubo de gelo fica mais forte (raio +30%, congela 60% mais tempo); e de vez em quando cai um raio (trovão e clarão) num alvo sorteado na tela: um jacaré (70 de dano em área), a casa (30), o primo Antony (35), uma cerca (45) ou o próprio jogador, que fica atordoado por 0,9 s (anda devagar e não atira). Na chuva venta forte: árvores e tufos balançam umas 4x mais, deitam para a esquerda e passam folhas voando. O som da chuva é baixo e fica abafado na pausa, nas cartas de upgrade e na loja. Teste: `?chuva` na URL força a chuva.
  - **Eventos de wave** (raros: 12% por wave a partir da wave 4, cada evento só depois da estreia do inimigo dele (ventania a partir da 11, lua cheia da 16, neblineiro da 21), nunca na wave em que chega um inimigo novo, e depois de um evento ficam pelo menos 3 waves sem outro; cada um dura 1 wave, com banner próprio). **Dia quente** (só de dia e sem chuva): tudo fica alaranjado; só jacarés básicos, com 60% mais vida, 30% mais rápidos, brilhando e soltando brasas; a mordida põe fogo na casa (focos que queimam 2/s por 4 s, até 5 focos) e faz 50% a mais no Antony e nas cercas; não pegam fogo e não congelam. **Noite de lua cheia** (só de noite): lua enorme no céu; só rushers, com o dobro de vida e de velocidade e mordida 3. **Ventania** (dia ou noite): vento forte com folhas voando; só ranges, 45% com escopeta e, dos outros, 90% com dois revólveres. **Neblineiro** (só com chuva): neblina que deixa ver só perto do jogador; 70% tanks 50% mais rápidos e 30% healers. Os eventos têm menos inimigos que a wave normal (lua 80%, ventania 60%, neblineiro 50%). Teste: `?evento=hot|moon|wind|fog` na URL força o evento em toda wave; no painel de testes há botões para cada um.
  - Ao fim de cada wave aparecem na frente da porta uma caixa de munição pequena (4 + 1,5 por wave; 9 mm: 16 + 2 por wave) e um curativo que recupera 20% da vida da casa. Somem em 5 s; com a casa em 100%, o curativo some na hora.
  - Entre uma wave e outra há uma pausa de 4 s.
  - **Ritmo**: a wave 1 já vem com 8 jacarés chegando a cada 1 s (+5 jacarés por wave, cada vez mais seguidos e em grupos maiores); entre as waves a pausa é de só 1,5 s depois de escolher a carta; as caixas de recompensa voam sozinhas até o jogador. Quando sobram 3 ou menos jacarés na wave, eles ficam 70% mais rápidos (um "!" vermelho em cima) e setas vermelhas na borda da tela mostram onde estão.
  - Na visita do Bill, depois de entrar e sair da loja, sobe uma **gaveta roxa** discreta em pixel art embaixo da tela: tecla ENTER + "prosseguir" (também dá para clicar nela).
  - Ao fim de cada wave o jogo congela e aparecem 3 cartas de upgrade; escolha 1 (clique ou teclas 1/2/3). Os upgrades acumulam durante a partida:
    - Cartas novas: **Fôlego de Jacaré** (+30% de fôlego), **Ímã de Dentes** (+35% de alcance), **Caixa Reforçada** (+25% de munição nas caixas da wave), **Farpas na Porta** (quem morde a casa leva 8 de dano) e **Catador de Cartuchos** (+30% de chance dos inimigos derrubarem munição).
    - **SUPER UPGRADE** no fim das waves 5, 10, 15...: 3 cartas douradas, cada uma só uma vez: **Jacaré-Bomba** (todo jacaré explode ao morrer, 15 de dano em volta), **Fortaleza** (+30% de vida da casa e conserta tudo), **Fúria do Pântano** (+20% de dano, +12% de velocidade de ataque), **Faca Giratória** (a faca acerta em volta toda, +10% de alcance), **Mira Letal** (+10% de crítico e crítico 2,5x), **Boca de Ouro** (+50% de dentes), **Cinturão de Balas** (+12 de reserva e enche a munição) e **Pulmão de Aço** (correr cansa pela metade, +10% correndo).
    crítico +5%, vampirismo +1% (o dano causado cura a casa; no máximo 5 níveis = 5%), velocidade de ataque +10%, dano +10%, velocidade de recarga +10% (estas três e Calibre Maior valem para todas as armas), vida máxima da casa +15%, recarga da faca −10%, dano da faca +10, balas 10% maiores, +2 projéteis, empurrão da faca +15%, alcance da faca +5%, Arrancador (+5% de chance dos inimigos dropar dentes) e Pernas Ligeiras (+5% de velocidade de movimento).
  - Os stats aparecem discretos à esquerda da tela e mudam em tempo real (Ctrl mostra/esconde).

## Dev mode

No campo de treino, digite **0806** para abrir o painel de testes (digite de novo ou clique no × para fechar). Nele dá para:

- mudar o nível de cada upgrade (passe o mouse no nome para ver o que ele faz);
- adicionar jacarés, tanks, ranges, rushers e healers, que atacam a casa do campo de treino (ela ganha vida enquanto houver inimigos de teste);
- ligar munição infinita, casa invencível, noite e **chuva** (fica até desligar), fazer **cair um raio** num inimigo na tela, encher a munição e curar a casa;
- chamar o velho Bill, ganhar 20 ou 100 dentes e rever a cutscene do primeiro encontro.

## Menu e configurações

Botões do menu, de cima para baixo: **JOGAR** (modo horda), **HISTÓRIA**, **TREINAMENTO** (campo de treino) e **CONFIGURAÇÕES** (também abre pela pausa, ou com C no menu).

Em Configurações: volume da música, volume dos efeitos, som ligado/mudo (M), tremor da tela (desligado, baixo, normal, forte), tela cheia, painel de atributos (Ctrl), recarga automática, dicas de controles no começo da partida e contador de FPS. Ao lado aparece a lista de controles. **PADRÃO** volta tudo ao original. Os ajustes ficam salvos no navegador. Mouse ou teclado (↑↓ escolhe, ←→ ajusta, ESC volta).

## História

No menu, o botão **HISTÓRIA** (ou a tecla H) mostra o storyboard *Beware Gators*: os 10 quadros de `sprites/historia/historia.gif`, um por vez em tela cheia, com o texto aparecendo como máquina de escrever na faixa preta de baixo de cada quadro. Clique, espaço ou Enter avançam (o primeiro clique completa o texto); ESC volta ao menu. Durante a história toca **Gator Story** (`musica/gator-story.mp3`), que começa do início toda vez e dá lugar ao tema do menu ao sair.

## Cenário

A partida acontece numa clareira cercada de mata, num mapa maior que a tela: a câmera acompanha o jacaré com zoom (puxando um pouco na direção da mira), e quanto mais longe da casa, mais densa fica a mata. Quando a casa sai da tela, uma seta na borda aponta para ela e fica vermelha quando ela está sendo atacada. Jacarés escondidos atrás da casa aparecem como uma silhueta vermelha por cima dela (só a parte encoberta). Os tiros passam por trás das copas e troncos das árvores que estão na frente deles (só no desenho; o tiro continua igual). As árvores balançam com o vento, soltam folhas e tremem quando um jacaré passa por elas. As bordas ficam na sombra das árvores, o centro tem luz de sol, e alguns vagalumes piscam perto da mata. O jacaré anima as pernas ao andar e pisca de vez em quando.

**Dia e noite (modo horda):** 5 waves de dia, 5 de noite, e assim por diante (noite nas waves 6–10, 16–20…). A noite cai aos poucos no intervalo antes da wave 6 e o banner avisa ("A NOITE CAIU" / "AMANHECEU"). Uma coruja pia quando começa a anoitecer e o galo canta quando começa a amanhecer. À noite tudo fica escuro e azulado (a clareira da casa fica um pouco mais clara, como se recebesse a luz da lua de cima), aparecem muitos vagalumes, o jogador ilumina em volta, os tiros (seus e dos ranges) iluminam o caminho com luz amarelada, a casa acende as janelas (luz amarelada) e os jacarés ficam com um ponto vermelho brilhando nos olhos.

## Música

- **Gator Shooter Theme** toca no menu e no campo de treino; no modo horda (roguelike) a música segue o dia e a noite: de dia revezam **Swamp Attack** (a partida começa com ela) e **Morning Scale**; de noite revezam **Midnight Moss** e **River Wave**. Cada faixa toca até o fim e passa a vez para a outra, e cada dia ou noite novo começa pela faixa que não tocou por último; **Old Bill Shop** toca enquanto o velho Bill está na área com a loja (depois a horda volta de onde parou).
- O volume abaixa na pausa e na escolha de cartas. Os volumes de música e efeitos ficam em **Configurações**. M silencia música e efeitos.

## Arquivos

```
gator-shooter/
├── favicon.png   ícone da aba (cabeça do jacaré)
├── index.html      o jogo inteiro (código + sprites embutidos em base64)
├── README.md
├── musica/         músicas (carregadas pelo index.html: precisa ir junto)
├── sons/           originais da coruja e do galo (já embutidos)
└── sprites/        cópias originais dos sprites, só para referência e edição
    ├── jogador/    corpo, pernas, escopeta, uzi, revólver, faca
    ├── inimigos/   basico/, tank/, range/, rusher/, healer/
    ├── velho-bill/ Bill e o carrinho
    ├── itens/      itens da loja, caixas de munição, dentes, fogo
    ├── cenario/    casa, areia, grama, tufos, árvore
    ├── interface/  ícones das cartas, título, mira
    ├── historia/   storyboard Beware Gators
    └── antigos/    versões antigas que não são mais usadas
```

Todos os sprites estão embutidos no `index.html`, então mexer na pasta `sprites/` não muda o jogo: ela serve para guardar os originais.
