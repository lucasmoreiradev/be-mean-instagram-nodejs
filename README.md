# be-mean-instagram-nodejs 
Guia de referência do conteúdo ministrado no módulo **Nodejs** do curso gratuíto [*Construa seu Instagram com MEAN*](http://dagora.net/be-mean/) da [Webschool.io](https://github.com/Webschool-io/)

#### Apresentação (Slides)
[Link para slides](https://docs.google.com/presentation/d/1_CHh_fTkzgxAnxB3MlZ5WRhTqMLViMk__jkCZiZ3IMA/edit#slide=id.ge8762dc44_0_0)

# Aula 01 

## Definição de Nodejs

**Nodejs** é um interpretador de JavaScript que funciona no servidor em cima do V8, que é o motor de JavaScript do Google, e foi criado em 2009 por Ryan Dahl. 

Sim... o Nodejs foi feito em cima do V8. Mas o que é V8 especificamente? Ele nada mais é que um interpretador de **JavaScript**, tipo uma Máquina Virtual, desenvolvido pelo Google e utilizado no Chrome, feito em C++ e open source. :metal: O trabalho dele é compilar o código JavaScript para o código nativo de máquina para então executá-lo. Ele levou velocidade dos códigos compilados para o JavaScript. Uma analogia: **JVM**.

## Single Thread

O Nodejs trabalha *apenas* com uma thread, mas outras podem ser criadas. Isso economiza muita memória e CPU. Para conseguir gerenciar tudo com apenas uma Thread, existe uma fila infinita que recebe todos os eventos emitidos pelo Nodejs e os executa assincronamente. Esse processo é chamado de **Event Loop**.

## I/O Async

Qualquer função do Nodejs, por padrão, é assíncrona. 

O termo I/O Async quer dizer que qualquer leitura ou escrita de dados não espera seu processo finalizar para continuar o script. Os processos ocorrem "paralelamente" à execução.

## API do Nodejs

```
- tem como base o Unix
- extensivamente modularizada
- extensivamente assíncrona
```

##### Links da Aula
- [Vídeo da Aula](https://www.youtube.com/watch?v=OgfO37F6mdg)
- [Exercício Solicitado](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/classes/nodejs/exercises/class-01.md)
- [Exercício Resolvido](https://github.com/fauker/be-mean-instagram-nodejs/blob/master/exercises/class-01-resolved-fauker-lucas-moreira.md)

# Aula 02

## HTTP

Verbos/métodos mais utilizados: `GET`, `POST`, `PUT`, `DELETE`

## Status Codes

São códigos de retorno HTTP padrão retornados pelo servidor.

1xx - Informational

2xx - Successful

3xx - Redirection

4xx - Client Error

5xx - Internal Server Error

## Função CreateServer

`http.createServer(function(request, response) {});`

Essa função recebe dois parâmetros: request e response.

Request: dados enviados do navegador para o servidor

Response: dados enviados do servidor para o navegador. É a resposta do
servidor.

## QueryString

A **QueryString** é um modelo clássico de manutenção do estado da página. Elas são nada mais do que conjuntos de pares/valores anexados a URL, em diversos sites hoje em dia vemos o uso delas.

Seu uso é simples, após a URL de determinada página, adicionamos o primeiro valor usando a seguinte sintaxe: **?Chave=Valor**. Para passarmos mais de um conjunto, os mesmos devem ser concatenados usando o caractere coringa &.


##### Links da Aula

- [Vídeo da Aula](https://www.youtube.com/watch?v=mDtNcosGgiU)
- [Exercício Solicitado](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/classes/nodejs/exercises/class-02.md)
- [Exercício Resolvido](https://github.com/fauker/be-mean-instagram-nodejs/blob/master/exercises/class-02-resolved-fauker-Lucas-Moreira.md)

# Aula 03

Um pouco de prática com o módulo **http**.

##### Links da Aula

- [Vídeo da Aula](https://www.youtube.com/watch?v=TpNofR3Axsk)
- [Exercício Solicitado](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/classes/nodejs/exercises/class-03.md)
- [Exercício Resolvido](https://github.com/fauker/be-mean-instagram-nodejs/blob/master/exercises/class-03-resolved-fauker-Lucas-Moreira.md)

# Aula 04

## Callbacks

Nas aulas de **callback** pude conhecer o estilo **continuation-passing
style** de programação**, em que passamos por parâmetro para nossa
função uma função de continuação, que é chamada de callback.

## FileSystem

É um módulo nativo do **Node.js**. Ele manipula os diretórios estaticos
do servidor.

Métodos:

- **writeFile**: escreve em um arquivo. Se o arquivo já existe, ele
  apenas escreve no arquivo existente. Caso o arquivo não exista, ele
  irá criar.

```
//forma síncrona

var write = fs.writeFileSync('./file.txt', 'oi');

//forma assíncrona

fs.writeFile('./file.txt', 'Oie', function(err, result) {
  if (err) throw err;
  console.log(result);
})
```

- **mkdir**: Manipular diretórios.

```
//cria um diretório
//assync
fs.mkdir('./euFuiCriadoComONode', function(err, result) {
  if (err) throw err;
  console.log(result);
});

//sync
fs.mkdir('./euFuiCriadoDeFormaAssincronaComONode');
```

- **open**:

```
// r -> flag de apenas leitura
fs.open('./hello.text', 'r', function(err, data) {})
```

- **readdir**: Lista os arquivos de um diretório.

```
fs.readdir('/.meusARquivos', function(err, files){});
```

- **readFile**: função para ler arquivos

```
fs.readFile('./arquivo', 'utf-8', function(err, data){});
```

- **rename**: renomeia um arquivo

```
fs.rename('./arquivo', './renomeado', function(err, data){});
```

##### Links da Aula

- [Vídeo da Aula](https://www.youtube.com/watch?v=f9SE7Y0qYEg)
- [Exercício Solicitado](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/classes/nodejs/exercises/class-04.md)
- [Exercício Resolvido](https://github.com/fauker/be-mean-instagram-nodejs/blob/master/exercises/class-04-resolved-fauker-Lucas-Moreira.md)

# Aula 05

## NPM

Gerenciador de pacotes do Node.js. O **NPM** trabalha através do arquivo
**package.json**, que contém várias informações e dependências do projeto.

- `npm init`: criará o arquivo **package.json**.

- `npm install`: instala as dependências listadas no package.json
  - `npm install -g ou -global *nome_do_modulo*`: instala globalmente
  - `npm install --save ou -S`: instala o módulo localmente e insere o
    mesmo no **package.json**
  - `npm i --save modulo@versao`: instala uma versão em específico
  - `npm i --production`: instala somente as dependências de produção
  - `npm i --save-dev`: instala dependências que serão usadas apenas em
    desenvolvimento
  - `npm i --dev`: instala somente as dependências que serão usadas no
    desenvolvimento
  - `npm i --save-optional`: instala dependências que não interferem no
    script do projeto

- `npm run`: irá executar scripts

## Objetos Globais

Podem ser chamados de qualquer módulo do Nodejs sem uma prévia
importação `require`.

Obs: o `nodejs` não possui variáveis globais. Uma variável criada dentro
de um arquivo só poderá ser acessada dentro deste arquivo.

Voltando aos **objetos globais**, estes são alguns exemplos:

`__dirname`, `__filename`, `new Buffer('teste')`, `setTimeout(function())`,

##### Links da Aula

- [Vídeo da Aula parte 01](https://www.youtube.com/watch?v=Kg4RovUQWeg)
- [Vídeo da Aula parte 02](https://www.youtube.com/watch?v=DD1XKyaq9NE)
- [Exercício Solicitado](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/classes/nodejs/exercises/class-05.md)
- [Exercício Resolvido](https://github.com/fauker/be-mean-instagram-nodejs/blob/master/exercises/class-05-resolved-fauker-Lucas-Moreira.md)

# Aula 06

## Mongoose

É um dos projetos mais utilizados quando trabalhamos
com o MongoDb, pois ele nos dá uma funcionalidade
que não possuímos nativamente, que são os **Schemas**.

### Schema

Como criar um Schema:

```
var mongoose = require('mongoose');

mongoose.connect('mongodb://localhost/be-mean-instagram');
var Schema = mongoose.Schema;
// Criação do Schema
const pokemonSchema = new Schema({
  name:  String,
  description: String,
  type:   String,
  attack:   Number,
  defense:   Number,
  height:   Number
});
```

Após fazer a conexão com o MongoDB, através do função **connect**, são
disponibilizados os seguintes eventos:

```
mongoose.connection.on('connected', function () {
  console.log('Mongoose default connection open to ' + dbURI);
});
mongoose.connection.on('error',function (err) {
  console.log('Mongoose default connection error: ' + err);
});
mongoose.connection.on('disconnected', function () {
  console.log('Mongoose default connection disconnected');
});
mongoose.connection.on('open', function () {
  console.log('Mongoose default connection is open');
});
```

E para finalizar finalizar a conexão com o banco quando o processo do
Nodejs for finalizado:

```
process.on('SIGINT', function() {
  mongoose.connection.close(function () {
    console.log('Mongoose default connection disconnected through app termination');
    process.exit(0);
  });
});
```

### Default

Valor padrão que determinado atrituto da collection sempre terá.

### Tipos de Dados

Tipos de dados suportados pelo **mongoose**.

```
- String
- Number
- Date
- Buffer
- Boolean
- Mixed
- ObjectId
- Array
```

### Validação

Antes de entrarmos em suas especificidades, vamos conhecer algumas regras:

- Validação é definida no tipo do campo, no Schema;
- Validação é uma peça interna do Middleware;
- Validação ocorre quando um documento tenta ser salvo, após ter sido definido com seu padrão;
- Validadores não são executados em valores indefinidos. A única exceção é a validação required;
- Validação é assincronamente recursiva, quando você chamar a função `save` do *Model*, a validação dos sub-documentos é executado também. Se ocorrer um erro ele será enviado para o *callback* da função `save`;
- Validação suporta a personalização completa.

#### Validação Padrão

Como já vimos anteriormente o Mongoose possui validações padrão para alguns tipos de campos, além disso todos os tipos também possui a validação de required. Porém alguns tipos possuem validadores mais específicos como:

- Number: possui os validadores de max e min
- String: possui os validadores de enum, match, maxlength e minlength

**Obs.: Na aula 08 a parte de validações personalizadas será abordada
melhor**

### Model

O Model é a implementação do Schema, sendo o objeto com o qual trabalhamos.

var Model = mongoose.model('Model', schema);

#### Save

```
const _schema = {
  name:  String
}
const pokemonSchema = new Schema(_schema);
const PokemonModel = mongoose.model('Pokemon', pokemonSchema);
const dataModel = { name: 'Suissamon' };
const Suissamon = new PokemonModel(dataModel);

Suissamon.save(function (err, data) {
  if (err) return console.log('ERRO: ', err);
  return console.log('Inseriu:', data);
})
```

Iremos sempre separar o JSON com os dados 
do Model(dataModel) da sua criação 
new PokemonModel(dataModel) para depois executar a função save, passando como parâmetro uma função de callback que irá sempre receber 2 parâmetros nessa ordem: erro(err) e retorno(data).

#### Retrieve

```
const pokemonSchema = new Schema(_schema);
const PokemonModel = mongoose.model('Pokemon', pokemonSchema);
const query = {name: 'Pikachu', attack: {$gt: 90}};

PokemonModel.find(query, function (err, data) {
  if (err) return console.log('ERRO: ', err);
  return console.log('Buscou:', data);
});
```

Caso você queira limitar quais campos devem ser retornados basta passar como JSON 
no segundo parâmetro.

```
const pokemonSchema = new Schema(_schema);
const PokemonModel = mongoose.model('Pokemon', pokemonSchema);

const query = {name: 'Pikachu', attack: {$gt: 90}};
const fields = {name: 1};

PokemonModel.find(query, fields, function (err, data) {
  if (err) return console.log('ERRO: ', err);
  return console.log('Buscou:', data);
})
```

#### findOne

```
const pokemonSchema = new Schema(_schema);
const PokemonModel = mongoose.model('Pokemon', pokemonSchema);

const query = {};

PokemonModel.findOne(query, function (err, data) {
  if (err) return console.log('ERRO: ', err);
  return console.log('Buscou:', data);
})
```

#### findById

```
const pokemonSchema = new Schema(_schema);
const PokemonModel = mongoose.model('Pokemon', pokemonSchema);

const id = '564220f0613f89ac53a7b5d0';

PokemonModel.findById(id, function (err, data) {
  if (err) return console.log('ERRO: ', err);
  return console.log('Buscou:', data);
})
```

#### update

```
const _schema = {
      name:  String,
      description: String,
      type:   String,
      attack:   Number,
      defense:   Number,
      height:   Number
    };
const PokemonSchema = new Schema(_schema);
const Pokemon = mongoose.model('Pokemon', PokemonSchema);
const query = {name: /pikachu/i};
const mod = {attack: 666};

Pokemon.update(query, mod, function (err, data) {
  if (err) return console.log('ERRO: ', err);
  return console.log('Alterou:', data);
});
```

#### delete

```
const Schema = mongoose.Schema;
const _schema = {
      name:  String,
      description: String,
      type:   String,
      attack:   Number,
      defense:   Number,
      height:   Number
    };
const PokemonSchema = new Schema(_schema);
const Pokemon = mongoose.model('Pokemon', PokemonSchema);
const query = {_id: '569b27ebfdafdac00914d495'};

Pokemon.remove(query, function (err, data) {
  if (err) return console.log('ERRO: ', err);
  return console.log('Deletou:', data);
});

Obs: o remove do mongoose é `multi: true`, ou seja, ele remove mais de
um documento. O ideal ao utilizá-lo é sempre passando o id da coleção
que se deseja remover.
```

##### Links da Aula

- [Vídeo da Aula parte 01](https://www.youtube.com/watch?v=O8odFa3dl-k)
- [Vídeo da Aula parte 02](https://www.youtube.com/watch?v=02a_lo_KLwU)
- [Vídeo da Aula parte 03](https://www.youtube.com/watch?v=XeLRYhrcKJo)
- [Exercício Solicitado](https://github.com/Webschool-io/be-mean-instagram/blob/master/Apostila/classes/nodejs/exercises/class-06.md)
- [Exercício Resolvido](https://github.com/fauker/be-mean-instagram-nodejs/blob/master/exercises/class-06-resolved-fauker-Lucas-Moreira.md)
