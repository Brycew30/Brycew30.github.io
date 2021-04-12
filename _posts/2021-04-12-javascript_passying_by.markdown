---
layout: post
title:      "JavaScript Passying By"
date:       2021-04-12 19:25:42 +0000
permalink:  javascript_passying_by
---


As I've inadvertently made this blog a sort of "JavaScript for Beginners" in my deeper studying of JavaScript for myself, I realized a concept that I skipped over writing about early on that is really an important fundamental differentiation to make. I'd like to give an overview of how JavaScript assigns value to variables. This is small point that goes a really long way in writing code that's free of bugs, and this small distinction can save programmers (especially beginners) from a lot of headaches.

## Let's Start from the Beginning
JavaScript has two kinds of types: Value (Primitive) Types and Reference Types. If you've spent an hour learning JavaScript, you've already seen this. But, I learned it probably 10 times before actually understanding its significance in writing practical code.

**Primitive** Types include: String, Number, Boolean, (as of ES6) Symbol, undefined, and null <br>
**Reference** Types include: Array, Object, Function

**Why is Knowing This Significant?**<br>
Okay, we understand the difference in types stored in JavaScript. Cool, we learned that before anything else when we started studying the language. Now what? Let's look at examples of passing by value and passing by reference to see the difference in the real world.

## Primitive Values
```
let x = "Hello World";
let y = 10;
let z = y;
```
<table>
  <tr>
    <th>Variable</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>x</td>
    <td>"Hello World"</td>
  </tr>
  <tr>
    <td>y</td>
    <td>10</td>
  </tr>
	  <tr>
    <td>z</td>
    <td>10</td>
  </tr>
</table>
Here, like we've done a thousand times, we've assigned variables by putting the value we want to set right of the equal sign for its corresponding variable. Simple enough. When we add that last variable `z` into the mix, we can be comfortable assuming its value will be 10 because the value of `y` is 10. A **copy** is made of the actual value stored in `y`, so any changes to `z` will be made to this copy of `y` rather than the original value. This standard assignment is what is meant by the term "passed by value".

Let's take it a step further to solidify the difference that we'll see in just a little bit.
```
let x = "Hello World";
let y = 10;
let z = y;
z = z + 10;
```
<table>
  <tr>
    <th>Variable</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>x</td>
    <td>"Hello World"</td>
  </tr>
  <tr>
    <td>y</td>
    <td>10</td>
  </tr>
	  <tr>
    <td>z</td>
    <td>20</td>
  </tr>
</table>
We're updating our `z` variable here to add 10. When `z` is updated, why doesn't `y` change as well? This is how we can be sure we've set these variables by *value*. `z` is set to its own value of 10 when it's assigned; it's a totally separate 10 than the `y` 10. `y` and `z` point to two different values in the computer's memory, so updating the variable `z` updates the value stored in memory for `z` but has no impact at all on the `y` value in memory. When I learned this, it put this idea of a tangible thing being stored in my mind which really helped me going forward.

## Passing By Reference
Now that we've seen how a value can be stored in memory and called for a primitive value, let's see how Reference Types differ.
```
let a = "Hello World";
let b = 10;
let c = [1, 2, 3];
```
<table>
  <tr>
    <th>Variable</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>a</td>
    <td>"Hello World"</td>
  </tr>
  <tr>
    <td>b</td>
    <td>10</td>
  </tr>
	  <tr>
    <td>c</td>
    <td><001></td>
  </tr>
</table>
Now that we've assigned an array (a reference type) to the variable `c`, we're actually storing a reference to where that object is stored in memory. It's not storing `[1, 2, 3]`, but rather whatever code it uses to reference the memory storage location (I arbitrarily chose `<001>` which isn't what's used, but I think gets the point across).
Essentially what this table is saying, is we can think of this separate table as what is being referenced:
<table>
  <tr>
    <th>Address</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>001</td>
    <td>[1, 2, 3]</td>
  </tr>
</table>
This gives us a picture of how `<001>` actually represents the reference to the address `001` which has a value of `[1, 2, 3]`.

### Taking this example a step further:
To continue the example we used in the Primitive section, let's add another variable which will solidify the difference.
```
let a = "Hello World";
let b = 10;
let c = [1, 2, 3];
let d = c;
```
<table>
  <tr>
    <th>Variable</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>a</td>
    <td>"Hello World"</td>
  </tr>
  <tr>
    <td>b</td>
    <td>10</td>
  </tr>
	  <tr>
    <td>c</td>
    <td><001></td>
  </tr>
		<tr>
    <td>d</td>
    <td><001></td>
  </tr>
</table>
You'll notice right away that the reference we saw above for `c` is the same for `d`. That's because `d` now points to the **exact same** memory address (and therefore the exact same piece of memory) as `c`.

I think you can already tell where I'm going with this. This can be pretty costly in terms of opening us up to bugs. Since it points to the same piece of memory, any changes we make to `d` will consequently change `c`. The way to avoid these problems is to manually assign `d`, such as `d = [1, 2, 3];`. This creates a **new** reference in memory that is separate from the `c` variable, and now we can change `d` as much as possible without changing any other variables.

Hopefully this helps you prevent some errors in your programming from here on out. Thanks for reading!

#### References:
* I really like how **Programming With Mosh** describes things, so maybe you'll find [this](https://www.youtube.com/watch?v=fD0t_DKREbE) video as helpful as I did.
* There's also [this](https://www.educative.io/courses/step-up-your-js-a-comprehensive-guide-to-intermediate-javascript/7nAZrnYW9rG) intermediate teaching from Educative.io that goes into quite a bit more depth than I did today.

![](https://media.giphy.com/media/zZs5mIUOmW7eM/giphy.gif)


