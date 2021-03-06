# Módulos
Con el objetivo de favorecer la mantenibilidad de una aplicación, durante el desarrollo se intenta construrila de la forma más modular posible. Esto se logra a partir de la composición de un conjunto de piezas de funcionalidad desacopladas, almacenadas en distintos módulos. De esta manera, una aplicación puede ser desarrollada a partir de un conjunto de módulos, interconectados entre sí a través de sus dependencias.

## Módulos en ES5
En ES5 no existe una implementación que soporte la importación y exportación de módulos nativamente, por lo que los desarrolladores debían optar por la utilización de distintos patrones implementados por terceros, estando [AMD](http://requirejs.org/docs/whyamd.html) y [CommonJS](http://wiki.commonjs.org/wiki/Modules/1.1) entre los más usados.

## Módulos en ES6
El estándar ES6 define una interfaz por la cual es posible implementar módulos nativamente en JavaScript. El concepto central es similar al de otras implementaciones, permitiendo importar y exportar funcionalidad a través de las nuevas palabras reservadas `import` y `export`.

A través de la cláusula `import` es posible tomar lo exportado por otro módulo, y hacerlo disponible como una variable local, con la posiblidad de renombrar si es necesario para evitar conflictos.

La declaración `export` expone porciones de código para hacerlas accesibles desde otros módulos, con posibilidad de leerlas pero no de modificarlas.

### Exports

A través de la cláusula `export` es posible definir de distinas maneras qué partes del módulo serán accesibles desde otros.

#### Exportar variables o funciones con nombre

```javascript
export const pi = 3.14;
export function foo() {};   
```

#### Exportar como default

```javascript
export default 100;         
export default function foo() {};   
```

#### Exportar una variable con un nuevo nombre

```javascript
const pi = 3.14;
export { pi as shortPi };
```

#### Exportar parte de otro módulo

```javascript
export { pi as piNumber } from 'math';
```

#### Exportar otro módulo completo

```javascript
export * from 'math';   
```

### Imports

La sentencia `import` permite ligar al contexto local del módulo, variables exportadas por otro.

#### Importar sin redefinición local

```javascript
import 'jquery';  
```
#### Importar el default export

```javascript
import $ from 'jquery';
```

#### Importar una variable con nombre

```javascript
import { $ } from 'jquery';   
```

#### Importar y renombrar una variable con nombre

```javascript
import { $ as jQuery } from 'jquery';
```

#### Importar un módulo entero

```javascript
import * as Math from 'math';
```
## Desafíos

1- Utilizando el default export, crear un módulo que exporte una función `myFunc`. Importar dicha función desde un módulo distinto, e invocarla.


#### Solución
```javascript
//------ aModule.js ------
export default function () {

}

//------ anotheModule.js ------
import myFunc from 'aModule';
myFunc();
```

2- Crear un módulo con una serie de constantes. Exportar cada una a través de diferentes 'named exports'. Desde otro módulo, importar alguna de ellas.

#### Solución
```javascript
//------ constants.js ------
export const one = 1;
export const two = 2;
export const three = 3;
export const four = 4;

//------ anotheModule.js ------
import { one, two } from 'constants';
console.log(one + two);
//3
```

3- Crear un módulo que importe el anteriormente creado de constantes, agregue una serie de nuevas, y exporte el conjunto conformado por las importadas y las nuevas creadas.

#### Solución
```javascript
//------ constants.js ------
export const one = 1;
export const two = 2;
export const three = 3;
export const four = 4;

//------ constants2.js ------
export * from 'constants';
export const five = 5;
export const six = 6;

//------ anotheModule.js ------
import { one, five } from 'constants2';
console.log(one + five);
//6

```
