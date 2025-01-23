#programacion #cs #algoritmos #DSA

> **Tabla de contenidos:**
- [[#Title 1]]
- [[#Title 2]]
	- [[#Subtitle 1]]
	- [[#Subtitle 2]]
- [[#Title 3]]

# ==🔨ARTICLE IN CONSTRUCTION ==

---

*Cualquier concepto que este erróneo o mal explicado, hágamelo saber con una Issue/Pull Request*

DSA es un acrónimo de **"Data Structures and Algorithms"** (Estructura de datos y algoritmos) e influye un rol importante en la programación debido a que, quieras o no, siempre vas a ser uso de estructuras de datos como **Arrays, Stacks, Queues**, etc. para optimizar la forma en la cual almacenas los datos, y los algoritmos son esenciales para realizar acciones de **búsqueda, agrupación, iterar listas** hasta conceptos mas complejos como buscar el camino mas corto.

**Todos estos conceptos se pueden fortalecer en plataformas como [LeetCode](https://leetcode.com)**
Empecemos sin dar tanta vueltas.

## Associative array (Maps/Dictionaries)

El concepto de **Mapa** se utiliza por Java y C++ mientras que **Diccionario** es usado por .Net y Python, así que tratare de englobar esto lo mas que pueda.

Un **Associative Array (Arreglo Asociativo)** almacena los datos en una colección utilizando una *key* y el *value* el cual será el dato. A diferencia de una Hash Table, este si se puede iterar y no suele tener una *key* única que lo defina bien.

Utilizare a JavaScript para realizar este ejemplo.

```javascript
// Associative arrays in JS are Objects
const myAssociativeArray = {day: "monday", temperature: 23, isRaining: false} 
console.log(myAssociativeArray.day) // monday
console.log(myAssociativeArray["isRaining"]) // false

// Good use for hashTables:
const HTTPHashTable = {
	GET: () => "SELECT * FROM table",
	POST: () => "INSERT INTO user(name,age) VALUES('Juan',20) ",
	DELETE: () => "DELETE FROM user WHERE id = 1"
	//... etc
}
const query = HTTPHashTable['GET'] // SELECT * FROM table
await sql(query())
```

## Linked Lists

Una **Linked List (Lista Enlazada)** es una *Linear Data Structure (Estructura de datos lineal)* de nodos, cada uno referenciando al siguiente y al anterior. Esto tiene variaciones, pero prefiero ir a la base y no indagar en sus diferentes tipos.

La diferencia que tiene de un *Arreglo* es que cada nodo almacena la referencia de memoria de sus nodos adyacentes. El primer nodo se llama *head* y el ultimo nodo se llama *tail*  y suele apuntar a un valor *nulo* para indicar que no hay mas valores a continuación.

Me gusta demasiado asociar esta estructura con POO (aunque no estén relacionados de ninguna manera). Imagínate una instancia con 3 atributos, uno es el *value* y vamos a suponer que contiene el numero 5 y las otras dos son instancias de la misma clase con el nombre *previousNode* y *nextNode*.

**Si hacemos un *previousNode.value* nos daría 4 y *nextNode.value* nos daría 6.**

Ejemplo en C# de su utilización:

```c#
using System; // this is for the String type & the Console.WriteLine
using System.Collections.Generic; // this is for the LinkedList class

public class Program
{
	public static void Main()
	{
		LinkedList<String> linked = new LinkedList<String>();
		linked.AddLast("head node");
		linked.AddLast("second node");
		linked.AddLast("third node");
		
		Console.WriteLine(linked.First.Next.Value); //second node
	}
}
```

*Lo ideal seria realizar una función recursiva y detenerse al momento que encuentre un **null**, no conozco demasiado C# para hacer un ejemplo mas pequeño que este pero recomiendo que chequen este desafío en [LeetCode](https://leetcode.com/problems/linked-list-cycle/).*

---

# Bibliografía

Me he guiado de los siguientes artículos para desarrollar este tema: 

- [Google Tech Dev Guide.](https://techdevguide.withgoogle.com/paths/data-structures-and-algorithms)
- [Geeks For Geeks.](https://www.geeksforgeeks.org/data-structures/)
