# Clases

## Introducción

En ES6 se ha añadido el uso de clases, como una manera de reusar código.

### ES6

```javascript
class Dog {
  constructor() {
    this.sound = 'woof';
  }
  talk() {
    console.log(this.sound);
  }
}
const firulais = new Dog();
firulais.talk() // "woof"
```

Aquí se ha creado la clase Dog. En su constructor, él asigna una propiedad a sí mismo llamada "sound". La clase tambien tiene un método "talk" el cual usa a "sound".

Luego se ha creado un perro, firulais, el cual al llamar el método talk(), imprime correctamente la palabra "woof".

## Desafios

1. Crear una clase llamada Animal, donde en su constructor se asigne una propiedad
llamada "mammal" con valor true. Luego crea dos métodos llamados bark() y meow(), los cuales imprimirán en consola "woof" y "meau" respectivamente, luego crear dos instancias de la clase Animal, una llamada "dog" que invocará el método bark() y otra llamada "cat" que invocará el método meow().

```javascript
class Animal {
  constructor() {
    this.mammal = true;
  }
  bark() {
    console.log('woof');
  }
  meow() {
    console.log('meau');
  }
}
const dog = new Animal();
dog.bark() // "woof"
const cat = new Animal();
cat.meow() // "meau"
```