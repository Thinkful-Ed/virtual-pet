# Intro to JavaScript: Build a Virtual Pet

## Introduction
Today we’re going to get an introduction to JavaScript by building a [simple virtual pet application](https://cumbersome-vole.glitch.me/). 

[Thinkful](https://www.thinkful.com/) is hosting this event. Thinkful is a bootcamp that helps people become developers and data scientists through 1-on-1 mentorship and project-based learning.

Today you’ll be working with junior Thinkful mentors to learn the key concepts and build the project. The lessons you see below are taken and abridged from Thinkful's full-stack developer program. As you read this, make sure to ask for help from your TA's when you're confused about a concept.  

Lets get started!

## Programming in JavaScript

Programming is the process of translating a problem stated in plain language into a set of instructions for solving that problem (this is what is meant by the term *algorithm*), and then expressing your algorithm in terms that your computer can understand (that is, expressing it in a programming language).

A *program*, in simplest terms, is a set of instructions for a computer to carry out. In the context of frontend web development, you might write a program for validating form inputs when the user submits their username and password to a form, or checking to make sure they’ve typed a valid phone number before passing the data to a server. Or you might have a program that retrieves data from the Twitter API and displays an interesting visualization of your user's friend and follower network. There's literally an infinite number of programs you could write.

## Variable Basics

A variable is a name that is attached to a value. Variables open up two possibilities.

First, they give us a shorthand way to refer to values created elsewhere in a program. We can declare and define a variable once, and pass that value around in our code without having to rewrite it each time.

Second, variables give us a way to manage *state* in a program. *State* has to do with persisting values over time in a program. That probably sounds abstract, so let's look at a concrete example. Consider the following interface, which displays to the user how many times they've clicked a button (super useful, right!?):

<iframe height="500px" width="100%" src="https://repl.it/IgSp/2"></iframe>

Take a minute to read through the code comments in the JavaScript code in this Repl.it to get a sense of what it's doing. Click the "index.js" tab to see the JavaScript code, then click the "run" button at the top of the Repl.it to run the code. Remember, the goal at this moment is not to master the syntax; instead, we want you to start get a feel for this idea of *state*.

In this simple program, the application state is maintained in a single `clickCount` variable. When the user clicks the button, we add 1 to the value currently stored in `clickCount`, display the updated click count to the user, then wait for any additional clicks, and when they happen, run the same instructions again. We say that in between successive calls to the function (that is, the `function(event) {....}` part of the code), the application's state is maintained in the `clickCount` variable. At any point when this program is running, the `clickCount` variable tells everyone else how many clicks have happened. Variables give us a way of persisting this information for the life of the program.

## Defining variables with `let`

`let` is used to define variables whose values can (but need not) be reassigned.

```javascript
let pi = 3.14159;
console.log(pi); // => 3.14159
// on second thought, let's round to the nearest tenth place...
pi = 3.1;
console.log(pi); // 3.1
```

In this example, we initially create a variable `pi` whose value is 3.14159. We print out that value, then change the value of `pi` to 3.1, and then print that value. Because we've defined this variable using `let`, the browser allows us to assign a new value to `pi`.

We can initially *declare* a variable without yet assigning a value. When you *declare* a variable, you create a link between a variable name, and a place in the computer's memory that stores the value of that variable. The syntax for declaring a variable looks like this:

```javascript
let myVar;
```

When you declare a variable, it doesn't have a value yet. By default, JavaScript gives declared (but unassigned) variables the special value `undefined` (which we’ll discuss below).

To assign a value to a declared variable, we use the same assignment operator we saw above:

```javascript
let myVar;
myVar = 6;
```

Here we've said that the value of the variable `myVar` is 6, and that information is stored in memory.

## Naming variables

The names you choose for variables are important.

On the one hand, there are some rules about how variable names *must* look in order for the JavaScript interpreter to recognize that our code is talking about a variable. On the other hand, there are stylistic conventions about how we *should* name our variables.

You can find a full account of the rules governing variable names in JavaScript [here](https://mathiasbynens.be/notes/javascript-identifiers). Here, we mention the following:

* **Reserved words**: Reserved words are a special category of words that you're not allowed to use as variable names in a given programming language. For instance, in JavaScript, you can't reassign the name `var` to a new value (that is, you can't  do `var var = 'some value';`). If you try to use a reserved word as a variable name, you'll get an error. Note that reserved words *can* be used within a variable name (so `var varFoo;` is okay).
* **Character restrictions**: A variable name must begin with an upper or lower case letter, `$` or `_`.  It cannot begin with a number. Numbers can be used elsewhere in the variable name (`var myFoo2;` is okay). Spaces cannot appear anywhere in the variable name (`var my Foo = 'bar';`, not okay). Comparison and logical operators cannot be used in variable names (`var my+Foo;` is  not okay).

There are also best practices that you *should* follow. If you don't it won't cause your code to break, but it will make your code look strange to other JavaScript developers and make it harder to maintain. Here are the most important stylistic guidelines:

* **camelCasing**: JavaScript developers have an unwritten agreement to use *camel-casing* for variable names. Camel-casing looks like this: `thisIsCamelCasing`. A camel-cased variable name starts with a lowercase letter, and then uses lowercase letters throughout, except for the first letter of any new words in the variable name after the first -- for these first letters, use uppercase. There are agreed upon cases where we use TitleCasing in JavaScript (for instance, when creating [object constructors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/constructor#Examples), which is an advanced topic that you don't need to understand at the moment), but the general rule is use camel-casing.
* **Choose meaningful variable names*: When we learned about HTML, we learned about the idea of *semantic HTML*, which says that the type of element we choose should reflect the type of content that element provides. In a similar way, when we choose variable names in JavaScript, we should choose names that reflect how the variable gets used in the program. A well chosen variable name can help other people reading the code to understand how the variable is intended to be used. In the click counter app at the top of this reading, we had the variable name `clickCount`. When you read that name, you already have a sense of what it does. If we had named that same variable `y`, the code would have worked exactly the same, but its meaning becomes less clear.

## Javascript Data Types
A *data type* is a kind of value that variables can have in a given programming language. JavaScript has six data types: `String`, `Number`, `Boolean`, `Null`, `Undefined`, and `Object`. We'll give you a brief introduction to all 6 data types. The goal here is to give you a lay of the land, not for you to memorize all the information in this reading.

### Strings

Strings are delineated by opening and closing quotes (either single or double, but both must be same kind, you can't open with a single, and close with a double): `let foo = 'bar';` and `let bar = "foo";` are both valid.

Strings are used to represent text. It's [*basically* the case](http://stackoverflow.com/a/11141331) that any character from the [Unicode](https://en.wikipedia.org/wiki/Unicode) character encoding scheme can be represented in a JavaScript string.

We'll explore strings in depth later in this lesson.

<img src="string-variables.gif" class="no-expand">

### Numbers

The number type in JavaScript is used to represent numbers — both integer values (that is to say, whole numbers like 1, 2, 3, 10000000...) and floating point decimal numbers (that is, numbers like 1.234999).

We'll explore numbers in depth later in this lesson.

<img src="number-variables.gif" class="no-expand">

### `null`

`null` is a special value used to indicate that a variable has no value. It's not uncommon to see code that defaults to assigning `null` when other data is not available.

Be aware that if you run `typeof null` in JavaScript, you'll get an eyebrow-raising answer: "object". Even though `null` is a distinct data type, `typeof` says it's an object. This is a relic of a much earlier version of JavaScript that was not fixed in ES5 or ES6.


### booleans

```javascript

let loggedIn = false;

if (!loggedIn) {
  redirectToLoginScreen();
}
```

Booleans signify truth and falsity. A boolean has two possible values: `true` and `false`. In the example above, we set `loggedIn` to false, and we then have a block of code that runs if and only if the user is not logged in. The `!` in `!loggedIn` inverts the Boolean value of the item to the right of it, so `!false` evaluates to `true` and `!true` evaluates to false.

We'll learn more about Booleans in the lesson on application logic.

### `undefined`

We encountered `undefined` in the previous assignment when we discussed *declaring* variables before assigning values to them. `undefined` is a special value that the browser assigns to variables when it first creates them in memory.

You should never directly set a value to `undefined`. It's fine to check if a variable is `undefined`, but you shouldn't do `let foo = undefined;`. If you want to represent the absence of a value, use `null`.

### functions

A function is a mini program that you define once in your code and invoke or call elsewhere. We saw three functions in the Fibonacci example earlier in this lesson: `generateFib`, `getFibListLength`, and `displayFibs`.

```javascript
function sayHello(personName) {
 const greeting =  "Hi there, " + personName;
 console.log(greeting);
}

```

Functions are values, but not in quite the same way as the preceding data types. Whereas numbers, strings, Booleans, null, and undefined all represent a discrete, specific value, a *function* describes a thing that's a bit hard to pin down: a set of instructions that can be run elsewhere. These instructions can create, manipulate and reference the simple data types described above.

Like any other object, a function can be passed around your code, assigned to a variable, etcetera. You can write a set of instructions once, and invoke or call that set of instructions elsewhere in your code.

We'll explore functions in depth later in this unit.


### objects

Objects are considered to be a *complex data type* because they combine the *primitive data types* we've just explored (numbers, strings, Boolean, null, undefined).

Objects allow us to have variables that don't point to a single value (say for instance, a single string), but instead to a collection of values. Here's an example of a JavaScript object:

```javascript
const person = {
  name: 'Jane Doe',
  greet: function() {
    console.log('Hello world');
  }
}

console.log(person.name); // => Jane Doe
person.greet(); // => Hello world
```

Here we've created an object called `person` that has a name property and a greet method.

Note that [*arrays*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array), which are basically just lists, are technically objects, but the syntax for creating them is different:

```javascript
const myFriends = ['Tweedle Dee', 'Tweedle Dum'];
```

We'll cover these data types in detail in the remainder of this unit.

## Coercion

To close out this assignment, we want to make you aware of the idea of *coercion*. In JavaScript, if you try to use an operator — say the `+` operator — with two values who have different data types, JavaScript will *coerce* (that is, force) one of the variables to the data type of the other.

```javascript
const stringVar = 'Kilroy was here ';
const numVar = 12;

const combined = stringVar + numVar;
typeof combined; // => string
console.log(combined); // => Kilroy was here 12
```

The example above demonstrates that if you combine a number with a string using the `+` operator, the resulting value will be a string.

## Function Basics
Functions are one of the most important concepts in programming. A function describes a repeatable process or behavior. You define that behavior once, and you can call it whenever you need to run your set of instructions.

Let's look at an example: JavaScript's built in `alert` function. Open the JavaScript console in Developer Tools, enter the following command, and hit enter: `alert('Hello from JavaScript land')`. You should see a pop up window displaying 'Hello from JavaScript land'.


![js-dev-tools-alert.gif](js-dev-tools-alert.gif)


`alert` takes one *argument*, the text you want to display in the alert. In the context of functions, an *argument* (or *parameter*) is a variable that gets passed to the function when it's called.

The name `alert` is well chosen. Just knowing the name of the function gives us a good sense of what it does. A well chosen function name can make clear what might otherwise require multiple lines of comments to explain.

Well crafted functions like alert have a *single responsibility*. This means that they are designed to do one thing and do it well. `alert`'s sole responsibility is to display a pop-up window to the user with a message in it.

Well crafted functions are also *determinate*. Given the same inputs on separate invocations, the result should be exactly the same. No matter what else is happening in your program, when you run `alert('foo bar!')`, it will always cause an alert pop up to be displayed to the user with the text 'foo bar!'.

## Defining and invoking functions

Let's define a function `alertHelloWorld` that displays a pop up alert saying "Hello world" to the user.

```javascript

function alertHelloWorld() {
  alert('Hello world');
}

alertHelloWorld();
```

The `function` keyword signifies that a function is about to be defined. Next comes the function name (in this case, "alertHelloWorld"), followed by its *call signature* `()`. *Call signature* refers to the arguments or parameters — if any — that get passed to a function. `alertHelloWorld` doesn't get any parameters (aka, arguments) passed to it, but we'll see an example of that in a moment. Between the `{ .. }` brackets comes the main block of the function. This is the behavior that will be carried out each time the function is run.

Note that we *call* or *invoke* the function by entering a line with the function name followed by the call signature (empty, in the case of `alertHelloWorld` above: `alertHelloWorld()`).

Also, note that *defining* a function and *calling*/*invoking* it are separate things, and when you define a function, the code isn't automatically run. You only run it by calling it as described above.

Here's an example of a function that takes one argument (`name`) in its call signature:

```javascript
function hello(name) {
  return 'Hello ' + name + '!';
}

console.log(hello('Thomas')); // => "Hello Thomas!"
```

This function abstracts out the name. We now can call it and pass in any value for `name`, and it will output a string that says "Hello " + the value of `name`.

This function has a *return statement*, as do many functions. A return statement causes a function to return the value to the right of the `return` keyword. We can assign values returned by a function to a variable (`const hiTom = hello("Thomas")`) or pass them as inputs to other function calls (`console.log(hello("Thomas"))`).

Note that functions that do not set an explicit return value via `return` still return something, namely, `undefined`:


```javascript
function noReturn() {
  // don't do anything
}

const foo = noReturn();

console.log(foo); // => undefined
```

Here's a function that takes two numbers and computes their average.

```javascript
function averageOfTwo(num1, num2) {
  return (num1 + num2) / 2;
}
```

Just like in `hello` above, inside the function body (that is, any code between the {...} brackets) we can access the variables passed in as num1 and num2 when the function is called. `averageOfTwo` expects to be called with two numbers but it can handle any combination of real numbers sent in when it's called. It first adds together the two numbers, then divides that value by 2 to get the average, which it returns.

## Function Declarations vs. Function Expressions

There are two ways to define functions in JavaScript. The way we saw above...

```javascript
function myFunction() {
  console.log("myFunction");
}
```

...is called a *function declaration*.

The other way to define a function is with a *function expression* and it looks like this:

```javascript
const myFunction = function(arg1, arg2) {
  console.log("myFunction");
};
```

These two functions behave the same when invoked, they mainly differ in the syntax used to define them. But there is also a difference in how the browser reads the function definition and can use it.

Try copy and pasting the following snippet into your JavaScript console in Developer Tools:

```javascript
myFunction();

function myFunction() {
  console.log("Hello World");
}
```

Note that we call `myFunction()` in the first line *before* we define it. That may strike you as odd: how does the browser know how to run the function if it hasn't encountered its definition yet? We'll answer this question in a moment, but let's first see what happens with a function expression:

```javascript
myFunction2();

const myFunction2 = function() {
  console.log("Hello World");
}
```

If you copy and paste that into Developer Tools, and run it, you'll get an error message: `Uncaught TypeError: myFunction2 is not a function`. This behavior makes more intuitive sense. It *seems* like you really shouldn't be able to call a function if you haven't defined it. So why are we able to call the function before defining it when we use a function declaration (that is, the `function myFunction() {}` syntax)?

The reason has to do with how browsers initially read in or *parse* JavaScript code. When the browser is loading an HTML page and encounters a `script` element, it opens the file pointed to by the `src` attribute. Before executing any code, it first looks through the entire file and finds any and all variables, and sets aside spaces in memory to store these variable names. At this point, these variable names don't have any value — they're set to `undefined` by default.  After the browser has created all the variables as undefined, it then reads through the code top to bottom, executing commands. This process is known as *hoisting*.

In that same initial read-through where the browser is setting aside space in memory for undefined variables, when it encounters a function declaration, it also sets aside a space in memory. But instead of setting the function's initial value to undefined, it sets its value to the function block. This means that when the browser encounters:

```javascript
myFunction();

const foo = 'foo';

function myFunction() {
  // do something
}
```

It reads through this code once, initially setting aside space for `foo` in memory (whose value at this point is `undefined`) and setting aside space for `myFunction` (whose value is set to the instructions in the function's block).  It then reads through the code a second time to execute it. When it encounters `myFunction()` at execution time, it already knows that myFunction refers to a function.

If this all sounds confusing, don't worry — it *is* objectively hard to wrap your head around, even for experienced programmers. For now, it's enough to know that there are two ways of defining functions. In the coming lessons you’ll begin to use functions regularly and you’ll build your intuition for when to write a function. We recommend that you consistently use function declarations over function expressions unless you have a specific reason to do otherwise. But at the same time, be aware that function expressions are valid, and if you join a team that prefers that style, you should adapt.

## Default function parameters

ES6 introduces a convenient new language feature to JavaScript: [default function parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters).

Consider the following function:

```javascript
function tenPower(power = 2) {
    return 10 ** power
}

tenPower() // => 100
tenPower(1) // => 10
tenPower(3) // => 1000
```

This function takes a single parameter: `power`. It then returns the value generated by raising 10 to that power.

We've set a default value for power to be 2 (`power = 2`). This allows us to call the function without explicitly passing in a value for `power`. If we don't pass a value for `power`, we'll get the default value of 2, otherwise, we'll get the value we pass into our function.

Note that it's possible to get the same kind of functionality in ES5, but it requires more lines of code:

```javascript
function tenPower(power) {
    // this is a *conditional* block
    // which you'll learn about later in this unit. 
    // it reads "if not power"
    if (!power) {
        power = 2;
    }
    return 10 ** power
}

tenPower() // => 100
tenPower(1) // => 10
tenPower(3) // => 1000
```

In this example, if `tenPower` gets called without passing in a value for the `power` parameter, the line `if (!power)...` will evaluate to true (because power will be undefined), and `power` will get set to 2 (`power = 2`). We mention this alternative approach now not because you need to use it, but because you may see it in legacy code, and it's good to understand what's happening.

You'll see examples of default function parameters throughout the Web Development Bootcamp, especially when we get to Node and React.

## ES6 arrow functions

ES6 introduces an additional, more compact way of creating functions: arrow functions, which get their name from the use of the so-called "fat arrow" `=>`.

We'll use arrow functions extensively in the Node and React portions of this course, and we'll also use them later in this curriculum, when we begin working with arrays and anonymous functions (which are functions that you define and use just once).

For now, we just want to introduce you to the syntax for arrow functions, so you'll recognize it when you see it.

Below we have a function expression creating an `add` function, which returns the value of adding two numbers passed as parameters. We also have a comparable expression using the `function` keyword:

```javascript
const add = (num1, num2) => num1 + num2;
add(2, 3) // => 5;

// same as above
const addAlt = function(num1, num2) {
  return num1 + num2;
}
```

In `add`, we enclose the function parameters in parentheses. Next we have the fat arrow `=>`. Finally we have a single statement that will be returned by the function. Even though there is no explicit `return` keyword here, the value `num1 + num2` will be returned by this function.

Arrow functions can also be used for multi-line functions.

```javascript
const add = (num1, num2) => {
  console.log('Adding', num1, num2);
  return num1 + num2;
};

// same as above
const addAlt = function(num1, num2) {
  console.log('Adding', num1, num2);
  return num1 + num2;
}
```


When creating a multi-line arrow function, you use curly brackets (`{ }`), and if the function is meant to return a value, you have to include the `return` keyword like you do with `function`.

Just like functions defined with `function`, arrow functions need not take any parameters. When defining an arrow function that takes no parameters, you use empty parens, followed by the fat arrow:


```javascript
const alertMe = () => alert("You've been alerted!");

// same as
const alertMeAlt = function() {
  alert("You've been alerted");
}
```

When defining an arrow function that takes a *single* parameter, the parentheses are optional:

```javascript
// `num % 2 === 0` evaluates to true if there
// is no remainder when the number is divided
// by 2, otherwise false. We'll learn more about
// working with numbers soon!
const isEven = num => num % 2 === 0;

// same as

const isEvenAlt = (num) => num % 2 === 0;

// same as

const isEvenAltAlt = function(num) {
  return num % 2 === 0;
}
```


## In conclusion

If you're feeling a bit overwhelmed with all this new syntax, don't worry. For the moment, focus first on understanding the mental model for functions:

* a function is a block of instructions that you can call in your code
* some functions take arguments (or parameters), which are variables that the body of the function has access to
* some functions can *return* a value, which means that they output a value that can be assigned to a variable

For now, we also suggest focusing on mastering the `function` keyword. You'll get a chance to learn more about arrow functions later in this unit.

## Working with Strings
In your life as a frontend web developer, you'll frequently work with strings. Here are some common scenarios where you need to understand strings:

* validating form submissions
* injecting data into an HTML template
* alphabetically sorting a set of items by some property

As you read through this assignment, we recommend typing up the code snippets in a Developer Tools JavaScript console.

## What is a string?

```javascript
const myVar = 'this is a string';
```

A string is a collection of characters. In JavaScript, we can assign string values to variables by using either single or double quotes.

```javascript
const foo = "foo";
const bar = 'bar';
console.log(foo); // => foo
console.log(bar); // => bar
```

Either single or double quotes are fine. The key is that the outermost quote delimiters must both be either single or double.

Strings are used to represent text. It's [*basically* the case](http://stackoverflow.com/a/11141331) that any character from the [UTF-16](https://en.wikipedia.org/wiki/UTF-16) character encoding scheme can be represented in a JavaScript string.


## Concatenating Strings

JavaScript lets us use the `+` operator to *concatenate* — which just means "connect" — two strings into a bigger one.

```javascript
const innerText = 'The quick brown fox jumps over the lazy dog.'
const paragraph = '<p>' + innerText + '</p>';
console.log(paragraph) ;// => '<p>The quick brown fox jumps over the lazy dog.</p>'
```


## Special Characters and Escaping

Let's say you want to use the `"` character inside of a string that you're wrapping with double quotes — how can we do that?

This is a case where we need to use a `\` backslash in order to *escape* the quotation mark delimiter:

```javascript
const heSaid = "He said, \"Foo!\"";
console.log(heSaid); // => He said "Foo!"
```

In other contexts, the backslash is used to indicate special characters, such as line breaks and tabs. For instance, `'name:\tJohn'` would give us a string with "name:" and "John" separated by a tab.

`\n` represents a new line, and is also commonly used.

You can find a [full list of escaped special characters here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Escape_notation).


## Long strings

At greater than ~80 characters per line, code gets difficult to read. If you need to represent a string that's larger than 80 characters, you can split it over multiple lines by using either the escape character (`\`) or by closing the quote, adding a `+` sign, and starting a new string on the next line. Both of the following are valid:

```javascript
const element = '<p>The quick brown fox jumps over the lazy dog. The \
  quick brown fox jumps over the lazy dog. The quick brown fox jumps over \
  the lazy dog.</p>';

const element2 = '<p>The quick brown fox jumps over the lazy dog. The quick ' +
  'brown fox jumps over the lazy dog. The quick brown fox jumps over the ' +
  'lazy dog.</p>';
```

Also, know that *template strings*, which we discuss at the end of this assignment, provide a way to split text over multiple lines.

## Comparing Strings

You can use the `===` operator to compare two strings to see if they're identical.

```javascript
const string1 = 'foo';
const string2 = 'foo';
const string3 = 'bar';

string1 === string2; // => true
string2 === string3; // => false
```

## String methods

All strings in JavaScript share a number of built-in methods. Here are just a few:

```javascript
const fooBar = 'foo bar foo bar';
fooBar.length; // => 15
fooBar.charAt(0); // => "f"
fooBar.slice(4); // => "bar foo bar"
fooBar.slice(4, 7); // => "bar"
fooBar.split(" "); // => ["foo", "bar", "foo", "bar"]
fooBar.toUpperCase(); // => "FOO BAR FOO BAR"
fooBar.replace('foo', 'bar'); // => 'bar bar foo bar'
```

You can find the full list at [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#String_instances).


## Template strings in ES6

One particularly useful new feature in ES6 is *template strings*. Template strings give us a way to refer to variables and execute JavaScript code inside of a string:

```javascript
const foo = 'foo';
function sayHello() {
  return 'hello ';
}

const myString = `foo is set to ${foo}. Let's say hello: ${sayHello()}`;
```

Template strings are indicated by surrounding text between opening and closing backticks (`` ` ``). Inside a template string, you can refer to variables or execute code by using `${}`.

Template strings are especially valuable when you need to fill in details in a string from data you're getting from elsewhere. You might write code that handles generating text for greeting a user, and that refers to their home address. With ES6 template strings, you can write a string that gets filled in with values from variables defined in the surrounding code environment.

Template strings can also include line breaks. If you want to use `'literal strings'` to write HTML, for instance, you would have to use concatenation (with `+`) to keep it looking neat.

```javascript
const badArtTips = (
  '<p>How to draw an owl:</p>' +
  '<ul>' +
    '<li>Draw a circle</li>' +
    '<li>Draw the rest of the owl</li>' +
  '</ul>'
);
```

With template literals, we do not need to concatenate.

```javascript
const badArtTips = (
  `<p>How to draw an owl:</p>
  <ul>
    <li>Draw a circle</li>
    <li>Draw the rest of the owl</li>
  </ul>`
);
```

## Working with Numbers

In JavaScript, there's a single data type for representing integers (that is, whole numbers like -4, 0, 3, 1000, etc.) and floating point decimal numbers (like 3.234): `number`.

JavaScript can comfortably represent numbers ranging from (-2\*\*53, 2\*\*53), which is an acceptable level of precision for many applications.

Open the JavaScript console, and try inputting the following commands to get a feel of how numbers work in JavaScript:

```javascript
typeof 7 === "number"; // => true
let total = 1 + 2 + 3 + 4;
console.log(total); // => 10
total = total + 1;
console.log(total); // => 11
total += 3;
console.log(total); // => 14
total ++;
console.log(total); // => 15
console.log(3/10); // => 0.3
```

### Arithmetic operators

Numbers can be manipulated using the following *arithmetic* operators:

* `+` addition
* `-` subtraction
* `*` multiplication
* `/` division
* `**` exponentiation
* `%` remainder (also known as the "modulo" or "modulus" operator)

```javascript
5 + 5; // => 10

let foo = 2 + 2;
foo - 1; // => 3

let bar = foo * 2;
bar; // => 8

bar ** 2; // => 64
bar/3 // => 2.6666666666666665
bar/4; // => 2;

```

JavaScript also gives us a couple of shortcut functions for incrementing numbers:

```javascript
let counter = 0;
console.log(counter) // => 0
counter += 1;
console.log(counter) // => 1
counter += 9;
console.log(counter) // => 10
counter -= 1;
console.log(counter) // => 9
```

These compound operators allow us to change the value of a number variable in place — that is, we don't have to say `counter = counter + 1;`. Calling `counter ++` also increases the value of `counter` by 1.

Note that you can also increment like this `++counter`. The difference between the two is illustrated here:

```javascript
let i = 0;
let j = 0;

// postfix operator
let x = i++;

// prefix operator
let y = ++j;

console.log(x); // 0
console.log(i); // 1

console.log(y); // 1
console.log(j); // 1

```

With both the prefix (`++j`) and postfix (`i++`) operators, the original variable is incremented by 1 (that is, after running `++j`, `j` is equal to 1, and after running `i++`, `i` is equal to 1). The difference is in the value that is *returned* by the operator. When you run the `++` either before or after a variable, it returns a value. In the case of the prefix operator, it increments *before* it returns the value. In the case of the postfix operator, it increments *after* it returns the value.

Note that operations can be grouped, as in Algebra, with parentheses. JavaScript handles *operator precedence* via *PEMDAS* (parenthesis, exponents, multiplication/division, addition/subtraction), which you may remember from grade school. So, for instance, in `let foo = 3 + 2 * 6 / 3`, foo will evaluate to 7 because we first do `2 * 6  /  3`, which gives us 4, and add that to 3, for 7.

You can read more about arithmetic operators [here on Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators).


### Comparing numbers

Numbers can be compared using the following operators:

* `<` less than
* `<=` less than or equal to
* `>` greater than
* `>=` greater than or equal to
* `===` equal
* `!==` not equal

Here are some examples of comparing numbers:

```javascript

let foo = 1;
let bar = 2;

foo < bar // => true
foo === 1 // => true
foo >= foo + bar // false
```


### Built-in Math Methods

Although we do not cover it here, JavaScript has a built-in `Math` object which has methods for various mathematical operations like random number generation, rounding, getting absolute value, etc. You can read more about `Math` [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math).

## Making Logical Assertions


In this reading, we'll introduce how to make logical assertions in JavaScript. An assertion is a statement that evaluates to either true or false — for example: `true === true` or `1 <= 5`.

Used in combination with `if` and `else`, which we'll discuss in the next reading, logical assertions allow us to write conditional logic into our programs. We can tell our code to carry out one set of instructions if our assertion is true, and another if it is false.

Fair warning: you may find the content in this reading in particular to be a bit dry. Just remember that in order to correctly reason about how JavaScript code works, you need to understand which kinds of values JavaScript thinks of as `true` vs. `false`, and understand how to make logical assertions that evaluate to `true` or `false`.

## Truth in JavaScript

Before discussing logical operators, which compare the truth value of two assertions, we need to understand the way JavaScript evaluates individual assertions as true or false.

To explore how JavaScript thinks about truth and falsity, we're going to use the built in `Boolean` function, which is used to convert a value into either `true` or `false`.

![dev-tools-truth.gif](dev-tools-truth.gif)


Open the JavaScript console in Developer Tools and try out variations on the statements above.

The easiest way to remember which values are true and which ones are false in JavaScript is to memorize the "falsy" ones (that is, the values other than `false` that evaluate to `false` when coerced to a boolean):

```javascript
// values that evaluate to false
Boolean(false);
Boolean(""); // empty string
Boolean(0);
Boolean(null);
Boolean(undefined);
Boolean(NaN);
```

![falsy-values.gif](falsy-values.gif)

If it's not `false`, `""`, `0`, `null`, `undefined`, or `NaN`, it evaluates to `true`. That's the rule. That means that negative numbers, empty arrays (`[]`, which we'll learn about later), and empty objects (`{}`, which we'll also learn about later) all evaluate to `true`.


## Logical Operators

Logical operators are used to make assertions about two or more statements or values. Let's start with `&&` (logical and), which is used to assert whether or not two statements are true. If you run `true && false` in a JavaScript console, you'll see that you get `false`. JavaScript checks to see if *both* expressions evaluate to true, and if so, it returns true. (Technically it returns the second value if the first one is true; this is sometimes useful, since other things count as false than just the boolean value.)

In the case of `true && false`, both values being compared are already Booleans, so no conversion takes place. Since one side of the `&&` is false, the whole assertion evaluates to false.

Logical operators can also be used with non-Boolean values like strings and numbers. For instance `true && "foo bar"` evaluates to `true` because JavaScript treats non empty string values as `true`.

In JavaScript we have three logical operators: `&&` (and), `||` (or), and `!` (not). `&&` evaluates to true if the values on both sides of the operator evaluate to true. `||` evaluates to true if one of the values evaluate to true. `!` negates a boolean value, so `!true` evaluates to `false` and `!false` evaluates to `true`.

```javascript
const foo = true;
const bar = false;
foo === bar; // => false
foo || bar; // => true
foo && bar; // => false
!foo; // => false
!bar; // => true
```


## Equality, strict equality, and coercion

We've already come across the strictly equals operator `===`.  Now that we have discussed truthiness and how different values get converted into boolean values, we're in a position to understand how `===` strict equality differs from simple equality `==`.

If you run `true === 1` , you'll see that this evaluates to `false`. While `true` and `1` are both truthy values (that is to say, the boolean value of 1 is `true`), `true` is a boolean value, while `1` is a number. The strict equality operator `===` first compares data type of the two items being compared, and if they're not the same data type (as in this case), it returns `false`. If they are the same type, it then checks to see if they have the same value. Checking the type of both sides of the comparison — this is what makes the strict equality operator *strict*.

The `==` operator in JavaScript has a looser notion of equality. When it compares two items, if it finds that the two values are not of the same type, it *coerces* (or converts) one of the value types to the type of the other.  So `true == 1` evaluates to `true`, because when you have a boolean and a number, the number gets converted to a boolean, and Boolean(1) is `true`.

![two-equalities.gif](two-equalities.gif)

## Control Folow and Conditionals
In this reading, we discuss *control flow*. Control flow dictates how programs execute different sets of instructions based on differing conditions. You might have one branch that executes if a condition is true, and another that executes if it's false. That's control flow, and it's a powerful tool.

We're going to discuss two ways of achieving control flow: conditionals (`if`, `else`, `else if`) and `try/catch/finally` blocks.

## Conditionals `if`, `else`, `else if`

JavaScript gives us three keywords for working with conditionality: `if`, `else`, and `else if`. Let's start with an example of `if`:

```javascript

function sanityCheck() {
  if (true === true) {
    console.log("true is still true. that's reassuring");
  }
}

sanityCheck() // => "true is still true. that's reassuring"
```

To use a conditional, you begin with the command (`if` in this case), followed by an expression wrapped in parentheses `(true === true)`. Between the curly brackets (`{...}`) comes the statement(s) to be executed if the expression evaluates to true.

The same syntax is used for `else` and `else if`, but these both have the additional requirement that they must come after an adjacent `if` block.

```javascript
function analyzeNumber(num) {
  if (typeof num !== 'number') {
    console.log('not a number');
  }
  else if (num % 2 === 0) {
    console.log('even number');
  }
  else {
    console.log('odd number');
  }
}
```

A common pattern is to set a variable's value to a default value and then reassign it based on one or more conditional statements:

```javascript
let myVar = null;
if (condition1) {
  myVar = 'something other than default';
}
```

JavaScript gives us the [*ternary* operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) as a shortcut for this situation:

```javascript
let myVar = condition1 ? 'something other than default' : null;
```

The syntax for a ternary operator is a logical expression (or something that can be coerced to a boolean) followed by the `?` operator, followed by the value to be returned if the condition is `true`, followed by the `:` operator, and finally the value to be returned if the condition is not true.

Ternary operators and assignment via ternary operators are common in JavaScript code, and you should expect to encounter them frequently.

And expect to encounter `if` and `else` even more frequently.


## `try`/`catch`/`finally`

JavaScript gives us three commands (`try`, `catch`, `finally`) for dealing with conditional logic in the case of *errors*. These language constructs allow us to specify a block of behavior that is to be tried (the `try` block). If that does not succeed, the behavior in the `catch` block runs. And in either the success or failure case, the instructions in the `finally` block will run. Note that `try` and `catch` can be used without `finally`.

```javascript
try  {
  // this will raise an error because
  // nonExistentVariable is undefined
  nonexistentVariable += 'foo';
}
catch (e) {
 // this block runs if the try block fails. `e`
 // is an object representing the error
 console.log('Something went wrong');
 console.dir(e);
}
finally {
  console.log('This happens in both success and failure case!');
}
```

The `e` that you see in `catch(e)` will be an object representing the error. You'll learn more about objects later in this unit, but for now, just know that the error object will have information about the error that occurred.

Also, note that there's nothing forcing you to refer to the error as `e` in `catch(e)`. It's also common to see `catch(err)`, and in principle you could name that parameter whatever you'd like. But stick to `e` or `err` since those are the conventions. And know that inside the `catch` block, you refer to whatever variable name you pass to `catch()`.

Another thing to be aware of: in this example we did something to intentionally throw an error (namely, concatenating text to an non-existent variable). We could have also made use of the `throw` keyword to intentionally raise an error:

```javascript
try {
  throw 'myException';
}
catch (e) {
  // do something
}
```

Finally, know that when a catch block runs, the error no longer "bubbles up" like it would otherwise. The browser will run the catch block and then continue running the next line of code. This is in contrast to an uncaught error, which bubbles up and stops code execution.

## Object Basics
Objects are a *complex* data type that allow you to bring together common properties and behaviors into a single entity.  Objects provide an excellent way of organizing code that belongs together, help you avoid global variables, and let us represent individual instances of some model.

For instance, you can take the idea of a person and come up with a generalized model of that person’s attributes. A person has a name, and can say hello. Then we can have individual instances of that `person` model. We might have an individual person named "Sue" who greets others by saying "Howdy y'all", and another individual person named "Greta" who greets others by saying "Hi there".  All instances of a person share these traits (they have a name and can greet others).

Objects give us a way of representing instances of an idea or model, and because of that they're used all the time in programming. At the end of this course, in your capstone project, you'll create an app that retrieves data from a third party API and displays it to your user. In your JavaScript code, the results from the API will be represented as an array of objects.

In this lesson you'll learn the syntax for interacting with objects in JavaScript.

Objects are a data structure used to hold *key/value pairs*. If you've ever used a dictionary, you already have an intuitive sense of what a key/value pair is: you look up a word (aka, *key*), and you find its definition (aka, its *value*).

Here's an example of an object representing the classic rock band Led Zeppelin:

```javascript
const ledZeppelin = {
  singer: 'Robert Plant',
  guitar: 'Jimmy Page',
  bass: 'John Paul Jones',
  drums: 'Jon Bonham'
}
```


The curly bracket syntax above (`{}`) is one way we can create a new object. When you create an object like this, it's called an *object literal*. The keys in our `ledZeppelin` object are `singer`, `guitar`, `bass`, and `drums`. The values for these keys are 'Robert Plant', 'Jimmy Page', 'John Paul Jones', and 'Jon Bonham'. Each key is followed by a colon (`:`). Each key/value pair is separated by a comma (`,`).

Notice that the keys in the example above are not enclosed in quotation marks. This is the default way of indicating keys in an object literal, but there are times where you need to use quotation marks. For instance if you need a space or period in a key, you'd need to use quotation marks around the key:

```javascript
const ledZeppelin2 = {
  'lead singer': 'Robert Plant',
  'lead guitar': 'Jimmy Page',
}
```

Also, know that the keys in an object must all be *unique* -- that is, each key can be used only once in the object.

The values in an object can be any valid JavaScript data type. In the example above, all the values are strings, but values can also be numbers, booleans, other objects, `null`, or functions.

When an object has a value that is a function, we refer to that key/value pair as a `method`. Here's an example of an object representing a mammal, that features an `evolve` method.

<iframe src="https://repl.it/G9LN/3" width="100%" height="600px">

```javascript
const mammal = {
  numEyes: 2,
  warmBlooded: true,
  evolve: function() {
    console.log("I'm not mutating, I'm evolving.");
    mammal.numEyes ++;
  }
}

console.log(`mammal has ${mammal.numEyes} eyes`);
mammal.evolve();
console.log(`mammal has ${mammal.numEyes} eyes`);
```
</iframe>


### Getting values and running methods

Once the object is created, you can *get* values and run object methods in one of two ways: *dot notation* ( `ledZeppelin.singer`) or with *bracket notation* (`ledZeppelin2['lead singer']`). Using the example objects from above, both `ledZeppelin.singer` and `ledZeppelin2['lead singer']` would return the value 'Robert Plant'. Usually we use dot notation to get values from an object, but if you need to get a key with spaces or periods, you *must* use bracket notation.

The same syntax is used to run methods on an object. In the `mammal` example above, we use dot notation to call the `evolve` method.

Note that just like functions outside of objects, an object method can take arguments. Here's an example:

```javascript
const simpleCalculator = {
  add: function(a, b) {
    return a+b;
  }
};

simpleCalculator.add(1, 1); // => 2
```


### Adding key/value pairs to an object

Once an object is defined, you can add new key/value pairs to it using either dot or bracket notation. Here's an example:

```javascript
const myFamily = {
  lastName: 'Doe',
  mom: 'Cynthia',
  dad: 'Paul',
};

myFamily.sister = 'Lucinda';
myFamily['brother'] = 'Merle';
myFamily.sayHi = function() {
  console.log(`Hello from the ${myFamily.lastName}s`);
}
myFamily.sayHi() // => Hello from the Does
```


### Updating values

Updating values in objects is just like adding them.

```javascript
const foo = {
  bar: 'bizz'
};

foo.bar = 'bang';
```


### Deleting key/value pairs

To delete a key/value pair from an object, use the `delete` command:

```javascript
const foo = {
  bar: true
};
delete foo.bar;
console.log(foo.bar); // => undefined
```


### Self reference and `this`

In the `myFamily` object we looked at earlier, we added a method called `sayHi` that made use of *self-reference*:

```
const myFamily = {
  lastName: 'Doe',
  mom: 'Cynthia',
  dad: 'Paul',
  sayHi: function() {
    console.log(`Hello from the ${myFamily.lastName}s`);
  }
};

myFamily.sayHi() // => Hello from the Does
```

The `sayHi` method is able to refer to other properties on the object (in this case `lastName`). In this example, we've achieved self reference by repeating the variable name (`myFamily`) inside the `sayHi` method.

Usually the way we do this, though, is with the `this` keyword, which we use to achieve self reference. The example above could be re-written like this:

```javascript
const myFamily = {
  lastName: 'Doe',
  mom: 'Cynthia',
  dad: 'Paul',
  sayHi: function() {
    console.log(`Hello from the ${this.lastName}s`);
  }
};

myFamily.sayHi() // => Hello from the Does
```


Instead of reusing the variable name `myFamily`, we use `this`. This is more maintainable because our `sayHi` function is no longer coupled with the variable name.

There's more to learn about `this` in JavaScript (some of it heady), and we'll get a chance to explore it more in the next unit when we discuss using event handlers with jQuery. But for now, as you work with object literals, just understand that in object methods, `this` refers to the object itself, and gives you access to other properties and methods on the object.

# Building the Virtual Pet Project

You'll be building your projects in Glitch. Glitch allows you to write code in your browser and instantly see (and keep) the live version of your site. [Here's the link](https://glitch.com/edit/#!/spotless-chemistry?path=README.md:1:0) to start building your virtual pet projects. 

When you run into issues, make sure to raise your hand and ask your junior mentor for assistance.
