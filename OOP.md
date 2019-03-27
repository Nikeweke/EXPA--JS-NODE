# JS - OOP 
#### ES6 vs Prototypes

Содержание
* ES6 Classes features
* Создание класса
* Private and public fields
* Наследование 
* Вызов родительского конструктора

--- 


### ES6 Classes features
* constructor
* static methods
* setters/getters
* extends


### Создание класса
```js
// Function-class
function Animal (name, size) {
  // нет явного конструктора,
  // используем переданные параметры функции
  
  // поля (свойства)
  this.name = name || ''
  this.size = size || ''
  
  // методы
  this.sayHello = function () {
    console.log(`${this.name} (${this.size}) says hello`)
  }
}

const anim = new Animal('cow', 'big')
anim.sayHello()
```

```js
// ES6 class
class Animal {
  constructor (name, size) {
	// поля (свойства)
	this.name = name || ''
    this.size = size || ''
  }
  
  // методы
  sayHello() {
    console.log(`${this.name} (${this.size}) says hello`)
  }
}

const anim = new Animal('cow', 'big')
anim.sayHello()
```

### Private and public fields
```js
// Function-class
function Animal () {
  let private_var = 'i am private here'
  this.public_var = 'i am public 1'
  
  this.getPrivateVar = function () {
    return private_var
  }
  
  this.setPrivateVar = function (value) {
    private_var = value
  }
}

const anim = new Animal()
anim.setPrivateVar('Alloha')
console.log(anim.getPrivateVar())
```

```js
// ES6 class
class Animal {
  constructor () {
	var private_var = 'i am private here'
 	this.public_var = 'i am public 1'
  }
  
  getPrivateVar () {
    return this.private_var
  }
  
  setPrivateVar(value) {
    this.private_var = value
  }
}

const anim = new Animal()
anim.setPrivateVar('Alloha')
console.log(anim.getPrivateVar())
```


### Наследование 
```js
// Function-class
// наследование сделанное через прототипы работает быстрее
function Car(){}
function Volvo(){}
// Volvo extends Car (with prototypes)
Volvo.prototype = Object.create(Car.prototype)

console.log(Car)   
console.log(Volvo) 
```

```js
// ES6 class
class Animal{}
class Dog extends Animal {}

console.log(Animal)
console.log(Dog)
```

### Вызов родительского конструктора
```js
// Function-class
function Cat () {
  Animal.call(this) 
}
```

```js
// ES6 class
class Cat extends Animal {
  constructor() {
    super()
  }
}
```