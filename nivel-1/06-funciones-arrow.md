# Funciones Arrow   

## Introducción   

Como su nombre lo indica, son funciones definidas usando una flecha **=>**, pero estas se comportan de una manera diferente a las funciones tradicionales en varios aspectos.   

### Sintaxis   

La sintaxis de las funciones flecha tiene diferentes formas, dependiendo de la tarea que se quiera realizar. Todas las variaciones comienzan con los argumentos de la función, seguidos por la flecha, seguidos por el contenido de la función. Tanto los argumentos como el contenido pueden tener diferentes formas dependiendo de su uso. En el siguiente ejemplo, la funcion flecha toma un único argumento y simplemente lo devuelve.

```javascript
var reflect = value => value;

// Que sería lo mismo que hacer esto:
var reflect = function (value) {
  return value;
};
```   

```html
   <font color="green">Cuando las funciones flecha reciben un solo argumento, ese único argumentopuede ser utilizado directamente sin necesidad de agregar los paréntesis. La flecha viene después y la expresión final se evalúa y es retornada. No es necesario declarar el return de manera explícita, la función flecha retorna el primer argumento que encuentre </font>
```  

