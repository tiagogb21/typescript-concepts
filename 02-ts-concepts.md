## Javascript

JS: é uma linguagem NÃO tipada.NÃO precisamos definir um tipo ao criar uma variável.

JS: uma variável pode receber valores diferentes.

Linguagens tipadas: ao criar uma variável, precisamos definir qual o tipo ela vai assumir.

## Typescript

TS: adiciona tipagem no JS. No final, o TS é convertido em JS.

* TS é um recurso utilizado para desenvolvimento, no momento em que o build é feito, o código é convertido para JS.

## Exemplo:

código TS:

```ts
    type Result = 'pass' | 'fail';

    const message: Record<Result, string> = {
        'pass': 'the code has passed!',
        'fail': 'the code has failed!',
    }

    function verify(result: Result) {
        return message[result];
    }

    console.log(verify('pass')); // 'the code has passed!'

    console.log(verify('fail')); // 'the code has failed!'

    console.log(verify()); // avisa que existe um erro
```

build to js: faz a remoção da tipagem

```js
    const message = {
        'pass': 'the code has passed!',
        'fail': 'the code has failed!',
    }

    function verify(result) {
        return message[result];
    }

    console.log(verify('pass')); // 'the code has passed!'

    console.log(verify('fail')); // 'the code has failed!'

    console.log(verify()); // undefined
```

## Vantagens em utilizar typescript

1. Feedback mais rápido de erros;
2. Antecipa erros que seriam vistos em execução;
3. Ajuda a manter a consistência do código;
4. Ajuda no trabalho em times;
5. Refatoração mais fácil;
6. Recurso de autocomplete;
