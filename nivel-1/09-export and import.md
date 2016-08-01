# Importacion y exportacion de modulos

## Introducción

Otros lenguajes usan conceptos como **paquetes** (package) para definir diferentes *alcances* (**scope**) de su codigo. En JS se llaman **modulos**.

Antes de ES6, todos las funciones JS compartian un unico **scope global**, lo cual obligaba a buscar alternativas para evitar conflictos. Esas soluciones, eran implementadas por librerias de terceros como CommonJs o AMD. 

### Modulos
Por modulo entendemos una pieza de codigo que es ejecutada una vez cargada:
* En ese codigo, puede haber todo tipo de declaraciones (variables, funciones, definiciones de clases, etc.)
* Por defecto, esas declaraciones permanecen locales al modulo.
* Se pueden marcar algunas para exportar, y otras no, por lo cual no podran ser importadas desde otro modulo.

Con las llegada de ES6, JS adopta muchas de las buenas practicas desarrolladas por esas librerias y las hace parte de JS de forma nativa. Algunas de esas buenas practicas son:

* Las variables de un modulo no forman parte del Scope Global. Solo tienen alcance dentro del modulo.
* El valor de `this` en el primer nivel del scope de un modulo es `undefined`.
* Soporte para carga sincronica y asincronica.
* Soporte apra dependencias ciclicas entre modulos.
* Los modulos son singletons. Incluso si un modulo es importado varias veces, una y solo una instacia existe en ejecucion.

Si se quisiera determinar dinamicamente que modulos cargar, existe una API, llamada **programmatic loader API**.

Una de sus limitaciones es que import y export deben ser usados fuera de funciones y definiciones.

```javascript
function tryImport() {
    export function flag (){};    // syntax error
}
```

## export

### Descripcion

Un modulo puede exportar muchas cosas, antecediendo a su declaracion la palabra `export`. Estos *exports* seran llamados **named exports**.

Dentro de un modulo vamos a encontrar 2 tipos de nombres:
* **Local name**: es el nombre bajo el cual lo "exportado" se encuantra en el modulo. 
    ```javascript
    export function myFunc() {} // myFunc es el local name
    ```
    
    Puede existir un default que no posea nombre
    ```javascript
    export default function () {}
    export default class {}
    ```
    El valor default para un modulo es una variable, funcion o clase especificada con la palabra clave `default`. Y solo puede definirse **un solo `default` por modulo**. En realidad es un export name definido como default.

* **Export name**: es el nombre que se usa para importar y acceder a ese codigo.
     ```javascript
    import myFunc from "myFile.js"; // myFunc es el export name
    ```

### Sintaxis

```javascript
// exportando datos
export var color = "red";
export let name = "Nicholas";
export const magicNumber = 7;

// export de una funcion
export function sum(num1, num2) {
    return num1 + num1;
}

// export de una clase
export class Rectangle {
    constructor(length, width) {
        this.length = length;
        this.width = width;
    }
}

// esta funcion quedaria como "privada" apra el modulo
function subtract(num1, num2) {
    return num1 - num2;
}

// defino una funcion...
function multiply(num1, num2) {
    return num1 * num2;
}

// ...y luego la exporto.
export { multiply };



// Tambien puede listarse todo lo que se quiera exportar al final del modulo
export { MY_CONST, myFunc };


// Definimos una funcion como default para la exportacion del modulo. Como sera default, podemos obviar su nombre y definir una funcion anonima.
export default function () {} 
```


## import

### Descripcion

Cuando se importa un modulo, es como si se definiera una variable como `const`. Esto significa que no puede definirse otra variable con el mismo nombre o cambiar su valor. Esto se debe a que `import` crea definiciones de solo-lectura (read-only) para variables, funciones y clases. Pero asi como **el modulo que importa otro modulo no puede cambiar sus valores, el modulo importado si puede cambiar sus propias variables.**

```javascript
//------ lib.js ------
export let counter = 3;
export function incCounter() {
    counter++;
}

//------ main.js ------
import { counter, incCounter } from './lib';

// The imported value `counter` is live
console.log(counter); // 3
incCounter();
console.log(counter); // 4
```

Los `import` son **hoisted** (internamente son movidos al principio del actual `scope`). Por lo tanto no importa donde se declaren en el modulo, **mientras no esten dentro de ninguna definicion o funcion**.

```javascript
function tryImport() {
    import flag from "./example.js";    // syntax error
}
```

### Sintaxis

```javascript
// import simple:
import name from "module-name";
console.log(name);

// import por nameSpace: importa el modulo como un objeto (con una propiedad por cada elemento exportado dentro del modulo).
import * as alias3 from 'module-name';
console.log(alias3.sum(1, 2));

// import de propiedades especificas:
import { member } from "module-name";
console.log(member(1, 2));

import { member as alias } from "module-name";
console.log(alias(1, 2));

import { member1 , member2 } from "module-name";
console.log(member2(1, 2));

import { member1 , member2 as alias2 , [...] } from "module-name";
console.log(alias2(1, 2));


// Se puede renombrar los imports:
// Renombrando: import `name1` como `localName1`
import { name1 as localName1, name2 } from 'src/my_lib';
console.log(localName1.sum(1, 2));
  
// Renombrando: import el default export como `foo`
import { default as foo }  from 'module-name';
console.log(foo.sum(1, 2));

// El default siempre va primero:
import default, * as alias3 from 'module-name';
console.log(default.sum(1, 2));

import default, { member } from "module-name";
console.log(default.sum(1, 2));
```

Donde:

**name**:  Nombre del objeto que recibirá los valores importados.

**member, memberN**:  Nombre de los miembros exportados para ser importados.

**alias, aliasN**: Nombre del objeto que recibirá la propiedad importada.

**module-name**: El nombre del módulo para ser importado. Este es un nombre de archivo.