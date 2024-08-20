## Conceito

```js
    interface User {
        id: number;
        name: string;
        email: string;
    }

    let createUser: User = {
        id:1,
        name: 'John',
        email: 'Doe',
    }

    // Partial --> Torna todas as propriedades opcionais
    let updateUser: Partial<User> = {
        name: 'John Doe',
    }
```