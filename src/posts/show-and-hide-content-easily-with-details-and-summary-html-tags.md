---
title: Show and Hide Content Easily With details and summary HTML Tags
date: 2020-09-30
tags:
  - css
  - codenewbie
layout: layouts/post.njk
---

_This article was originally published in the DEV Community._

Here's a neat little trick:

You can use the `<details>` and `<summary>` HTML tags to create a simple accordion/collapsible UI.

![Summary/Details tags example](https://dev-to-uploads.s3.amazonaws.com/i/fnfv4dzovmj7smzx50vr.gif)

The only problem here is that it looks rather plain and uninteresting.

But nothing that a few lines of CSS can't fix! Here's how it looks with just a little bit of styling.

codesandboxEmbed pel2y view=preview module=/index.html

Remember that you can click the "Open Sandbox" button and edit the styles yourself. I'm sure that you can make it look even nicer. 😄

Oh, and here's the CSS, take a look. It features a couple hacks with `padding` and `box-shadow` to make the "border" look consistent but, other than that, it is a pretty simple change.

```css
/* The --padding variable help us control
the <details> and <summary> spacing */
:root {
  --padding: 16px;
}

details {
  padding: 0 var(--padding);
  box-shadow: inset 0 0 0 4px;
  border-radius: 4px;
}
details[open] {
  padding-bottom: var(--padding);
}

details > summary {
  display: flex;
  padding: var(--padding);
  margin: 0 calc(var(--padding) * -1);
  border-radius: 4px;
  font-size: 24px;
  cursor: pointer;
  justify-content: space-between;
  list-style: none; /* Hides the default arrow */
}
details[open] > summary {
  box-shadow: 0 4px;
}
/* Adds an icon when the <details> is closed... */
details > summary::after {
  content: "+";
}
/* ...and switches it when <details> is open */
details[open] > summary::after {
  content: "-";
}
/* Removes the ugly default arrow on Chrome */
details > summary::-webkit-details-marker {
  display: none;
}
```

I love how much you can accomplish with plain HTML and CSS.

And by using standard HTML tags you get great accessibility for free!

## But wait, there's more!

You can go even further and transform these two tags into a powerful and, dare I say, [_extremely reusable_](https://dev.to/vtrpldn/series/8380) component.

## Let's add some React to it! ⚛️

These two tags work very well with React's component composition pattern.

So you can just go ahead and create a component to help you toggle stuff more consistently and easier.

Look:

codesandboxEmbed 3fjee view=editor module=/src/Collapsible.js

Then you can import that component and use it like so:

codesandboxEmbed 3fjee view=split module=/src/App.js

This is a great component to have on your toolbelt for when you need to implement a few accordions quickly.

## Thanks for checking out this neat little trick 👋

I hope it comes in handy soon!

Do you have a suggestion for a neat little trick? Leave it on the comments!

Oh! And remember to check the other articles on this series below. They are some spicy little nuggets of webdev knowledge.

Cover photo by [Dominik Vanyi](https://unsplash.com/@dominik_photography?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on Unsplash

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
