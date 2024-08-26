# Informações

* 3 pontos:

    1. JS

    2. Ambiente de execução

        - Node (backend) - ambiente de execução

        - Browser (frontend)

* Como o JS faz requisições:

    1. XMLHttpRequest (desde 1998)

        - obs.: recebe esse nome por que na época NÃO existia o conceito de JSON

        - Por ser um objeto necessita ser instanciado, parametrizado, além disso necessita solicitar o envio da requisição e ouvir a resposta através de eventos

        - AJAX: ir no servidor, buscar a informação, SEM a necessidade de recarregar a página

        - Vantagem: concede um controle maior da requisição

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

    - obs.: devemos colocar o < script > dentro do < head >, por que como estamos criando um código de interceptação, queremos que ele carregue o mais cedo possível

    2. fetch (desde 2015)

        - É uma função que retorna uma Promise

        - Desvantagem: NÃO tem tratamento de evento - faz a requisição e recebe

        - ex.: NÃO permite fazer uma barra de progresso de quanto falta de download

* quando utilizar:

    - XMLHttpRequest --> se precisar de controle sobre a requisição

    - fetch --> se precisar de algo mais simples
