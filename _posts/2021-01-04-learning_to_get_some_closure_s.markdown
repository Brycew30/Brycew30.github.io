---
layout: post
title:      "Learning to get some Closure(s)"
date:       2021-01-04 22:36:43 +0000
permalink:  learning_to_get_some_closure_s
---

I'm someone who really likes to know why and how something works the way it does to get a good understanding of using it. This goes for sports, it goes for nature, and I've learned it goes for coding as well. It was one of my biggest stumbling blocks early on with Flatiron- we learned when to use different bits of code, but it never really sunk in until I took the time to understand why that code goes there and how to use it going forward. So after graduation, as I've gone back through a lot of what I learned from the top level from June to November, I'm now trying to go a level deeper in my understanding (currently in JavaScript) so I'll quickly be able to remember concepts as a whole and not just something I learned once. A word I feel like I've encountered 100 times in my reading is **closures**. Though I've seen it so many times, I don't think I could give you a specific enough definition of it that meant anything. So, let's see if this helps (both of us.)

*Disclaimer: there are a million and one blogs/videos out there to learn about closures. I'll link the sites that gave me my understanding of them, so if this blog looks like a jumbled mess by the end, I recommend you check them out.*

## What is a Closure?
Right off the bat, I quickly discovered that I had been using closures all along and didn't even know it, so hopefully this is an encouragement to anyone that fells like I did before researching it.
I've also discovered in writing this post that I'm much better at describing what a closure is than I am at defining it literally (but I'll still give a definition at the end of this section.) So let's start from the beginning. When we declare a variable, we know that it has a scope, and we (I) generally expect a local variable to leave the code's memory when it exits a block or function. A closure hangs on to local variables even after the code's execution has left the block. Any variables that were in scope when a function was first defined will still be available to use later when we call the function, even if we call the function in different context. I've heard an analogy of a closure being like a bag that holds its variables that were in scope at the time of creation, so wherever that bag goes, its variables go with it.
**Whenever a function accesses a variable that is declared outside of it, it is a closure.**



## An Example:
I learn much better by seeing than by just reading. Let's break it down.
```
function favoriteColor() {
    let color = 'blue';
    console.log(color + ' is my favorite color');
}

favoriteColor(); // Logs 'blue is my favorite color'
```
To start, we have this straightforward function that logs my favorite color, which is blue in this case. But if we want to change the color outside of the function, we should do this:
```
let color = 'blue'; // We moved the variable outside of the function

function favoriteColor() {
    console.log(color + ' is my favorite color');
}
```
Now we can change the value of color any time we want to to produce:
```
favoriteColor(); // Logs 'blue is my favorite color'
color = 'green';
favoriteColor(); // Logs 'green is my favorite color'
color = 'red'
favoriteColor(); // Logs 'red is my favorite color'
```
The takeaway here is that although our variable is defined outside of the function, it has no trouble accessing it.

```
function rainbow() {
    let color = 'blue';
    
    function favoriteColor() {
        console.log(color + ' is my favorite color');
    }
    favoriteColor();
}
rainbow()
```
Because `favoriteColor` is inside of `rainbow`, it can see all of its variables, which is why it can read the color variable.

**This is a closure!**


##### References I found helpful:
* [This](https://stackoverflow.com/questions/36636/what-is-a-closure#:~:text=Languages%20which%20support%20closure%20(such,that%20block%20or%20function%20somewhere.) StackOverflow post and many of its replies
* [This](https://medium.com/@prashantramnyc/javascript-closures-simplified-d0d23fa06ba4) post on Medium by author Prashant Ram
* [This](https://www.youtube.com/watch?v=ZVXrJ4dnUxM) video from Codesmith is awesome, but it's also about an hour long (also covering scope and execution context)- I really enjoy the way he teaches and find the hour well worth it.

![](https://media.giphy.com/media/5wWf7H89PisM6An8UAU/giphy.gif)

