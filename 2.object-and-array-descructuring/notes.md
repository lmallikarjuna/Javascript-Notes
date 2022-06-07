<h1  align="center"> Object and array Destructuring </h1>

<h2 style="color: violet"> Object Destructuring </h2>
When we create an object and want to add properties to it, we can add one property at a time using **dot notation** like this:

```js
let user = {};

user.firstName = "John";
user.secondName = "Smith";
```

In the same way we can extract the property values one at a time:

```js
let user = {};

user.firstName = "John";
user.secondName = "Smith";

let firstName = user.firstName;
let secondName = user.secondName;
```

And we also have a way to add multiple properties at the same time to the object using **object notation** like this:

```js
let user = {
  firstName: "John",
  secondName: "Smith",
};
```

But, we did not have a way to extract multiple property values of the object at the same time until javascript
introduced **object destructuring**

This code:

```js
let user = {};

user.firstName = "John";
user.secondName = "Smith";

let firstName = user.firstName;
let secondName = user.secondName;
```

can be converted to this:

```js
let user = {};

user.firstName = "John";
user.secondName = "Smith";

let { firstName, secondName } = user;
```

The last line of the above code, creates two new let variables, and initialize the corresponding values from the user object.

<h2  style="color: violet"> Array Destructuring </h2>

Similar to object destructuring, we can also destructure arrays when we know what we have at the specific index.

```js
let user = ["John Smith", "john.smith@gmail.com", "823764"];

let name = "John Smith";
let gmail = "john.smith@gmail.com";
let userID = "823764";
```

The above code can we re writting using destructuring like this:

```js
let user = ["John Smith", "john.smith@gmail.com", "823764"];

let [name, gmail, userID] = user;
```

<h2  style="color: violet"> Advanced Destructuring Concepts </h2>

Sometimes we want to destructure the values of the object but to a different named variables than the corresponding property names. For example, if we look at the object below, the property names are not understandable,

```js
let user = {
  f: "John",
  s: "Smith",
  m: "john.smith@gmail.com",
};
```

In this case, we can rename the destructured variables like this:

```js
let user = {
  f: "John",
  s: "Smith",
  m: "john.smith@gmail.com",
};

let { f: firstName, s: secondName, m: lastName } = user;
```

Lets look at how we can use destructuring in function arguments and parameters.
In some situations, we have too many number of parameters in a function, in that can we may encounter few issues like:

1. The order of arguments will matter
2. We will have to check of null values for each of the arguments

```js
function getRepos(language, minStar, maxStar, createdBefore, createdAfter) {}

getRepos("JavaScript", 100, null, new Date("01/01/2022"), null);
```

Instead of passing all the arguments one by one, we can send them as one single object.

```js
function getRepos({
  language,
  minStar,
  maxStar,
  createdBefore,
  createdAfter,
}) {}

getRepos({
  maxStar: null,
  createdBefore: new Date("01/01/2022"),
  language: 'JavaScript'
  minStar: 100,
  createdAfter: null
});
```

By doing the we dont have to worry about the sequence of the values.
We can also eliminate the properties which are null and initialize those values to default values in the function definition.

```js
function getRepos({
  language='All',
  minStar=0,
  maxStar=0,
  createdBefore='',
  createdAfter=''
}) {}

getRepos({
  createdBefore: new Date("01/01/2022"),
  language: 'JavaScript'
  minStar: 100
});
```

<h1  align="center"> Shorthand Properties </h1>

```js
function user(name, userID, location) {
  return {
    name: name,
    userID: userID,
    location: location,
  };
}
```

In the above piece of code, we are returning an object.
When the key name and the value has the same name, we can omit the key itself and just write the value

```js
function user(name, userID, location) {
  return {
    name,
    userID,
    location,
  };
}
```

One more shorthand feature added in ES6 is that, when we have a function as a property in an object we used to write it in this way:

```js
function user(name, userID, location) {
  return {
    name,
    userID,
    location,
    work: function () {},
  };
}
```

Using the shorthand feature, we can omit the function keyword.

```js
function user(name, userID, location) {
  return {
    name,
    userID,
    location,
    work() {},
  };
}
```

<h1  align="center"> Computed property names </h1>

In some situations, you may want to name a property in an object using which we receive from the argument. In that situation we do it in this way using the **bracket notation**

```js
function objectify(key, value) {
  let obj = {};
  obj[key] = value;
  return obj;
}

objectify("name", "John"); // returns { name: 'John' }
```

In ES6 we have a shorthand for this, where we can use the bracket notation directly in the object property.

```js
function objectify(key, value) {
  return {
    [key]: value,
  };
}

objectify("name", "John"); // returns { name: 'John' }
```
