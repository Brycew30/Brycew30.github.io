---
layout: post
title:      "Practice Coding Challenge: Find The Parity Outlier"
date:       2021-03-22 15:49:52 +0000
permalink:  practice_coding_challenge_find_the_parity_outlier
---


Today I decided to go back to the early days of blogging where  I would break down how I would solve a Codewars challenge. I enjoyed [this](https://www.codewars.com/kata/5526fc09a1bbd946250002dc/train/javascript) challenge because it got me to think starting from the solution and work backward toward the beginning question. To me, this seems like one of those transferrable tasks that may look slightly different in a real world setting but the process of solving it would still be the same or similar.

## The Problem
**I like to always recommend trying the problem on your own before reading ahead. That way you can compare solutions or see what you/I did differently.**

The title of the challenge (and blog post) is Find The Parity Outlier and here's the description:

>You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.
>
>Examples
>[2, 4, 0, 100, 4, 11, 2602, 36]
>Should return: 11 (the only odd number)
>
>[160, 3, 1719, 19, 11, 13, -21]
>Should return: 160 (the only even number)

## My Solution
So, the first thing that sticks out to me is where it says "a length of at least 3, but could be very large". That tells me we need to find a solution that checks more than just the first 3 or 4 integers. Otherwise, my thinking was to just hard code the solution to check the first 3 integers, which would tell us if we were looking at an array of odd numbers with an even one slipped in there somewhere or an array of even numbers with an odd one slipped in. But, since it warns that the array could be very large, just knowing which version of the array is input would only solve part of the problem. I kind of approached this problem without putting too much into comparing time complexities, because (at least, at first) I assume I can find the solution with just one `for` loop.

Given:
```
function findOutlier(integers) {
    // Your code here
}
```
Here's the breakdown of what I did for my solution
```
function findOutlier(integers){
    // in case it's an array of odd numbers:
    let oddArray = [];
		
    // in case it's an array of even numbers:
    let evenArray = [];
		
    // we'll iterate through to determine if each integer input is even or odd
    for (let i = 0; i < integers.length; i++) {
        if (integers[i] % 2 == 0) {
            // if even, we'll push the integer into the even array
            evenArray.push(integers[i]);
						
            // if odd, we'll push the integer into the odd array
        } else {
        oddArray.push(integers[i])
        }
    }
		
    // now to solve it, I'm checking if the odd ball (not necessarily odd number) is even or odd and returning it
    if (evenArray.length == 1) {
        return evenArray.pop();
    } else {
        return oddArray.pop();
    }
}
```
Again, I strongly encourage you to solve this problem on your own to get a good grasp of how you'd approach it, but you can find some of the more common solutions from other users [here](https://www.codewars.com/kata/5526fc09a1bbd946250002dc/solutions/javascript) after you've submitted your solution.

I like finding the problems that seem like practical examles of coding that will be used in a real world setting rather than the most complex algorithms. To me, this problem has some real world uses like maybe in accounting or real estate with addresses. So, it's not terribly complex, and like I said in the beginning, I'm sure you could find a more efficient time complexity to solve this, but I like the simple challenge.

Thanks for reading!

![](https://media.giphy.com/media/tZCkL6BsL2AAo/giphy.gif)
