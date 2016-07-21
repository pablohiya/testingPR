# Uso del nuevo objeto Set

## Introducción

Otra de las estructuras pendientes en ES5 es la implementación de un set de datos arbitrarios y unívocos. ES6 introduce el objeto Set para este propósito, una colección de elementos únicos con una interfaz de métodos (add(), has(), etc) sencilla para su manipulación:

- new Set([iterable]);

En ES5, para almacenar una colección de elementos unívocos debemos recurrir a objetos donde las claves son únicas (tipo string) ó por medio de arreglos donde los índices son únicos (tipo number). Por su parte, el nuevo objeto Set de ES6 funciona para cualquier tipo de dato, es igual de eficiente y maneja el NaN correctamente. 

### ES5
```javascript
var myObjSet = {'chris': true, 'derek': true, 'tony': true};
console.log(Object.keys(myObjSet)); // 'chris', 'derek', 'tony'
```

### ES6
```javascript
let mySet = new Set();
mySet.add('chris');
mySet.add('derek');
mySet.add('tony');
console.log(mySet.keys()); // 'chris', 'derek', 'tony'
```

## Set

El objeto Set([iterable]) permite guardar una colección elementos únicos de cualquier tipo, esto es, valores primitivos (string, number, etc) tanto como referencia a objetos. Todos los elementos del objeto iterable (opcional) pasado como parámetro en su creación serán agregados al nuevo objeto Set, sino están duplicados. Esto significa que cada elemento en el set puede agregarse una sola vez por lo que no pueden existir dos o más elementos iguales en el conjunto.

```javascript
let mySet = new Set([1]);
console.log(mySet); //Set {1}
mySet.add(1); // already exists, so ignored
console.log(mySet); //Set {1}
mySet.add('1'); // different type
console.log(mySet);// Set {1, "1"}
mySet.add({foo: 'bar'});
console.log(mySet); //Set {1, "1", Object {foo: "bar"}}
mySet.add({foo: 'bar'}); //different object reference
console.log(mySet); //Set {1, "1", Object {foo: "bar"}, Object {foo: "bar"}}
```

## Desafíos
### A- Dado el siguiente arreglo de nombres.

```javascript
const people = ['tony', 'marie', 'serena', 'katy', 'tony', 'marie', 'serena', 'serena', 'derek', 'chris'];
```

#### 1- Crear un objeto Set para eliminar los nombres repetidos, y luego chequear cuantos duplicados había.

### Solución
```javascript
let peopleSet = new Set(people);
console.log(people.length - peopleSet.size); // 4
```

### 2- Chequear si todos los distintos nombres de la lista inicial fueron efectivamente agregados al Set.

### Solución
```javascript
const allNamesSaved = people.every(name =>{
  return peopleSet.has(name);
});
console.log(allNamesSaved);// true
```

### B- Evaluar como el Set maneja los diferentes valores falsy en javascript.

### Solución
```javascript
let mySet = new Set();
mySet.add(0);
mySet.add('');
mySet.add(false);
mySet.add(+0); //treated as 0
mySet.add(-0); //treated as 0
mySet.add(null);
mySet.add(undefined);
mySet.add(NaN);
console.log(mySet); //Set {0, "", false, null, undefined, NaN}
```