---
layout: post
title:      "Practice Coding Challenge: Fibonacci Sequence"
date:       2021-02-08 20:27:31 +0000
permalink:  practice_coding_challenge_fibonacci_sequence
---


For this blog, I wanted to take a break from only solving CodeWars challenges for one of the more popular JavaScript interview questions. It seems like I've seen this challenge on [every](https://medium.com/@sojibrahmatuzzaman/10-common-javascript-interview-challenges-f2547db5370b) [single](https://www.sitepoint.com/5-common-coding-interview-challenges/) [blog](https://www.interviewcake.com/javascript-interview-questions) I've read preparing to take JavaScript interviews. It wasn't until I started preparing for this blog that I really understood why it's so common. It's not because it's a particularly challenging problem ([this](https://medium.com/developers-writing/fibonacci-sequence-algorithm-in-javascript-b253dc7e320e) author solves the problem with 2 lines of code.) I believe this question is more about being familiar with the question and being able to explain your solution than it is about how much JavaScript you know.

## What is the Fibonacci Sequence?
Although the name sounds a little intimidating, the Fibonacci Sequence is just a series of numbers made up by adding the two previous numbers together. So in written numbers, it essentially just looks like 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, etc... Also known as the Golden Ratio, you can read more about the history and significance of it [here](https://en.wikipedia.org/wiki/Fibonacci_number), because I think it gets pretty interesting how it appears in different forms in [nature](https://www.mathsisfun.com/numbers/nature-golden-ratio-fibonacci.html). You'll likely see this image in one form or another while reasearching this topic, because it graphically shows why it's significant.
![](https://upload.wikimedia.org/wikipedia/commons/2/2e/FibonacciSpiral.svg)
*Image from [Wikipedia](https://en.wikipedia.org/wiki/Fibonaccinumber)*

## Coding the Fibonacci Sequence
I'm not exactly trying to show you the best solution to solve the Fibonacci Sequence in this blog, because you can find tons of great solutions with a quick Google search. I'm more aiming to bring awareness to the question from my own studying, as well as maybe talk through some of the solutions I've tried/seen. 

**Write a function to return an n element of the Fibonacci Sequence.**

Starting out, we know we want to turn F<sub>n</sub> = F<sub>n - 1</sub> + F<sub>n - 2</sub> into a function.

#### For Loop Solution
```
function fibonacci(n) {
    let startingArray = [0,1];
    for (let i = 2; i < n +1; i++) {
        startingArray.push(startingArray[i - 1] + startingArray[i - 2])
    }
    return startingArray[n]
}
```
This solution sets the beginning up for you so that you don't have to make your for loop more complext to account for 0 and 1. The loop starts at 2 and adds numbers to the startingArray as it iterates through until the length of the array is n + 1.

#### While Loop Solution
```
function fibonacci(n) {
    let num1 = 1;
    let num2 = 0;
    let next;
    while (n >= 0) {
        next = num1;
        num1 = num1 + num2;
        num2 = next;
        n--;
    }
    return num2;
}
```
This one is similar but iterates in a different way, where we calculate the next number by adding the current number to the previous one.

#### Recursive Solution
```
function fibonacci(n) {
    if (n <= 1) {
        return 1;
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}
```
This solution starts off by having a fallback plan if n is less than 1 and then simple addition. The problem with this solution is that the higher number you provide as the argument, the time it takes to solve becomes exponentially greater.

#### Memoization Solution
```
function fibonacci(n, mem) {
    mem = mem || {};
    if (mem[n]) {
        return mem[n];
    }
    if (n <= 1) {
        return 1;
    }
    return mem[n] = fibonacci(n - 1, mem) + fibonacci(n - 2, mem);
}
```
[Memoization](https://en.wikipedia.org/wiki/Memoization) is a technique that attempts to increase a function's performance by caching its previously computed results. We're storing the value of each index in a hash to really decrease the time the function takes to run.

## Conclusion
Hopefully this was an informative take on different Fibonacci Sequence solutions. They've become somewhat common in my studying, so I enjoyed doing a little bit of research for this one. I hope this gives you a good launching point to learn more about the pros and cons of each of these solutions in case you come across this problem in a challenge or an interview.

![](https://media.giphy.com/media/xT9Igg1Kq1xmy7123m/giphy.gif)
