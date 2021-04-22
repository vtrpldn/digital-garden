---
title: 3 Cool CSS Tricks to Impress Your Friends at Parties
date: 2020-06-23
tags:
  - codenewbie
  - css
  - tricks
layout: post
---

_This article was [originally published](https://dev.to/vtrpldn/3-cool-css-tricks-to-impress-your-friends-at-parties-k19) in the DEV Community._

---

Wait, no one does that...

But the tricks are still great, _I swear_. So let's start with an intro:

My experience with CSS along all those years has been both rewarding and very frustrating at times. But one thing that helped me implement polished, elegant interfaces was collecting and most important, remembering to use some very specific tricks for very specific solutions.

I mean, I couldn't emphasize more the importance of understanding how CSS works and how essential it is to master the basics, but it is just so rewarding when you help someone struggling with CSS with a quick "oh, why don't you try this trick?".

And with that in mind, here are some of my favorite CSS party tricks. I hope that they serve you well on your front-end journey!

## Pseudo-element overlay

Overlays are a super useful solution that many designers use to handle hover states and improve legibility of text over image. And one super easy way to implement a flexible, predictable overlay is by using a pseudo-element.

As you might know, we can use pseudo-elements to extend the behavior of an element in manners that otherwise would only be possible by adding another element inside it.

And that can be, like, super cool. Check out the examples below, each one represents a common UI problem that a well implemented overlay can help.

{% codepen "OJMmMvR" "default-tab=css,result" %}

Next trick!

## Responsive aspect ratio

You may know the pain, making iframes, videos or embeds responsive is not as easy as it seems.

One thing that responsive CSS does great is making the width of an element respond to the browser's width, a simple `max-width: 100%;` is pretty much all you need in order to make an element squish horizontally so it stops overflowing out of the screen.

But if you also need to make the height of said div react to the browser's width, the answer isn't as obvious. And this problem is particularly visible in the situation below:

{% codepen "ExPmKyq" "default-tab=css,result" %}

This trick works because when you use percentage on `padding` it is always relative to the parent width. So a `padding-bottom: 75%;` would give you a 4:3 aspect ratio and a `padding-bottom: %56.25;` gives you the classic 16:9 widescreen.

Neat! Next one please.

## Quick, no JS, show on click

This one is a rather popular trick for when you need to add some basic functionality but can't or don't want to mess with JavaScript. And it uses so many different details of CSS and HTML that it becomes an actually beautiful hack.

Here, have a look a the CSS and HTML tabs:

{% codepen "QWyvNOZ" "default-tab=css,result" %}

**Why it works?**

1. :checked pseudo-class selector targets our checkbox when it is checked, much like :hover would if a cursor was over it
2. the + combinator targets the immediate element right
   after our checkbox
3. The label element, by using the attribute `for=''`, acts as an alternative way to check the checkbox. We use it so we add text and style the "button"

## Final words

You know, it may depend a little on what kinds of (nerdy) parties you go to but these tricks may actually impress your friends!

But if they don't, I hope that they are useful and can make your work easier, so you are able to expend your energy on other stuff.

Comments and feedback are super welcome!

## Thanks

Cover photo by [Drew Farwell](https://unsplash.com/@outdoor_junkiez) on Unsplash

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
