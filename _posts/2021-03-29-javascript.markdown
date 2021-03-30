---
layout: post
title:      "...JavaScript"
date:       2021-03-30 03:58:31 +0000
permalink:  javascript
---


You know those features that you come across in your coding journey that just make your life easier the more you understand them? That's [rest parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters) and [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) for me. I understand why a lot of early JavaScript fundamentals are taught without introducing these two ES6 features, but I've become more and more comfortable using them in my code and subsequently more appreciative of them.

## Spread Operator
The spread operator does exactly what the name says: it spreads/extends the values of arrays and strings (iterables) to their individual elements and can allow a function call with an iterable where 0 or more arguments are expected. You'll see the spread operator as three dots before the iterable, such as `...example`.
This next example contains a function called `trianglePerimeter` which expects 3 arguments `sideOne`, `sideTwo`, `sideThree`. Let's say we have an array with 3 elements (triangle sides), and we want to pass them as arguments for the function in a simple, concise way. The spread operator is perfect for that:
```
function trianglePerimeter(sideOne, sideTwo, sideThree) {
    return sideOne + sideTwo + sideThree;
}
const triangle = [1, 2, 3];
console.log(trianglePerimeter(...triangle));
// 6
```
The above is essentially saying:
```
function trianglePerimeter(sideOne, sideTwo, sideThree) {
    return sideOne + sideTwo + sideThree;
}
const triangle = [1, 2, 3];
console.log(trianglePerimeter(triangle[0], triangle[1], triangle[2]));
// 6
```

The spread operator is really versatile in the many ways it can be used (often in place of using the `.apply()` function). Like the MDN page explains, it can be used inside function calls where there is a *specific* number of parameters, such as: `function(...iterableObject);`. This feature lets us pass multiple iterables if we want to, and even combine with normal values.


## Rest Parameter
The rest parameter, also seen as `...`, gives us a simpler, cleaner way of working with an *indefinite* number parameters. It uses the same syntax as the spread operator, which can be confusing at times, but I've recently learned how nicely they can be used hand-in-hand with one another. We can look at a similar, yet **importantly different**, example as the one used above. Since perimeter is always the sum of all sides of a geometric shape, a new perimeter function could be:
```
function perimeter(...sides) { // sides is the name for the array of measurements here
    let total = 0;
    for (let side of sides) total += side;
    return total;
}
console.log(perimeter(1, 2, 3)); // 6
console.log(perimeter(1, 2, 3, 4)); // 10
console.log(perimeter(1, 2, 3, 4, 5)); // 15
```
This is different because we don't know before calling the `perimeter` function how many sides will be measured for the shape we're given. We could be measuring a triangle, or a square, or something with many more sides, and this syntax allows us to avoid a problem with having too many arguments.
Some important (yet relatively easy) rules to remember when using this syntax:
* Other parameters can be used alongside the rest parameters, but only **one** argument is able to use the rest format. So, `function(a, ...rest)` *is* a valid format, but `function(a, ...rest, ...another)` is *not*.
* When rest parameters are used as an argument function, they must be the last argument listed. So, `function(a, ...rest)` *is* a valid format, but `function(...rest, a)` is *not*.

## Quick Clarification
These two JavaScript features, at first glance, seem like such a small thing to think of to improve code, but they actually pack a pretty large punch in terms of simplifying code to make it easier to read. And because they almost serve opposite purposes, I think it's helpful to clarify one more time before the end.
To reiterate, the spread operator lets us **spread** an iterable object across a list of arguments. The rest parameters can be used to gather the **rest** of the arguments into an iterable.

Hopefully this can help jumpstart you to a life of writing cleaner/simpler code with just three dots!

![](https://media.giphy.com/media/xUA7b6aN2u1BFnYOgE/giphy.gif)
