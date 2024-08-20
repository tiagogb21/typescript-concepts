```js
    // Permite escolher quais serão os tipos das chaves e dos valores
    const scores: Record<string, number> = {
        "id": 123
        "score": "abc", // retorna um erro - Type 'string' is not assignable to type 'number'
    }
```

```js
    // Para limitar valores
    type Profile = "admin" | "user" | "guest";

    const user: Record<Profile, number> = {
        "admin": 1,
        "adm": 1, // retorna erro, por que não existe o valor adm no type Profile
        "admin": "abc" // retorna erro, por que espera que o valor seja um number
    }
```
