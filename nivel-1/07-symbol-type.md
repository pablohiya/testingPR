# Tipo Symbol

## Introducción   

Tipo de dato unico e inmutable que se utiliza como un identificador para las propiedades del objeto. El simbolo puede tener una descripcion opcional, pero solo con fines de depuración.

### ES5:
```javascript
// no equivalent in ES5

```


### ES6
```javascript
Symbol("foo") !== Symbol("foo") // true
const foo = Symbol()
const bar = Symbol()
typeof foo === "symbol" //true
typeof bar === "symbol" //true
let obj = {}
obj[foo] = "foo"
obj[bar] = "bar"    
JSON.stringify(obj) // {}
Object.keys(obj) // []
Object.getOwnPropertyNames(obj) // []
Object.getOwnPropertySymbols(obj) // [ foo, bar ]
```

### Desafíos
**Desafío 1**  
Dado la siguiente lista de sentencias:

`typeof Symbol() === 'symbol'`
`typeof Symbol('foo') === 'symbol'`
`typeof Symbol() === 123`
`typeof Symbol.iterator === 'symbol'`

Evaluar y contestar cual seria la respuesta de cada una de ellas.

**Solución**  
   
`typeof Symbol() === 'symbol'`   // true
`typeof Symbol('foo') === 'symbol'`  //true
`typeof Symbol() === 123`  // false
`typeof Symbol.iterator === 'symbol'`  //true   
   