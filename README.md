# Soul Jump — Grupo GVS

Jogo estilo *Doodle Jump* com o Soul, mascote do Grupo GVS. Página estática: HTML + Canvas, sem dependências, sem backend.

## Execução

1. Abra `index.html` no navegador (duplo clique), ou
2. sirva a pasta: `python -m http.server 8765` e acesse `http://localhost:8765`.

Mantenha a pasta `assets/` ao lado do `index.html`.

## Controles

| Ação | Teclado | Toque |
|---|---|---|
| Mover | `←` `→` ou `A` `D` | botões ‹ › no canto inferior da tela |
| Pausar / continuar | `Espaço` | botão de pausa |
| Iniciar | `Enter` | botão Jogar |
| Voltar ao menu | `Esc` (pausa ou fim de jogo) | botão Menu |

## Telas

- **Computador**: o campo ocupa toda a altura da janela (mantendo a proporção) e o painel lateral traz logo, pontos, raios, recorde, barra de poder, som, pausa e tema. Não há cabeçalho sobre a área jogável.
- **Celular** (ou janela estreita): painel vira uma faixa compacta no topo, o campo usa a largura toda e dois botões grandes (esquerda / direita) aparecem nos cantos inferiores durante o jogo. Segure para mover; dá para trocar de lado sem soltar o dedo.
- **Arquivo único para celular**: `soul-jump-celular.html` traz imagens e estilos embutidos (≈1,5 MB) e pode ser enviado direto ao celular. Ele é gerado a partir de `index.html`; ao alterar o jogo, gere-o de novo. O `index.html` depende da pasta `assets/` ao lado.

## Regras

- Altura vira pontos (1 ponto a cada 15 px); raio coletado = +30; drone derrotado = +100.
- Viga azul: plataforma normal · esteira laranja: se move · rocha cinza: quebra e não rebate · mola: pulo alto · drone roxo: pule em cima para derrotar, encostar de lado encerra o jogo.
- Obstáculos novos: **espinhos** sobre plataformas (pousar neles encerra o jogo), **centelha/morcego** que voa em onda (sempre fatal) e **pedra/abóbora** que cai do topo depois de um alerta piscante. O drone/fantasma continua podendo ser pisado. Com o foguete (ou vassoura) ligado, todos são destruídos.
- Duas versões, escolhidas no menu: **Original** (mina e energia) e **Halloween** (noite assombrada: fantasmas, morcegos, abóboras, lápides, chapéu de bruxa no Soul, doces no lugar dos raios e vassoura no lugar do foguete). A escolha e o recorde ficam salvos por versão.
- **Acessórios de voo** (ícone sobre as plataformas; dentro do voo o Soul é invulnerável e destrói obstáculos): **turbina solar** (pás de painel solar, voa como helicóptero por 2,5 s) e **hidrelétrica** (voa como foguete por 4 s). O foguete/vassoura da barra de poder continua existindo.
- **Pedras de imunidade** (sem dano de obstáculos, mas cair no vazio ainda encerra o jogo): **preta** 5 s, **marrom** 10 s, **ouro** 15 s. A faixa na base do campo mostra a pedra e o tempo restante; pegar uma pedra mais curta não reduz a atual.
- **Botas e capacete**: o Soul começa sem botas e sem capacete (há vários espalhados pelo caminho). Com **botas**, os espinhos não o matam, mas as botas se perdem até achar outras. Com **capacete**, a primeira batida em um obstáculo é absorvida: o capacete se perde, o Soul pisca por 1,5 s protegido e só depois fica vulnerável de novo. A pedra preciosa protege sem gastar o capacete.
- **Pisar derrota**: pular em cima de qualquer obstáculo (drone, fantasma, centelha, morcego, pedra, abóbora, nuvem, ANM) o destrói e rebate o Soul como uma mola.
- **Obstáculos**: **ANM** (monstrinho grande e parado, de olhões, orelhas em leque e pés de pato, de blusa com a sigla, sobre uma plataforma larga) e **nuvem cinza** (vai de um lado a outro, escurece o entorno e é fatal ao toque).
- **Missão "Usina parada"**: a partir de ~3.000 px de altura (e depois a cada 4.500 a 7.000 px) um alerta vermelho pisca no topo, os obstáculos somem e aparece uma peça acima. Pegue a peça (ela passa a girar ao redor do Soul) e encoste na usina apagada, mais acima: as luzes acendem, o alerta sai, +300 pontos e os obstáculos voltam. Se a peça ou a usina ficarem para trás, são recolocadas mais acima. Uma seta no topo indica onde está o alvo.
- Barra de poder: cada raio coletado carrega 1 ponto; com 10 o foguete liga por 4 segundos. Nesse tempo o Soul sobe rápido, atravessa plataformas e destrói qualquer obstáculo (drones, +100 cada). A barra esvazia durante o uso e só volta a carregar depois; raios coletados com o foguete ligado contam pontos, mas não carregam a barra.
- Recorde guardado só no navegador (`localStorage`, chaves `gvsSoulJumpRecorde` e `gvsSoulJumpRecordeHalloween`). Nenhum dado pessoal é coletado.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | jogo completo (HTML, CSS e JS comentados) |
| `assets/tokens.css` | tokens visuais oficiais (skill `gestao-visual`), copiados sem alteração |
| `assets/logo-gvs.png`, `logo-gvs-negativa.png` | logo oficial (tema claro / escuro) |
| `assets/soul.png` | Soul completo (usado no menu), recortado de `soul-original.png` |
| `assets/soul-base.png`, `soul-botas.png`, `soul-capacete.png` | camadas do Soul: base sem capacete e sem botas, mais botas e capacete sobrepostos |
