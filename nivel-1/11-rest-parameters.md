# Rest Parameters

## Introducción
A veces resulta necesario crear una función que acepte un número variable de parámetros. Por ejemplo, una función que concatene strings puede aceptar un número ilimitado de strings a concatenar como argumentos.
ES6 provee una nueva forma de manejar este tipo de funciones.
Veamos cómo sería una función que tiene que verificar si un texto contiene una serie de strings, de modo que:

```javascript
contieneTodos("banana", "b", "nan"); // true
contieneTodos("banana", "c", "nan"); // false.
```

En ES5, lo haríamos de la siguiente forma:

```javascript
function contieneTodos(texto) {
  for (var i = 1; i < arguments.length; i++) {
    var string = arguments[i];
    if (texto.indexOf(string) === -1) {
      return false;
    }
  }
  return true;
}
```

Esta implementación utiliza el objeto "mágico" **arguments**, que es un objeto **array-like** que contiene los argumentos parámetros que fueron pasados a la función. El código funciona, pero resulta poco legible. La función tiene un sólo parametro **texto**, de modo que a primera vista no se puede deducir que acepte otros. Aparte necesitamos ser cuidadosos al iterar sobre el resto de los parámetros desde el índice 1 (y no el 0), y si quisiéramos cambiar la función para que acepte otro parámetro deberíamos modificar la implementación.

Veamos entonces la forma de hacer esto con ES6:

```javascript
function contieneTodos(texto, ...strings) {
  for (let string of strings) {
    if (texto.indexOf(string) === -1) {
      return false;
    }
  }
  return true;
}
```

## Diferencia entre los parámetros rest y el objeto arguments

Hay 3 principales diferencias entre los parámetros rest y el objeto arguments:

* Los parámetros rest son sólo los que no se les ha asignado un nombre, mientras que el objeto arguments contiene todos los argumentos pasados a la función
* El objeto arguments no es un arreglo real, mientras los parámetros rest son instancias de Array, lo que significa que los metodos como sort, map, forEach o pop pueden aplicarse directamente;
* El objeto arguments tiene una funcionalidad adicional específica para ella misma (como la propiedad callee).


## Desafíos

###Desafío 1
Dado la siguiente lista de sentencias:

```javascript
function sumarTodo() {
  var total = 0;
  for (var i = 0; i < arguments.length; i++) {
    total += arguments[i];
  }
  return total;
}

sumarTodo(4,5,6);
// <- 15

sumarTodo(10);
// <- 10

sumarTodo();
// <- 0
```

Reescribir la función sumarTodo utilizando ES6 y Rest Parameters.

**Solución**
```javascript
function sumarTodo(...sumandos){
  return sumandos.reduce( function( valorAnterior = 0, valorActual ){
    return valorAnterior + valorActual;
  }, 0);
}
```
