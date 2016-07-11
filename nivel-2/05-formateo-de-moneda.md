# Formateo de moneda

## Introducción
ECMAScript cuenta con un [API de Internacionalización](http://norbertlindenberg.com/2012/12/ecmascript-internationalization-api/index.html), el cual
incluye el objeto
```javascript
Intl.NumberFormat
``
que permite el formateo de moneda.

### ES5 & ES6

#### Sintaxis
```javascript
new Intl.NumberFormat([locales][, options])
```
Para formatear moneda usaremos el argumento "options", donde agregaremos en el objeto
las propiedades {style: 'currency', currency: 'aquí especificaremos el tipo de moneda'}

En el siguiente ejemplo vamos a formatear un número al formato de moneda actual de Alemania: el euro.

```javascript
let number = 123456.789;

console.log(new Intl.NumberFormat('de-DE', { style: 'currency', currency: 'EUR' }).format(number));
// → 123.456,79 €
```

## Desafío

1. Formatear un número a la moneda yen de Japón.

```javascript
let number = 123456.789;

console.log(new Intl.NumberFormat('ja-JP', { style: 'currency', currency: 'JPY' }).format(number));
// → ￥123,457
```
