<h1  align="center"> var 🆚 let 🆚 const</h1>

**Perrequisite**

# 1️⃣ Variable declarations vs Initialization

Variable declaration is when a new identifier is introduced. Initially when the variable is declared they are initialized by default to undefined.

```js
var name;
console.log(name); // undefined
```

Initialization is when we first assign a value to a variable

```js
var name = "Lohith";
console.log(name); // "Lohith"
```

# 2️⃣ Scopes in Javascript

Scopes defines when the variables and functions are accessible inside the program.

## There are two types of scopes:

1. Global Scope
2. Function Scope

![Scopes in Javascript](/assets/images/scopes.jpg "ECMAScript spec")

If we are declaring a variable inside a function using the var keyword, the variable is only accessible
inside that function and the nested functions. If we declare the variable without using the var keyword, the variable is created as a property on the global object, that is, it is accessible throughout the program.

# 3️⃣ Hoisting

When Javascript interpreters the code, it will move all the function and variable declarations to the top of the current scope. This is referred to as hoisting.

Example code:

```js
console.log(name);
console.log(z);
var name;
function func() {
  var num;
  for (var i = 0; i < 10; i++) {
    var square = i * i;
    var cube = i * i * i;
  }
  console.log(i);
  console.log(square);
  console.log(cube);
}
var z = 1;
func();
```

The above code will be converted to the following:

```js
var name;
var z;
console.log(name);
console.log(z);
function func() {
  var num;
  var i;
  var square;
  var cube;
  for (i = 0; i < 10; i++) {
    square = i * i;
    cube = i * i * i;
  }
  console.log(i);
  console.log(square);
  console.log(cube);
}
z = 1;
func();
```

Output:

```shell
undefined
undefined
10
81
729
```

# var 🆚 let

var

- Function scope
- undefined

let

- Block scope {}
- reference error

Example:

```js
let name;
function func() {
  let num;
  for (let i = 0; i < 10; i++) {
    let square = i * i;
    let cube = i * i * i;
  }
  console.log(i);
  console.log(square);
  console.log(cube);
}
let z = 1;
func();
```

Output:

```shell
i is not defined
```

# const

The only difference between let and const is that, once we assign a value to cost we cannot reassign it.
We can mutate the value.

```js
let name = {
  firstName: 'John',
  secondName: 'Snow'
}
const age = 22
age = 23  ❎
name.secondName = 'Huge' ✅
```