## Cantina do Campus: correções do style.css ##

## Os seis erros ##

1. **Cascata:** o `h1` usava `color: #14213d !important`. O `!important` ignora a ordem normal da cascata e dificulta qualquer sobrescrita futura. Removi o `!important`; a cor continua a mesma porque nenhuma outra regra disputa o `h1`.
2. **Especificidade:** o preço em promoção ficava escuro porque `#cardapio .preco` (um id + uma classe) tem mais peso que `.promocao` (só uma classe). Troquei o seletor por `#cardapio .promocao`, que empata em especificidade e, por vir depois no arquivo, vence. Sem `!important`.
3. **Box model:** `.cartao` tinha `width: 100%` mais `padding` e `border`. Com `content-box`, a largura real passava de 100% e criava rolagem lateral. Adicionei `* { box-sizing: border-box; }` e troquei o `width` por `flex: 1 1 280px`.
4. **Contraste:** `.subtitulo` usava `#c4c4c4` sobre branco, razão de cerca de 1,7:1. Mudei para `#4b5563`, razão de cerca de 7,6:1 (mínimo exigido: 4,5:1).
5. **Foco:** `.menu a:focus { outline: none; }` apagava o contorno e quem navega com Tab não via onde estava. Removi a regra e criei `.menu a:focus-visible` com contorno laranja de 2px, visível sobre o fundo azul.
6. **Alinhamento:** `.menu li { margin-left: 610px; }` empurrava o menu no chute e quebraria em qualquer outra largura de tela. Removi a margem; o alinhamento agora vem do flexbox.

## Layout com flexbox ##

- `.topo`: `display: flex; justify-content: space-between; align-items: center;` coloca a marca de um lado e o menu do outro. Em `.menu ul`, `display: flex; gap: 24px` põe os links em linha.
- `.cartoes`: `display: flex; flex-wrap: wrap; gap: 16px;` deixa três cartões lado a lado na tela grande, quebrando linha na janela estreita. Tirei o `margin-bottom` dos cartões porque o `gap` já cuida do espaçamento.

O `index.html` não foi alterado e não há `!important` no arquivo.
