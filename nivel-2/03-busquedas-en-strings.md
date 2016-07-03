# Búsquedas en strings

## Introducción

ES6 ha incluido el método includes(), el cual determina cuando un string puede ser encontrado
dentro de otro string, retornando true o false según sea el caso.

### ES5

```javascript
var str = "Hello wOrld";

if (str.indexOf("wOrld") !== -1) {
  console.log("contains string wOrld");
}
```

### ES6

La sintaxis del método includes es la siguiente:
```javascript
str.includes(searchString[, position])
```
donde "searchString" es el string a ser búscado dentro del string "str"
y "position" es un parámetro opcional, el cual representa la posición
en la cual comenzará a ser buscado el string "searchString" dentro del string "str",
si no agregas este segundo parámetro, él tendrá un valor por defecto de 0 lo
que significa que buscará desde el comienzo del string.

```javascript
// El método includes() es sensible a mayúsculas o minúsculas
'Blue Whale'.includes('blue'); // returns false
'Blue Whale'.includes('Blue'); // returns true
```

## Desafios

1. Dado el string
```javascript
let str = 'To be, or not to be, that is the question.';
```
realiza una búsqueda del string "not to be", ingresando el parámetro position
y asegurate que el resultado sea true.

```javascript
// El segundo parámetro debe ser <= 10 para que el resultado sea el esperado
str.includes("not to be", 10)
```
