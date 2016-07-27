# Getters y Setters

## Introducción

En ES6 se ha añadido el uso de clases, como una manera de reusar código.

### ES6

```javascript
class Dog {
  get prop() {
    return 'getter';
  }
  set prop(value) {
    console.log('setter: '+value);
  }
}

let firulais = new Dog();
firulais.prop = 'My name is Firulais'; // setter: My name is Firulais
console.log(firulais.prop) // 'getter'
```

## Desafios

1. Crear una clase llamada MyClass, que contenga getter y setter.

```javascript
class MyClass {
  get prop() {
    return 'getter';
  }
  set prop(value) {
    console.log('setter: '+value);
  }
}

let inst = new MyClass();
inst.prop = 123; // setter: 123
console.log(inst.prop) // getter
```