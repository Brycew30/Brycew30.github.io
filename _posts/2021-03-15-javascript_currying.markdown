---
layout: post
title:      "JavaScript Currying"
date:       2021-03-15 18:51:48 +0000
permalink:  javascript_currying
---

As a beginner programmer, I often feel as though I'm in a state of constantly trying to level up my JavaScript knowledge. The more research I find, the more topics appear for which I have little or no knowledge. I like to Google different terms as ways to find benchmarks or goals to set for myself for taking small bites out of more complex topics.

The article I found today that caught my eye was [this](https://madasamy.medium.com/15-javascript-concepts-that-every-nodejs-programmer-must-to-know-6894f5157cb7) one that included some intermediate concepts, some of which I've studied before and some that I haven't. So, today I wanted to talk a little bit about **currying** in JavaScript.

[JavaScript.info](https://javascript.info/currying-partials) gives a really nice overview of currying from basic examples all the way to more advanced use. In short, a curried function takes several arguments <u>but only one at a time</u>. It's a way of breaking down a function with multiple arugments into one that takes one argument and returns a function that takes in the next argument, which returns a function that takes in the next argument, etc.

## Some Real World Uses
The easiest examples of currying to understand, to me, are when it's used with addition and multiplication:
```
// Addition
function add(a) {
    return function (b) {
        return a + b;
    }
}

---which is the same as:

const add = a => b => a + b;

add(5)(5)
// 10
```
```
// Multiplication
const multiply = a => b => a * b;

add(5)(5)
// 25
```
As we can see here, the function first takes in `a` and then returns an entirely new function, which then takes in `b` and returns the sum/product of the two. Because each argument is taken one at a time here, the same steps could be taken to continue adding parameters with new funcitons returned each time.
This is basically a more useful example of the `multiply` function above, but I think it hammers home how it's used:
```
// Knowing the formula for volume of a cube/box is volume = length * width * height,
function volume(length) {
    return (width) => {
        return (height) => {
            return length * width * height
        }
    }
}

const bigBox = volume(24)(18)(24)
// 10, 368
```
Currying works by using [closures](https://brycew30.github.io/learning_to_get_some_closure_s). The nested functions keep access to outer arguments, which makes the inner-most function be able to use each one of the arguments supplied. In this case, the last arrow function has access to the `length` and `width` arguments because it is enclosed in the two outer functions.
## Why Curry?
After seeing how it works, the next natural question would be "why use currying?". The most useful reason I have found for currying is that smaller parts can be changed and reused easier than having one function with multiple variables and then making sure you have the right parameters (or default arguments if not) and maintaining them throughout. Currying is also really helpful with event handling and data ([here](https://bjouhier.wordpress.com/2011/04/04/currying-the-callback-or-the-essence-of-futures/) is a somewhat complex but really thorough article for more information than I'd be able to explain myself.) And lastly, currying in JavaScript can just help keep you from passing the same variable again and again if you have similar functions or a really large project with multiple similarities.

## Wrapping Up
I already listed all of the resources I used for studying currying. But as always, I encourage you to take this and run with it if you found it interesting. I'm sure there are some really great videos of people using this in a much more practical way than I was able to give. Thanks for reading, and happy JavaScripting!
<br>
<br>

![](https://media.giphy.com/media/dUHHciwZdWXd2XZo8n/giphy.gif)
