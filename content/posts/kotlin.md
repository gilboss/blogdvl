# Kotlin

## Introducción
Kotlin es un lenguaje de programación creado para correr sobre la JVM, por lo que el código debe ser compilado a *Java bytecode* antes de ser ejecutado. Cuenta con otras características como ser transpido a código javascript o compidado a código nativo de otras plataformas como iOS o Windows.


---

## Instalación
### Instalación mediante sdk en Mac OS
```shell
sdk install kotlin
```

---

## Hello world

Para la ejecución de kotlin desde REPL (Read, Evaluated, Print, Loop), ingresar desde la consola el comando `kotlin`, escribir el código y presionar enter.
```shell
println("Hello world")
```

Mediante un script `hello_workd.kts`
```kotlin
fun greet() {
    println("Hello world")
}
greet()
```
Ejecución del script.
```shell
kotlin hello_world.kts
```

---

## Variables
Declaración y tipos de variables

```kotlin
var nameVar: Int = 0 //variable
val otherVar: Int = 0 //de sólo lectura
```
Las variables no son nulables a menos que se les especifique
```kotlin
var nameVar: String = "" //no nulo
val otherVar: String? = null //se especifica que es nulable
```

---

## Funciones
