---
layout: post
title:      "Learning Async/Await"
date:       2020-12-21 16:13:09 +0000
permalink:  learning_async_await
---

### Intro
While I'm in the midst of searching for jobs, I'm also trying to work hard at learning more JavaScript topics I currently have a surface level understanding of. Maybe I have enough of an understanding to have used it in a project before (or maybe not), or maybe it's something I'm learning so I *can* use it in a project sometime soon. Today, I wanted to study, and explain, Async/Await.

### What is Async/Await?
These two keywords, usually found together when being explained (because they're used together in code), were introduced in ES2017. In short, they give us a simpler way to handle [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise). Historically, developers could avoid callback hell with promises and a few `then`s to help resolve or reject them. `Async` and `Await` were created to help simplify these processes even more. `Async` is a keyword for the function declaration that returns a promise, and `await` is used within the `async` function to help handle the promise.

### Why use them?
One of the benefits you'll notice shortly after using `async` and `await` for asynchronous tasks, is that your code will be less cluttered and more precise. It's not a far reach to translate from using `then` and `catch`, but there's more readability because your code will be more clear from top to bottom.

### Example
It's often hard to clearly type out enough words to explain one preference over another in code, so let's show why this new implementation is useful.
```
async function fetchInformation() {
     let information = await fetch('/');
     let text = await information.text();
     console.log(text);
     return text;
}
let promise = fetchInformation().then(...);
```

### Walkthrough
Let's understand what's happening here together. First, the function `async` is declared, which allows `await` to be used from within the block. The `await` keyword is followed by a promise-producing action, (which the `fetch` API is.) The asynchronous `fetch` procedure runs and execution of further code halts (not blocks) until the asynchronous action finishes. Then the function resolves with the `return` value and a promise is returned. In writing this doesn't sound like much of a win compared to using `then`s, but notice how there's no need for so many callbacks! One good way to handle rejection with `catch` is to use the `try` and `catch` pair together.
##### The Old Way:
```
fetch('/something.json')
     .then(response => response.json())
     .then(json => {
          console.log(json);
     })
     .catch(error => {console.log('error!');})
```
##### The New Way:
```
async function fetchJson() {
     try {
          let response = await fetch('/something.json');
          let json = await response.json();
					console.log(json);
     }
     catch(error) {
          console.log('Error!', error);
     }
}
```

### Conclusion
Thanks so much to [this](https://www.youtube.com/watch?v=vn3tm0quoqE) video and [these](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) docs for great explanations of a still relatively new pair of keywords. Hopefully this will encourage you to explore `async` and `await` a little bit for your next project!

![](https://media.giphy.com/media/eeL8EcBBTwSMLACw6F/giphy.gif)



