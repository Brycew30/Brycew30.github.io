---
layout: post
title:      "Practice Coding Challenge: Palindromes"
date:       2021-03-08 22:46:52 +0000
permalink:  practice_coding_challenge_palindromes
---


I wanted to continue my streak of common JavaScript coding challenges with the Palindrome challenge. A Palindrome, according to [Wikipedia](https://en.wikipedia.org/wiki/Palindrome), is:
>"a word, number, phrase, or other sequence of characters which reads the same backward as forward, such as madam or racecar."

This is pretty similar to my [blog](https://brycew30.github.io/practice_coding_challenge_eleven_plus_two_twelve_plus_one) from two weeks ago about anagrams. However, Palindromes not only have the same characters, but they also have the same order of characters- just reversed.

## Approach
As is the case with a lot of coding challenges, we probably first want to strip away any unnecessary characters and convert to lower case. It took a little time to nail down, but I liked the solution from the anagram challenge of stripping away characters using a regular expression.

I'll show a couple different ways to come to a solution for this one, plus one bonus at the end.

## My 1st Solution
My first idea for solving this challenge was to just compare a reversed string to its initial string and return true or false based on them being equal or not.
```
const isPalindrome = function(str) {
    const formattedStr = str.toLowerCase().replace(/[\W_]/g, '');
    const reversedStr = formattedStr.split('').reverse().join('');
    return reversedStr === formattedStr;
}
```
I like this one because of it's simplicity. I think this is the approach someone with zero coding experience could reason through by explanation.

## 2nd Solution
Another approach could be to iterate through the characters of the input with a `for` loop. Start by comparing the first character with the last, second to second last, etc. to check their equality. This may help with time complexity by only having to iterate through half of the input.
```
const isPalindrome = function(str) {
    const formattedStr = str.toLowerCase().replace(/[\W_]/g, '');
    for (let i = 0; i < formattedStr.length / 2; i++) {
        if (formattedStr[i] != formattedStr[formattedStr.length - 1 - i]) {
            return false;
        }
    }
    return true;
}
```
This one is less readable than the first solution, but it is probably faster due to only reading half of the input and being able to be cut off immediately when an inconsistancy is found.

## 3rd Solution
One last solution would be to convert the input (assuming it's a string here) to an array and iterate through it.
```
const isPalindrome = function(str) {
    cosnt formattedStr = str.toLowerCase().replace(/[\W_]/g, '');
    const matches = formattedStr.split('').map((s, i) => {
        return s != formattedStr[formattedStr.length - 1 - i];
    })
    return matches.some(m => !m);
}
```
This solution uses `map()` to give us a new array with true or false for each element based on if it is the same character as its counterpart from the end. At the bottom, we see the `some()` [method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some) sneak in there, which uses a function on each element of the array, which in our case, is to see if it contains false.

## Bonus Solution
A Palindrome challenge was the first time I ever tried paired-programming. It was with a member of my Flatiron School cohort named Carlos and we used Ruby to solve it. I figured I'd throw in my Ruby solution here (after the obvious one), because first solving this challenge is where a lot of my initial problem solving for it came.
```
def isPalindrome?(string)
    string.downcase == string.downcase.reverse
end
```
Ruby has that really nice feature that will give you a boolean with a method ending in a ?.
Now, the challenge we had was to do the above but without the `reverse` method.
```
def reverse_string(string)
    string_split = string.split("")
    reversed_chars = []
    string.size.times {reversed_chars << string_split.pop}
    reversed_chars.join
end

def isPalindrome(string)
    string == reverse_string(string)
end
```

### Resources
* [Regexr](https://regexr.com/)
* [This](https://www.youtube.com/watch?v=hvV48xfwZCs) YouTube video from whatsdev
* [This](https://www.freecodecamp.org/news/two-ways-to-check-for-palindromes-in-javascript-64fea8191fd7/) article from FreeCodeCamp

![](https://media.giphy.com/media/Wt6kNaMjofj1jHkF7t/giphy.gif)
