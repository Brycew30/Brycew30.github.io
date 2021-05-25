---
layout: post
title:      "Couch to 5k React Edition"
date:       2021-05-25 01:20:36 +0000
permalink:  couch_to_5k_react_edition
---

A couple weeks ago, I mentioned that I was going to explain a little bit of the transition from Vanilla JavaScript over to using React.js. In that [post](https://brycew30.github.io/making_the_transition_from_vanilla_js_to_react), I talked about some useful topics to be extra familiar with to make your life a little bit easier when learning React, such as arrow functions and the ternary operator. I called this post the Couch to 5k because it will give a little bit (plus resources) of a lot of information, and it's up to you to take it and run with it!

Now, I think it's time to dive into React.js a little bit! We previously talked a little bit about the "what" of React, so that leads us to the next question:

## Why Use React?
I think this is a logical first step in branching out to a new library/framework/language. The question, in reality, is usually: what are the strengths of using it compared to not using it/using something else. React's specialty is helping create Single Page Applications (SPAs). While you don't *need* to import the React library to create a solid SPA (I'm wincing as I type that, because my JavaScript project seemed to get more and more confusing as I added features to it), your life becomes significantly easier and more organized as you start to add more and more buttons, forms, etc for functionality.

### That's because of COMPONENTS!

[Components](https://reactjs.org/docs/components-and-props.html) are pieces of code that are able to be reused, which lets you think of parts of your code as pieces of the puzzle rather than trying to solve the whole thing in one go. That's where you'll find the magic of React, and why it became so popular so quickly after being created by Facebook. In a Vanilla JavaScript SPA, a small change in code will cause you as a developer to have to check multiple places to make sure you didn't accidentally break your app (spoiler alert: you most likely did); however, if your code is broken down into components using React, your code will most likely work the same as before due to the components' individuality. I really like [this](https://www.youtube.com/watch?v=fd2Cayhez58&ab_channel=LearnCode.academyLearnCode.academy) video from LearnCode.academy of a short and sweet explanation of components and rendering with React.

### Virtual DOM
Another really nice feature of React is the Virtual DOM, which essentially means your browser takes a screenshot of the page and compares to the updated screenshot if something is updated, and is then able to just change that one updated piece rather than have to refresh the whole page. The biggest win here comes in performance as your SPA grows in size.

### Support
A lesser talked about feature for React (in my experience) is that its [huge popularity](https://insights.stackoverflow.com/survey/2020#technology-most-loved-dreaded-and-wanted-web-frameworks-loved2) has given users tons of space to ask questions and get help. As someone starting to learn React in 2020/2021, I've really benefited from all of the answers to questions before me that I have needed help with that someone else ran into as well.

## How?
### JSX
React utilizes [JSX](https://www.w3schools.com/react/react_jsx.asp), which converts HTML tags into React elements. It makes `const greeting = <h1>Hello World</h1>` into usable code by compiling.

### Create-React-App
Now that we've learned a little bit about React as a library, it's time to get your SPA up and running. With the help of [Node](https://nodejs.org/en/), just type:
```
npx create-react-app app-name
cd app-name
npm start
```
[Create-React-App.dev](https://create-react-app.dev/docs/getting-started/) allowed me to copy over this really helpful outline of the file structure generated with this command:
my-app
```
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    ├── serviceWorker.js
    └── setupTests.js
```
And now you already have a working SPA! This will specifically give you a working frontend for your application to use with a backend if you'd like.

Now all that's left is creating an app (or 20) and playing around with JSX, components, and all of the other gifts React presents to take all that Vanilla JavaScript knowledge we've practiced over the last several weeks and get really creative with it!

![](https://media.giphy.com/media/celii7i9UMbW1uG41B/giphy.gif)
