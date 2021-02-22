---
layout: post
title:      "Practice Coding Challenge: eleven plus two = twelve plus one"
date:       2021-02-22 20:13:36 +0000
permalink:  practice_coding_challenge_eleven_plus_two_twelve_plus_one
---


Sorry. That title is the best joke I could [find](https://www.funny-jokes.com/funny-anagrams.htm). For those of you not familiar with the cryptic title's meaning, today I'm going to go over another classic interview challenge: the anagram. An anagram is a word or phrase that is created from a different arrangment of the same letters. Some [examples](https://examples.yourdictionary.com/anagram-examples.html) to clear the definition up a bit further: arc = car, state = taste, listen = silent, etc.

Well, it's also a common JavaScript (and other languages, I'm sure) interview question to test your ability to manipulate strings. I'll break this one down into detailed steps, because it's important to know how it works, yet once we come to a solution, it's pretty easy to read.

## Solution Reasoning
First, if given two strings, we'll need to compare each letter in each string for a) which letters are present in each and b) how many of each present letter are there. This is starting to look very similar to a [previous](https://brycew30.github.io/pratice_coding_challenge_create_an_object_with_a_strings_letter_count) blog I wrote about tracking letter occurances in a string by storing them in an object literal.

Some people like to attack the problem where they first come up with a working solution and then work around any edge cases that might trip their solution up. I'm going to work from the opposite end today, where I list the edge cases I can think of, and work them into the solution as I'm coming up with it. Some edge cases I can think of:
* we'll need to change all letters to lower case before comparing them
* we need to account for characters that aren't letters, such as spaces and punctuation

## Solution
There are a few different approaches we could take, so I'll show a couple different versions.
### Sorting method
This is a pretty efficient answer where we arrange each string's letters alphabetically and compare them with each other.
```
function anagram(firstString, secondString) {
    // edge cases: remove any non-letter characters with regex and change both strings to lower case
    firstString = firstString.replace(/[^\w]/g, "").toLowerCase();
    secondString = secondString.replace(/[^\w]/g, "").toLowerCase();
    
    // returns true or false based on if the sorted letters are the same
    return sortedString(firstString) === sortedString(secondString);
}

function sortedString(str) {
    // splits the string into characters, sorts them alphabetically, and joins them back together
    return str.split('').sort().join('');
}
```
### Splice method
This solution converts `secondString` to an array, loop through to check if each character from `firstString` exists in the array of `secondString`, and use `.splice()` to remove it from the array if it does.
```
function anagram(firstString, secondString) {
    firstString = firstString.replace(/[^\w]/g, "").toLowerCase();
    secondString = secondString.replace(/[^\w]/g, "").toLowerCase();
    
    // start by making sure the strings are the same length
    if (firstString.length !== secondString.length) {
        return false;
    }
    
    let arr = secondString.split("");
    for (let letter of firstString) {
        if (!arr.includes(letter)) {
            return false
            break;
        } else {
            arr.splice(arr.indexOf(letter), 1);
        }
    }
    return true;
}
```
### Character Map method
This solution checks if the character already exists as a property in `charMap`, increments it if it does, or adds it as a property with a value of 1 if it doesn't. This is the approach similar to my previous blog linked above. This one will have a little bit of a longer run time than the previous two due to its nested function and multiple loops.
```
function anagram(firstString, secondString) {
    function characterMap(str) {
        let charMap = {};
        for (let char of str) {
            if (charMap.hasOwnProperty(char)) {
                charMap[char]++
            } else {
                charMap[char] = 1
            }
        }
    return charMap;
    }
    if (firstString.length === secondString.length) {
        let firstMap = characterMap(firstString);
        let secondMap = characterMap(secondString);
        for (let char in firstMap) {
            if (firstMap[char] !== secondMap[char]) {
                return false;
            }
        }
        return true;
    } else {
        return false;
    }
}
```

## Conclusion
There we have it! Three different ways of determining if two provided strings are anagrams. Hopefully this was helpful as you prepare for an interview or study JavaScript. Here are a couple sites I found helpful in writing this:
* [Regexr](https://regexr.com/)
* [w3resource](https://www.w3resource.com/javascript-exercises/fundamental/javascript-fundamental-exercise-206.php)
* [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)

![](https://media.giphy.com/media/McD7VzBio1126ShL0l/giphy.gif)

