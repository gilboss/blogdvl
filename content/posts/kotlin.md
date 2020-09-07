# Kotlin

## Introducción
Kotlin es un lenguaje de programación de tipado estático creado para correr sobre la JVM, por lo que el código debe ser compilado a *Java bytecode* antes de ser ejecutado. Cuenta con otras características como ser transpido a código javascript o compidado a código nativo de otras plataformas como iOS o Windows.


---

## Instalación
### Instalación mediante sdk en Mac OS
```shell
sdk install kotlin 1.4
```

---

## Hello world

Para la ejecución de kotlin desde REPL (Read, Evaluated, Print, Loop), ingresar desde la consola el comando `kotlin`, escribir el código y presionar enter.
```shell
println("Hello world")
```

Mediante un script `hello_world.kts`
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
### Diferencia entre archivos .kts y .kt
Los archivos `.kts` se refieren a que el contenido del archivo es un script.
Los archivos `.kt` no son scripts y se usan para definir clases.

Para ejecutar un script solo se requiere el commando `kotlin` más el nombre del archivo `kts`
```shell
kotlin hello_world.kts
```
Para ejecutar un archivo `kt` primero debe ser compilado, para el arcvhivo `hello_world.kt`
```kotlin
fun main() {
    println("Hello world")
}
```
Mediante el compilador de kotlin `kotlinc` se compila el archivo
```shell
kotlinc hello_world.kt
```
El cual genera un archivo con el mismo nombre más la terminación *Kt* `Hello_worldKt.class` que es el que se ejecuta.
```shell
kotlin Hello_worldKt
```
Ya que el compilador de kotlin genera *bytecode* también puede ser ejecutado por Java.
```shell
java Hello_worldKt
```

---

## Variables
### Declaración y tipos de variables

Pueden ser principalmente de dos tipos `var` mutables o `val` inmutables.

```kotlin
var nameVar: Int = 0 //variable mutable
val otherVar: Int = 0 //variable inmutable
```
### Variables nulables
Las variables no son nulables a menos que se les especifique
```kotlin
var nameVar: String = "" //no nulo
val otherVar: String? = null //se especifica que es nulable
```

### Constantes
Definición de una constante
```kotlin
const val CONSTANT_NAME: String = "Value"
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
Son variables que su valor son una función
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
Es una función anónima que se envía como parámetro a otra función.
Ejemplo: Si se define una función que recibe como parámetro otra función
```kotlin
fun greet(greeting: () -> Unit) {
    greeting()
}
```
Se invoca de la siguiente forma
```kotlin
greet({ println("Hello!") })
````
También se pueden excluir los parámetros
```kotlin
greet{ 
  println("Hello!") 
}
```

## Funciones Inline
Se define mediante la palabra `inline`
```kotlin
inline fun functionName : () -> Int = {
  0
}
```
Su característica es que al ser compilado el contenido de esta función es pegado en dónde haya sido invocada.

