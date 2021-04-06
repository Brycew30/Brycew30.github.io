---
layout: post
title:      "Another Common Interview Challenge: FizzBuzz"
date:       2021-04-06 00:49:37 +0000
permalink:  another_common_interview_challenge_fizzbuzz
---


How did I miss this? I have no idea how I've made this many blogs and somehow haven't written a post about the classic FizzBuzz challenge. </br>
For those who aren't familiar, the FizzBuzz challenge is a common programming critical thinking exercise. The premise is pretty simple:
>Write a program that prints the numbers from 1 to 100. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”.

>([This](https://imranontech.com/2007/01/24/using-fizzbuzz-to-find-developers-who-grok-coding/) writing from Imran On Tech is the earliest version of the test I was able to find, and this description comes from there.)

In general, I like to try to write posts about topics/challenges that I think carry practical functionality outside of the limitations of a coding challenge. This challenge isn't necessarily like that, in that it doesn't require any overly complex programming knowledge (a simple way is just knowing how to use a `for loop`), but it seems to be an extremely common [question](https://www.sitepoint.com/5-common-coding-interview-challenges/) to test one's knowledge of a language.

So, we can start by kind of pseudo-coding our solution and then talk about a working solution or two.
```
Step one: list numbers (n) from 1 to 100
Step two: if n / 3, log "Fizz"
Step three: if n / 5, log "Buzz"
Step four: if n / 3 and n / 5, log "FizzBuzz"
Step five: if n !/ 3 and n !/ 5, log n
```

## Transferring to Code
Now that we've laid out what the challenge is actually looking for, we can reasonably change some of that wording into a solution typed out in code. If you've been programming for a little while (you probably wouldn't have found this page in the first place), you are probably already screaming in your mind, "REMAINDER OPERATOR!!" For those unfamiliar, the remainder operator (or modulo) is represented by **%**. In JavaScript, according to [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Remainder), "the remainder operator returns the remainder left over when one operand is divided by a second operand, and always returns the sign of the dividend." With that in our toolbelt, we can simplify our code a little bit:
```
for (let n = 1; n <= 100; n++) {
    if (n % 3 === 0 && n % 5 === 0) {
        console.log("FizzBuzz");
    } else if (n % 3 === 0) {
        console.log("Fizz");
    } else if (n % 5 === 0) {
        console.log("Buzz");
    } else {
        console.log(n);
    }
}
```
This is a perfectly fine solution for the FizzBuzz challenge- It gives us exactly what we're looking for to be printed to the console!

## An Alternative Solution
A quick google search can give you dozens of ways to solve this problem. Like I said, it's not an extremely complex challenge, but I think interviewers are really wanting to see your understanding of JavaScript and also how you approach different problems you may or may not know how to solve. Here's another one I liked that only requires slightly more JavaScript knowledge/experience:
```
function fizzBuzz() {
    for (let n = 1; n <= 100; n++) {
        console.log(((n % 3 ? "" : "Fizz") + (n % 5 ? "" : "Buzz")) || n);
    }
}
```
This one looks pretty similar, but it makes great use of the [ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) and concatenates the strings if they both evaluate to true.

## Conclusion
There we have it- a good launching point for the ever-common FizzBuzz challenge! Hopefully you found these solutions helpful enough to get you started with preparing for that interview question.

![](https://media.giphy.com/media/12R2bKfxceemNq/giphy.gif)
