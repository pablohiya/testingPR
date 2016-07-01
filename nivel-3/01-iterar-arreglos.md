# Iteración sobre arreglos

## Introducción

Procesar cada elemento de una colección es una operación recurrente. ECS6 introduce nuevos metodos para iterar sobre arreglos, eston son:

- Array.prototype.entries()
- Array.prototype.keys()
- Array.prototype.values()

El resultado de dichas funciones es una secuencia de valores accesibles por medio de un iterador, aunque podemos convertirlo a un array para su visualización.

## Array.Prototype.keys
El método keys() retorna un nuevo objeto iterador que contiene la clave correspondiente a cada indice en el arreglo.

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
El método values() retorna un nuevo objeto iterador que contiene el valor correspondiente a cada indice en el arreglo.

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
El método entries() retorna un nuevo objeto iterador que contiene el par clave/valor correspondiente a cada indice en el arreglo.

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
Utilizar for-of-loop para imprimir el resultado de cada elemento asociado al iterador devuelto por alguna de las funciones mencionadas anteriormente.

### Solución
```javascript
let names = ['chris', 'derek', 'tony'];

for (let value of names.values()) {
	console.log(value);
}
```

