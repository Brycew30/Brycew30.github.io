---
layout: post
title:      "How to Use setTimeout()"
date:       2021-04-26 02:15:12 +0000
permalink:  how_to_use_settimeout
---


Today's topic is another one of those methods that I've used or mentioned in a few past blogs, that I wanted to go back and give some context to with examples. The [setTimeout()](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) method gives us the ability to delay a piece of code from being executed until a set time (ah, the name makes sense) has passed.

### How It's Written
As you'll see in the MDN docs linked above, there are a few different ways to write this function, but they all include a callback function and a delay. Today, I'll just explain what's going on in one of them:
`var timeoutID = scope.setTimeout(function[, delay, arg1, arg2, ...]);`
* We don't need to worry too much about the use of `scope` here, but just know that it's a method that generally belongs to the `window` object.
* The first argument is a function. This can be a predefined function with the variable used, or it can be an anonymous function written right in this space.
* The second argument is (possibly) a combination of the length of the delay you'd like to use and whatever arguments are needed. It's perfectly fine (and quite common) to only use the delay part of this argument. For example: `setTimeout(doSomething();, 5000);`. In this example, since the delay is written in milliseconds, would execute `doSomething()` after 5 seconds. Simple enough!

### Another Example
Don't let the simple examples of this function make you think it's not a powerful tool, because it very much is. It's just something that I think can be explained with small examples that still scale in ease of use with bigger uses. Here's another simple one to look over:
```
function greeting(word, person) {
    alert(word + ', ' + person);
}

setTimeout(greeting, 3000, "Hi", "Matt");
// Hi, Matt
```
This small (and not very useful) function will wait 3 seconds (don't forget the milliseconds conversion!) to raise an alert saying, "Hi, Matt".

### Note of Warning
I had never used this in practice, but I learned that JavaScript will try to help by creating a function if a string is given as the first argument. For example: `setTimeout("alert('Hi Matt')", 3000);`. You (hopefully) won't see this very often for a few reasons, such as being slower than writing out the function and also some security risks invovled ([this](https://stackoverflow.com/questions/6081560/is-there-ever-a-good-reason-to-pass-a-string-to-settimeout) StackOverflow post gives some great help in regards to avoiding this.) The way around this problem (and a few other problems it turns out) is to use arrow functions as the callback in the first argument.

### Arrow Functions
Arrow functions are handy for several reasons, but maybe even just looking nicer/cleaner is a good enough one. The following example has pretty clear instructions for what it's trying to do:
```
const baby = {
    sound: 'waaaaa',
		cryingComing() {
        setTimeout(
            () => {console.log(`Baby boy says ${this.sound}!`)}, 2000
        )
    }
}

baby.cryingComing();
```
Because it's all clearly laid out, we know what to expect 2 seconds after calling the `cryingComing` function on `baby`.

## Conclusion
This is a really handy asynchronous tool. You can play around with different `setTimeout()` formats to get a better idea of how to use them in real world code. For example, one of the lessons in the Flatiron curriculum showed us that even calling `setTimeout` with a 0 millisecond delay, can mix out your code output if you're not already aware of its effect. This is one of those methods that may be really handy to just spend a few minutes on YouTube to learn about. I primarily used the MDN docs linked above as my reference for this article, but you can find tons and tons of people showing specific examples of how to correctly/incorrectly use this function. Hopefully you found this one helpful!

![](https://media.giphy.com/media/cdNRMLodDJu9hKZU8u/giphy.gif)
