---
layout: post
title:      "Practice Coding Challenge: Highest and Lowest"
date:       2021-01-11 20:14:23 +0000
permalink:  practice_coding_challenge_highest_and_lowest
---


## Welcome Back
If you're new around here, I'm posting some of the practice coding challenges I try. They might not be the hardest or most complex ones you've seen, but I like to post the ones that I think carry over some practical use in real coding environments. Lately, I've been trying to get a few challenges in on Codewars, so that's where [this](https://www.codewars.com/kata/554b4ac871d6813a03000035/train/javascript) next challenge comes from as well. This is a challenge in which I'm sure there are so many ways to approach and solve it, so let's see if how I solved it compares to how you would try it.

#### ***I highly suggest you try this challenge on your own before reading further. It can make for a good problem solving opportunity, and you can let me know what you did differently***

## The Problem
>In this little assignment you are given a string of space separated numbers, and have to return the highest and lowest >number.
>
>Example:
>
>`highAndLow("1 2 3 4 5");  // return "5 1"`
>
>`highAndLow("1 2 -3 4 5"); // return "5 -3"`
>
>`highAndLow("1 9 3 4 -5"); // return "9 -5"`
>
>Notes:
>
* >All numbers are valid Int32, no need to validate them.
* >There will always be at least one number in the input string.
* >Output string must be two numbers separated by a single space, and highest number is first.

## My Approach
So, starting out, I appreciate that this challenge has some pretty clear directions, which isn't always the case in coding challenges. I have a string of (valid!) numbers separated by spaces- that's a really nice hint that I can split the string up at the spaces to give me an array of individual numbers. My first way of thinking of a solution was to compare each element against the next and put the higher one in a separate array, but the code started to be a bit clunky. I also noticed that the three examples given have 5 numbers in them, but the directions only say there will be at least one number and I wanted my solution to be applicable regardless of the length of the string.

## My Solution
```
function highAndLow(numbers) {
  let splitArray = numbers.split(" ");
  let sortedNumbers = splitArray.sort(function (a, b) {
    return Number(a) - Number(b);
  });
  return sortedNumbers[sortedNumbers.length - 1] + " " + sortedNumbers[0];
}
```
**Breaking it down:**

Like I said above, the descrption was nice to us (this time) and said the numbers are all separated by a space. That's where the `.split(" ");` comes from. Now our splitArray contains an array of each number, but as a string (we'll come back to this point), from our original input string. Next, we can sort the contents of the splitArray with the `.sort()` method. As you can read [here](https://www.w3schools.com/jsref/jsref_sort.asp), this method would give us an error as it, because it is sorting our numbers as strings (as the example the website gives: "25" would be larger than "100" because 2 is larger than 1.) The solution for this is to provide the sort method with a compare function, which is where you'll see `Number(a)` and `Number(b)` being converted and sorted. Lastly, we return the two numbers as the problem asks for with the largest number first, a space, and then the smallest number. The format for this line is this way because the sorted array starts with the lowest number and increases ascendingly (is that even a word?) until the last element which is the largest number.

## Conclusion
Like I said, this isn't nearly the hardest coding challenge we could walk through; however, it *is* worth 7kyu on Codewars for whatever that's worth. I enjoyed reading up a little bit more on the `sort` method, and I think it's a very practical tool to have on hand when dealing with arrays in the real world. Thanks for following along with my processing for this challenge. I'd love to hear about how other people solved it!

![](https://media.giphy.com/media/QEIC6GZIEGStO/giphy.gif)
