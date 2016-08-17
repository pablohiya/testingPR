# Destructuring

## Introducción

La asignación por *Destructuring* permite extraer datos desde arrays u objetos hacia distintas variables. Como veremos esto aplica allí en donde se **reciben** datos. En este ejemplo utilizamos *Destructuring* en la asignación a una variable:

```javascript
var foo = { bar: 'pony', baz: 3 }
var {bar, baz} = foo
console.log(bar)
// <- 'pony'
console.log(baz)
// <- 3
```

Esto mismo en ES5 se escribiría:

```javascript
var foo = { bar: 'pony', baz: 3 }
var bar = foo.bar;
var baz = foo.baz;
```


Destructuring se puede utilizar en las siguientes situaciones. En todos los casos, se le asigna el valor 'a' a x.

```javascript
// Declaraciónd de variables:
let [x] = ['a'];
const [x] = ['a'];
var [x] = ['a'];
 // Asignación:
[x] = ['a'];

// Definición de parámetros:
function f([x]) { ··· }
f(['a']);
```

## Destructuring vs. constructing

Como ya conocemos, JavaScript tiene operaciones para *construir* datos:
```javascript
let obj = {};
obj.first = 'Jane';
obj.last = 'Doe';
```

Y también para extraer estos datos:
```javascript
let f = obj.first;
let l = obj.last;
```

Vemos que estamos utilizando la misma sintaxis que utilizamos para construir los datos.


Ahora bien, ya sabemos también que JavaScript tiene una sintaxis mucho más cómoda para construir objetos, el **object literal**:
```javascript
let obj = { first: 'Jane', last: 'Doe' };
```

En ES6 *Destructuring* permite el mismo tipo de sintaxis para extraer datos:
```javascript
let { first: f, last: l } = obj;
```

De la misma manera que el **object literal** nos permite definir varios valores (incluso anidados) a la vez, utilizando *Destructuring* podemos extraer varios valores al mismo tiempo.


## Mapear propiedades a alias:

```javascript
var foo = { bar: 'pony', baz: 3 }
var {bar: a, baz: b} = foo
console.log(a)
// <- 'pony'
console.log(b)
// <- 3
```

ES5:

```javascript
var foo = { bar: 'pony', baz: 3 }
var a = foo.bar;
var b = foo.baz;
```

Podemos obtener esas propiedades de tan profundo como queramos en la jerarquía de un objeto:

```javascript
var foo = { bar: { deep: 'pony', dangerouslySetInnerHTML: 'lol' } }
var {bar: { deep, dangerouslySetInnerHTML: sure }} = foo
console.log(deep)
// <- 'pony'
console.log(sure)
// <- 'lol'
```

Vemos como la variable *sure* quedó asignada con el valor de foo.bar.dangerouslySetInnerHTML.


Por defecto, las propiedades que no se hayan encontrado serán **undefined**, tal como sucede cuando accedemos propiedades de un objeto utilizando la sintaxis de punto o corchetes.

```javascript
var {foo} = {bar: 'baz'}
console.log(foo)
// <- undefined
```

Pero si queremos acceder a una propiedad anidada de un padre inexistente, obtendremos una excepción:

```javascript
var {foo:{bar}} = {baz: 'ouch'}
// <- Exception
```


## Valores default
TBD


## Usos Comunes
TBD
