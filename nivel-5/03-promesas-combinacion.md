# Combinación de Promesas
Como fue explicado en el capítulo anterior, el patrón de Promesas devuelve parte
de las ventajas del código síncrono al asíncrono, en particular, la composición
funcional y la propagación de excepciones.
## Serialización
```javascript
const promiseForResult = getUser('user');
promiseForResult
  .then(getFriendsForUser)
  .then(renderUsers);
```
## Paralelización
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
```javascript
Promise.all([
  getFriendsForUser('user'),
  getLikedpagesByUser('user')
]).then(function(results) {
  //both results are ready
});
```
```javascript
Promise.race([
  getFriendsForUser('user'),
  getLikedpagesByUser('user')
]).then(function(results) {
  //at least one result is ready
});
```
## Error Bubbling
```javascript
getUser('user')
  .then(getFriendsForUser)
  .then(ui.showFriends, ui.showError)
```
