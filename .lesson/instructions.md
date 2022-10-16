# Compare Scopes of the var and let Keywords

If you are unfamiliar with let, check out this challenge about the difference between let and var.

When you declare a variable with the var keyword, it is declared globally, or locally if declared inside a function.

The let keyword behaves similarly, but with some extra features. When you declare a variable with the let keyword inside a block, statement, or expression, its scope is limited to that block, statement, or expression.

For example:
```js
var numArray = [];
for (var i = 0; i < 3; i++) {
  numArray.push(i);
}
console.log(numArray);
console.log(i);
```
Here the console will display the values [0, 1, 2] and 3.

With the var keyword, i is declared globally. So when i++ is executed, it updates the global variable. This code is similar to the following:
```js
var numArray = [];
var i;
for (i = 0; i < 3; i++) {
  numArray.push(i);
}
console.log(numArray);
console.log(i);
```
Here the console will display the values [0, 1, 2] and 3.

This behavior will cause problems if you were to create a function and store it for later use inside a for loop that uses the i variable. This is because the stored function will always refer to the value of the updated global i variable.
```js
var printNumTwo;
for (var i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function() {
      return i;
    };
  }
}
console.log(printNumTwo());
```
Here the console will display the value 3.

As you can see, printNumTwo() prints 3 and not 2. This is because the value assigned to i was updated and the printNumTwo() returns the global i and not the value i had when the function was created in the for loop. The let keyword does not follow this behavior:
```js
let printNumTwo;
for (let i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function() {
      return i;
    };
  }
}
console.log(printNumTwo());
console.log(i);
```
Here the console will display the value 2, and an error that i is not defined.

i is not defined because it was not declared in the global scope. It is only declared within the for loop statement. printNumTwo() returned the correct value because three different i variables with unique values (0, 1, and 2) were created by the let keyword within the loop statement.
# Exercise
Fix the code so that i declared in the if statement is a separate variable than i declared in the first line of the function. Be certain not to use the var keyword anywhere in your code.

This exercise is designed to illustrate the difference between how var and let keywords assign scope to the declared variable. When programming a function similar to the one used in this exercise, it is often better to use different variable names to avoid confusion.

```js

function checkScope() {
  var i = 'function scope';
  if (true) {
    i = 'block scope';
    console.log('Block scope i is: ', i);
  }
  console.log('Function scope i is: ', i);
  return i;
}
```

# Use Arrow Functions to Write Concise Anonymous Functions

In JavaScript, we often don't need to name our functions, especially when passing a function as an argument to another function. Instead, we create inline functions. We don't need to name these functions because we do not reuse them anywhere else.

To achieve this, we often use the following syntax:
```js
const myFunc = function() {
  const myVar = "value";
  return myVar;
}
```
ES6 provides us with the syntactic sugar to not have to write anonymous functions this way. Instead, you can use arrow function syntax:
```js
const myFunc = () => {
  const myVar = "value";
  return myVar;
}
```
When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword return as well as the brackets surrounding the code. This helps simplify smaller functions into one-line statements:
```js
const myFunc = () => "value";
```
This code will still return the string value by default.
# Exercise
Rewrite the function assigned to the variable magic which returns a new Date() to use arrow function syntax. Also, make sure nothing is defined using the keyword var.

```js
var magic = function() {
  return new Date();
};

```

# Write Arrow Functions with Parameters

Just like a regular function, you can pass arguments into an arrow function.
```js
const doubler = (item) => item * 2;
doubler(4);

doubler(4) would return the value 8.
```
If an arrow function has a single parameter, the parentheses enclosing the parameter may be omitted.
```
const doubler = item => item * 2;
```
It is possible to pass more than one argument into an arrow function.
```
const multiplier = (item, multi) => item * multi;
multiplier(4, 2);
```
```multiplier(4, 2)``` would return the value 8.
# Exercise
Rewrite the myConcat function which appends contents of arr2 to arr1 so that the function uses arrow function syntax.
```js

var myConcat = function(arr1, arr2) {
  return arr1.concat(arr2);
};

console.log(myConcat([1, 2], [3, 4, 5]));
```

# Set Default Parameters for Your Functions

In order to help us create more flexible functions, ES6 introduces default parameters for functions.

Check out this code:
```js
const greeting = (name = "Anonymous") => "Hello " + name;

console.log(greeting("John"));
console.log(greeting());
```
The console will display the strings Hello John and Hello Anonymous.

The default parameter kicks in when the argument is not specified (it is undefined). As you can see in the example above, the parameter name will receive its default value Anonymous when you do not provide a value for the parameter. You can add default values for as many parameters as you want.

# Exercise
Modify the function increment by adding default parameters so that it will add 1 to number if value is not specified.

```js

// Only change code below this line
const increment = (number, value) => number + value;
// Only change code above this line
```




