# Funciones Arrow   

## Introducción   

Como su nombre lo indica, son funciones definidas usando una flecha **=>**, pero estas se comportan de una manera diferente a las funciones tradicionales en varios aspectos.   

## Sintaxis   

La sintaxis de las funciones flecha tiene diferentes formas, dependiendo de la tarea que se quiera realizar. Todas las variaciones comienzan con los argumentos de la función, seguidos por la flecha, seguidos por el contenido de la función. Tanto los argumentos como el contenido pueden tener diferentes formas dependiendo de su uso. En el siguiente ejemplo, la funcion flecha toma un único argumento y simplemente lo devuelve.

```javascript
var reflect = value => value;

// Que sería lo mismo que hacer esto:
var reflect = function (value) {
  return value;
};
```   

*Cuando las funciones flecha reciben un solo argumento, ese único argumentopuede ser utilizado directamente sin necesidad de agregar los paréntesis. La flecha viene después y la expresión final se evalúa y es retornada. No es necesario declarar el return de manera explícita, la función flecha retorna el primer argumento que encuentre.*  
   
En caso la función reciba más de un argumento, entonces sí debemos incluir los paréntesis, como en el siguiente ejemplo:

```javascript
var sum = (n1, n2) => n1 + n2;

// Que sería lo mismo que hacer esto:
var sum = function (n1, n2) {
  return n1 + n2;
};   
```

Un caso similar sería si la función no recibe ningún argumento, en ese caso van los paréntesis solos, como en el siguiente ejemplo:   
   
```javascript
var getName = () => "Luis Miguel";

// Que sería lo mismo que hacer esto:
var getName = function () {
  return "Luis Miguel";
};
```

Tambien podemos utilizar la sintaxis tradicional, como en el ejemplo a continuacion:   
   
```javascript
var sum = (n1, n2) => {
  return n1 + n2;
};

// Que sería lo mismo que hacer esto:
var sum = function (n1, n2) {
  return n1 + n2;
}
```   
   
*Podemos tratar el contenido de las llaves casi como lo hacíamos de la manera tradicional, con la excepción de que el valor arguments no estará disponible.*

En el caso de retornar un objeto, este se debe incluir entre parentesis:   
   
```javascript
var getTempItem = id => ({id: id, name: "Temp"});

// Que sería lo mismo que hacer esto:
var getTempItem = function (id) {
  return {
    id: id,
    name: "Temp"
  };
};
```   
   
*Esto se hace por que al encapsular el objeto entre paréntesis declaramos que las llaves son el objeto y no que pertenecen al cuerpo de la función.*   
   
## EXPRESIONES DE FUNCIÓN INVOCADAS INMEDIATAMENTE (IIFE)   
   
Las IIFEs por sus siglas en inglés, nos permiten crear funciones anónimas y llamarlas inmediatamente sin guardar una referencia de estas. Este patrón es muy útil cuando necesitamos crear un ámbito aislado del resto del programa. Por ejemplo:  

```javascript
let person = function (name) {
  return {
    getName: function() {
      return name;
    }
  }
}("Luis Miguel");

console.log(person.getName()); // <- Luis Miguel   
```   

*En este código, la IIFE es usada para crear un objeto con un método getName(). Este método usa el argumento name como valor de retorno, haciendo de name un valor privado dentro del objeto retornado.*   

Para lograr el mismo resultado usando funciones flecha, debemos encapsularlas entre paréntesis:   
   
```javascript
let person = ((name) => {
  return {
    getName: function() {
      return name;
    }
  }
})("Luis Miguel");

console.log(person.getName()); // <- Luis Miguel
```    
   
*Notemos que los paréntesis sólo están alrededor de la función flecha y no llegan hasta ("Luis Miguel").*

NO HAY THIS BINDING   
