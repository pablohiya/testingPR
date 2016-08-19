# Destructuring

## Introducción

La asignación por *Destructuring* permite extraer datos desde arrays u objetos hacia distintas variables. Como veremos esto aplica allí en donde se **reciben** datos. En este ejemplo utilizamos *Destructuring* en la asignación a una variable:

```javascript
var foo = { bar: 'pony', baz: 3 };
var {bar, baz} = foo;
console.log(bar);
// <- 'pony'
console.log(baz);
// <- 3
```

Esto mismo en ES5 se escribiría:

```javascript
var foo = { bar: 'pony', baz: 3 };
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
function f([x]) { ··· };
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
var foo = { bar: 'pony', baz: 3 };
var {bar: a, baz: b} = foo;
console.log(a);
// <- 'pony'
console.log(b);
// <- 3
```

ES5:

```javascript
var foo = { bar: 'pony', baz: 3 };
var a = foo.bar;
var b = foo.baz;
```

Podemos obtener esas propiedades de tan profundo como queramos en la jerarquía de un objeto:

```javascript
var foo = { bar: { deep: 'pony', dangerouslySetInnerHTML: 'lol' } };
var {bar: { deep, dangerouslySetInnerHTML: sure }} = foo;
console.log(deep);
// <- 'pony'
console.log(sure);
// <- 'lol'
```

Vemos como la variable *sure* quedó asignada con el valor de foo.bar.dangerouslySetInnerHTML.


Por defecto, las propiedades que no se hayan encontrado serán **undefined**, tal como sucede cuando accedemos propiedades de un objeto utilizando la sintaxis de punto o corchetes.

```javascript
var {foo} = {bar: 'baz'};
console.log(foo);
// <- undefined
```

Pero si queremos acceder a una propiedad anidada de un padre inexistente, obtendremos una excepción:

```javascript
var {foo:{bar}} = {baz: 'ouch'};
// <- Exception
```


También tenemos la posibilidad de definir valores por defecto en casos en los que no se encuentre el valor en los parámetros.

```javascript
var {foo=3} = { foo: 2 }
console.log(foo)
// <- 2
var {foo=3} = { foo: undefined }
console.log(foo)
// <- 3
var {foo=3} = { bar: 2 }
console.log(foo)
// <- 3
```

Lo que también podemos aplicar en caso de asignación por Array.
```javascript
var [foo] = []
console.log(foo)
// <- undefined
var [bar=10] = [undefined]
console.log(bar)
// <- 10
var [baz=10] = []
console.log(baz)
// <- 10
```

Para hacer esto en mismo en ES5 tendríamos que hacer la evaluación manualmente y asignar el valor por defecto en caso de no recibir valor.
```javascript
function foo(bar){
  bar = bar || 3;
  console.log(bar);
}
foo()
// <- 3
foo(2)
// <- 2
```


Usos prácticos del destructuring.

Retornar múltiples valores en una función:
```javascript
function calcularDimensiones(){
  return [10, 5];
}
var [ancho, alto] = calcularDimensiones();
console.log(ancho);
// <- 10
console.log(alto);
// <- 5
```
ES5
```javascript
function calcularDimensiones(){
  return {ancho: 10, alto: 5};
}
var obj = calcularDimensiones();
console.log(obj.ancho);
// <- 10
console.log(obj.alto);
// <- 5
```


Recibir parámetros de una función como un objeto puede ser muy útil para configuraciones, por ejemplo al hacer un llamado AJAX.
```javascript
function ajax({ url = 'localhost', puerto = 80, metodo = 'GET' }) {
  console.log('URL:', url, 'Puerto:', puerto, 'Método', metodo);
}

ajax({
  url: 'example.com',
  puerto: 8080
});
// <- URL: example.com Puerto: 8080 Método: GET

ajax({
  metodo: 'POST'
});
// <- URL: localhost Puerto: 80 Método: POST
```
ES5
```javascript
function ajax(config){
  var url, puerto, metodo;

  config = config || {};

  url = config.url || 'localhost';
  puerto = config.puerto || 'localhost';
  metodo = config.metodo || 'localhost';

  console.log('URL:', url, 'Puerto:', puerto, 'Método', metodo);
}
```

Podemos utilizarlo también para mapear atributos en un bucle.
```javascript
var libros = [
  { titulo: 'Titulo 1', autor: 'Autor 1' },
  { titulo: 'Titulo 2', autor: 'Autor 2' }
];
libros.forEach(function( { titulo, autor } ) {
  console.log(titulo, '-', autor);
});
// <- Titulo 1 - Autor 1
// <- Titulo 2 - Autor 2
```



### Desafíos

**Desafío 1**
Dado la siguiente lista de sentencias:

let [a = 'Bar', b] = [, 'Foo'];
console.log(a);

let [c = 'Bar', d] = ['Foo'];
console.log(c);

(function( { a, b, c } ){
  console.log(a);
})( { b: 'Bar' } );

(function ( { bar: baz } ){
  console.log(bar); 
})( { bar : 'a' } );


Evaluar y contestar cual seria la respuesta de cada uno de los llamados a console.log.

**Solución**
Bar
Foo
undefined
Exception: bar is not defined




**Desafío 2**
Dado la siguiente lista de sentencias:

function calcularCoordenadas(){
  console.log(x, y);
}

calcularCoordenadas({ coordX: 30, coorY:15 }); // esperado: 30, 10
calcularCoordenadas({ coordY: 30 }); // esperado: 15, 30
calcularCoordenadas({ z: 2 }); // esperado: 15, 10
calcularCoordenadas(); // esperado: 15, 10


Puedes reescribir la función calcularCoordenadas, utilizando destructuring, para que todas las sentencias impriman las coordenadas esperadas en cada caso?

**Solución**

function calcularCoordenadas( { coordX: x = 15, coordY: y = 10 } = {} ){
  console.log(x, y);
}
