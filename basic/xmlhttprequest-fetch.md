# Interceptando requisições HTTP no JavaScript

## Contextualização

* JS permite realizar requisições HTTP - comunicação entre cliente e servidor

* Principais ambientes de execução:

        - Backend: Node

        - Frontend: Browser

## Importância:

* Carregar dados de uma API SEM recarregar a página

## Como o JS faz requisições:

    1. XMLHttpRequest (desde 1998)

    2. Fetch

### XMLHttpRequest

* É um objeto

* obs.: XML, na época da criação ainda NÃO existia o conceito de JSON

* características;

    - **Controle mais detalhado**: Permite monitorar o progresso de uma requisição e trabalhar com eventos específicos.

    - **Instanciação**: Requer a criação de um objeto, configuração e escuta de eventos para gerenciar as respostas do servidor.

    - **Uso em AJAX**: Permite atualizar partes de uma página sem recarregar, como em aplicações AJAX.

* Vantagem: concede um controle maior da requisição

* ex.:

    ```js
        function ping(mode) {
            // instanciando o objeto XMLHttpRequest
            const xmlHttpRequest = new XMLHttpRequest();

            // abrindo uma requisição do tipo POST
            // true --> indica que o código deve ser assíncrono
            xmlHttpRequest.open('POST', 'url', true)

            // enviando a requisição
            // antes do send podemos amarrar eventos
            xmlHttpRequest.send();

            // chamando novamente a requisição após 10s
            xmlHttpRequest.onload = () => setTimeout(() => ping(), 10000);
        }
    ```

* Nota: Coloque o código `<script>` no `<head>` para garantir que ele seja carregado o mais cedo possível, uma vez que estamos criando um código que intercepta requisições.

### fetch (desde 2015)

* É uma função que retorna uma Promise - facilita o tratamento assíncrono de requisições

* características:

    - Mais simples

* Desvantagem:

    - NÃO tem tratamento de evento - faz a requisição e recebe

* ex.: Não suporta eventos como o XMLHttpRequest, o que dificulta o monitoramento de progresso, como o estado de download.

    ```js
        fetch('url')
            .then(response => response.json())
            .then(data => console.log(data));
    ```

## interceptação:

* Interceptar requisições permite monitorar, modificar ou registrar informações sobre as chamadas HTTP realizadas em uma aplicação. Isso pode ser útil para fins de depuração, monitoramento ou alteração de comportamento.

    ```js
        <script>
            // interceptação com XMLHttpRequest

            const originalXMLHttpRequest = window.XMLHttpRequest;

            // toda vez que o XMLHttpRequest for chamado, irá chamar a função associada
            // interceptamos a função, mas mantivemos a função original
            // conseguimos controle total sobre o código XMLHttpRequest
            window.XMLHttpRequest = function() {
                console.log(`XMLHttpRequest created`)
                const instance = new originalXMLHttpRequest(...Array.from(arguments));
                // readystatechange --> passamos o tratamento do evento
                // ao trabalhar com eventos, devemos usar function e não arrow function, para interceptar o this, se fossemos utilizar o af ao invés de this, deveriamos chamar o instance (depende do ambiente externo)
                instance.addEventListener("readystatechange", function () {
                    console.log(`XMLHttpRequest for URL "${this.responseURL}". State changed to: ${this.readyState}`)
                });
                return instance;
            }

            // Interceptação com fetch:

            const originalfetch = window.fetch;

            window.fetch = function() {
                console.log(`fetch called`)

                // Precisamos realizar a lógica para poder pegar de forma posterior a url
                const request = arguments[0]?.constructor === Request ? arguments[0] : undefined;

                // obtendo a url
                const url = request?.url ?? arguments[0];

                console.log(`Fetch called for url "${url}"`)

                return new Promise((resolve, reject) => {
                    originalFetch.apply(this, arguments)
                        .apply(this, arguments)
                        .then(function () {
                            const response = arguments[0];

                            console.log(`fetch returned for url "${url}" with status ${response.status} ${response.statusText}`)
                        })
                        .catch(function() {
                            const error = arguments[0];
                            console.log(`fetch fail for url "${url}": ${error}`);
                            reject.apply(this, arguments)
                        })
                        .finally(function() {
                            console.log(`fetch finished for url "${url}"`)
                        })
                });
            }
        </script>
    ```

## quando utilizar:

* **XMLHttpRequest**: É mais adequado quando você precisa de maior controle sobre a requisição, como monitorar o progresso de uploads ou downloads.

* **fetch**: Ideal para requisições mais simples e diretas, onde o controle fino dos eventos não é necessário.

## Conceito extra:

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
