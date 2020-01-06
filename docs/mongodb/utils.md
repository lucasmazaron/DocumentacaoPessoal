# Configuração e Comandos MongoDB
#### Windows

!!! important "Importante!!!"
    Na tela de variáveis de ambiente, "variáves do sistema" encontre PATH e adicione o caminho da pasta "BIN" da instalação do mongodb.

___

## Comandos mongodb

!!! note "nota"
    Lembrar que o mongo db é case sensitive como a maioria dos DBs.

* __Iniciar mongodb__: `mongod`  
* __Inicar console__: `mongo`  
* __Mudar de base__: `use nome_base`
* __Criar nova base__: 
    * > Para criar uma nova base, deve-se usar o "use" com o nome da nova base e na sequência criar uma "collection": `db.createCollection('nomeCollection')`.  
    É possível criar inserindo um dado diretamente: `db.nomeCollection.insert({name: "Janeiro/2020", month: 1, year: 2020})`
* __Mostrar dbs__: `show dbs`  
* __Mostar se existe Collections Criadas__: `show collections`  
* __Conforme mostrado acima, para inserir deve-se escrever `db.` seguido do nome da collection e tambem de `.insert`__: 

``` terminal

    db.nomeCollection.insert({
        name: "Janeiro/2020", month: 1, year: 2020, atribArray: [{chave: valor}]
    })

``` 

* __Salvar um dado utilizando save__: 
> O Save, tanto salva como atualiza um dado!

``` terminal
    db.nomeCollection.save(
        {name: "Fevereiro/2020", month: 2, year: 2020, atribArray: [{chave: valor}]}
    )
``` 
* __Atualizar dados__: 

``` terminal

    db.nomeCollection.update(
        {$and: [{month: 1}, {year: 2020}]},
        {$set:{month: 3}}
    )

```

___

### Fazendo consultas 

* __Trazer todos os dados da coleção__: `db.nomeCollection.find().pretty()` -- a função "pretty()" serve somente para formatar a saida do console.
* __Trazer o primeiro registro__: `db.nomeCollection.findOne()`
* __Trazer registro especifico__: `db.nomeCollection.findOne({month: 2})`
* __Trazer registros com condições__
    * __Usando OR__: `db.nomeCollection.find({$or: [{month: 1, month: 2}]}).pretty()`
    * __Verificando se existe um atributo__: `db.nomeCollection.find({atribArray:{$exists:true}}).pretty()`
    * __Pular registros__: `db.nomeCollection.find({year: 2020}).skip(1)`
    * __Pula e Limita registros__: `db.nomeCollection.find({year: 2020}).skip(1).limit(1)`
* __Trazer somente uma determinada coluna__: 

``` terminal
    db.nomeCollection.find(
        {atribArray:{$exists:true}},
        {_id:0, name:1}
    ).pretty()

```
___

### Agregações

!!! note "O que é $project e $group"
    * [Doc. Mongodb - Project](https://docs.mongodb.com/manual/reference/operator/aggregation/project/)
        * Projeta apenas os dados que interessam do documento
    * [Doc. Mongodb - Group](https://docs.mongodb.com/manual/reference/operator/aggregation/group/)
        * __$group__: Critérios de agrupamento utilizado para consolidar os dados de todas as coleções em unico registro.

Vamos imaginar que existe um atributo que chama "credits" onde contem o valor de crédito de determinada conta bancária.
Se eu quero trazer a somatória deste atributo, deve ser feito como abaixo:

``` terminal
    db.nomeCollection.aggregate([{
        $project:{
            credit:{$sum:"$credits.value"}
        },
        $group:{
            _id:null, 
            credit:{$sum:"$credit"}
        }
    }])
```

### Drop Database

!!! note "Nota"
    Lembrando que será dropada a base que estiver em utilização no momento. Garanta utilizando use nome_database

``` terminal
   
    db.dropDatabase()

```

### Exclução

``` terminal
   
    db.nomeCollection.remove(
        {month:2}
    )

```

### Count

``` terminal
   
    db.nomeCollection.count()

```

