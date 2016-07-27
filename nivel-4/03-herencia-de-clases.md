# Herencia de clases

## Introducción

En ES6 se ha añadido el uso de clases, como una manera de reusar código.

Cuando se desea heredar propiedades de una clase padre a una clase hija se usa la palabra "extends".

### ES6

```javascript
class Robot {
  drive() {
    console.log("I'm moving")
  }
}

class CleaningRobot extends Robot {
  clean() {
    console.log("I'm cleaning")
  }
}

const wally = new CleaningRobot();
wally.drive(); // I'm moving
```

Aquí se ha creado la clase padre Robot, el cual tiene un método drive().

Luego se ha creado una clase CleaningRobot que hereda de la clase Robot mediante la palabra "extends", así cuando creamos una instancia de la clase CleaningRobot, tenemos acceso al método drive() definido en la clase padre.

## Desafios

1. Crear una clase llamada FlightRobot, que tenga acceso al método clean() y drive().

```javascript
class FlightRobot extends CleaningRobot {};

const wally = new FlightRobot();
wally.drive(); // I'm moving
wally.clean(); // I'm cleaning
```