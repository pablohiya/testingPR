# Módulos
Con el objetivo de favorecer la mantenibilidad de una aplicación, durante el desarrollo se intenta construrila de la forma más modular posible. Esto se logra a partir de la composición de un conjunto de piezas de funcionalidad desacopladas, almacenadas en distintos módulos. De esta manera, una aplicación puede ser desarrollada a partir de un conjunto de módulos, interconectados entre sí a través de sus dependencias.

## Módulos en ES5
En ES5 no existe una implementación que soporte la importación y exportación de módulos nativamente, por lo que los desarrolladores debían optar por la utilización de distintos patrones implementados por terceros, estando [AMD](http://requirejs.org/docs/whyamd.html) y [CommonJS](http://wiki.commonjs.org/wiki/Modules/1.1) entre los más usados.

## Módulos en ES6
El estándar ES6 define una interfaz por la cual es posible implementar módulos nativamente en JavaScript. El concepto central es similar al de otras implementaciones, permitiendo importar y exportar funcionalidad a través de las nuevas palabras reservadas `import` y `export`.

A través de la cláusula `import` es posible tomar lo exportado por otro módulo, y hacerlo disponible como una variable local, con la posiblidad de renombrar si es necesario para evitar conflictos.

La declaración `export` expone porciones de código para hacerlas accesibles desde otros módulos, con posibilidad de leerlas pero no de modificarlas.
