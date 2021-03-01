---
layout: post
title:      "Immediately-Invoked Function Expressions (IIFE)"
date:       2021-03-01 19:54:40 +0000
permalink:  immediately-invoked_function_expressions_iife
---


## Definitions
A good place to start is defining what these terms mean before we explain how to use them. In JavaScript, we can define a function in two ways: a *declaration* and an *expression*.
* <b>Declarations:</b> begin with the function keyword, and then followed by the name of the function and any arguments it takes in. For example:
```
function sayHi(name) {
    console.log(`Hi, ${name}!`);
};
sayHi("John");
```
When defining a funciton using a declaration, the function is [hoisted](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting) which allows you to use a function before defining it. So, we could actually write the previous example like:
```
sayHi("John");
function sayHi(name) {
    console.log(`Hi, ${name}!`);
};
```

* <b>Expressions:</b> are functions that are assigned to a variable. For example:
```
const tellUserHi = function sayHi(name) {
    console.log(`Hi, ${name}`);
}
tellUserHi("John");
```
You can see that to call it, we use the variable name `tellUserHi` with the argument rather than the `sayHi` function. Function expressions are not hoised like declarations, so they are only available when their line is interpreted. The following would produce an error:
```
tellUserHi("John");
const tellUserHi = function sayHi(name) {
    console.log(`Hi, ${name}`);
};
```
Function expressions can also be anonymous, which in our example would mean taking out the "sayHi" function name. That would look like this:
```
const tellUserHi = function (name) {
    console.log(`Hi, ${name}`);
}
tellUserHi("John");
```

## What are IIFEs?
Okay, those definitions set us up to get to the point of this blog. Immediately-Invoked Function Expressions (somtimes pronounced "iffys" for short) are functions that are executed immediately after being defined. They are only executed once, and never again in your code. We invoked the functions immediately by putting parentheses at the end of the function closing.
```
(function() {
    // code
})();
```
The parentheses that surround the whole function tell JavaScript that it's a function expression, and the pair at the end invoke the function. IIFEs can also take in arguments like this:
```
(function(firstArgument, secondArgument) {
    // code
})("example", "arguments");
```
Arrow functions can also be IIFEs like this:
```
(() => // code)();
```
## When are IIFEs used?
There are a few different reasons for using IIFEs. If you only intend for a function to run once in your code, this is what you need. To see this play out, here's an example:
```
const runOneTime = function() {
    // Somthing I want to only run once
}
runOneTime();
```
This can actually be called anywhere (and any number of times) in our code. The solution would be to turn it into an IIFE:
```
(function() {
    // Somthing I want to only run once
})();
```
Their main use has to do with **scoping** and **privacy**. We know that functions in one scope don't have access to variables in an inner scope (only the opposite is true.) In practice, this means that an IIFE can prevent a variable from being overwritten in some other location within our code, maybe by user input, external libraries, or some other means.

## Changes with ES6
One last thing to point out when it comes to IIFEs is how ES6 has changed them. The `let` and `const` keywords create their own scope inside a block whereas the `var` keyword creates a variable with global scope. Therefore, IIFEs aren't necessarily used as much now that `let` and `const` are adopted with regular use.

### Resources
* [MDN](https://developer.mozilla.org/en-US/docs/Glossary/IIFE)
* [TutorialsTeacher](https://www.tutorialsteacher.com/javascript/immediately-invoked-function-expression-iife)
* [This](https://www.youtube.com/watch?v=3cbiZV4H22c) YouTube video from [FreeCodeCamp](https://www.freecodecamp.org/) is very short and sweet (and helpful)

![](https://media.giphy.com/media/JgfJrINqmg6dNw3qJ3/giphy.gif)
