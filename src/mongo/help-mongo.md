# MongoDB Notes
Para utilizar e instalar iremos utilizar a versão no mínimo 3.2+.

## No SQL:
Idealizado por Carlo Strozzi em 1998. Não utilizava SQL e por isso o nome é NoSQL. Modelo não relacional, os primeiros bancos NoSQL foram: BigTables(Google) e DynamoDB(AWS). Ou banco não relacional temos o Cassandra (Facebook). 

* Não relacional: Modelo Base
* Relacional: Modelo ASET

## História do MongoDB
Foi lançado oficialmente em 2009, a empresa 10gen que hoje é a organização MongoDB, teve ajuda do Facebook. O qual nasceu com propósito de resolver os problemas de performace e flexibilidade de dados. Ele é baseado em **documentos**. Através da linguagem JSON nós conseguimos criar estruturas de dados que mais tardar viraram documentos dentro de uma coleção de dados. 

Diferenças em outros banco entre Relacional e não relacional:
* Escalabidade, Dinanismo, Flexibilidade em trabalhar com documentos e armazenamento de dados;


## Aplicação do mongo
* Pode ser aplicado em qualquer tipo de aplicação, porém em casos de relacionamento não é indicado utilizar;
* Aplicações que possuem dados dinâmicos;
* Necessidade de perfomace;

## Estrutura baseada em documentos
* Estrutura totalmente diferente do modelo relacional (tabela, coluna , linha);
* Documento é escrito em JSON e gravado em BSON;
* Escrita dinâmica e flexível;

Exemplo:

```json
    "name": "Eliot Anderson"
    "email": "eliot@gmail.com"
    "height": 1.75
    "weight": 71
```

## Comandos MongoDB
### Inserindo um dado em minha coleção
```json
 db.getCollection('users').insertOne({
     name: 'Paulo Silva',
     email: 'paulo.silva@mongodb.com',
     age: 99,
     brazilian: true,
     address: {
         street: 'Rua das Palmeiras',
         number: 50
     },
     tags: ['a','b','c'],
     objectNull: null,
     _id: new ObjectId(),
 }
)
```


```json
 db.getCollection('users').insertMany({
     name: 'Joao',
     email: 'joao@mongodb.com',
     age: 32
 },{
     name: 'Maria',
     email: 'maria@mongodb.com',
     age: 12
 },{
     name: 'Pedro',
     email: pedro@mongodb.com',
     age: 74
 }
)
```


### Busca
#### Completa

```json
    db.getCollection('users').find({})
```

#### Específico

```json
    db.getCollection('users').findOne({
        name: 'Paulo Silva'
        age: 99
        })
```

### Atualizar Update
Altera um dado do objeto somente. 

```json
    db.getCollection('users').updateOne({
        name: 'Paulo Silva'
        age: 99
        }, {
            $set: {
                age: 100
            }
        })
```

```json
    db.getCollection('users').updateMany({
        email: 'bulk@gmail.com'
        }, {
            $set: {
                email: 'bulup@gmail.com'
            }
        })
```

### Atualizar Replace
Altera todo o objeto ou atualizar um objeto por completo.

```json
    db.getCollection('users').replaceOne({
        name: 'Paulo Silva'
        age: 99
        }, {
            $set: {
                age: 100
            }
        })
```

### Delete

```json
    db.getCollection('users').deleteOne({
        _id: ObjectId (NUMBER)
        name: 'Paulo Silva'
        age: 99
        }
    )
```


```json
    db.getCollection('users').deleteMany({
        _id: ObjectId (NUMBER)
        name: 'Paulo Silva'
        age: 99
        }
    )
```


### Bulk Operation
CRUD de lista de dados no Mongo.


