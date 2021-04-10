_Photo by Immo Wegmann on Unsplash_

If there is a thing that used to be unintuitive in CSS (or even ridiculously hard for beginners) is aligning stuff to both horizontal and vertical center. This visual little detail so easy to design usually meant a good amount of frustration for old-timey web developers.

Thankfully Flexbox came around and changed that but, despite it being my go to way of centering stuff, I believe that we have a lot to learn from alternative ways of doing so. So we are going to cover that and some other ways to solve this common UI problem.

Oh, and we're not talking CSS Grid here because that is a complex, very well resourced property with endless alignment possibilities that would need a full article to present.

Anyways, here we go:

#The good, reliable way

One good thing about Flexbox is that it feels like a very well thought standard. It can get a bit complex, yes, but if you give yourself a chance to actually understand how it works it empowers you to make very elegant and, well, very flexible layouts.

That being said, here's how you center stuff with Flexbox.

https://codepen.io/vtrpldn/pen/WNrGKKZ default-tab=css,result

No drawbacks, no bells and whistles, just a very good CSS property used the way it was intended to. It is so good that you don't even need to add properties to the child element, but if you really wanted to you could do something like `.child { align-self: center; }` instead of `.parent { align-items: center; }`.

#The classic align

If there is anything classic on web development is the good old `<table>` element.

Other than it's main use of creating tables, `<table>` used to be repurposed on sliced websites made with Photoshop and it still shines in email templates. However, back in the day, making use of its layout properties was a sure, albeit a bit hacky, way to align elements to the center of a parent.

Here's how you'd do it back in the day -- and how you probably still wanna do it in email templates because, let's be honest, Gmail won't fully support Flexbox anytime soon...

https://codepen.io/vtrpldn/pen/WNrGKLd default-tab=css,result

Not too shabby, right? It still is easy to read and understand but there is some bitterness in repurposing `display: table` and `display:table-cell` for only that but, whatever works, man.

#The X/Y align

This one makes use of some absolute positioning magic and transform properties. It is not as pure as the Flexbox approach, but it is useful for cases where you want child elements to overlap each other naturally.

Let's take a look at the example:

https://codepen.io/vtrpldn/pen/oNbzMOX default-tab=css,result

The main difference of this technique is that, considering that the children are absolute, any new child that you add will fill the exact same space inside the parent. And by changing the `transform` values or playing around with `opacity` that might be super useful.

#The line-height hack-align way

This one feels the hackyest so far, but it works well if the parent height doesn't vary and the child is an inline element like a `<span>`, `<a>` or a text node... You know what, you're probably better off with any of the other solutions, but here is how it works anyway:

https://codepen.io/vtrpldn/pen/YzwGjoq default-tab=css,result

I mean, it is suboptimal that you'd need to also change the line-height of the child if the parent height changed, but this is better than increasing the child's vertical padding pixel by pixel...

# Conclusion

A bit of well-used CSS can go a long way.

These four different solutions for a single problem can address multiple use cases and hopefully help you on your quest for an incredible UI implementation.

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
