---
layout: post
title:      "Pratice Coding Challenge: Create an Object with a string's letter count"
date:       2020-12-14 19:31:07 +0000
permalink:  pratice_coding_challenge_create_an_object_with_a_strings_letter_count
---


### Overview
I recently completed a practice JavaScript coding challenge with this problem: "Return an object containing each letter of a passed in string as a key and its number of occurances as the corresponding value." For example: the function `countLetters("Hello World")` should return {H: 1, e: 1, l: 3, o: 2, " ": 1, W: 1, r: 1, d: 1} because there are 3 occurances of the letter l, 2 of the letter o, and 1 of every other letter in the string.

### How I went about it
My thinking here was to split the string into individual characters in an array. Next I'd create an empty object that will eventually contain the letters. Then I'd create a for loop to iterate through the array, where I'm looking for if a key of a letter exists, and increase the value by 1 if it does, or create the key of that letter and set it equal to 1 if it doesn't already exist. That way the next loop will see that a key for that letter already exists and increase it rather than starting at a value of 1 again. *Side note: why does it feel like every code challenge requires a for loop?* Anyway, this plan gave me the overall idea of what I was going for. The question didn't ask me to remove any spaces or punctuation, so I didn't mind that those also received a key within my object. After trying a few different strings, I discovered one thing I hadn't thought about, which was capitalized letters. Thankfully this is easily solved with the `toLowerCase()` method. It may not be the perfect answer, but I think I'm now at a place where my solution returns what I need it to.

### My solution
```
function countLetters(str) {
    let lowerCaseString = str.toLowerCase();
    let letterArray = lowerCaseString.split("");
    let charCount = {};
    for (let i = 0; i < letterArray.length; i++) {
        if (charCount[letterArray[i]]) {
            charCount[letterArray[i]]++;
        } else {
            charCount[letterArray[i]] = 1;
        }
    }
    return charCount;
}
```

### Alternative solutions
After completing this challenge with what I thought to be a pretty decent solution, I went to [StackOverflow](https://stackoverflow.com/questions/18619785/counting-frequency-of-characters-in-a-string-using-javascript) to see someone else's perspective of how to solve the problem. I liked this link, because it gives us 3 similar but unique approaches to get the same answer.
* In the most upvoted answer, user [Jonathan Crowe](https://stackoverflow.com/users/1907093/jonathan-crowe) used the `charAt()` method, which also helped make their if/else statement a little nicer to read.
* In the next answer, user [russiansummer](https://stackoverflow.com/users/5813940/russiansummer) used the `reduce()` method on the split string and then the ternary operator to confirm whether the character had been added to the object yet or not.
* Lastly, user [sarunast](https://stackoverflow.com/users/2224366/sarunast) used the `forEach()` method on the split string and also used the ternary operator, which reduced the lines of code needed in each of our other attempts.

### Conclusion
Thanks for reading along with my outpouring of this JavaScript challenge! I enjoyed this post, because I like seeing how other people attempt to solve the same problem as me to see what I can improve on. I plan to add more of these as I come across new coding challenges in my practicing.

![](https://media.giphy.com/media/TIj1RfKYi82f4yrjSq/giphy.gif)
