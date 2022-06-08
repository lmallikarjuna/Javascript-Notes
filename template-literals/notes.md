<h1  align="center"> Template Literals </h1>

Template Literals are used for maily two things:
1. String interpolation
2. Multiline string


```js
function welcomeMessage({ firstName, lastName, email }) {
    return "Hello, " + firstName + " " + lastName + ". The email you used to signup is \"" + email + "\"";
}
```

Using the ES6 template literals the above code is equivalent to this:

```js
function welcomeMessage({ firstName, lastName, email }) {
    return `Hello, ${firstName} ${lastName}. The email uou used to signup is "${email}"`;
}
```