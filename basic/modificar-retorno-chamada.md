# Modificando o retorno de chamada em js:

* Em JavaScript, é possível modificar o retorno de um construtor, como mostrado no exemplo abaixo:

    ```js
        class Obj1 {
            constructor() {
                return "Dentro do obj1";
            }
        }

        class Obj2 {
            constructor() {
                return new Obj1();
            }
        }

        let obj = new Obj2()

        console.log(obj) // Retornará "Dentro do Obj1" (retorno do método constrututor de Obj1)
    ```
