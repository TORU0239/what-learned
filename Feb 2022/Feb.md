# Feb 2022
### 6 Feb
1. Just restarted Flutter and Dart, with a simple codelab
2. When factory pattern is needed, then we can use `factory` keyword at the head of class constructor.
3. Like using `extends` keyword to subclass a class in Java, Dart also uses same keyword, but `implements` is used to extend abstract class.

```
enum CarType {
    sedan,
    bus,
    truck
}
abstract class Car {
  factory Car(CarType type) {
     switch (type) {
       case CarType.sedan: return Sedan();
       case CarType.bus: return Bus();
       case CarType.truck: return Truck();
     }
  }
  
  String carName();
}

class Sedan implements Car {
  @override
  String carName() => "BMW 320i"
}

class Bus implements Car {
  @override
  String carName() => "Volvo B9TL"
}

class Truck implements Car {
  @override
  String carName() => "Benz Actros"
}
```
