---
layout: post
title:      "Practice Coding Challenge: Domain Name"
date:       2021-05-17 02:11:04 +0000
permalink:  practice_coding_challenge_domain_name
---


Today, I came across an older challenge on [Codewars.com](https://www.codewars.com/) that I felt deserved some blog time. It's a smaller coding challenge, and you'll see from the given directions that it's extremely straightforward. I like to write about challenges that I think really translate well into real world coding projects, and this one fits the bill exactly.

### Extract the Domain Name from a URL
[This](https://www.codewars.com/kata/514a024011ea4fb54200004b) is the challenge I completed today that sparked the idea for this post. As the name says, the challenge is to take a URL of some length and return only the domain name. This struck me as an extremely useful practice challenge that has all sorts of uses like different forms of web scraping. Let's break it down. Here's the challenge description:

**-----AS ALWAYS, DON'T JUST READ ON FOR THE SOLUTION. TRY IT FOR YOURSELF BEFORE READING FURTHER!-----**

>Write a function that when given a URL as a string, parses out just the domain name and returns it as a string. For example:
>
>domainName("http://github.com/carbonfive/raygun") == "github" 
>
>domainName("http://www.zombie-bites.com") == "zombie-bites"
>
>domainName("https://www.cnet.com") == "cnet"
>

Pretty limited directions, yet also plenty for us to work with. When I'm writing out my thought process with coding challenges, I generally try to stay away from using [Regular Expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) because they're confusing to write and even more confusing to try to explain (at least, to me.) This was one of those instances where using some RegEx really significantly reduced the amount of code to write. Here goes:
```
function domainName(url){
    let modifiedUrl = url.replace('http://','')
		.replace('https://','')
		.replace('www.','')
		.split(/[/?#]/)[0];
    let onlyDomainName = modifiedUrl.split(".")[0];
    return onlyDomainName;
}
```
Right off the bat, we've used [.replace()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace) and [.split()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split) before- they're both helpful string methods that each do exactly as their names imply. To break this down:
* `modifiedUrl` removes the "http://" prefix if there is one
*  `modifiedUrl` then removes the "https://" prefix if there is one
*   `modifiedUrl` then removes the "www." prefix if there is one
*    `modifiedUrl` uses [RegEx](https://regexr.com/) to help split the URL at any /, ?, or # that might trail the [top-level domain](https://en.wikipedia.org/wiki/Top-level_domain) (.com, .org, .edu, etc.) and stores the string at the zero-index location of the array
*    `onlyDomainName` removes the top-level domain from the end and stores only the string in the zero-index location of the array
*    then the domain name is returned!


### Conclusion
Like I said, this is a really straightforward coding challenge. I think it gives us some practice in a wider array of areas, with RegEx, string methods, and array indexing all being used. Hopefully this is a helpful way to brush up on things you would've already learned a little bit about if you've read some of my other practice coding challenges.

Thanks for reading!

![](https://media.giphy.com/media/5zsi2v0SD5wmo3fiQC/giphy.gif)
