#javascript #intermedio

> **Tabla de contenidos:**
- [¿Que es un Generator en JS?](#que-es-un-generator-en-js)
- [El problema con las funciones.](#el-problema-con-las-funciones)
- [Como se usan los Generators.](#como-se-usan-los-generators)
    - [Inicializacion:](#inicializacion)
    - [Método next();](#método-next)
    - [Breve explicación de lo que sucede.](#breve-explicación-de-lo-que-sucede)
- [Datos importantes a tener en cuenta.](#datos-importantes-a-tener-en-cuenta)
    - [Arrow Functions](#arrow-functions)
    - [Almacenamiento de informacion](#almacenamiento-de-informacion)
    - [Return en Generators](#return-en-generators)
    - [Asignación de parámetros](#asignación-de-parámetros)

---
## ¿Que es un Generator en JS?

Los generadores en JavaScript provienen de un objeto iterable llamado _Generador_ que fue introducido en el estándar **EcmaScript 2015** y nos permite _pausar, reanudar y producir varios valores_ en nuestras funciones heredadas de esta instancia (objeto que fue creado por una clase o un constructor).

Esto puede sonar mas complejo de lo que parece pero no te agobies, voy a explicarlo con ejemplos bastante sencillos.

## El problema con las funciones.

Como todos sabemos, una función **es una porción de código** a la cual podemos llamar con el nombre que le asignamos y dependiendo de como la hemos estructurado suele ejecutarse de principio a fin.

Pero como sabemos, **no hay manera de lograr que estas puedan pausarse en medio de una ejecución** y luego reanudar desde el punto que se había quedado posteriormente... ¿O si?.

Primero, voy a enseñar como se ejecutaría una función normalmente.

> En este programa vamos a querer contar hasta el paso numero tres **detenidamente**.
```js
function stepsToThree(){
	console.log("step 1")
	console.log("step 2")
	console.log("step 3")
}

stepsToThree()
```

En la consola nos mostraría lo siguiente:

``` 
Output:

step 1
step 2
step 3
```

Si queremos ir ejecutando cada paso uno por uno, seria imposible con esta estructura debido a que la propia naturalidad de las funciones no los impide y es por eso que nace la maravilla de **Generators**.

## Como se usan los Generators.

#### Inicializacion:

Para poder utilizarlos primero debemos saber como declararlos, y para eso necesitaremos poner un asterisco ( * ) después de nuestro **identificador "function"**, de la siguiente manera:

```js
function* generatorJavascript(){ }
```

También esta función trae consigo otro operador llamado *yield* que, similar al _return_, se diferencia debido a que **pausa y reanuda la ejecución de la función desde su declaración**.

```js
function* countingBy10(){
	console.log("first execution")
	yield 10;
	console.log("second execution")
	yield 20;
}

let result = countingBy10();
console.log(result);
```

``` 
Output:

Object [Generator] {}
```

#### Método next();

Como veras, ejecutando esta función no mostraría ningún mensaje ni tampoco retornaría ninguno de los valores que hemos definido porque aun no accedimos al método _next()_ que nos trae.

 (_El console.log() es solo para demostrar que retorna este método **next()**, no es necesario para ninguna ocasión a menos que sea didáctica_)

```js
function* countingBy10(){
	console.log("first execution")
	yield 10;
	console.log("second execution")
	yield 20;
}

let result = countingBy10();

console.log(result.next())
console.log(result.next())
console.log(result.next())
```

``` 
Output:

first execution
{ value: 10, done: false }

second execution
{ value: 20, done: false }

{ value: undefined, done: true }
``` 
#### Breve explicación de lo que sucede.

Vamos a fraccionar el código para comprenderlo mejor.

- Cuando llamamos la función *countingByTen()*, la vamos a almacenar en la variable *result*. Esta función **no** se ejecutaría y nos retornaría un objeto con varios métodos.

- Para lograr que esta función *countingByTen()* haga su primer recorrido, debemos utilizar el método *next()* que se encuentra almacenado en la variable *result*.

- Cuando hacemos la primera llamada al método *result.next()* esta misma se va iterar hasta llegar al siguiente *yield* y nos retornaría un simple objeto con dos valores **value** y **done**.
Siendo que la propiedad **value** seria lo que el *yield* nos retornaría (en este caso, 10) y **done** es un booleano que indicaría si la función ha llegado a su fin.
También hay que tener en cuenta que la consola solo ha mostrado el primer _console.log()_ con el mensaje _"first execution"_ y nada mas.

- En la segunda llamada al método _result.next()_ nos muestra el segundo _console.log()_ que contiene el mensaje _"second execution"_ y, una vez mas, nos retorna el mismo objeto. Con la diferencia que la _key (o llave)_ **value** es ahora 20 y no 10.

- Y por ultimo, en el tercer y ultimo llamado al método _result.next()_ ambas _keys_, tanto como **value** y **done** serán diferentes. Ya que, al no tener mas instrucciones, la _key_ **value** será indefinida y el **done** será verdadero.

## Datos importantes a tener en cuenta.

#### Arrow Functions

> ▪ El _function generator_ no funciona con _arrows functions_.

```js
const nextStep = ()* => {}; //❌ SyntaxError: Unexpected token
```

---

#### Almacenamiento de informacion

> ▪ Las _variables_ dentro de la función aun guardan sus valores. Es decir, si definimos que en la _ejecución_ la variable **expontential** es **2**, pausamos el bucle y posteriormente lo reanudamos, el valor de **expontential** va a "persistir" y aun el valor será **2** hasta que lo redefinamos.

```js
function* exponentialBy2(){
	let expontential = 2;
	while(true){
		expontential *= 2;
		yield expontential;
	}
}

const expontential = exponentialBy2();

expontential.next(); // { value: 4, done: false }
expontential.next(); // { value: 8, done: false }
expontential.next(); // { value: 16, done: false }
// and so on...
```

---
#### Return en Generators

> ▪ El _return_ se utiliza como la ultima sentencia en el bloque de código para salir de la función adecuadamente. Devolviendo la _key_ **done** como un booleano _true_ y retornando un **value**.
> Esto se hace para que la ultima ejecución no tenga la _key_ **value** indefinida (undefined) y nos ahorremos otra instancia de _grabOneFruit.next()_.

```js
function* fruitsInBasket(numberOfFruits){
	for(let i = numberOfFruits;  i > 0; i--){
		console.log(`You have ${i} fruit(s) left!`)
		yield i
	}
	console.log("There's no more fruits left!")
	return 0;
}

const grabOneFruit = fruitsInBasket(2); // you can pass parameters too!

grabOneFruit.next(); // { value: 2, done: false }
grabOneFruit.next(); // { value: 1, done: false }

grabOneFruit.next(); // returns { value: 0, done: true } 
// instead of { value: 0, done: false } if it would be yield
```

---
#### Asignación de parámetros

> Es posible asignar valores al metodo _next()_ para que el próximo _yield_ tenga ese valor.
> La primera vez que se llama a este método, su valor será ignorado.

En este caso, el primer método _next()_ no será _agregado_ al array debido a que va a de requerir de interpretar el valor que deba añadir y por eso se ejecuta la sentencia _yield_ primero, que hará pausar la ejecución del programa.
El siguiente método _next()_ sobrescribirá esta variable y seguirá desde el ultimo punto que se había situado, es decir, el _array.push()_ y continuara de esta manera indefinidamente. 
(Si el segundo método _next()_ no le asignamos ningún parámetro, se _agregara_ al array un valor _undefined_)

```js
class Task {
  constructor(name, isCompleted) {
    this.name = name;
    this.complete = isCompleted;
  }
}

function* ToDoList() {
  let array = [];
  let pushTask;
  
  while(true){
    console.log("Current tasks: ",array)
    array.push(yield pushTask)
  }

}

const addTask = ToDoList();

addTask.next("This would be ignored"); //first execution is always ignored
addTask.next(new Task('Make dinner', false))
addTask.next(new Task('Go shopping', true))

```

````
Output:

Current tasks: []
Current tasks: [ Task { name: 'Make dinner', complete: false } ]
Current tasks: [ Task { name: 'Make dinner', complete: false }, Task { name: 'Go shopping', complete: true } ]
```