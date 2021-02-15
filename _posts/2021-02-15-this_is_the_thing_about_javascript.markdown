---
layout: post
title:      "This is the Thing About JavaScript"
date:       2021-02-15 18:17:21 +0000
permalink:  this_is_the_thing_about_javascript
---


Today, on my mission to understand JavaScript even better, I'm going to try my best to explain the *this* keyword. I've been studying this since my first Flatiron JavaScript lesson, because it caused me quite a few errors in my final two projects (and some still.) It's one of those things that seems so simple when I read [blogs](https://www.javascripttutorial.net/javascript-this/) or watch [videos](https://www.youtube.com/watch?v=gvicrj31JOM&t=196s&ab_channel=ProgrammingwithMosh) about it, but then still trips me up when I least expect it. Hopefully my research can bring you some confidence and clarity in your coding, or at least can point you in the right direction.

<img src="https://media.giphy.com/media/XF473WvO789XMBz4qQ/giphy.gif" alt="buckle up" width="300"/>

**Look for the `this` differentiation, because things can get confusing saying 'this' so much.**

## What is this?
`this` is relatively common in different programming languages, with different rules, but JavaScript was my first experience working with it. I'll be explaining it from the perspective of someone with my background rather than a different language's perspective.<br>
The first thing to understand before diving into `this` is that for every function call, the JavaScript engine creates a new function execution context. With that out of the way, `this` becomes a little big clearer: `this` is the reference to the current execution context of every JavaScript function. Functions in JavaScript are basically objects, and like objects, they have their own properties- one of which is `this`. In other words, `this` tells us where, and when, and how the function is called (not declared.)


## Using this
Practically using `this` is trickier than understanding the concept of it, to me. Since the value of `this` is based on the current execution context, it can (and will) change depending on how its surrounding function is defined and invoked.

By default, the execution context of an execution is global, which means `this` refers to a global object (window in your browser.) 
```
function someFunction() {
    console.log(this === window);
}
someFunction() // true
```
*An exception to this is if strict mode is enabled, which can prevent anything from being declared on the global object and can make the value of `this` undefined.


## More Examples
```
function Person(first, last) {
    this.firstName = first;
    this.lastName = last;
    this.fullName = function() {
        console.log(`Hi, my name is ${this.firstName} ${this.lastName}!`);
    }
}
let john = new Person("John","Smith");
john.fullName() // Hi, my name is John Smith!
let lisa = new Person("Lisa","Jones");
lisa.fullName() // Hi, my name is Lisa Jones!
```
In the example of `john.fullName()`, `this` refers to a specific instance of `john` and then in `lisa.fullName()`, `this` refers to a specific instance of lisa, which is different instance of `Person`.
#### Method Invocation:
```
let car = {
    make: "Jeep",
    model: "Liberty",
    description: function() {
        console.log(`${this.make}  ${this.model}`);
    }
}
car.description()  // Jeep Liberty
```
In this example, the `this` object in the `description()` method references the `car` object.

## Call() and Apply()
This is where a little bit of relief comes in with functions. Every function has the `call`, `apply`, and `bind` methods, which can be used to set a custom value for `this` in the function's execution context.
```
function Person(first, last) {
    this.firstName = first;
    this.lastName = last;
    this.fullName = function() {
        console.log(`Hi, my name is ${this.firstName} ${this.lastName}!`);
    }
}
let john = new Person("John","Smith");
john.fullName() // Hi, my name is John Smith!
let lisa = new Person("Lisa","Jones");
lisa.fullName() // Hi, my name is Lisa Jones!
john.fullName.call(lisa) // Hi, my name is Lisa Jones!
```
You can see here that we can choose to set the value of our john variable to be the lisa object by borrowing its `this` value. The difference between call() and apply() is essentially how arguments are passed in, with apply() accepting the arguments as an array.

## Bind()
```
function Person(first, last) {
    this.firstName = first;
    this.lastName = last;
    this.fullName = function() {
        console.log(`Hi, my name is ${this.firstName} ${this.lastName}!`);
    }
}
let john = new Person("John","Smith");
john.fullName() // Hi, my name is John Smith!
let lisa = new Person("Lisa","Jones");
lisa.fullName() // Hi, my name is Lisa Jones!
let showLisa = john.fullName.bind(lisa) // Hi, my name is Lisa Jones!
```
Bind() returns a copy of the function rather than immediately executing the function like call() and apply do. When invoked bind() has the `this` set to the provided value. This is useful for when the function is executed later, you can know the context for `this` is correct.

## Conclusion
Okay, so `this` may or may not be more clear to you after reading this. Again, there are so many resources out there (I'll link some down below) that give clear definitions and examples. Generally, as I've studied `this`, the sites I'm reading tend to give specific examples of different contexts and methods being used. My best advice is to read as many of those as possible to just see lots of real world examples. I know that I learned even more from specific examples as I studied (and continue to study) to write this, so I hope to be able to point you toward something that will make it even clearler in your studying.

### Resources
* MDN for [all](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) [four](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) [of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) [these](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)
* I found [this](https://codeburst.io/all-about-this-and-new-keywords-in-javascript-38039f71780c) codeburst article by NC Patro particularly helpful
* [freeCodeCamp.org](https://www.youtube.com/watch?v=eOI9GzMfd24&ab_channel=freeCodeCamp.org) always puts out very helpful resources
* I didn't even go into `this` with arrow functions here, but [this](https://medium.com/better-programming/understanding-the-this-keyword-in-javascript-cb76d4c7c5e8) article by Pavan is very thorough for multiple `this` contexts.

![](https://media.giphy.com/media/QAqPBBoJxRLoI/giphy.gif)
