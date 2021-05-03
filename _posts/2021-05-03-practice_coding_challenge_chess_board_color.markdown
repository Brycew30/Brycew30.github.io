---
layout: post
title:      "Practice Coding Challenge: Chess Board Color"
date:       2021-05-03 16:00:33 +0000
permalink:  practice_coding_challenge_chess_board_color
---


I think it's fair to say that every programmer has this thought on their way to learning to code: "How can I show this off to my friends and family?". Right? Or, just me? Anyway, sometimes I'll come across a coding challenge on [CodeWars](https://www.codewars.com/dashboard) and think "Now, this is a skill I could really show off that also has very few real world applications". This post is going to be about one of those kinds of challenges. It's called **Chess Fun #1: Chess Board Cell Color** and you can find it at [this](https://www.codewars.com/kata/5894134c8afa3618c9000146/train/javascript) link to solve it for yourself.

Here are the instructions given:
>Task
>
>Given two cells on the standard chess board, determine whether they have the same color or not.
>
>Example
>
>For cell1 = "A1" and cell2 = "C3", the output should be true.
>
>
>For cell1 = "A1" and cell2 = "H3", the output should be false.
>
>Input/Output
>
>[input] string cell1
>
>[input] string cell2
>
>[output] a boolean value
>
>true if both cells have the same color, false otherwise.
>

You can see a picture of the chessboard at the link for the challenge to get a better idea of what those cell locations mean.

**As always, please work on solving this problem on your own, and only use this as a resource after trying or as a different walkthrough perspective.**

### Breaking It Down
Okay, I'm (sort of) kidding about this challenge only being helpful to show off. We'll talk about a couple different methods by the end that have practical uses outside of chess boards.

So, the directions here are pretty straightforward (and more clear if you're able to see the chess board pictures on the website.) We need to return true/false based on if two cell colors match. Now, how do we check the square colors to be able to compare then?

### My Solution
I went with a more hardcoded answer for this challenge. I decided to list every white square in an array to have a place to check the problem against and see if they match:
```
function chessBoardCellColor(cell1, cell2) {
  const whiteCells = [ 'B1', 'D1', 'F1', 'H1', 
                       'A2', 'C2', 'E2', 'G2', 
                       'B3', 'D3', 'F3', 'H3', 
                       'A4', 'C4', 'E4', 'G4',
                       'B5', 'D5', 'F5', 'H5',
                       'A6', 'C6', 'E6', 'G6',
                       'B7', 'D7', 'F7', 'H7',
                       'A8', 'C8', 'E8', 'G8' ];
  
  return whiteCells.includes(cell1) === whiteCells.includes(cell2);

}
```
After looking at the chess board given, I just broke down every white cell into its own array so that I could easily compare two cells and know right away if it was included in the same array (color) or not. I think this solution solves a problem I like to think about in my code, in that it is easily readable by someone new or inexperienced in coding. The `.includes()` [method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) is very straightforward in that it returns `true` if true or `false` if false. Easy enough.

The problem here is that this is a long and tedious way to solve a relatively simple solution. And, because I made it so specific, this function wouldn't transfer to any other kind of problem such as expanding the board or changing the labels. This solution works for this challenge and this challenge alone, which is fine for the time being. We'll go over another solution that's a little more flexible than this one in the long run. 

### A Better Solution
One of the things I like about CodeWars is that you have the chance to see how other people solved a problem after you've submitted a working solution yourself. There's even an option to discuss solutions if you choose to do so. One thing I always have to keep in mind, though, is that seeing other people's solutions can be used as a crutch if you're not careful (same goes for this post.) But, after being able to see how some more experienced coders tackled this problem, I gave it a try without hardcoding the board like I did above. Here's where I landed:
```
function chessBoardCellColor(cell1, cell2) {
  return (cell1.charCodeAt(0) + parseInt(cell1.charAt(1))) % 2 === (cell2.charCodeAt(0) + parseInt(cell2.charAt(1))) % 2
}
```
This is probably not the most efficient way to solve this problem, but I like that I had to think my way around it a little more than I did with my first solution. Since the problem is *actually* asking if the two cells are the **same** color, and not which color they are, we can concatenate the letter associated with the input and the integer associated with it. The `.charCodeAt()` [method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charCodeAt) gives us an integer at the given index of 0, and the `.charAt()` [method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/charAt) gives us the character at the given index of 1. This one doesn't solve the problem of being readable by newer coders, but it solves a much bigger problem of being transferable, such as on a larger scale if needed.

### Wrapping Up
Hopefully this is a helpful resource for you if you're learning array and/or string methods. Every now and then, I like to get myself to solve challenges that don't necessarily have real world implications, and I had a good time with this one. Thanks for reading!

![](https://media.giphy.com/media/JuUWDI13JB0XK/giphy.gif)
