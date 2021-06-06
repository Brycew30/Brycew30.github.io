---
layout: post
title:      "React First Steps"
date:       2021-06-06 23:56:36 +0000
permalink:  react_first_steps
---


Okay, now that we [know what React.js is](https://brycew30.github.io/making_the_transition_from_vanilla_js_to_react) and [how to get it up and running](https://brycew30.github.io/couch_to_5k_react_edition), let's spend today's post breaking down the pieces in front of us after using the `create-react-app` command we talked about two weeks ago. This is all going to be assuming you're following along and have the standard boiler plate file structure, so you can go ahead and create a new app if you need to. This will mostly just include what is happening at the very top level of React, because I don't think knowing exactly how every behind-the-scenes thing works is necessary to create your first simple app, and because I don't know if I feel comfortable enough myself to explain it to someone else yet.

I'm writing this out as if I'm speaking to only beginners who need the very basics to get started. If you've worked in React before, this post may not be for you (except as a refresher!)

Go ahead and navigate to the directory of your newly created project, and run `npm start` to see the changes you make in your browser in a live setting!

### App
It's often helpful (for me) to think of a React project in physical terms, such as the image of a tree. At the top point of the tree (think: angel on top of the Christmas tree), is the Root Element. For us, the Root Element is the App Component, which we know because under project folder --> src --> index.js, we see `ReactDOM.render(<App />, document.getElementById('root'))`. That 'root' element is displayed on our page via the project folder --> public --> index.html --> `<div id="root"></div>` element. Knowing more about this is an important first step in creating your project, but you don't really need to make any changes here for now. That's what Components are for.

### Components
I mentioned that Components are the magic behind React.js in my "Couch to 5k React Edition" post a couple weeks ago. Now we can talk a little bit about why that is. If our Root Element (App) is the angel on the tree, we can then build our different components of our app and think of them as subcategories (or children if you think in terms of a family tree structure.) Each different piece of the site can be a component: the navigation bar at the top, the search bar, a table, a sidebar, you name it. This is how we can make such flexible sites: because if a Component only handles one piece of responsibility, any changes to that Component will only affect it and nothing else! (and vice versa: changes made to other Components shouldn't affect this one).

### Components Broken Down
Now, if we think of one of our Components broken down into its own pieces, we can generally follow this flow:

Single Component >

A JavaScript Class >

-Component's State

-Render()

The JavaScript class encapsulates what is happening in the Component. If we're working in the NavBar Component, this class will hold our relevent information to the NavBar.

State here refers to the information we want to be displayed to anyone using the app. As this is changed, only the single Component the State belongs to needs to be updated. If we want to think about this in practical terms, let's think about a "like" button on a page that displays the number of times it has been clicked. When a person clicks "like" on the React site, only the counter changes on the page, rather than having to run all the code on the page again every time that button is pushed. Very efficient!

The Render method handles the actual display-ing on the page, such as how the page looks. This is done by writing [JSX](https://reactjs.org/docs/jsx-in-depth.html) to give style and function to our User Interface.

### Conclusion
This has just been the VERY basics of starting with your newly created React app. There's still a long way to go to adding functionality, styling, and purpose to whatever you're trying to make. So, take this and run with it and maybe one day soon you'll see a follow up post about an example project or something to follow along with (although YouTube has plenty of those already.) Thanks for reading my spew of React guidance!


### Resources:
This post comes from my experience in the Flatiron program, the [React Docs](https://reactjs.org/docs/getting-started.html), and coding along in my own example app like I've advised readers to do as well.

If you're looking for much more detailed instruction and guidance from someone who has been in this field for many years, I found [this](https://www.youtube.com/watch?v=sBws8MSXN7A) video from Traversy Media on [YouTube](https://www.youtube.com/c/TraversyMedia) (and SEVERAL other videos) really helpful when I was introduced to a new topic in the Flatiron program.
*  Looks like there's an updated version [here](https://www.youtube.com/watch?v=w7ejDZ8SWv8) that I can't recommend from experience but always find his videos helpful to me.

![](https://media.giphy.com/media/WQH7pj43rMzqFuB1xm/giphy.gif)
