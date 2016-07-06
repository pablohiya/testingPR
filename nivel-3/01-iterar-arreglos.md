# Iteración sobre arreglos

## Introducción

Procesar cada elemento de una colección es una operación recurrente. ES6 introduce nuevos métodos para iterar sobre arreglos, estos son:

- Array.prototype.entries()
- Array.prototype.keys()
- Array.prototype.values()

El resultado de dichas funciones es una secuencia de valores accesibles por medio de un iterador, aunque podemos convertirlo a un arreglo para su visualización.

## Array.Prototype.keys
El método keys() retorna un nuevo objeto iterador que contiene la clave correspondiente a cada índice en el arreglo.

### ES5
En ES5 se puede utilizar el método Object.keys pasando un arreglo como argumento en vez de un objeto. 
```javascript
var names = ['chris', 'derek', 'tony'];

console.log(Object.keys(names)); // ['0', '1', '2']
```

### ES6
```javascript
let names = ['chris', 'derek', 'tony'];
let entries = names.keys();

console.log(entries.next().value); // 0
console.log(entries.next().value); // 1
console.log(entries.next().value); // 2
console.log(entries.next().done); // true
console.log([...names.keys()]); // [0, 1, 2]
```

## Array.Prototype.values
El método values() retorna un nuevo objeto iterador que contiene el valor correspondiente a cada índice en el arreglo.

### ES5
No existe un método estandar similar para lograr el mismo resultado.

### ES6
```javascript
let names = ['chris', 'derek', 'tony'];
let entries = names.values();

console.log(entries.next().value); // chris
console.log(entries.next().value); // derek
console.log(entries.next().value); // tony
console.log(entries.next().done); // true
console.log([...names.values()]); // ['chris', 'derek', 'tony']
```

## Array.Prototype.entries
El método entries() retorna un nuevo objeto iterador que contiene el par clave/valor, en forma de arrreglo bidimensional, correspondiente a cada índice en el arreglo.

### ES5
No existe un método estandar similar para lograr el mismo resultado.

### ES6
```javascript
let names = ['chris', 'derek', 'tony'];
let entries = names.entries();

console.log(entries.next().value); // [0, 'chris']
console.log(entries.next().value); // [1, 'derek']
console.log(entries.next().value); // [2, 'tony']
console.log(entries.next().done); // true
console.log([...names.entries()]); // [[0, 'chris'], [1, 'derek'], [2, 'tony']]
```

## Desafíos
- Utilizar alguna de las funciones mencionadas anteriormente junto con el for-of-loop para imprimir el valor de cada elemento asociado al iterador devuelto.

### Solución
```javascript
let names = ['chris', 'derek', 'tony'];

for (let value of names.values()) {
	console.log(value);
}
```

- Analizar si el método Array.prototype.keys ignora o no los 'huecos'.

### Solución
```javascript
console.log([...new Array(3).keys()]); // [0, 1, 2] no ignora los huecos.
console.log(Object.keys(new Array(3))); // [] ignora los huecos
```