# Property Shorthand & Keys calculadas

## Introducción    
   
   ECMAScript 6 centra sus esfuerzos en mejorar la utilizacion de los objetos, lo cual tiene sentido ya que en Javascript todos los valores tienen un tipo de objeto. Adicionalmente, la cantidad de objetos utilizados en Javascript aumenta a medida que la complejidad de la aplicacion crece.   

ECMAScript 6 mejora la utilizacion de los objetos de diferentes maneras, desde simplificando la sintaxis como tambien la manipulacion de ellos.      

## Property Shorthand   
   
En ES5, los objetos literales eran simplemente colecciones de pares nombre-valor. Esto significa que habia una duplicacion cuando se inicializaban las propiedades. Por ejemplo:   
   
### ES5:   
   
```javascript
function createPerson(name, age) {
    return {
        name: name,
        age: age
    };
}
```

La funcion **createPerson** crea un objeto donde el nombre de las propiedades son iguales a los parametros de la funcion. El resultado es la duplicación de *name* y *age*, donde la clave *name* en el objeto retornado tiene asignado el valor contenido en la variable *name* y la clave *age* en el objeto retornado tiene asignado el valor contenido en la variable *age*.

En ECMAScript 6, se puede eliminar la duplicacion existente que existe entre la propiedad y los parametros de entrada de la funcion utilizando la forma **property shorthand**. Por ejemplo, **createPerson()** puede reescribirse en ES6 de la siguiente manera:

### ES6:   
   
```javascript
function createPerson(name, age) {
    return {
        name,
        age
    };
}
```

Cuando una propiedad en un objeto posee solo el nombre declarado, el motor de Javascript busca en el ambito variables con el mismo nombre. Si encuentra una, ese valor es asignado al mismo nombre del objeto. En este ejemplo, la propiedad *name* es asignada con al valor de la variable local *name*.

*Esta extension permite que la inicializacion de los objetos sea mas rapida y elimina los errores de naming.*

## Assign Methods

EMACScript 6 tambien mejora la sintaxis para la asignacion de metodos a objetos. En EMACScript 5, se debia especificar el nombre y despues la declaracion completa de la funcion para agregar un metodo a un objeto.

### ES5:

```javascript
var person = {
    name: "Nicholas",
    sayName: function() {
        console.log(this.name);
    }
};
```

En EMACScript 6, la sintaxis es mucho mas simple eliminando los dos puntos y la palabra clave *function*. El ejemplo anterior se puede reescribir de la siguiente manera.

### ES6:

```javascript
var person = {
    name: "Nicholas",
    sayName() {
        console.log(this.name);
    }
};
```

## Keys Calculadas

En ECMAScript 5 se podian realizar calculos de las propiedades en los objetos instanciados cuando esas propiedades se escribian con corchetes. Los corchetes permiten especificar el nombre de la propiedad donde se quiere acceder. 

###ES5:

```javascript
var person = {},
    lastName = "last name";

person["first name"] = "Nicholas";
person[lastName] = "Zakas";

console.log(person["first name"]);      // "Nicholas"
console.log(person[lastName]);          // "Zakas"
```

Adicionalmente, se pueden utilizar strings directamente en las propiedades del objeto.

### ES5

```javascript
var person = {
    "first name": "Nicholas"
};

console.log(person["first name"]);      // "Nicholas"
```

En EMACScript 6, las keys calculadas son parte de la sintaxis del objeto y se utiliza la notacion de corchetes tambien para acceder.

### ES6

```javascript
var lastName = "last name";

var person = {
    "first name": "Nicholas",
    [lastName]: "Zakas"
};

console.log(person["first name"]);      // "Nicholas"
console.log(person[lastName]);          // "Zakas"
```

Los corchetes adentro de un objeto indican que la propiedad es calculada, entonces su contenido es evaluado como string. Esto permite incluir expresiones, como se muestra a continuacion:

### ES6

```javascript
var suffix = " name";

var person = {
    ["first" + suffix]: "Nicholas",
    ["last" + suffix]: "Zakas"
};

console.log(person["first name"]);      // "Nicholas"
console.log(person["last name"]);       // "Zakas"
```

### Desafíos

**Desafío 1**

Dado el siguiente fragmento de ECMAScript 5:

```javascript
function createMonster(name, power) {
  return { type: 'Monster', name: name, power: power };
}
function createWitch(name) {
  return { type: 'Witch', name: name };
}
```

Reescribirlo aplicando **property shorthand**.

**Solución**

```javascript
function createMonster(name, power) {
  return { type: 'Monster', name, power };
}
function createWitch(name) {
  return { type: 'Witch', name };
}
```

**Desafío 2**

Crear una function **getCar** que reciba como 3 valores como parametro: make, model y value. Esta funcion debe retornar un objeto con las siguientes propiedades:
- make
- model
- value
- función llamada depreciate, que le reste a la propiedad value un numero arbitrario elegido por el usuario.

Una vez implementada la funcion:
1) Declarar una variable car y asignarle getCar pasando los correspondientes parametros como string. 
2) Imprimir la variable car
3) Llamar al metodo depreciate
4) Imprimir la variable car nuevamente

**Solución**

```javascript
function getCar(make, model, value) {
    return {
        // with property value shorthand
        // syntax, you can omit the property
        // value if key matches variable
        // name
        make,  // same as make: make
        model, // same as model: model
        value, // same as value: value
        // Method definition shorthand syntax
        // omits `function` keyword & colon
        depreciate() {
            this.value -= 2500;
        }
    };
}

let car = getCar('Kia', 'Sorento', 40000);

// output: {
//     make: 'Kia',
//     model:'Sorento',
//     value: 40000,
//     depreciate: function()
// }
console.log(car);
car.depreciate();
// output: 37500
console.log(car.value);
```