---
layout: post
title:      "ES6 Deep Dive: Generators and Iterators"
date:       2021-01-18 21:33:04 +0000
permalink:  es6_deep_dive_generators_and_iterators
---


## Introduction
I've spent the last couple months trying to get more familiar with JavaScript and deepen my understanding of the language a little bit. If you missed the earlier blogs I made about what I'm learning, you can see them [here](https://brycew30.github.io/learning_async_await) and [here](https://brycew30.github.io/learning_to_get_some_closure_s). These might be some somewhat obscure topics and not your typical "Learning Objects" or "Arrow Functions!" type blogs that cover broader useful ideas, but like I've said before, my brain understands things better when I understand the small things in greater detail. Since so many of the algorithmic challenges I've been working on require some type of iteration, I wanted to talk about these two additions with ES6.

## Iterators
The `for` loop has always been available to us in JavaScript, which typically looks like:
```
for (let i = 0; i < anything.length; i++) {
    // do something with i
}
```
But we have an alternative as of ES6 that looks like:
```
for (const i of anything) {
    // do something with i
}
```
This looks slightly less clunky, which makes it easier to read and work with. But apart from looking nice, it also allows us to interact with the elements of data set *anything* directly. I've been working on what this looks like with a function determining if a number is prime or not. Here's what that function may look like with previous convention:
```
function isPrime(num) {
    if (num < 2) {
        return false;
    } else if (num === 2) {
        return true;
    }
    for (let i = 2; i < num; i++) {
        if (num % i === 0) {
            return false;
            break;
        }
    }
    return true;
}
```
I'm sure there's a slightly quicker way to make this with pre-ES6 convention, but this works for example purposes. Next, we need to loop through a list of numbers to determine if each is prime:
```
let potentialPrimeNums = [73, 6, 90, 19, 15];
let primeNums = [];

for (let i = 0; potentialPrimeNums.length; i++) {
    if (isPrime(potentialPrimeNums[i])) {
        primeNums.push(potentialPrimeNums[i]);
    }
}
// primeNums = [73, 19]
```
Same deal- it's lengthy but it works. With ES6 though, we're now able to write the `for` loop as:
```
let potentialPrimeNums = [73, 6, 90, 19, 15];
let primeNums = [];

for (const i of potentialPrimeNums) {
    if (isPrime(i) {
        primeNums.push(i);
    }
}
// primeNums = [73, 19]
```
Now, the variable *i* represents an actual item in the array `potentialPrimeNums`, so we don't have to use its index anymore. From my (admittedly limited) understanding, ES6 added the [`Symbol.iterator()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol/iterator) method. This returns a JavaScript object containing the next value in the loop and a `done` key which is either `true` or `false` depending if the loop is finished or not.

## Generators
Generators give us a special, self-defined way to loop through things:
```
function* getNextPrimeNum() {
    let nextNum = 2;
    while (true) {
        if (isPrime(nextNum)) {
            yield nextNum;
        }
        nextNum++
    }
}
```
That weird asterisk after `function` tells JavaScript we're defining a generator. The `yield` keyword remembers its place while running so it can pick up where it left off next time it's called. Our next step is to do this:
`const nextPrimeNum = getNextPrimeNum();`
Then we call `nextPrimeNum` when we want to find the next prime number:
```
console.log(nextPrimeNum.next().value); // 2
console.log(nextPrimeNum.next().value); // 3
console.log(nextPrimeNum.next().value); // 5
```
We could also just call `nextPrimeNum.next()` which would return the object `{value: 2, done: false}` which has a `done` keyword to tell us if the task is completed (which it never would be in this scenario.)

## Conclusion
This is a lot of words for something that can also be explained well [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*). These give us some flexibility in allowing us to write JavaScript in a cleaner way. Thanks for reading, and hopefully this encourages you to explore some behind-the-scenes details when writing your code.

#### Resources I found helpful:
* [Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators) of course
* [This](https://github.com/lukehoban/es6features) GitHub post lays out ES6 features in a nice list
* [This](https://jakearchibald.com/2014/iterators-gonna-iterate/) post shows some nice examples of Iterators and Generators at work

![](https://media.giphy.com/media/l0MYwrucQ9amOkFHO/giphy.gif)
