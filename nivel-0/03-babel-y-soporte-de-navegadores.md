# Babel y Soporte de Navegadores

Actualmente, las últimas versiones de los navegadores más utilizados, en sus versiones de escritorio, tienen muy buen soporte para las distintas características incluidas en la última versión del estándar. Al momento de escribir este artículo, Microsoft Edge, Mozilla Firefox y Google Chrome soportan más del 90% del estándar de ES6, y Apple anunció hace pocos días que el motor Webkit empleado por Safari soporta el 100% del estándar en su última versión. Existe una tabla actualizada con referencias a las características soportadas por distintas versiones de navegadores y plataformas de JavaScript [aquí](https://kangax.github.io/compat-table/es6/).

En caso de querer soportar navegadores más antiguos o móviles, pero trabajando con la sintaxis de ES6, existe un proyecto muy maduro llamado Babel, que permite procesar código escrito en la última versión del estándar y transformarlo a código escrito en la versión 5, que tiene soporte casi perfecto en todas las plataformas, tal como se puede ver [aquí] (http://kangax.github.io/compat-table/es5/).

Si se emplea NodeJS para trabajar con JavaScript en el servidor, a partir de la versión 6 más del 90% del estándar está soportado ya que está basado en V8, el motor empleado por Google Chrome. Esto puede verse en la primera tabla comparativa referida más arriba.
