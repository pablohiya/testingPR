# Convertir datos a arreglo

## Introducción

Permitir convertir en un arreglo otros tipos de datos de forma trivial era una funcionalidad que se venia postergando. ES6 introdujo finalmente esta posibilidad por medio del método:

- Array.from

Este método acepta varios tipos de datos como entrada, pero su uso frecuente es mapear objetos iterables y objetos array-like en un tipo de dato arreglo, como por ejemplo sobre consultas en el DOM.

```javascript
let mySet = new Set();
mySet.add('chris');
mySet.add({ foo: 'bar'});
mySet.add(5);
console.log(Array.from(mySet)); //Ejemplo sobre objeto iterador
// ['chris', {foo: 'bar'}, 5]

console.log(Array.from((document.querySelectorAll('ul li'))) //Ejemplo sobre un objeto array-like
// [<li>, <li>, ...]
```

## Array.from

El método Array.from(arrayLike[, mapFn[, thisArg]]) retorna un nuevo arreglo. Acepta los siguientes argumentos:
- arrayLike: Requerido. Estructura a ser convertida en arreglo.
- mapFn: Opcional. Función invocada por cada elemento del arreglo.
- thisArg: Opcional. Objeto a usar al ejecutar mapFn.

El método from() puede verse también como alternativa al uso de map(), y también logra el mismo cometido que el operador spread (...) de ES6.

### ES5
```javascript
function cast () {
  return Array.prototype.slice.call(arguments)
}
console.log(cast('chris', 'derek', 'tony')); // ['chris', 'derek', 'tony']
```

### ES6
```javascript
function cast () {
  return Array.from(arguments)
}

console.log(cast('chris', 'derek', 'tony')) // ['chris', 'derek', 'tony']
```

## Desafíos

##### 1- Convertir a arreglo el siguiente objeto array-like:

```javascript
const obj = { length: 3, '0': 'chris', '1': 'derek', '2': 'tony'};
```

### Solución

```javascript
console.log(Array.from(obj)); // ['chris', 'derek', 'tony']
```

##### 2- Dada la siguiente lista, retornar un arreglo de strings con el nombre de cada persona capitalizado.

```javascript
const people = [
    {name: 'tony', genre: 'M'}, {name: 'marie', genre: 'F'}, { name: 'serena', genre: 'F'},
    {name: 'katy', genre:'F'}, {name: 'derek', genre: 'M'}, {name: 'chris', genre: 'M'}
];
```
### Solución

```javascript
function capitalize (person) {
	return person.name.charAt(0).toUpperCase() + person.name.substr(1).toLowerCase()
}

console.log(Array.from(people, capitalize));
// ['Tony', 'Marie', 'Serena', 'Katy', 'Derek', 'Chris']
```

##### 3 - Generar una secuencia de números de 1 a 10 a partir de un arreglo vacío de 10 posiciones.

### Solución

```javascript
console.log(Array.from(new Array(10), (number, index) => {return index + 1}));
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```