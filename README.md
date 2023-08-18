# Projeto-09
https://www.figma.com/file/K9cOW7SvBA9wV10ANyEpMm/Galaxies-%E2%80%A2-Projeto-Explorer-(Community)?type=design&node-id=0-755&mode=design&t=axgzQpoA522miX4t-0

O Grid CSS, também conhecido como "CSS Grid Layout" ou simplesmente "Grid", é um sistema de layout bidimensional que permite criar layouts complexos e responsivos no HTML de forma mais eficiente e flexível. Ele permite dividir o espaço em linhas e colunas, criando uma estrutura de grade na qual os elementos podem ser posicionados.

O Grid CSS oferece um alto nível de controle sobre o posicionamento e o dimensionamento dos elementos em relação às linhas e colunas definidas. Ele é especialmente poderoso para criar layouts complexos de páginas da web, onde elementos podem ser facilmente organizados em diferentes áreas da grade, permitindo um melhor alinhamento, espaçamento e distribuição de conteúdo.

Fronteditor: https://www.fronteditor.dev/


Todo grid é composto de 2 principaos grupos:
`container: o pai` e `itens: o(s) filhos`

--
### CONTEINER (pai) precisa ter:
- display: grid; (Eu posso utilizar o grid columns e row no mesmo pai)

![Alt text][def]
[def]: image.png


- grid-template-columns: (um ao lado do outro, podendo criar colunas automáticas para     baixo, agrupando quando excede o espamento na lateral)
  A propriedade grid-template-columns é uma das muitas ferramentas poderosas oferecidas pelo sistema Grid CSS para criar layouts flexíveis e responsivos. Ela permite definir a estrutura das colunas da grade, que é fundamental para organizar o conteúdo de forma eficiente em um layout.
  - 1fr 1fr 1fr (posso utilizar como uma fração para cada coluna)
  - 100px 200px 300px (posso utilizar colunas com tamanhos diferentes)
  - reapet(3, 1fr) (posso utilizar reapet, no primeiro campo coloco quantas vezes quero   que repita, e na segunda o tamanho da fração)

    Tamanhos Fixos: Você pode definir tamanhos fixos para as colunas usando unidades de medida como px, em, rem, etc.
    Porcentagens: É possível definir as colunas em relação a porcentagens da largura do contêiner da grade.
    Frações (Fr): As frações (fr) distribuem o espaço disponível igualmente entre as colunas.
    Mínimo e Máximo: Você pode usar a combinação de valores como minmax(min, max) para definir um tamanho mínimo e máximo para as colunm

    .grid-container {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr; /* 3 colunas com proporções 1:2:1 */
  }

    .grid-container {
    display: grid;
    grid-template-columns: 100px auto 200px; /* 3 colunas com tamanhos fixos e uma coluna flexível */
  }

    .grid-container {
     display: grid;
     grid-template-columns: repeat(3, 1fr); /* 3 colunas iguais com frações */
  }

    .grid-container {
     display: grid;
     grid-template-columns: minmax(150px, 1fr) 2fr; /* Primeira coluna com mínimo de 150px e máximo de 1fr */
    }



- grid-template-rows (altura das linhas);
  A propriedade grid-template-rows é fundamental para definir a estrutura das linhas da grade, permitindo que você organize o conteúdo verticalmente de maneira eficiente em um layout. Ela é uma parte importante do sistema Grid CSS para criar layouts flexíveis e responsivos.

    Tamanhos Fixos: Você pode definir tamanhos fixos para as linhas usando unidades de medida como px, em, rem, etc.
    Porcentagens: É possível definir as linhas em relação a porcentagens da altura do contêiner da grade.
    Frações (Fr): As frações (fr) distribuem o espaço disponível igualmente entre as linhas.
    Mínimo e Máximo: Você pode usar a combinação de valores como minmax(min, max) para definir um tamanho mínimo e máximo para as linhas.

.grid-container {
  display: grid;
  grid-template-rows: 1fr 2fr 1fr; /* 3 linhas com proporções 1:2:1 */
}

.grid-container {
  display: grid;
  grid-template-rows: 100px auto 200px; /* 3 linhas com tamanhos fixos e uma linha flexível */
}

.grid-container {
  display: grid;
  grid-template-rows: repeat(3, 1fr); /* 3 linhas iguais com frações */
}

.grid-container {
  display: grid;
  grid-template-rows: minmax(150px, 1fr) 2fr; /* Primeira linha com mínimo de 150px e máximo de 1fr */
}


### ITENS (filhos)

- grid-column;
  - grid-column-start;
  - grid-column-end;

EXEMPLO:
#app div:nth-child(1) {
  grid-column-start: 1;
  grid-column-end: 3;

  Nesse caso a linha 1 da coluna preenchera 2 "quadrados"
}

