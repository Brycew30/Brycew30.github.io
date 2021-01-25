---
layout: post
title:      "Practice Coding Challenge: Who Likes It?"
date:       2021-01-25 21:04:02 +0000
permalink:  practice_coding_challenge_who_likes_it
---


## Intro
No, the title of this blog *is not* a snarky rhetorical question about whether you like coding challenges or not. It is the name of [this](https://www.codewars.com/kata/5266876b8f4bf2da9b000362) coding challenge on Codewars I'd like to talk through today. The gist of the challenge is to create a quasi-Faceook "like" display system. Here's the challenge written out for us:
>You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.
>
>Implement a function `likes :: [String] -> String`, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:
>
>`likes([]) # must be "no one likes this"`
>
>`likes(["Peter"]) # must be "Peter likes this"`
>
>`likes(["Jacob", "Alex"]) # must be "Jacob and Alex like this"`
>
>`likes(["Max", "John", "Mark"]) # must be "Max, John and Mark like this"`
>
>`likes(["Alex", "Jacob", "Mark", "Max"]) # must be "Alex, Jacob and 2 others like this"`
>
>For 4 or more names, the number in and 2 others simply increases.

## ** I encourage you to attempt this challenge for yourself before reading further!**
## --------------------------------------------------------------------------------

At frist glance, this is a really simple challenge with several `else if` keywords plugged in. At least that's how I went to solve this challenge when I read it. And while you still may see this as an easy challenge by the time I get to the end of the blog, you'll at least hopefully see the nuance of it and why I chose to write about it today.

## Breaking It Down
Let's start off by writing the directions down in plain English and then go from there. We know we're given an *array* called `names`. We want it to read "no one likes this" when the array is empty. We want to have it read "likes" when `names` only has one name in it, but we want it to be "like" when `names` has 2 or more names in it. Lastly, we need special formatting when `names` has 4 or more names in the array.

## My First Solution
After seeing this challenge, I first wanted to knock out a solution that was correct before trying to simplify or refactor. I remember having a similar challenge to this in the Learn curriculum. Here's what I came up with to get all the tests to pass:
```
function likes(names) {
    if (names.length === 0) {
        return 'no one likes this'
    } else if (names.length === 1) {
        return `${names[0]} likes this`
    } else if (names.length === 2) {
        return `${names[0]} and ${names[1]} like this`
    } else if (names.length === 3) {
        return `${names[0]}, ${names[1]}, and ${names[2]} like this`
    } else if (names.length > 3) {
        return `${names[0]}, ${names[1]} and ${names.length - 2} others like this`
    }
}
```
For 6 kyu this isn't a terribly time consuming challenge.

## (Slightly Better) Second Solution
There's nothing really wrong with the first solution as far as I know. But I also wanted to challenge myself a little bit more. I thought this challenge was the perfect opportunity to bust out the handy dandy [switch](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/switch) statement! This is ultimately why I decided to write about this challenge today. I've been looking for more chances to use `switch` with Vanilla JS. Here's what I came up with for my second solution:
```
function likes(names) {
    switch(names.length) {
        case 0: return 'no one likes this';
        case 1: return `${names[0]} likes this`;
        case 2: return `${names[0]} and ${names[1]} like this`;
        case 3: return `${names[0]}, ${names[1]} and ${names[2]} like this`;
        default: return `${names[0]}, ${names[1]} and ${names.length - 2} others like this`;
    }
}
```

I'll admit, I'm still at a very beginner level of understanding [Big O](https://en.wikipedia.org/wiki/Big_O_notation) and JavaScript runtimes. But from [this](https://www.oreilly.com/library/view/high-performance-javascript/9781449382308/ch04.html#:~:text=As%20it%20turns%20out%2C%20the,than%20it%20is%20for%20switch%20.) really helpful article, I was supported in my assumption that `switch` statements are overall faster than `if else` as more conditions are added.

Thanks for reading along on my journey to understand JavaScript at a deeper level!

![](https://media.giphy.com/media/d3MMG783p7VBlkEU/giphy.gif)
