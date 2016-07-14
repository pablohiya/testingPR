# Promesas en ES6
El patrón de Promesas surge para simplificar el manejo de operaciones asincrónicas. Este patrón
no es nuevo, y aunque en el estándar ES5 no estaba presente, ya estaba disponible a través de
implementaciones como [Q](https://github.com/kriskowal/q), [rsvp.js](https://github.com/tildeio/rsvp.js) e
incluso jQuery, aunque este último no respeta la especificación de [Promises/A](http://wiki.commonjs.org/wiki/Promises/A).

## Introducción: Concepto de promesa
El concepto principal que propone este patrón es que toda operación asincrónica debe retornar una
Promesa. Una promesa representa el resultado eventual de dicha operación, y puede estar en uno de tres estados:
en espera, resuelta, o rechazada. En adición, contiene un método `when` que permite el pasaje de funciones para
manejar tanto cuando sea resuelta, como cuando sea rechazada.  
Como resultado de la aplicación de este patrón, se logra simplificar el código asínscrono acercándolo a su contraparte
síncrona, dotándolo principalmente de [composición funcional y propagación de errores](https://blog.domenic.me/youre-missing-the-point-of-promises/).

## Ejemplos
En el siguiente ejemplo, la operación asincrónica `getUser` retorna una Promesa, que un inicio está en espera, y que
más tarde puede ser resuelta o rechazada. A través de los métodos `then` y `catch` es posible actuar en consecuencia
de ambos casos, mediante el pasaje de callbacks.

```javascript
const promiseForResult = getUser('user');
promiseForResult.then(updateUI);
promiseForResult.catch(showErrorMessage);
```
## Desafíos

1- Crear una función `getData` que simule una operación asincrónica, y que retorne una promesa. Invocarla y mostrar su respuesta por consola.

#### Solución
```javascript
function getData() {
  const randomTime = (Math.floor(Math.random() * 5) + 1) * 100;
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
      resolve(randomTime);
    }, randomTime);
  });
}

getData().then(function(data) {
  console.log(data);
});
```

2- Crear una función `getDataWithError` que simule una operación asincrónica que falle. Invocarla, capturar el error y mostrarlo por consola.


#### Solución
```javascript
function getDataWithError() {
  const randomTime = (Math.floor(Math.random() * 5) + 1) * 100;
  return new Promise(function(resolve, reject) {
    setTimeout(function() {
      reject(randomTime);
    }, randomTime);
  });
}

getDataWithError().catch(function(data) {
  console.log(data);
});
```