-grid-row;
  - grid-row-start;
  - grid-column-end;

### Areas

  - grid-template-areas:
  "A B B"
  "A B B"
  "A C D"

  `grid-template-areas` é uma propriedade do CSS utilizada em Grid Layout para definir a disposição visual de células (ou áreas) dentro de um grid. Ela permite criar um layout mais claro e semântico, atribuindo nomes específicos às áreas do grid e depois associando esses nomes aos elementos HTML que serão posicionados nesses espaços.

  A propriedade `grid-template-areas` permite que você crie um "mapa" visual do seu layout, onde cada célula do grid é representada por um nome que você escolhe. Aqui está um exemplo de como você pode usar essa propriedade:

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
  grid-template-areas:
  "A B B"
  "A B B"
  "A C D"
}

.header {
  grid-area: A;
}

.main {
  grid-area: B;
}



Nesse exemplo, o layout é dividido em três linhas (header, main e footer) e duas colunas (main e sidebar). O `grid-template-areas` associa esses nomes às áreas correspondentes do grid.

Essa abordagem facilita a compreensão e manutenção do layout, especialmente quando se trabalha com designs complexos. Além disso, ajuda a deixar o código mais semântico, já que os nomes das áreas são mais descritivos do que índices numéricos.

Lembrando que a propriedade `grid-template-areas` deve ser usada em conjunto com outras propriedades do Grid Layout, como `grid-template-columns` e `grid-template-rows`, para definir a estrutura completa do grid.

.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
  grid-template-areas:
    "header header"
    "main sidebar"
    "footer footer";
}

.header {
  grid-area: header;
}

.main {
  grid-area: main;
}

.sidebar {
  grid-area: sidebar;
}

.footer {
  grid-area: footer;
}

<aside> é um elemento HTML utilizado para representar conteúdo relacionado ou complementar ao conteúdo principal de uma página web. Geralmente, o conteúdo dentro do elemento <aside> é considerado secundário ou opcional, e sua finalidade é fornecer informações adicionais que não são essenciais para a compreensão do conteúdo principal da página.

A propriedade gap é um shorthand para as propriedades row-gap e column-gap```

### PROPRIEDADE DE ALINHAMENTO

Existem 9 propriedades fundamentais

** 6 aplicadas em container **
`align-content` (eixo Y)
`justify-content` (eixo X)
`place-content` (eixo X e Y)

`align-itens` (eixo Y)
`justify-itens`(eixo X)
`place-itens` (eixo X e Y)

** 3 aplicadas em itens **
`align-self` (movimenta dentro dele mesmo eixo y)
`justify-self` (movimenta dentro dele mesmo eixo x)
`place-self`(movimenta dentro dele mesmo eixo x e y)

Então podemos separar em 3 grupos;
`align`, `justify`, `place`

Em cada um deles irá observar ou o
  - conteúdo do elemento  `content`
  - itens do elemento `itens`
  - o próprio elemento `self`

  .container {
  display: flex;
  justify-content: center; /* Alinha os itens ao centro ao longo do eixo X */
}

.container {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  justify-content: space-between; /* Distribui os itens com espaços entre eles ao longo do eixo X */
}

### PROPRIEDADES AUTO

  - grid-auto-flow
  - grid-auto-row
  - grid-auto-columns

  A propriedade CSS grid-auto-flow é utilizada no contexto do Grid Layout para controlar como os itens (ou células) são automaticamente posicionados dentro do grid quando não há espaço suficiente nas linhas ou colunas existentes.

Essa propriedade permite definir como o grid deve se comportar quando há itens excedentes que não couberam nas linhas ou colunas especificadas anteriormente. Existem quatro valores possíveis para grid-auto-flow:

row: Os itens são posicionados automaticamente nas linhas do grid, criando novas linhas conforme necessário para acomodar os itens.
column: Os itens são posicionados automaticamente nas colunas do grid, criando novas colunas conforme necessário.
row dense: Similar a row, mas tenta preencher os espaços vazios nas linhas criadas.
column dense: Similar a column, mas tenta preencher os espaços vazios nas colunas criadas.
Exemplo de uso:

css
Copy code
.container {
  display: grid;
  grid-template-columns: repeat(3, 100px);
  grid-auto-flow: row; /* Posiciona os itens automaticamente nas linhas */
}
Neste exemplo, se houver mais itens do que pode ser acomodado em três colunas, eles serão automaticamente posicionados em novas linhas.

A propriedade grid-auto-flow é especialmente útil quando se trabalha com grids dinâmicos em que o número de itens pode variar e não é possível definir uma estrutura fixa de linhas e colunas. Ela oferece mais flexibilidade ao layout do grid ao permitir que ele se ajuste dinamicamente conforme os itens são adicionados.




