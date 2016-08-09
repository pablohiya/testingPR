# Operadores filter y map

## Introducción

El metodo `forEach()`, que poseen todos los array de JS nos permite iterar sobre el array y trabajar sobre cada elemento.
Como resultado de esto, vemos que nuestro array se ha modificado y cada valor corresponde al nuevo valor.

```javascript
var numbers = [1,2,3,4,5,6,7,8,9,10];

console.log(numbers);
[1,2,3,4,5,6,7,8,9,10]
```

### ES5

```javascript
numbers.forEach((n, index) => {
  numbers[index] = n + 1;
});
```

Ahora `numbers` va a ser igual a:
```javascript
console.log(numbers);
[2,3,4,5,6,7,8,9,10,11]
```

O sea, que el array cambió (mutó).

## Array.map

Si quisiéramos mantener el array original sin cambios, iterando en sus elementos, aplicandoles una función y luego obtener un array diferente con los resultados, en **ES5** hubieramos hecho:

```javascript
var numbers = [1,2,3,4,5,6,7,8,9,10];
```

### ES5

```javascript
var plusone = [];
numbers.forEach( function(n, index) {
  plusone [index] = n + 1;
});
```

### ES6

Pero en **ES6** podemos usar la función `map()` .

```javascript
const plusone = numbers.map((n) => n+ 1 );
```

### Resultado

```javascript
console.log(plusone);
[2,3,4,5,6,7,8,9,10,11]
```

## Array.filter

Si en lugar de modificar los elementos de un array, quisieramos ademas elegir cuales son los que formaran parte del nuevo array, en **ES5** podriamos hacer:

```javascript
var numbers = [1,2,3,4,5,6,7,8,9,10];
```

### ES5

```javascript
var evens = [];
numbers.forEach( function(n, index) {
  if( n % 2 === 0 ){
      evens.push (n);
  }
});
```

### ES6

Podemos usar `Array.filter()` para iterar sobre cada elemento, igual que con la función `map()`. Pero la función que usaremos en `filter()` debe dar como resultado `true` para que los elementos pasen al nuevo array, o `false` para evitarlos. Al igual que con `map()`, **no se afecta el array original**.

```javascript
let evens = plusone.filter((n) => n % 2 === 0 );
```

### Resultado

```javascript
console.log(evens);
// => evens : [ 2 , 3 , 4 , 5 , 6 , 7 , 8 , 9 , 10 , 11 ]
```

## Desafios

1. Implementar en ES6 una función `nombresUnicosMayusculas()` que acepte un array de nombres, y devuelva solo aquelos que sean nombres unicos y le cambie su formato pasandolos a mayusculas:



Solución
```javascript
const nombres = [
    "pablo",
    "jazmin",
    "juan carlos",
    "luciana",
    "pablo daniel",
    "maria soledad",
    "nicolas",
    "maura"
];

const nombresUnicosMayusculas = (nombres) => {
    // Extraigo los del array solo aquellos nombres que sean solo una palabra, o sea, que no haya ningun espacio en el valor
    const nombresUnicos = nombres.filter( (nombre) => { return nombre.indexOf(' ') < 0; });
    console.log('1 - Los que son un solo nombre: ', nombresUnicos);
  
    console.log('--------------------------------------------');
    // Convierto los valores a mayusculas
    const nombresUnicosMayusculas = nombresUnicos.map((nombreUnico) => { return nombreUnico.toUpperCase(); });
    console.log('2 - Los nombres en mayusculas: ',nombresUnicosMayusculas);
  
    console.log('--------------------------------------------');
  
    return nombresUnicosMayusculas;
}


// ejecuto la función
const resultado = nombresUnicosMayusculas(nombres);

console.log('3 - El array original permance sin cambios: ',nombres);
console.log('--------------------------------------------');
console.log('4 - El resultado de la función es: ', resultado);
```

[JSBin](https://jsbin.com/xewupo/1/edit?js,console) con la solucion
