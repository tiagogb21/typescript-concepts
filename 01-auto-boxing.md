# Conceito:

Em JavaScript, tipos primitivos **não possuem propriedades nem métodos** diretamente.

* Tipos Primitivos:

    1. number
    2. string
    3. boolean
    4. null
    5. undefined
    6. symbol
    7. bigInt

## Então, como conseguimos acessar métodos de uma string?

Isso acontece porque o JavaScript realiza uma conversão implícita do tipo primitivo para um objeto wrapper temporário, que tem métodos e propriedades associadas. Essa conversão é conhecida como **auto-boxing**.

Exemplo:

```js
    let name = 'John'; // Tipo primitivo

    // Acessando um método de string
    let upperName = name.toUpperCase(); // 'JOHN'

    // Por trás dos panos, o JS transforma 'name' em um objeto temporário de String
```

## Auto-Boxing:

O JavaScript automaticamente "empacota" o tipo primitivo string em um objeto String temporário para que você possa acessar métodos como .toUpperCase().

```js
    let name = 'John';
    typeof name; // 'string'

    let upperName = name.toUpperCase();
    typeof upperName; // 'string'
```

## Conversão Temporária:

A conversão de primitivo para objeto acontece de forma temporária. Após o método ser chamado, o valor retorna ao seu estado primitivo sem modificar o original.
