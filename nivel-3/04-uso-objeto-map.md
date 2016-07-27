# Uso del nuevo objeto Map

## Introducción

Hacía falta contar con una estructura de datos capaz de mapear valores arbitrarios a otros valores. Lo mejor que se podía lograr con ES5 era un mapeo de strings a valores arbitrarios, por medio del uso de objetos. ES6 estandariza la requerida funcionalidad por medio del siguiente objeto:

- new Map([iterable])

El nuevo objeto Map introducido con ES6 permite utilizar valores arbitrarios como clave (incluso objetos) y es por eso gratamente bienvenido. Otras de las ventajas en comparación con el uso de objetos, es que tanto iterar como obtener el tamaño de un Map es directo, y además no hereda propiedades adicionales.

Utilizar objetos convencionales sigue siendo la opción más recomendable hoy en día. Sin embargo, cuando requeris datos de tipo clave-valor donde no sabes de antemano los tipos de clave, es recomendable almacenarlo en un ES6 Map.

## Map

El objeto Map([iterable]) es un simple mapeo clave/valor. Se crea por medio del operador 'new' y el parametro opcional 'iterable' (arreglo u objeto iterable), y cuenta con una serie de métodos para su manipulación, como set() y get(), al igual que los anteriormente mencionados keys(), values y entries() para arreglos.

### ES5
```javascript
var obj = {};
obj[0] = 'chris';
obj[1] = 'derek';
obj[2] = 'tony';

console.log(obj); // Object {0: "chris", 1: "derek", 2: "tony"}
console.log(Object.keys(obj).length); //3
for (var key in obj) { //iteración sobre un objeto
   if (obj.hasOwnProperty(key)) {
      console.log(key + ':' + obj[key]);
   }
}
```

### ES6
```javascript
let map = new Map();
map.set(0, 'chris');
map.set(1, 'derek');
map.set(2, 'tony');

console.log(map); // Map {0 => "chris", 1 => "derek", 2 => "tony"}
console.log(map.size); //3
for (const [key, value] of map) { //iteración sobre un Map
  console.log(key + ':' + value);
}
```

## Desafíos
Dada el siguiente string json.

```javascript
const jsonStr = '[ [0, {"people": 3}], ["males", ["chris", "tony"]], [{"females": true}, {"name": "serena"}]]';
```

#### 1- Almacenarlo en un objeto Map.

### Solución
```javascript
let myMap = new Map(JSON.parse(jsonStr));
console.log(myMap); // Map {0 => Object {people: 3}, "males" => ["chris", "tony"], Object {females: true} => Object {name: "serena"}}
```

#### 2- Convertir en strings las keys del Map que no son de ese tipo.

### Solución
```javascript
let auxMap = new Map();
for (const [key, value] of myMap) {
	if (typeof key === 'string') {
		auxMap.set(key, value);
	} else if (typeof key === 'object') {
		auxMap.set(JSON.stringify(key), value);
	} else {
		auxMap.set(String(key), value);	
	}
}
myMap = auxMap;
console.log(myMap); // Map {"0" => Object {people: 3}, "males" => ["chris", "tony"], "{"females":true}" => Object {name: "serena"}}
```