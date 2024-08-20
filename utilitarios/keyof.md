```js
    // Ao invés de termos que trabalhar com todos os dados de um objeto, podemos trabalhar com apenas os especificados
    const paths = {
        home: "./home",
        auth: "./auth",
        admin: "./admin",
    };

    type Path = typeof paths;

    // Se tentarmos fazer:
    // const paths: Path = "home"
    // Vai gerar um erro, por que está esperando que todo o objeto seja passada, não apenas um item
    // const paths: Path = { home: "./home" }

    // Para não gerar um erro, precisamos utilizar todas as chaves:
    const path1: Path = {
        home: "./home",
        auth: "./auth",
        admin: "./admin",
    };

    // Para utilizar uma única chave precisamos fazer:
    const path2: keyof Path = "home";
```
