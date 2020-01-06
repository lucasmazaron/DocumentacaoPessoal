# NodeJS

!!! important "Importante"
    * O NodeJS é baseado em módulos.
    * Cada arquivo representa um módulo.
    * Importa-se um módulo utilizando `require('nomemodulo')`
    * Será importado o que foi exportado por "module.exports = nomefuncao" no outro arquivo

## Singleton

!!! important "Importante"
    * Quando você importa determinado módulo "require('')", atribuindo a uma variável, por padrão o que é retornado é um singleton.
    * Um singleton é um objeto que tem uma unica instancia. É compartilhado com quem pedir aquele mesmo módulo.


## Objeto Global (correspondente do window)

!!! important "Importante"
    * __Evitar escopo global__
    * Ao declarar um Objeto em um módulo, ele não é declarado como global.


> Declarando um objeto global:

``` javascript

    global.obj = { name: "sou global!"}

```

> Acessando objeto global

``` javascript

    console.log(global.obj.name)

```

## Lodash

!!! important "Importante"
    * Lodash não faz parte do core do node. Para utilizar, deve-se instalar o mesmo. `npm i lodash`
    * [Doc. Lodash](https://lodash.com/docs/4.17.15)


## npm init

!!! important "Importante"
    * `npm init` cria o __package.json__ que fica guardado as configs da aplicação como módulos a serem baixados quando utilizado `npm i`

* Utilizar --save para que o node salve a dependencia em package.json, Ex.: `npm i lodash --save`. Utilizar --save-dev quando a dependencia for necessária somente para desenvolvimento.


## Passagem de parâmetro

> Módulo que recebe o parâmetro

``` javascript

    module.exports = function(param) {
        console.log(`O param informado foi ${param}`)
    }

```

> Módulo que utiliza a função

``` javascript

    const moduloComParam = require('./arq')

    //O param informado foi este aqui
    moduloComParam('este aqui')

```


## Process (ARGV)

!!! important "Importante"
    * `process.argv` retorna todos os parâmetros utilizados na chamado do arquivo node.

> Exemplo de Utilização

``` javascript

    console.log(process.argv)

    function temParam(param) {
        return process.argv.indexOf(param) !== -1
    }


    if (temParam('--producao')) {
        console.log('Atenção, aplicação em ambiente de produção!')
    } else {
        console.log('Aplicação em ambiente de desenvolvimento!')
    }
```


### STDIN /STDOUT

!!! important "Importante"
    * `process.stdout.write()` imprime algo no console
    * `process.stdin.on()` recebe valor digitado pelo usuário

> EX:

``` javascript

    process.stdout.write('Informe a porta que a API ficará escutando: ')

    process.stdin.on('data', function(data){
        process.stdout.write(`Aplicação iniciando na porta ${data.toString()}`)
    })
```


## Módulo FS

!!! note "Nota"
    * Serve para ler/modificar arquivos, listar pasta, etc...
    * Faz parte do core do Nodejs.

``` javascript

    const fs = require('fs')

    //__dirname constante padrão nodejs. É a pasta atual do projeto
    const files = fs.readdirSync(__dirname)


    files.forEach(f => console.log(f))
```