---
layout: post
title:      "Practice Coding Challenge: Dubstep Decoder"
date:       2020-12-28 18:35:27 +0000
permalink:  practice_coding_challenge_dubstep_decoder
---


## Intro
If you read my [blog](https://brycew30.github.io/pratice_coding_challenge_create_an_object_with_a_strings_letter_count) a couple weeks ago or the [one](https://brycew30.github.io/learning_async_await) from last week, you'll know that I'm currently working on building upon my Vanilla JavaScript foundation with lessons and coding challenges. Sometimes this looks like researching different JS methods I may be less familiar with, and sometimes it may be me working through some challenges on [HackerRank](https://www.hackerrank.com), [Codewars](https://www.codewars.com), etc. I've found that the difficulty of the challenges (for me, at least) doesn't always match up with the reward system for each site, so I like to bounce around to different levels to see what I can do. I liked this challenge enough to post about it today, because a) I thought it used pretty practical skills to have brushed up on as a programmer, and b) I thought the story scenario was pretty fun/funny.

## The Problem
You can find this challenge [here](https://www.codewars.com/kata/dubstep/javascript) if you're interested in solving it for yourself before seeing how I did it. I recommend it! It's a relatively short challenge overall. Okay, here's the scenario from Codewars:

>Polycarpus works as a DJ in the best Berland nightclub, and he often uses dubstep music in his performance. Recently, >he has decided to take a couple of old songs and make dubstep remixes from them.
>
>Let's assume that a song consists of some number of words (that don't contain WUB). To make the dubstep remix of this >song, Polycarpus inserts a certain number of words "WUB" before the first word of the song (the number may be zero), >after the last word (the number may be zero), and between words (at least one between any pair of neighbouring words), >and then the boy glues together all the words, including "WUB", in one string and plays the song at the club.
>
>For example, a song with words "I AM X" can transform into a dubstep remix as "WUBWUBIWUBAMWUBWUBX" and >cannot transform into "WUBWUBIAMWUBX".
>
>Recently, Jonny has heard Polycarpus's new dubstep track, but since he isn't into modern music, he decided to find out >what was the initial song that Polycarpus remixed. Help Jonny restore the original song.
>
>Input
>The input consists of a single non-empty string, consisting only of uppercase English letters, the string's length doesn't >exceed 200 characters
>
>Output
>Return the words of the initial song that Polycarpus used to make a dubsteb remix. Separate the words with a space.
>
>Examples
>songDecoder("WUBWEWUBAREWUBWUBTHEWUBCHAMPIONSWUBMYWUBFRIENDWUB")
>  // =>  WE ARE THE CHAMPIONS MY FRIEND

## Plan of Action
To be honest, I had to read through this description 3 times to get a good understanding of what it's asking me to do. Here is ultimately what it's asking us to find: Remove the **"WUB"**  from the song lyrics given, but maintain spaces between words in the lyrics. My pseudocode version of the solution looks like:
```
songDecoder(songLyrics) {
    replace "WUB" with " "
}
```

## My Solution
In the end, my actual code didn't look much different from the pseudocode (hence a good reason to start there!) My thought process went like this:
1. Split the string at the "WUB" into an array
2. Remove the empty strings from the array
3. Join the words from the array to a new string of song lyrics
```
function songDecoder(songLyrics) {
    return (
        songLyrics
            .split("WUB") //Step 1: Split the string at the "WUB" into an array
            .filter(Boolean) // Step 2: Remove the empty strings from the array
            .join(" ") //Step 3: Join the words from the array to a new string of song lyrics
    )
}
```

Overall, this solution is mostly pretty straight forward. The new thing I learned with this was that `.filter(Boolean)` step. I'll try my best to explain my understanding of it, but definitely check out [this](http://www.devign.me/javascript-tip-remove-falsy-items-out-of-an-array) post on Devign.me for a very thorough explaination (like I did.) An addition in ES5, the filter method here removes all falsy values (false, null, undefined, 0, NaN, and empty string) from an array. I used this to remove the empty strings from my array of split words, which then let us join them together with a space in between.

## Conclusion
Like I said in the beginning, this is a relatively straight forward challenge. Ultimately, the difficulty comes down to deciphering what all the words are really asking you to do. Had I used Google, I would've found an even more straight forward [answer](https://medium.com/@czaneg/you-dont-need-code-to-be-a-programmer-cde7cd484ae2) of `song.replace(/(WUB)+/g, " ").trim()` before thinking through the challenge step by step the way I did above. Thanks again for reading! I plan on continuing this theme of alternating writing a coding challenge I've worked through with what JavaScript topic I'm currently working on, so be on the lookout for that later.

![](https://media.giphy.com/media/KctrWMQ7u9D2du0YmD/giphy.gif)
