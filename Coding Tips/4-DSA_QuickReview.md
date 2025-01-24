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

**Todos estos conceptos se pueden fortalecer en plataformas como [LeetCode](https://leetcode.com) y las actividades recomendadas estarán en esa plataforma.**
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
await sql`${query()}`
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

*Lo ideal seria realizar una función recursiva y detenerse al momento que encuentre un **null**, no conozco demasiado C# para hacer un ejemplo mas pequeño que este pero recomiendo que chequen este [desafío](https://leetcode.com/problems/linked-list-cycle/).*

## Trees

Un **Tree (Árbol)** es una *Non-linear Data Structure (Estructura de datos NO lineal)*, es decir, sus elementos no están alineados secuencialmente por lo tanto no pueden ser todos recorridos en una sola ejecución. Esta estructura jerarquiza sus nodos, como si fuese un sistema de carpetas.

```python
Root
├── Home
│	├── MyPC
│	└── User
│
└──	Desktop
	└── Homework
		├── Math
		└── Programming
```

> *Binary tree example*
![[TreeExample.png]]


**Un poco de terminología para estar en la misma pagina:**
- El nodo mas alto se llama *Root* (pintado de rosa).
- Los nodos sin hijos (nodos descendientes) se llaman *Leaf Node* (pintados de verde).
- Un *Subtree* (Subárbol) es un conjunto de nodos (junto a sus descendientes) a destacar dentro del mismo árbol principal. Ejemplo: Un subárbol podría ser Home, MyPC y User.

**Un ejemplo de código sencillo en Python:**

```python
class Tree:
    def __init__(self):
        self.left = None
        self.right = None
        self.name = None

root = Tree()
root.name = "Root"
root.left = Tree()
root.left.name = "Home"
root.right = Tree()
root.right.name = "Desktop"
```

Y así, definiríamos un subárbol de los primeros niveles.

*Al igual que el anterior, esto se podría recorrer con una función recursiva. Recomiendo este [ejercicio sencillo](https://leetcode.com/problems/binary-tree-paths/) para empezar a entender arboles mejor.*
#### Tipos de Arboles:
 - Un nodo de un *Tree* puede tener un numero infinito de hijos, mientras que un *Binary Tree (Árbol Binario)* tiene un máximo de 2 hijos, cuales suelen ser referidos como *Left Node* y *Right Node*.
 
 - Un *Binary Search Tree (Árbol de búsqueda binaria)* suele utilizar números como valores, en vez de nombres previamente visto en los ejemplos. Supongamos que el *Root* empieza con el valor de **10**, el hijo izquierdo de este siempre será menor al nodo padre, es decir, tendrá el valor de **9** o menos mientras que el hijo derecho siempre será mayor al nodo padre, por ejemplo, **11** o mayor. Y así recursivamente con los hijos.

Hay mas tipos de arboles, pero creo que estos tres mencionados dan una base solida para adentrarse a las estructuras de datos. Procura de estudiarlos bien ya que son los mas comunes.

## Stacks & Queues

#### Stacks (Pila/Montón)
Una manera sencilla de entender este concepto es imaginarlo como si fuese un *Array/Arreglo* en el cual al añadir un elemento, este creará un nuevo espacio y se insertara a lo ultimo de este arreglo. Y la forma para remover elementos, es quitando el ultimo elemento. Esto esta basado en el principio **LIFO** (Last In First Out) el cual el primer elemento añadido es procesado a lo **ultimo** y el ultimo elemento es el **primero** a procesar. 

**Ejemplo en JS:**
Imagínate que estas lavando los platos y los vas apilando uno arriba del otro, y en el momento que terminas de lavarlos, tienes una pila gigantesca de estos.
Lo mas lógico seria ir quitando desde el mas arriba (El ultimo añadido a la pila) hasta llegar al primer plato que lavaste (El primero añadido a la pila).
```js
const dishStack = [21, 45, 78] //the numbers does not represent anything in particular

// we add more dishes to the stack
dishStack.push(96) 
dishStack.push(4) 

console.log(dishStack) // [21, 45, 78, 96, 4]

// and then we start to removing the dishes off the stack
dishStack.pop() 
console.log(dishStack) // [21, 45, 78, 96]

dishStack.pop()
dishStack.pop()
console.log(dishStack) // [21, 45]
```

#### Queues (Cola/Fila/Hilera)
No es tan distinto a las Stacks a diferencia de que este caso se aplica el principio **FIFO** (First In First Out) que trata que el primer elemento añadido (o el elemento con mas tiempo en la fila) sea el primero a ser procesado.

**Ejemplo en JS:**
Visualiza que estas en un supermercado bastante conocido ubicado en el centro de la ciudad donde te resides. Agarras un carrito y empiezas a colocar los productos que necesitas y una vez que termines de seleccionar lo necesario te diriges a un cajero del mismo establecimiento. 
Pero, desafortunadamente, de tanta gente comprando se hizo una **fila**. El que llego mas pronto al cajero va a ser atendido y si alguien llega después de vos, va a ser atendido luego que tu compra termine.

```js
const peopleQueue = ["Alfred","Jane","Herbert"]

//cashier is taking care of the queue
peopleQueue.shift()
peopleQueue.shift()

console.log(peopleQueue) // ["Herbert"]

//more people are joining the queue
peopleQueue.push("Kasey")
peopleQueue.push("Cydney")

console.log(peopleQueue) // ["Herbert", "Kasey", "Cydney"]

```

#### Conceptos Generales sobre Stacks y Queues.

- Ambos son *Linear Data Structure* y contienen un tamaño dinámico.
- A diferencia de un Array, estos no pueden insertar datos en posiciones aleatorias.
- Todas sus operaciones son de complejidad O(1) ([Articulo sobre el Big O Notation](https://the-amazing-gentleman-programming-book.vercel.app/en/book/Chapter06_Algorithms#big-o-notation)).

---

# Bibliografía

Me he guiado de los siguientes artículos para desarrollar este tema: 

- [Google Tech Dev Guide.](https://techdevguide.withgoogle.com/paths/data-structures-and-algorithms)
- [Geeks For Geeks.](https://www.geeksforgeeks.org/data-structures/)
