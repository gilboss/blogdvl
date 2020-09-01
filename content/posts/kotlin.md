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
### Declaración y tipos de variables

```kotlin
var nameVar: Int = 0 //variable
val otherVar: Int = 0 //de sólo lectura
```
### Variables nulables
Las variables no son nulables a menos que se les especifique
```kotlin
var nameVar: String = "" //no nulo
val otherVar: String? = null //se especifica que es nulable
```

---

## Funciones
### Estructura general de las funciones

```kotlin
private fun nameOfFunction(param1: Int, param2: String = ""): Boolean{
    println("First param: ${param1}")
    println("Second param: ${param2}")
    return true
}
```
`private` Modificador de visivilidad, si es público puede ser omitido.

`fun` Palabra reservada para indicar que es una función.

`nameOfFunction` Nombre de la función.

`param1, param2` Nombre de los parámetros.

`param2: String = ""` Parámetro con valor por default.

`: Int, : String` Tipo de dato del parámetro.

`: Boolean` Tipo de dato retornado por la función. 

`return true` Valor devuelto por la función.

***Los parámetros de las funciones son de sólo lectura (val)***

### Funciones en una sóla expresión
```kotlin
fun increase(x: Int) = x + 1
```
### Funciones con nombre de función como String
Se asigna el nombre de la función entre ``
```kotlin
fun `function as string`(): String {
    return ""
}
```
### Invocar funciones definiendo el nombre de los parámetros enviados
```kotlin
nameOfFunction(param2 = "x", param1 = 1)
```

### Function type
Son variables que su valos son una función
```kotlin
val functionName: (String, Int) -> String = {param1, param2 -> 
    "param1 String ${param1} param2 Int ${param2}"
}

functionName("one", 2)
```

### Funciones anónimas
Son bloques de código delimitado por corchetes y como su nombre lo indica no tienen nombre

Estructura de las funciones anónimas
```kotlin
{ 
    val a: Int = 0
    val b: Int = 1
    a + b
}()
```
Normalmente enviados como parámetro a otras funciones o también retornadas por otras funciones.
```kotlin
println(
 { 
    val a: Int = 1
    val b: Int = 2
    a + b
}()   
)
```

### Lambda
Es una función anónima