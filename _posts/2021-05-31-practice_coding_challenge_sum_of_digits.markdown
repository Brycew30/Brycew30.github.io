---
layout: post
title:      "Practice Coding Challenge: Sum of Digits"
date:       2021-06-01 02:09:35 +0000
permalink:  practice_coding_challenge_sum_of_digits
---


I want to start this post today with the caveat that, although really simple in idea, I really struggled with this coding challenge. So, if at any point you're thinking, "the answer to this HAS to be simpler than this, right?" well you're probably right, but I can't help you there. I'll post what I did to make the tests pass, and then I'll post an alternate solution a friend of mine sent to me that maybe will get you thinking in a different way.

Today's challenge from [Codewars.com](http://www.codewars.com/) is titled **Sum of Digits / Digital Root** (another caveat here: I didn't know what Digital Root meant before this challenge, but you can find a really nice explanation [here](https://brilliant.org/wiki/digital-root/#:~:text=The%20digital%20root%20or%20digital,single%2Ddigit%20number%20is%20reached.) from Brilliant.org, but fair warning: this might give you more hints at the solution for this problem than you may be wanting when visiting). You can find a link to this specific problem [here](https://www.codewars.com/kata/541c8630095125aba6000c00) to solve it yourself.

Here's the challenge's description:
>Digital root is the recursive sum of all the digits in a number.
>
>Given n, take the sum of the digits of n. If that value has more than one digit, continue reducing in this way until a single-digit number is produced. The input will be a non-negative integer.
>
>Examples
>    16  -->  1 + 6 = 7
>   942  -->  9 + 4 + 2 = 15  -->  1 + 5 = 6
>132189  -->  1 + 3 + 2 + 1 + 8 + 9 = 24  -->  2 + 4 = 6
>493193  -->  4 + 9 + 3 + 1 + 9 + 3 = 29  -->  2 + 9 = 11  -->  1 + 1 = 2

Let's get started!

**AS ALWAYS, SOLVE THIS PROBLEM ON YOUR OWN BEFORE READING FURTHER. THIS POST IS FOR ME TO EXPLAIN MY SOLUTION, WHICH IS MEANT TO OFFER SUPPORT/ALTERNATIVE PERSPECTIVE AND NOT JUST GIVE READERS THE ANSWER.**

## My Solution
Upon first reading the problem, my thinking first goes to: I should split the digits.

Then my new challenge is: how do I combine elements that have been split?

In comes the handy array method: [.reduce()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)!

```
function digital_root(n) {
return n.toString().length == 1 ? n :
digital_root(Number(n).toString().split('').reduce((total,current) => Number(total) + Number(current), 0))
}
```

Let's break this down:
* By checking the length of `n`, we know anything less than 10 is just going to need to return `n`, so that's taken care of with the ternary operator.
* Next (ignoring the `digital_root()` part for now) we convert `n` to a string for the purpose of splitting it by each character with the back-to-back quotation marks.
* Now .reduce() comes into use: the total (accumulator) parameter here is returning the combination of the previous total and the current number in the iteration
* All of steps two and three are recursive, which means they'll run as many times as they're able to until step one returns a length of 1, giving us the total sum of digits!

The .reduce() method isn't one I use often enough to be comfortable with, so I speant a lot of time in that linked MDN page. Overall, I like this solution and the way I was able to get to it. I'd like to offer one alternative solution that I might have gotten to with a little different thinking:

## Alternative Solution
```
function digital_root(n) {
  return (n - 1) % 9 + 1;
}
```

Okay, this one is cheating a little bit. This one takes into account some outside math theory that is pretty unrelated to being able to program a solution. This solution comes from the above linked site explaining about digital roots. Here, the remainer of the input number minus one and divided by nine with the one added back in, will always provide a number's digital root.

## Conclusion
Thanks for reading along! This challenge was simply explained, yet challenging (for me) in practice. I liked having to study the .reduce() method enough to write about it! Hopefully this gives you a jumpstart on a challenge by giving a refesher on this very helpful method.

![](https://media.giphy.com/media/26gskaXMHwQFmuXAc/giphy.gif)
