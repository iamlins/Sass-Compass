# Documentação Sass e Compass

<div id="topo"></div>  

1. [O que é Sass?](#sass)
2. [O que é Variáveis?](#variáveis)
3. [O que é Mixins?](#mixins)
4. [O que é Aninhamento?](#aninhamento)
5. [O que é Operadores?](#operadores)
6. [O que é Controle de fluxo?](#controle-de-fluxo)
7. [O que é Loops?](#loops)
8. [O que é Funções?](#funções)
9. [Para que serve Importação de arquivos?](#importação-de-arquivos)
10. [Para que serve os Comentarios?](#comentários)
   






## Sass
### O que é Sass? 
SASS (Syntactically Awesome Style Sheets), um pré-processador de CSS que oferece recursos adicionais e facilita a organização e manutenção dos estilos
em uma aplicação web. O SASS permite criar variáveis, classes aninhadas, particionar arquivos e importar estilos e variáveis de forma mais fácil.

[voltar ao topo da página](#topo)

## Variáveis
### O que é variáveis?
Variáveis em Sass (Syntactically Awesome Style Sheets) são usadas para armazenar valores que você deseja reutilizar em seu código CSS. Elas são declaradas com o prefixo $ seguido de um nome de variável e um valor. As variáveis facilitam a manutenção do código, pois permitem que você defina um valor em um único lugar e o use em vários locais dentro do seu arquivo Sass.

Abaixo mostro um exemplo de como criar uma variável em Sass:
```
$cor-primaria: #FF0000; $cor-secundaria: #00FF00;

body { background-color: $cor-primaria; }

h1 { color: $cor-secundaria; }
```
[voltar ao topo da página](#topo)

## Mixins
### O que é Mixins?
Os mixins são uma funcionalidade do SASS que permitem criar blocos de código reutilizáveis. Eles funcionam de forma semelhante a funções em outras linguagens de programação.
Com os mixins, é possível definir um conjunto de estilos que pode ser aplicado a diferentes elementos ou classes. Isso ajuda a evitar repetições de código e facilita a manutenção dos estilos.
Para criar um mixin, você utiliza a diretiva `@mixin` seguida do nome do mixin e dos estilos que deseja aplicar. Por exemplo:

```
@mixin estilo-botao {
  background-color: blue;
  color: white;
  padding: 10px;
  border-radius: 5px;
}

.botao {
  @include estilo-botao;
}
```

### Nesse exemplo, o mixin estilo-botao define um conjunto de estilos para um botão. Em seguida, o mixin é aplicado à classe .botao utilizando a diretiva @include. Isso faz com que os estilos definidos no mixin sejam aplicados à classe.
Os mixins podem receber parâmetros, o que permite torná-los mais flexíveis e reutilizáveis. Por exemplo:

```
@mixin estilo-botao($cor, $tamanho) {
  background-color: $cor;
  color: white;
  padding: $tamanho;
  border-radius: 5px;
}

.botao {
  @include estilo-botao(blue, 10px);
}
```
### Nesse exemplo, o mixin `estilo-botao` recebe dois parâmetros: `$cor` e `$tamanho`. Ao utilizar o mixin, é possível passar valores diferentes para esses parâmetros, personalizando os estilos do botão.
Os mixins são uma poderosa ferramenta do SASS que ajudam a tornar o código mais modular, reutilizável e fácil de manter.

[voltar ao topo da página](#topo)

## Aninhamento 
### O que é Aninhamento?

Classes aninhadas são uma funcionalidade do SASS que permite definir estilos para elementos HTML que estão dentro de outros elementos. Com as classes aninhadas, é possível escrever estilos de forma mais organizada e modular, evitando repetições de código. Por exemplo, ao definir um estilo para um elemento pai, é possível definir estilos para os elementos filhos dentro dessa classe, sem precisar repetir o seletor completo. Isso torna o código mais legível e fácil de manter.

Suponha que você tenha a seguinte estrutura HTML:


```<div class="container">
  <div class="header">
    <h1>Título</h1>
    <p>Descrição</p>
  </div>
  <div class="content">
    <p>Conteúdo principal</p>
  </div>
</div>
```

### Agora em Sass ele ficaria da seguinte maneira:

```
.container {
  background-color: #f0f0f0;
}

.container .header {
  background-color: #333;
  color: #fff;
}

.container .header h1 {
  font-size: 24px;
}

.container .header p {
  font-size: 16px;
}

.container .content {
  padding: 20px;
}
```
[voltar ao topo da página](#topo)

## Operadores
### O que é Operadores? 
Os operadores são utilizados para realizar operações matemáticas e manipular valores. Existem quatro tipos de operadores em Sass:

1. Operadores aritméticos: São utilizados para realizar operações matemáticas, como adição (+), subtração (-), multiplicação (*) e divisão (/).

```
$largura: 200px; $altura: 150px;
div { width: $largura + 50px; height: $altura - 20px; font-size: $largura * 0.5; line-height: $altura / 2; }
```
2. Operadores de comparação: São utilizados para comparar valores, como igual a (==), diferente de (!=), maior que (>), menor que (<), maior ou igual a (>=) e menor ou igual a (<=).

```
$idade: 18;
@if $idade >= 18 { // Código para maiores de idade } @else { // Código para menores de idade }
```
3. Operadores lógicos: São utilizados para combinar expressões lógicas, como "e" (and), "ou" (or) e "não" (not).

```
$cor-fundo: #FFFFFF; $cor-texto: #000000;
@if $cor-fundo == #FFFFFF and $cor-texto == #000000 { // Código para cores padrão } @else { // Código para outras combinações de cores }
``` 
4. Operadores de concatenação: São utilizados para concatenar strings, como o operador de concatenação (+).

 ```
$nome: "João"; $sobrenome: "Silva";
$nome-completo: $nome + " " + $sobrenome;
p { content: "Olá, " + $nome-completo + "! Bem-vindo!"; }
 ```

Esses operadores são úteis para realizar cálculos, comparações e manipulações de valores dentro do Sass, permitindo criar estilos dinâmicos e reutilizáveis. Espero que isso esclareça sua dúvida!

## Controle de fluxo
### O que é Controle de fluxo? 
Controle de fluxo é uma estrutura utilizada em programação para controlar a execução de um programa, permitindo que certas partes do código sejam executadas apenas se determinadas condições forem atendidas.
Em Sass, o controle de fluxo é geralmente realizado por meio de diretivas condicionais, como @if, @else if e @else. Essas diretivas permitem que você execute diferentes blocos de código com base em condições específicas.

```
$idade: 18;
@if $idade >= 18 { // Código para maiores de idade } @else { // Código para menores de idade }
```

### Nesse exemplo, utilizamos a diretiva @if para verificar se a variável $idade é maior ou igual a 18. Se a condição for verdadeira, o bloco de código dentro do @if será executado. Caso contrário, o bloco de código dentro do @else será executado.

[voltar ao topo da página](#topo)

## Loops
### O que são os Loops?
Loops, ou laços de repetição, são estruturas utilizadas em programação para executar um bloco de código várias vezes. Em Sass, existem duas diretivas principais para a criação de loops: @for e @each.


1.  @for: Essa diretiva permite que você crie um loop baseado em um contador. Você pode definir uma variável de controle, um valor inicial, uma condição de parada e um incremento.

```
@for $i from 1 through 5 { // Código a ser repetido width: 100px * $i; }
```

2. @each: Essa diretiva permite que você crie um loop baseado em uma lista ou mapa. Você pode percorrer cada item da lista ou mapa e executar um bloco de código para cada um deles.

 ``` 
$cores: red, green, blue;
@each $cor in $cores { // Código a ser repetido background-color: $cor; }
```

[voltar ao topo da página](#topo)

## Funções
### O que é Funções?
As funções são blocos de código reutilizáveis que podem receber parâmetros e retornar um valor. Elas permitem criar estilos dinâmicos e personalizados de acordo com as necessidades do projeto.

[voltar ao topo da página](#topo)

## Importação de arquivos
### Para que serve a Importação de arquivos
A importação de arquivos em Sass permite dividir o código em vários arquivos e organizá-los de forma modular. Isso facilita a manutenção e reutilização do código, tornando-o mais legível e organizado.

[voltar ao topo da página](#topo)

