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
### 8 Feb
1. Fastlane doesn't seem to work to deploy directly to internal track.
   * I should wait for the alpha track to be reviewed at least 2 days, (found while testing promoting to alpha from internal) 
   * Have to provide the graphics e.g full size icon and more than 2 screenshots per device type, for Alpha

### 10 Feb
1. The latest version of Firebase crashlytics might require JAVA 11

### 17 Feb
1. interface singleton in Kotlin
```
interface Server {
    fun execute(request: Request): Response
    companion object : Server {
        private val client = OkHttpClient()
        
        override fun execute(request: Request): Response =
            client.newCall(request).execute()
    }
}
```
* By creating a companion object for an interface, it's possible to refer to both the interface and its singleton implementation at the same time.

### 23 Feb
1. api vs implementation in Gradle
    * The main difference is how the dependencies can expose themselves when a dependency references another dependency in the diagram structure.
    * Given A <- B <- C, when A is declared as `api`, then C can access to A. Moreover if A has been modified, then B and C will be built again.
    * But when A is `implementation`, C will have no access to A, and only B will be built again. 
2. `runtimeOnly` vs `compileTimeOnly`
    * `runtimeOnly` can tell that this dependency will be needed in runtime e.g. log
    * `compileTimeOnly` can inform us that this dependency will be only used in compile time, not in runtime
