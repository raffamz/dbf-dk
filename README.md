# Dbf

Gerar arquivos DBF em NodeJs.

## Instalação

```
Npm install dbf-dk
```

## Implementação

No Nodejs:

```js
var dbf = require('../'),
    fs = require('fs');

var buf = dbf.structure([
    {foo:'bar',noo:10},
    {foo:'louie'}
]);

fs.writeFileSync('foo.dbf', toBuffer(buf.buffer));

function toBuffer(ab) {
    var buffer = new Buffer(ab.byteLength);
    var view = new Uint8Array(ab);
    for (var i = 0; i < buffer.length; ++i) {
        buffer[i] = view[i];
    }
    return buffer;
}
```

Esta versão foi personalizada para fornecer também a opção de passar, como parâmetro, valor do tamanho da coluna:

```js
var tamanhoColuna=10;

var buf = dbf.structure ([
    {Foo: 'bar', noo: 10},
    {Foo: 'louie'}
],tamanhoColuna);
```
## API 

### `dbf.structure (array)`

Dado um conjunto de objetos com atributos de cadeia ou número, retornar um objeto DataView que faz referência a um ArrayBuffer que contém um DBF completo estrutura de arquivos.

### `dbf.structure (array,int)`

Dado um conjunto de objetos com atributos de cadeia ou número, e um inteiro referente ao tamanho da coluna do header,  retornar um objeto DataView que faz referência a um ArrayBuffer que contém um DBF completo estrutura de arquivos.

