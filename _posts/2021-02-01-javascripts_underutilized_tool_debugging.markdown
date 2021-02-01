---
layout: post
title:      "JavaScript's Underutilized Tool: Debugging"
date:       2021-02-01 19:24:45 +0000
permalink:  javascripts_underutilized_tool_debugging
---


## Intro
Maybe I'm projecting a bit here, but I think some programmers (me) have a bit of a pride issue when it comes to finding and fixing bugs in our code. In general, my go-to method of debugging is skimming through all the lines of my code, trying to find something that looks redundant or out of place, and then using the tried-and-true `console.log()` to see a value within the console in my browser.

<img src="https://i.imgur.com/DozDcYR.png" alt="Console.log()"
	title="Console.log()" width="500" />
	*Image from [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Console/log)*

While there's nothing wrong with that, I've found that I can save a decent chunk of time on larger projects with some of these other methods I'll share today, and maybe you'll be able to debug a bit quicker on your next project.

*For reference, the shortcuts and phrasing I'll be using here assume you're using Google Chrome as your browser. Other browsers have these same features, but they may be different to navigate.*

### Debugger Keyword
Inserting the `debugger` line within a function was the first way I was taught to catch problems in my JavaScript code.
<img src="https://media.prod.mdn.mozit.cloud/attachments/2014/02/07/6963/5d7adcdf2383d094d6d2cfc8e7fa1462/Screen%20Shot%202014-02-07%20at%209.14.35%20AM.png" alt="Debugger"
	title="Debugger Keyword" width="700" />
	*Image from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/debugger)*

As you can see, inserting `debugger` on line 80 will cause the browser to pause the code running as it hits that line. Within the Sources panel of DevTools in Chrome, you'll have a ton of control to decide next steps as the code stays paused. On the left side, you'll see all files used in the broswer you've got open, which can be opened to see each line of code (which also acts as a code editor.) Also, you'll see the JavaScript debugging section where we'll (later) talk about how to step through the code. Using the `debugger` keyword is especially useful when you have a good idea of what is going wrong with your code but don't exactly know which line is causing the error.

### Breakpoints
As you've seen (and probably know already), using `console.log()` is the quick way to sort out confusion within a line of code, and inserting `debugger` is the way to find why your error is happening. This makes breakpoints the way to dig deep into your code when you've already invested a couple minutes into finding a solution but coming up short.
<img src="https://developers.google.com/web/tools/chrome-devtools/javascript/imgs/conditional-loc-breakpoint.png" alt="Breakpoints"
	title="Breakpoints" width="700" />
	*Image from [Google](https://developers.google.com/web/tools/chrome-devtools/javascript/breakpoints)*

That flag you see on line 32 in the picture can be added by just clicking on the number of the line you'd like to inspect. When the code is paused after adding a breakpoint, you have the ability to see a variable's scope, get an idea of how the call stack is ordered, and you can edit your code for its next run time. Not only that, but you can even add a breakpoint within that line to stop right before or after a function executes.

DevTools gives breakpoints so much user functionality within the Sources pane. You can activate or deactivate all of your breakpoints if you need to completely run through your code again. There's also an option to pause on a breakpoint, which is similar to what we did with debugger above, or you can pause on caught exceptions in your code on an error without blindly adding a breakpoint. Another underutilized (by me) tool in this pane is the ability to step into or out of a function while paused to incrementally run through parts of your code. To go even a step (see what I did there?) further, you have the ability to use Event Listener Breakpoints from the dropdown arrow, which let you pause on the line of any event listener that executes within your code.

### Conclusion
Okay, so there's a thin line between explaining some different debugging practices and just giving a DevTools walkthrough. Hopefully this remained on the former's side and you'll be able to experiment some more with the latter. I have found myself getting stuck in my ways by just console.log()-ing everything when it would've really been more efficient for me to step through a few lines instead. There are so many tools out there to debug that I didn't get into (like [Black Box](https://raygun.com/blog/javascript-debugging-with-black-box/) or [Watch](https://developers.google.com/web/tools/chrome-devtools/javascript/watch-variables) but maybe this will encourage you to find a good routine for your debugging and dive into it like I did.


#### References
* [Google](https://developers.google.com/web/tools/chrome-devtools/javascript)
* [Raygun](https://raygun.com/learn/javascript-debugging-tips)
* [JavaScript.info](https://javascript.info/debugging-chrome)

![](https://media.giphy.com/media/duL28c2tptZ0zAopCf/giphy.gif)
