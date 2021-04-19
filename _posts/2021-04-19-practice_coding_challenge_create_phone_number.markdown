---
layout: post
title:      "Practice Coding Challenge: Create Phone Number"
date:       2021-04-19 16:03:20 +0000
permalink:  practice_coding_challenge_create_phone_number
---


I was sent a couple different coding challenges for Front End Developer jobs this week as part of my job search/interviewing process. After submitting them, I decided to check out another [Codewars](https://www.codewars.com/) challenge or two to try to stay sharp in case another professional coding challenge came my way. I saw this challenge on Codewars, and immediately I recognized some of the same wording from the challenge as I did in the two coding challenges this week. It seems (rightfully so) that finding different ways to format phone numbers is a fairly common ask in the interview process, because it's so common in the real world. There may be different ways for different companies of collecting and formatting numbers, but hopefully this is a useful starting place.

So, lets check out the challenge description from [this](https://www.codewars.com/kata/525f50e3b73515a6db000b83/train/javascript) link:
>Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.
>
>Example:
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0])
>
>// => returns "(123) 456-7890"
>
>The returned format must be correct in order to complete this challenge.
Don't forget the space after the closing parentheses!

This might be the shortest coding challenge description I've seen so far! Essentially we're transitioning the array to a string with the parentheses and hyphen included in the format.

**Once again, please give this challenge a try before reading on. It will help you not only understand my solution, but it'll help you approach challenges in the future!**

## How I Solved It
Of course, as is the case with most coding challenges I've found, we'll need to loop through the array for this challenge. I've also spent a lot of time recently studying the different array and string methods, so they're a little fresh on my mind. My solution combined these two steps in converting the array of numbers to a formatted string.
```
function createPhoneNumber(numbers){
    let formattedNumber = "(***) ***-****";
    for(let i = 0; i < numbers.length; i++) {
        formattedNumber = formattedNumber.replace('*', numbers[i]);
    }
    return formattedNumber;
}
```
There are a couple things I liked about this specific solution (after MANY iterations of it were tried). First of all, I like its readability. After finding a working solution, I like to try to think about the code itself as someone with little to no coding experience to see if the way it reads makes sense from that perspective. I think it does based on the `formattedNumber` variable at the beginning kind of setting the stage. I also like that we can totally disregard the warning that says "Don't forget the space after the closing parentheses!". By doing all of the formatting at the beginning, we don't need to worry about the correct spacing in our solution because it's already built in!

To walk us through in plain english what is happening in this solution:
* We create a variable to set our correct format from the very beginning
* We loop through the `numbers` array and **replace** each `*` with its corresponding number in the array (for example: the first number in the array goes in the first `*` spot, the 2nd number in the second `*` spot, etc.)
* Finally, we return the fully replaced, new phone number!

This challenge was the first "real world" scenario where I thought to use the .replace() method (that wasn't prompted by an assignment), and I love how simple this code turned out. Let's look at one of the other ways I tried to solve this just to see a different perspective.

### Bonus Solution
This second solution also perfectly solves the problem asked in the challenge. The reason I didn't stick with this solution for this blog post, is mainly because of its lack of readability. It's a simple answer, using widely used array methods to concatenate individual sections of the array into a string form, but it doesn't solve my first criteria above of being readable by someone with little experience in this field. If this is how you solved the challenge, there's nothing at all wrong with it, and props to you!
```
function createPhoneNumber(numbers){
  return '(' + numbers.slice(0,3).join('') + ') ' + numbers.slice(3,6).join('') + '-' + numbers.slice(6).join('');
}
```

Hopefully these solutions give you a good launching point for formatting phone numbers. I'm finding more and more situations where it's important to store phone numbers, email addresses, addresses, etc. in the correct format on the backend. In different scenarios, it may be necessary to include arrays, strings, even RegEx, etc., so it's important for us to have a working knowledge for any of these.

Thanks for reading!

![](https://media.giphy.com/media/D31WLoosoxmQo/giphy.gif)

