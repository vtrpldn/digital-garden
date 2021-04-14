---
title: Grab Your Users Attention With the Focus-Within CSS Selector
date: 2020-10-30
tags:
  - neat little tricks
  - css
  - html
  - beginners
layout: layouts/post.njk
---

_This article was [originally published](https://dev.to/vtrpldn/grab-your-user-s-attention-with-the-focus-within-css-selector-4d4) in the DEV Community._

---

Here's a neat little trick:

You can use the `:focus-within` selector to style the parent of a focused element.

![An example of how on focus overlay works](https://dev-to-uploads.s3.amazonaws.com/i/0lja1zmk1zynjzdkr7d7.gif)

That allows you to create some interactive form UI without a single line of JavaScript. Try the example below:

codesandboxEmbed ubhp7

This demo uses `:focus-within`, plus the `::before` pseudo-selector and some absolute positioning magic. We'll go through the details but you can check the full source below.

codesandboxEmbed ubhp7 view=editor

## `:focus-within` selector + `::before` pseudo-elements + absolute positioning

All in a single declaration block! Let's have a look at the most important part of this example.

```css
body:focus-within::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
}
```

## `body:focus-within`

This selector will apply styles whenever there is **focus**... **within** the body!

Oh, and `:focus-within` works with any element. We're sticking with `body` only for this example.

You can be creative and come up with `.literallyAnyElement:focus-within` and use this selector as you please.

## `body:focus-within::before` + absolute positioning

In our example, that means that whenever any field is focused on the body, a `::before` pseudo-element will be created with those styles:

```css
content: "";
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
background-color: rgba(0, 0, 0, 0.7);
```

The `content: ''` property is required for pseudo-elements and everything else are properties used to create a dark, transparent overlay that fills the whole screen!

## Extra stuff to make it work properly

Keep in mind that you still need to make a couple of tweaks to make the overlay work perfectly.

```css
html,
body {
  height: 100vh;
}
```

This makes sure that the overlay fills the whole screen even if there isn't enough content on the page.

```css
form {
 position: relative;
```

This `position: relative;` ensures that the overlay renders below the form.

---

And that's it for this week's neat little trick. Thanks for reading!

Make sure the check the other tricks in the series and [follow me on Twitter](https://twitter.com/paladini_dev) if you found any of my articles helpful 😄

---

EDIT: Make sure to check Andrew's suggestion in the comments below!

---

Photo by [Stefan Cosma](https://unsplash.com/@stefanbc) on Unsplash
