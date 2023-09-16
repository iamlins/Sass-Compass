# Documentacao Sass e Compass

1. [O que é Sass?](#sass)
2. [O que é Variáveis?](#variáveis)
3. [O que é Mixins?](#mixins)
4. [O que é Aninhamento?](#aninhamento)
5. [O que é Operadores?](#operadores)
6. [O que é Controle de fluxo?](#controle-de-fluxo)
7. [O que é Loops?](#loops)
8. [O que é Funções?](#variáveis)
9. [Para que serve Importação de arquivos?](#importação-de-arquivos)
10. [Para que serve os Comentarios?](#comentários)
   






## Sass
### O que é Sass? 
SASS (Syntactically Awesome Style Sheets), um pré-processador de CSS que oferece recursos adicionais e facilita a organização e manutenção dos estilos
em uma aplicação web. O SASS permite criar variáveis, classes aninhadas, particionar arquivos e importar estilos e variáveis de forma mais fácil.

## Variáveis
### O que é variáveis? 
Variáveis em Sass (Syntactically Awesome Style Sheets) são usadas para armazenar valores que você deseja reutilizar em seu código CSS. Elas são declaradas com o prefixo $ seguido de um nome de variável e um valor. As variáveis facilitam a manutenção do código, pois permitem que você defina um valor em um único lugar e o use em vários locais dentro do seu arquivo Sass.

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


