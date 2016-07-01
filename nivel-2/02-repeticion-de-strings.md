# Repetición en strings

## Introducción

ES6 cuenta con un nuevo método para repetir strings: repeat()

<< Desarrollo >>

### ES5

```javascript
String.prototype.repeat = function (num) {
  return new Array(num + 1).join(this)
}
console.log('hola'.repeat(4)); // holaholaholahola
```

### ES6
ES6 ya cuenta con el método repeat por defecto
```javascript
console.log('hola'.repeat(4)); // holaholaholahola
```

## Desafios

1. Repite el string "doo" tres veces usando el método repeat() de ES6,
asegúrate de dejar espacio entre palabra y palabra.

```javascript
console.log('doo '.repeat(3)); // doo doo doo
```
