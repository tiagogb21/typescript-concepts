## Type

* Define um alias (apelido) para qualquer tipo, incluindo tipos primitivos, objetos, funções, etc.

```js
    type Point = {
        x: number;
        y: number;
    };
```

## Interface

* Usada para definir a forma de objetos. Especifica as propriedades e métodos que um objeto deve ter.

```js
    interface Point {
        x: number;
        y: number;
    }
```

## Diferenças:

* Suporte a extensão e composição

    1. Type:

    - Mais versátil: pode definir qualquer coisa, como tipos primitivos, interseções, uniões, arrays, tuplas, etc.

    ```js
        type StringOrNumber = string | number;

        type Tuple = [number, string];
    ```

    - Pode usar união (|) e interseção (&) de tipos, permitindo combinar vários tipos.

    ```js
        // União de tipos:

        type Shape = Circle | Square;
    ```

    ```js
        // Interseção de tipos:

        type Point = {
            x: number;
            y: number;
        };

        type Point3D = Point & {
            z: number;
        };
    ```

    - Obs.: Não pode ser mesclado. Se tentarmos declarar o mesmo type duas vezes, o TypeScript retornará um erro.

    ```js
        type User = {
            name: string;
        };

        type User = {
            age: number;
        }; // Erro: Duplicate identifier 'User'
    ```

    - Obs.: Não pode ser implementado diretamente em uma classe, mas podemos usá-lo para definir a forma dos objetos que as classes manipulam.

    ```js
    ```

    2. interface:

    - Suporta herança (extends). Uma interface pode estender outra interface, permitindo o uso da herança de múltiplas interfaces.

    ```js
        interface Point {
            x: number;
            y: number;
        }

        interface Point3D extends Point {
            z: number;
        }
    ```

    - Obs.: Pode ser mesclada. Se declararmos a mesma interface mais de uma vez, o TypeScript as combinará em uma única interface.

    ```js
        interface User {
            name: string;
        }

        interface User {
            age: number;
        }

        // Agora, User tem tanto 'name' quanto 'age'
        const user: User = { name: "Tiago", age: 28 };
    ```

## Diferenças filosóficas
