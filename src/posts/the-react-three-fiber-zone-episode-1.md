---
title: The react-three-fiber Zone, Episode 1
date: 2020-08-05
tags:
  - css
  - codenewbie
layout: layouts/post.njk
---

_This article was originally published in the DEV Community._

I've got to a point in my career where I'm able to build good interfaces in a relatively short time frame.

That may not sound super humble but it's just a consequence of doing the same thing for a long time, you start to get good at it.

However, despite being capable of building really good UI, I've never built something that made people go "wow".

I'm talking about this kind of stuff:

twitterEmbed 1288861216073490432

_Wow_, right?

That tweet got me thinking that react-three-fiber may be exactly what I need to step up my front-end game. So I decided to learn it, and _learn it good_.

And guess what? I'm taking you with me in a series of articles as we cross into…

## The react-three-fiber Zone

[\*cue spooky intro tune\*](https://www.youtube.com/watch?v=XVSRm80WzZk)

As you can see from the earlier tweet, we can make some mean 3D stuff with react-three-fiber. But we need to crawl before we walk so let's start from the beginning and keep it simple.

Today on "The react-three-fiber Zone" we are going to answer only two questions: "What is a React renderer?" and "What is three.js?".

Let us begin:

As per its readme.md, react-three-fiber is:

> **"a React renderer for Threejs on the web and react-native."**

I'm assuming that you have some experience with React here. We're also focusing on a web environment. So that leaves us with:

> _"renderer for Threejs on the web"_

## What is a React renderer?

> Renderers manage how a React tree turns into the underlying platform calls. - React Docs

That is a precise definition but it feels too abstract, let's try an imagination exercise instead.

First I need you to **imagine a tree**. Any tree works, try an apple tree for instance.

You can think of your regular React application as that tree. With each React.Component being a branch that may hold one or more leaves.

That tree by itself doesn't do much, it is just information. We need to **move that tree somewhere** to make it useful, like into a browser.

And we do that using a renderer, more specifically, ReactDOM.

See, React was originally created for browsers, so anything written with React would be translated into DOM API calls using ReactDOM renderer.

However, some really smart folks at Facebook realised that you can **move that tree to other platforms**, like smartphones, by writing a different renderer focused on that platform.

And that's how React Native, and the whole concept of **renderers** was born.

Now, let's take this newfound knowledge and read the official definition again:

> "Renderers manage how a React tree turns into the underlying platform calls."

Doesn't it make more sense now? **At the end of the day renderers are machines that translate React code into a specific API**.

React Native does it for mobile, React DOM does it for the DOM API and react-three-fiber does it for three.js.

## What is three.js?

Three.js is the most popular JavaScript 3D library by a huge margin. It has a whopping 62k stars on GitHub and a fantastic showcase of projects using it.

It works by wrapping your browsers default **WebGL API** into a comprehensive set of tools and best practices. Here's an example of it at work:

![Example 1](https://dev-to-uploads.s3.amazonaws.com/i/s5fwujtp8r7e2z460z4w.gif)

![Example 2](https://dev-to-uploads.s3.amazonaws.com/i/4ymh9o7ni8t451tj2wv7.gif)

We have a problem, though. 3D is complex, so a fast-growing three.js project can get quite cumbersome to maintain.

**The whole deal of react-three-fiber is making three.js API easier to develop and maintain**.

## And that's it for today.

This is a series where I share everything that I've learned about react-three-fiber, while I learn it!

In the next posts we'll talk more about code and implementation details, but it is important to go over the basics first.

See you next week and stay tuned for the next episode of...

_The react-three-fiber Zone_ 👁

---

Cover photo by [David Becker](https://unsplash.com/@beckerworks?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on Unsplash

Questions and feedbacks are always welcome!

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
