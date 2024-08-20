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

    // Podemos escolher quais propriedades queremos utilizar de uma interface
    // Vantagem: reaproveitamos a tipagem
    type Student = 'name' | 'email';

    let updateUser: Pick<User, Student> = {
        name: 'John Doe',
        email: 'johndoe@gmail.com'
    }
```
