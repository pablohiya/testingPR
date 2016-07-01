# Interpolación de strings

## Introducción

En ES5, si se quería concatenar diferentes strings o quizás insertar
variables en strings, se debía usar concatenaciones usando el operador
'+' o tal vez los métodos concat o join aplicados a un array.
ES6 ofrece una sintaxis de template mucho más usable.

### ES5

```javascript
function print (first, last) {
  const msg = 'Welcome ' + first + ' ' + last + '!';
  // teniendo en cuenta que en nuestro HTML tenemos un tag con id igual a msg
  // por ejemplo <h2 id="msg"></h2>
  document.getElementById('msg').innerHTML = msg;
}
```

### ES6

```javascript
function print (first, last) {
  // el string completo debe ser encerrado en (` `) caracter
  // y las variables deben ir dentro de llaves precedidas por el signo dólar "$"
  const msg = `Welcome ${first} ${last} !`;
  // teniendo en cuenta que en nuestro HTML tenemos un tag con id igual a msg
  // por ejemplo <h2 id="msg"></h2>
  document.getElementById('msg').innerHTML = msg;
}
```

## Desafios

1. Crea una función que acepte un número como parámetro y usando interpolación de strings
retorna el doble de ese número

Solución
```javascript
function double (number) {
  const prod = `${number * 2}`;
  // teniendo en cuenta que en nuestro HTML tenemos un tag con id igual a msg
  // por ejemplo <h2 id="msg"></h2>
  document.getElementById('msg').innerHTML = prod;
}
double(6); // 12
```

2. Construye una petición HTTP donde uses interpolación de strings para enviar los parámetros

Solución
```javascript
POST`http://foo.org/bar?a=${a}&b=${b}
  Content-Type: application/json
  X-Credentials: ${credentials}
  {
    "foo": ${foo},
    "bar": ${bar}
  }`(myOnReadyStateChangeHandler);
```