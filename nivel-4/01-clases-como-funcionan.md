# Funcionan distinto las clases en ES6?
## Introducción: Clases en JavaScript
La utilizacion de clases y del paradigma orientado a objetos en programación es una forma de proveer mayor reutilización a través de agrupar funcionalidad por su cohesión semántica.
Aunque las clases están presentes en diversos lenguajes, en JavaScript no lo estuvieron hasta la especificación de ES6. Sin embargo, es necesario aclarar que en este estándar, las clases no existen realmente, son sólo una representación más clara, ordenada, y simple de utilizar de la misma funcionalidad provista hasta ES5.

## Clases en ES5
En JavaScript no existe el concepto de Clase, no al menos como tipo de dato. La forma de simular su implementación, y obtener las ventajas de la programación orientada a objetos, es a través de funciones, y de la herencia a través de la propiedad `prototype` estas poseen. Así, para escribir una "Clase" se puede proceder de la siguiente manera:

```javascript
function Person(name, age) {
    this.name = name;
    this.age = age;
}

Person.prototype.sayName = function() {
    console.log(this.name);
}

Person.prototype.sayAge = function() {
    console.log(this.age);
}

var person = new Person('Lionel', 29);
person.sayName(); //Lionel
```
Cuando una función es invocada en conjunto con la sentencia `new`, el contexto queda ligado a la instancia en particular a través de la cual se la invoca, por lo que `this` será una referencia al objeto en uso, permitiendo escribir métodos de forma similar a como se hace en Clases.
La propiedad `prototype` permite añadir a una función propiedades y métodos que luego permitirán simular herencia.

## Clases en ES6
En ES6, al igual que en ES5, no existe el tipo de dato Clase, a pesar de que sí permite su definición. Esto significa que aunque  permite la declaración y el uso de Clases, por detrás es simplemente un decorado sobre la clásica implementación de funciones y `prototypes`. Sin embargo, añade mayor legibilidad, y da acceso a la cláusula `super` que permite extender funcionalidad utilizando herencia más cómodamente.
Así, en ES6, el mismo ejemplo anterior podría escribirse así:

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    sayName() {
        console.log(this.name);
    }

    sayAge() {
        console.log(this.age);
    }
}

const myInstance = new Person('Lionel', 29);
person.sayName(); //Lionel
```
Puede comprobarse que la implementación por detrás sigue constituyendo funciones y prototypes, de la siguiente manera

```javascript
typeof Person; // "function"
```

A través de la cláusula `extends` es posible heredar funcionalidad de una clase padre, y definir así subclases.

```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    sayName() {
        console.log(this.name);
    }
}

class Child extends Person {
    constructor(name, age) {
        //Se reutiliza el constructor de la clase padre
        super(name, age);
    }

    // A través de la cláusula super, se accede al método del padre, y es posible extender su funcionalidad
    sayName() {
        super.sayName();
        console.log(`I am a child`);
    }
}
const myChild = new Child('Lionel', 29);
myChild.sayName();
// Lionel
// I am a child

```
