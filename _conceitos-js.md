# Conceitos

* Obs.: TODOS os casos abaixos são referentes a conversão implícita de tipos que o JS realiza.

## O seguinte caso será sempre verdadeiro:

```js
    let x;

    if (1 < x < 3) {
        console.log('Qualquer valor será incluído!')
    }
```

### Explicação:

* compara da esquerda para a direita

    1. 1 < x (retorna true)

    2. true < 3 (converte true (boolean) em 1 (number), depois compara 1 < 3 - retorna sempre true)


## O seguinte caso irá retornar NaN

```js
    const obj = { width: 10, height: 15 };

    const area = obj.width * obj.heigth;

    console.log(area)
```

### Explicação:

* JS permite acessar valores de objetos que não foram definidos, retornando undefined

    1. heigth está escrito de forma errada

    2. Acessar obj.heigth irá retornar undefined

    3. Qualquer valor * undefined --> retorna NaN


## O código seguinte irá retorna Infinity:

console.log(4 / []);

### Explicação:

* JS converte [] para 0

    1. [] é convertido para 0

    2. 4 / 0 retorna Infinity


## Math.random < 0.5 irá retornar um erro

### Explicação:

* Math.random é uma função (método), mas ao escrever Math.random sem os parênteses (), estamos acessando a referência dessa função, e não a executando. Isso retorna a própria função, não o valor gerado por ela.

    1. Operator '<' cannot be applied to types '() => number' and 'number'.

    2. Estamos comparando uma função com um número. O JavaScript tentará converter ambos os lados para tipos comparáveis, o que normalmente envolve a conversão de ambos para números.

    3. Como a função Math.random não pode ser convertida para um número diretamente, o JavaScript a tratará como NaN

    4. Então a comparação que realmente acontece é: NaN < 0.5, e comparações com NaN sempre resultam em false, não em um erro.


## Variable 'value' is used before being assigned.

```js
    let value: number

    console.log(value)
```

### Explicação:

* O que acontece:

    1. Quando declaramos uma variável com let, estamos criando um espaço na memória para essa variável.

    2. Criamos o espaço em memória, mas ainda não atribuímos um valor a ele.

    3. Em TypeScript, se tentarmos usar essa variável antes de atribuir um valor a ela, o compilador gera um erro para indicar que estamos tentando acessar uma variável que ainda não foi inicializada.
