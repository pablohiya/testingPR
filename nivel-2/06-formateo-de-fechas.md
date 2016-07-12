# Formateo de fechas

## Introducción
ECMAScript cuenta con un [API de Internacionalización](http://norbertlindenberg.com/2012/12/ecmascript-internationalization-api/index.html), el cual
incluye el objeto
```javascript
Intl.DateTimeFormat
``
que permite el formateo de fechas.

### ES5 & ES6

#### Sintaxis
```javascript
new Intl.DateTimeFormat([locales[, options]])
```
Donde "locales" es un parámetro opcional, el cual es un array de strings que contiene el
sistema númerico o calendario a usar.

El parámetro "options" es tambien opcional, y es un objeto con las siguientes propiedades:
localeMatcher, timeZone, hour12, formatMatcher, weekday, era, year, month, day, hour,
minute, second, timeZoneName.

El valor por defecto para cada componente de fecha y hora es undefined, pero si todos las propiedades son undefined, entonces, año, mes y día se asume que son numéricas.

A continuación hay un ejemplo de formateo de fecha al inglés de Estados Unidos.

```javascript
let date = new Date("2015-01-02");

// El inglés de Estados Unidos usa el orden mes-dia-año
console.log(new Intl.DateTimeFormat('en-US').format(date));
// → "1/2/2015"
```

## Desafío

1. Formatear una fecha al idioma alemán.

```javascript
var date = new Date("2015-01-02");

// El alemán usa el orden dia.mes.año
console.log(new Intl.DateTimeFormat('de-DE').format(date));
// → "2.1.2015"
```
