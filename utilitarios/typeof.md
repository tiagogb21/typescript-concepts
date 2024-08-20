## Conceito:

* Permite extrair a tipagem de um objeto

```js
    interface Product {
        id: number;
        name: string;
    }

    const product1: Product = {id: 1, name: "Produto X"}

    const product2: typeof Product = {id: 2, name: "Produto Y"}
```

