# Estruturas de controle, Funções e Closure;

Nesta aula abordamos as principais características de funções.

Abaixo segue alguns links e material de apoio:

# Funções em JavaScript

Funções em JavaScript são de primeira classe, ou seja, podem ser atribuidas a variáveis, passadas por parâmetro e retornadas por outras funções.

## Declaração

Sua declaração se da a partir da palavra chave **function** e podem ser ciada das seguintes formas:

### Function Declaration

```js
  function soma(x, y) {
    return x + y;
  }

  soma(1, 2);
  > 3
```

### Function Expression

```js
  var soma = function(x, y) {
    return x + y;
  };

  soma(1, 2);
  > 3
```

A grande diferença entre as duas é que as **Function Declaration** são carregadas antes da interpretação do código. Lembrando que em JavaScript as declarações são içadas ([Hoisting](http://www.w3schools.com/js/js_hoisting.asp)).

## Invocação

A declaração de uma função não necessariamente implica na invocação da mesma. Para invocar uma função existem quatro maneiras distintas:

### Invocação direta

A invocação direta se dá através do **()**.

Exemplo:

```js
  soma(1, 2);
  > 3
```

### Invocando funções de objetos

Invocação de funções dentro de objetos se dá através de variáveis.

Exemplo:

```js
  var getNomeCompleto = function() {
    return this.nome + ' ' + this.sobrenome;
  };

  var pessoa = {
    nome: 'Taco',
    sobrenome: 'barry',
    getNomeCompleto = getNomeCompleto
  };

  pessoa.getNomeCompleto();
  > Taco barry

  getNomeCompleto();
  > undefined undefined
```

Repare que o **this** na função assume o contexto de onde ela está sendo invocada.

### Invocação através de call e aply

Funções podem ser invocadas através dos métodos **call** e **aply** contidos nelas mesmas. Para este tipo de invocação devemos especificar o contexto e seus respectivos parâmetros.

```js
  var pessoa = {
    nome: 'Taco',
    sobrenome: 'barry'
  };

  var getNomeCompleto = function() {
    return this.nome + ' ' + this.sobrenome;
  };

  getNomeCompleto.call(pessoa);
  > Taco barry

  getNomeCompleto.apply(pessoa, []);
  > Taco barry
```

A diferença de **call** e **aply** se da na forma como passamos os parâmetros para a função a ser chamada onde em **call** utilizamos a passagem de parâmetros convencionais e no **apply** utilizamos um array de parâmetros.

### Invocação através do operador new

Través do operador **new** podemos invocar funções para a criação de objetos. Por convenção as funções que serão utilizadas desta forma são criadas com a primeira letra em maíusculo assim como as classes em Java.

Exemplo:

```js
  function Pessoa(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }

  var taco = new Pessoa('Taco jp', 24);
  var jov = new Pessoa('matheus', 26);
```

Para entender melhor como o operador **new** funciona basicamente ele cria um novo objeto para passar como escopo da função ou seja, this referencia o objeto que está sendo criado e desta forma conseguimos simular uma estrutura similar as classes do Java.

## Closures

Closures (fechamentos) é a capacidade das funções de "lembrarem" do contexto onde as mesmas foram criadas. Esta capacidade de associar dados do ambiente com uma função  está diretamente ligada a orientção a objetos, onde os objetos nos permitem associar dados (propriedades do objeto) utilizando um ou mais métodos.

Exemplo:

```js
function soma(x) {
  return function(y) {
    return x + y;
  };
}

var somaBase = soma(5);

var soma5 = somaBase(5);
> 10

var soma10 = somaBase(10);
> 15
```

## Callback

Callback é um pedaço de código executável que é passado como parâmetro para ser executado em um momento oportuno, seja após a consulta assincrona a um banco de dados ou após a obtenção da resposta de uma requisição ajax.

Esta estratégia é bem parecida com o padrão de projeto listener.

Exemplo:

```js

let query = { nome: 'Taco' };
Cliente.find(query, callback);

// Esta função será executada após a pesquisa no banco de dados
function callback(err, data) {
  if (err) console.log(err);
  else console.log(data);
}

```

## Artigos

We Love Dev:
- [Zero to Hero JavaScript - Funções]()

## Video Aulas

Rodrigo Branas:
- [Desvendando a linguagem JavaScript - #12 - Operadores](https://www.youtube.com/watch?v=lqTjJGQCq_4&index=12&list=PLQCmSnNFVYnT1-oeDOSBnt164802rkegc)
- [Desvendando a linguagem JavaScript - #7 - Function - Parte 1](https://www.youtube.com/watch?v=OqR0hE-DQn4&index=7&list=PLQCmSnNFVYnT1-oeDOSBnt164802rkegc)
- [Desvendando a linguagem JavaScript - #8 - Function - Parte 2](https://www.youtube.com/watch?v=m9uPpURTI0c&index=8&list=PLQCmSnNFVYnT1-oeDOSBnt164802rkegc)

Aulas de Programação:
- [ECMAScript 2015 (ES6) - Aula 08: Parâmetro Padrão](https://www.youtube.com/watch?v=l7HcsrVcNe4)
- [ECMAScript 2015 (ES6) - Aula 09: Operador Spread/Rest](https://www.youtube.com/watch?v=8mTJPEcF3bw)
- [ECMAScript 2015 (ES6) - Aula 10: Arrow Function (Parte 1)](https://www.youtube.com/watch?v=KrB6wFuK6Qg)
- [ECMAScript 2015 (ES6) - Aula 11: Arrow Function (Parte 2)](https://www.youtube.com/watch?v=bJT1wz-72BU)

## Exemplos dados na aula:

## Exercícios de fixação:
