# Repetición en strings

## Introducción

ES6 cuenta con un nuevo método para repetir strings: el método repeat().

### ES5

```javascript
String.prototype.repeat = function (num) {
  return new Array(num + 1).join(this)
}
console.log('foo'.repeat(4)); // foofoofoofoo
```

### ES6
ES6 ya cuenta con el método repeat() por defecto
```javascript
console.log('foo'.repeat(4)); // foofoofoofoo
```

## Desafios

1. Repite el string "bar" tres veces usando el método repeat() de ES6,
asegúrate de dejar espacio entre palabra y palabra.

```javascript
console.log('bar '.repeat(3)); // bar bar bar
```
