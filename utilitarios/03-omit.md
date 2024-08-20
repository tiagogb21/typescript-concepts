```js
    interface User {
        id: number;
        name: string;
        email: string;
        age: number;
    }

    let createUser: User = {
        id:1,
        name: 'John',
        email: 'Doe',
        age: 37,
    }

    // Podemos informar quais propriedades NÃO devem ser utilizadas
    let updateUser: Omit<User, "id" | "age"> = {
        name: 'John Doe',
        email: 'johndoe@gmail.com'
    }
```