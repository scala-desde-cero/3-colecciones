# 3-colecciones
1. [Introducción a las colecciones](#schema1)
2. [Colecciones Inmutables](#schema2)
3. [Colecciones Mutables](#schema3)
4. [Operaciones Comunes en Colecciones](#schema4)

<hr>

<a name="schema1"></a>

## 1. Introducción a las colecciones

Las colecciones en Scala son una parte fundamental del lenguaje y proporcionan estructuras de datos ricas y versátiles para almacenar y manipular grupos de elementos. Scala tiene una biblioteca de colecciones bien diseñada que incluye listas, conjuntos, mapas, vectores, entre otros. 

![Intro](./img/intro_1.png)
![Intro](./img/intro_2.png)
![Intro](./img/intro_3.png)
![Intro](./img/intro_4.png)


### **Tipos de Colecciones en Scala**
Las colecciones en Scala se dividen en dos categorías principales:

- Colecciones inmutables: Estas colecciones no pueden ser modificadas una vez creadas. La mayoría de las colecciones en Scala son inmutables por defecto.
- Colecciones mutables: Estas colecciones pueden ser modificadas después de su creación.

<hr>

<a name="schema2"></a>

## 2. Colecciones Inmutables


### **List (Lista)**
Las listas en Scala son inmutables y se implementan como listas enlazadas.

```scala
val fruits = List("apple", "banana", "cherry")
```
- Operaciones comunes:

```scala
val head = fruits.head          // "apple"
val tail = fruits.tail          // List("banana", "cherry")
val isEmpty = fruits.isEmpty    // false
val size = fruits.size          // 3
val newList = fruits :+ "date"  // List("apple", "banana", "cherry", "date")
```
### **Set (Conjunto)**
Los conjuntos son colecciones sin duplicados.

```scala
val fruitSet = Set("apple", "banana", "cherry")
```
- Operaciones comunes:

```scala
val containsApple = fruitSet.contains("apple")  // true
val newSet = fruitSet + "date"                  // Set("apple", "banana", "cherry", "date")
val anotherSet = fruitSet - "banana"            // Set("apple", "cherry")
```
### **Map (Mapa)**
Los mapas son colecciones de pares clave-valor.

```scala
val fruitPrices = Map("apple" -> 1.0, "banana" -> 0.5, "cherry" -> 2.0)
```
- Operaciones comunes:

```scala
val applePrice = fruitPrices("apple")            // 1.0
val containsBanana = fruitPrices.contains("banana")  // true
val updatedMap = fruitPrices + ("date" -> 1.5)   // Map("apple" -> 1.0, "banana" -> 0.5, "cherry" -> 2.0, "date" -> 1.5)
```
### **Vector (Vector)**
Los vectores son similares a las listas, pero están optimizados para el acceso rápido a elementos y operaciones de actualización.

```scala
val numbers = Vector(1, 2, 3, 4, 5)
```
<hr>

<a name="schema3"></a>

## 3. Colecciones Mutables

Scala también proporciona colecciones mutables, que pueden ser modificadas después de su creación. Estas se encuentran en el paquete scala.collection.mutable.

### **Mutable ListBuffer**
```scala
import scala.collection.mutable.ListBuffer

val buffer = ListBuffer(1, 2, 3)
buffer += 4            // ListBuffer(1, 2, 3, 4)
buffer -= 2            // ListBuffer(1, 3, 4)
```
- **Añadir Elementos:**

```scala
listBuffer += 4               // ListBuffer(1, 2, 3, 4)
listBuffer.append(5)          // ListBuffer(1, 2, 3, 4, 5)
listBuffer.prepend(0)         // ListBuffer(0, 1, 2, 3, 4, 5)
```
- **Eliminar Elementos:**

```scala
listBuffer -= 2               // ListBuffer(0, 1, 3, 4, 5)
listBuffer.remove(0)          // ListBuffer(1, 3, 4, 5)
```
- **Acceder a Elementos:**

```scala
val firstElement = listBuffer(0)  // 1
val lastElement = listBuffer.last // 5
```
- **Iterar sobre ListBuffer:**

```scala
for (element <- listBuffer) {
  println(element)
}
```

### **Mutable Set**
```scala
import scala.collection.mutable.Set

val mutableSet = Set("apple", "banana")
mutableSet += "cherry"       // Set("apple", "banana", "cherry")
mutableSet -= "banana"       // Set("apple", "cherry")
```
### **Mutable Map**
```scala
import scala.collection.mutable.Map

val mutableMap = Map("apple" -> 1.0, "banana" -> 0.5)
mutableMap("cherry") = 2.0      // Map("apple" -> 1.0, "banana" -> 0.5, "cherry" -> 2.0)
mutableMap -= "banana"          // Map("apple" -> 1.0, "cherry" -> 2.0)
```
<hr>

<a name="schema4"></a>

## 4. Operaciones Comunes en Colecciones
### **Transformaciones**
Puedes aplicar funciones a los elementos de una colección para transformarlos:

```scala
val numbers = List(1, 2, 3, 4, 5)
val doubled = numbers.map(_ * 2)  // List(2, 4, 6, 8, 10)
```
### **Filtrado**
Puedes filtrar elementos que cumplan una condición:

```scala
val evenNumbers = numbers.filter(_ % 2 == 0)  // List(2, 4)
```
### **Reducción**
Puedes combinar todos los elementos de una colección usando una operación:

```scala
val sum = numbers.reduce(_ + _)  // 15
```
### **Agrupamiento**
Puedes agrupar elementos según una clave:

```scala
val groupedByParity = numbers.groupBy(_ % 2)  // Map(1 -> List(1, 3, 5), 0 -> List(2,
```