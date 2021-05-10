---
layout: post
title:      "Making the Transition from Vanilla JS to React"
date:       2021-05-10 15:57:54 +0000
permalink:  making_the_transition_from_vanilla_js_to_react
---


I think we're at the point in this blog series with a significant amount of base vanilla JavaScript knowledge to get us started using [React.js](https://reactjs.org/). React is a library ([not a framework](https://www.freecodecamp.org/news/is-react-a-library-or-a-framework/)) that uses JavaScript to build powerful web applications. It has quickly become one of top ways of using JavaScript to build easily scalable sites.

We'll get into more of the ins and outs of React in a couple weeks, so be sure to be on the lookout for that. For now, I want to talk about important JavaScript topics to be very familiar with as you transition to building with React. Of course it's good to be an expert in a language before diving deeper into libraries and frameworks, but hopefully this can be a good guide to knowing where to start.

I've written about many of these topics in pervious blogs, so be sure to check those out, as well as the resources I've linked in them.

### Arrow Functions
There are going to be several [ES6](https://github.com/lukehoban/es6features) features in this list, so it's always a good idea to be very comfortable with latest best practices. React [Hooks](https://reactjs.org/docs/hooks-intro.html) help us deal with `this` a lot better than before. But arrow functions don't redefinte the value of `this`, so they help us keep track of `this` much better within our component's `render` method with fewer bugs.

### Template Literals
This is one of the first things I learned in JavaScript after transitioning from learning Ruby, but I never knew how often I'd use them as I learned to build React apps. Defined by inserting backticks, template literals allow us easy interpolation with expressions.
```
import React from 'react';
import ReactDOM from 'react-dom';

const firstName = John;
const lastName = Smith;

ReactDOM.render(
    <>
        <h1>{`Hi, my name is ${firstName} ${lastName}.`}</h1>
    </>
);
```

With our main purpose for building a React app to be flexibility and scalability, template literals allow us to quickly change small pieces of code without affecting the whole page.

### Rest and Spread
Knowing when to use `...` to handle values will give you a huge jumpstart in your journey to learning React. Props and state are blogs for a different day, as this is just to even get started using React, but one of the most common uses for spread (that I have found) is using it for `setState()`. In this example, we want to update our list array with a new list while keeping the lists it already contains:
```
addList(newList) {
    this.setState( { todoLists: [...this.state.todoLists, newList] } )
}
```

### Ternary Operator
The simple `:` syntax is useful for simplifying `if else` statements in Vanilla JavaScript, but I think it becomes an overpowered tool when used in React. Here's one small example of how useful it is to determine what you want to render:
```
// ...
<button onClick={ someCondition ? this.handleEdit : this.handleSubmit } >{someCondition ? 'Edit' : 'Submit'}</button>
```
Here, if some condition is met, one button appears. But if that condition isn't met, a completely different button is rendered. You can see just how often you'll use this in web applications from this one small example.

## Wrapping Up
Like I said, this is just a starting point to our introduction into using React.js.  Of course there is more to React than these four or five JavaScript topics, but knowing these topics fairly well will help get you off the ground much quicker while learning to use the library. Hopefully this was helpful for you, and be sure to check back as I write more introductions to using React!

![](https://media.giphy.com/media/fwbZnTftCXVocKzfxR/giphy.gif)
