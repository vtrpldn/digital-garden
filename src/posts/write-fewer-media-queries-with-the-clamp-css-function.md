---
title: Write Fewer Media Queries With the clamp() CSS Function
date: 2020-09-07
tags:
  - css
  - codenewbie
layout: layouts/post.njk
---

_This article was originally posted in the DEV Community._

Here's a neat little trick:

You can use the `clamp()` CSS function to make `font-size` responsive and fluid!

![Gif depicting a clamp() example with font-size](https://dev-to-uploads.s3.amazonaws.com/i/0fe8zr0bmhl90wk1r0tg.gif)

It works by "clamping", or restricting, a flexible value between a minimum and a maximum range.

Here's how to use it:

1. Choose a minimum value: E.g. `16px`
2. Choose a maximum value: E.g. `34px`
3. Choose a flexible value: E.g. `5vw`

```css
h1 {
  font-size: clamp(16px, 5vw, 34px);
}
```

In this example, the `h1` `font-size` value will be `5%` of the viewport width. But only if that value is bigger than `16px` and smaller than `34px`.

For instance, if your viewport width is `300px`, your `5vw` value will be equal to `15px`. However, you clamped that `font-size` value to a minimum of `16px`, so that is what is going to be.

On the other hand, if your viewport width is `1400px`, you `5vw` will be a whooping `70px`! But luckily you clamped that maximum value to `34px`, so it won't grow past that.

Oh, and it also works with padding! And margin!

![Gif depicting a clamp() example with padding](https://dev-to-uploads.s3.amazonaws.com/i/7hfatretkjobl2d6zt5b.gif)

And literally any other property that accepts a [length, frequency, angle, time, percentage, number, or integer](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp)!

[Browser support](https://caniuse.com/css-math-functions) is also pretty good if you don't need to support IE/older Safari versions, look:

![Browser support table](https://dev-to-uploads.s3.amazonaws.com/i/1j00ls8ty5d6uq2d8za3.png)

I _love_ modern CSS. What are your thoughts on `clamp()`?

---

EDIT: Be sure to check [Darshak's suggestion](https://dev.to/dar5hak/comment/14jfh) in the comments if you need to add an alternative implementation for older Safari!

---

Cover photo by [Matt Artz](https://unsplash.com/@mattartz?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on Unsplash

Thanks to [Madza](https://dev.to/madza/comment/14d0a) for the name of this series 😄

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
