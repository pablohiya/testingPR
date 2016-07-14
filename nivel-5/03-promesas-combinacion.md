# Combinación de Promesas
Como fue explicado en el capítulo anterior, el patrón de Promesas devuelve parte
de las ventajas del código síncrono al asíncrono, en particular, la composición
funcional y la propagación de excepciones.
## Serialización
Parte de la especificación del patrón de Promesas exige que el método `then` retorne
una nueva Promesa. De esta forma, se pueden encadenar una serie de operaciones asíncronas
de forma serializada.

```javascript
const promiseForResult = getUser('user');
promiseForResult
  .then(getFriendsForUser)
  .then(renderUsers);
```
## Paralelización
Haciendo uso de la primera referencia a la promesa inicial, se pueden combinar paralelamente otras operaciones que dependan de su valor de retorno. Esto deja en evidencia que `then` no modifica a la promesa sobre la cual se invoca, sino que retorna una nueva.

```javascript
const promiseForResult = getUser('user');
promiseForResult
  .then(getFriendsForUser)
  .then(renderUsers);
promiseForResult
  .then(getLikedpages)
  .then(renderLikedPagesBox);
```
## Otras combinaciones
A través de la API de Promise que ofrecen los exploradores, es posible combinar un cojunto promesas nativamente de dos formas adicionales. Los métodos `all` y `race` reciben un arreglo de promesas, y retornan una nueva, que se resuelve en el primer caso cuando todas las pasadas en el arregla son resueltas, y en el segundo, cuando al menos una lo es.

```javascript
Promise.all([
  getFriendsForUser('user'),
  getLikedpagesByUser('user')
]).then(function(results) {
  //Ambas promesas fueron resueltas
});
```
```javascript
Promise.race([
  getFriendsForUser('user'),
  getLikedpagesByUser('user')
]).then(function(results) {
  //al menos una promesa fue resuelta
});
```
## Error Bubbling
Como se pudo ver en el capítulo uno, la forma de trabajar con operaciones asincrónicas sin utilizar promesas, vuelve complejo el manejo de errores. Con el mero uso de pasaje de callbacks, se debe realizar un control de fallas a cada paso, sin las ventajas de las sentencias `try/catch` del código sincrónico.
La implementación del método `then` y el algoritmo de resolución de promesas, asegura que ante una excepción durante la ejecución de una pieza de código asincrónico, será propagada hasta que encuentre un callback que lo trate, recuperando así el error bubbling que se perdía con el enfoque de pasaje de callbacks.
En el siguiente ejemplo, cualquier excepción durante la ejecución de las funciones `getFriendsForUser` o `getLikedpagesByUser` se propagará y será trata por el callback `ui.showError`.
```javascript
getUser('user')
  .then(getFriendsForUser)
  .then(getLikedpagesByUser)
  .then(ui.showFriends, ui.showError)
```
## Desafíos

1- Utilizando la función `getData` escrita para los desafíos del capítulo anterior, encadenar dos llamadas consecutivas, mostrando la salida de la última llamada por consola.

2-
