---
title: How to Copy a Big Object or Array From Console to Clipboard
date: 2020-09-03
tags:
  - neat little tricks
  - javascript
  - beginners
  - webdev
layout: post
---

_This article was [originally published](https://dev.to/vtrpldn/how-to-copy-a-big-object-or-array-from-console-to-clipboard-3hi) in the DEV Community._

---

Have you ever found yourself trying to `Ctrl-C` a `console.log()` output, only to get mad when it doesn't really work with long Objects and Arrays?

![Gif showing a failed attempt to copy a big object](https://dev-to-uploads.s3.amazonaws.com/i/655smltt9jovq8khg6gm.gif)

## Here's what you should do instead:

1 - Right-click the `console.log()` output
2 - Click "Store as global variable"
3 - Run `copy(temp1)`
4 - `Ctrl-V` it wherever you want

![Gif showing how to copy a long object](https://dev-to-uploads.s3.amazonaws.com/i/0rix6lr6mkjolggmprbu.gif)

Success! You may find that useful when debugging complex data structures or request payloads.

Let me know in the comments what else `copy()` might be useful for! 😄

---

Cover photo by [Paolo Nicolello](https://unsplash.com/@paul_nic?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on Unsplash

_Why the cover photo is a monkey? Well, I make the same face when I'm debugging._

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
