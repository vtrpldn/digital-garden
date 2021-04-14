---
title: How to DEV | Tips I've found in Forem repository
date: 2020-08-26
tags:
  - css
  - codenewbie
layout: layouts/post.njk
---

_This article was originally published in the DEV Community._

I don't know about you, but I find DEV Community's commitment to openness and transparency _fantastic_.

I love that we can simply download the code that makes _this_ run, snoop around and find how it works.

That's what I did last weekend and today I'm sharing some things I've learned.

> Keep in mind that things might change (they did _[while I was writing](https://github.com/forem/forem/commit/bd6a996bce31dae85318573649f7f453f0d22445)_ this post 😄) so let me know in the comments if something is not up to date.

## Make sure your article has a cover image

[Reference](https://github.com/forem/forem/blob/master/app/javascript/articles/Feed.jsx#L18)

It is general advice to always add a relevant cover/feature image to your posts as it makes it more attractive.

Here in DEV it has the extra benefit of making your post suitable to the first position of the feed.

Be aware that while having a cover image _will not_ guarantee that your post is featured as the first of the feed, not having one _will_ make it impossible.

## Avoid using `#discuss` and `#watercooler` tags together

[Reference](https://github.com/forem/forem/blob/master/app/black_box/black_box.rb#L16)

I'm guilty of this one.

`#discuss` and `#watercooler` sound quite similar but they serve different purposes.

`#discuss` is for "questions designed to elicit community responses" while `#watercooler` is meant "for slightly, or majorly offtopic subjects".

_My take_ of these guidelines is that `#discuss` is good for work/career/tech/industry-related discussions while `#watercooler` is for laid back chats with people on the community.

With that in mind, it comes as no surprise that articles with the `#watercooler` tag get a small penalty in the feed algorithm. So adding `#watercooler` to your serious `#discuss` thread may actually make it harder to reach its audience.

So, if your discussion is more focused and serious go for `#discuss`. For just-for-fun chats that respect the code of conduct, `#watercooler` is that way to go.

## Understand the "hotness score"

[Reference](https://github.com/forem/forem/blob/master/app/black_box/black_box.rb#L4)

Every article has a score that helps the feed algorithm decide which articles to show on your DEV homepage.

At the time of writing, that hotness score takes a few things in consideration:

1. How recent is the article
2. How many reactions it has
3. How big is the article comment score
4. How spammy the article looks

I'm not going deep on numbers because, I'm not even kidding, the rules of the ranking [changed](https://github.com/forem/forem/commit/14e85493c1e457f57dec9d30fbf79933d85d6df5) _[twice](https://github.com/forem/forem/commit/1336d8c439d0d48867ed0b76fc9ef0013bf0c9e0)_ until I got to this part of the text. 🥴

## How recent is the article

Article freshness is calculated by getting the difference between the article time of publish and DEV epoch date (2010-01-01 00:00:01).

Freshly posted articles also get a score bonus that gradually decreases until the mark of 4 days. From then on it receives a penalty that decreases the weight of reactions on the score, so older posts get a bit less attention.

## How many reactions it has

This one is pretty straight-forward, a post with lots of ❤️, 🦄 and 🔖 get a bigger hotness score.

## How big is the article comment score

An article comment score is the sum of all of its comments _own score_.

A comment score is based on:

1. How many ❤️ it has.
2. How many replies it has.
3. How spammy the comment looks

The comment also gets a bonus if it is bigger than a specific size or includes code samples.

## How spammy the article looks

Article spamminess decreases the hotness score.

If you are a trusted user (couldn't find what that means) or have any badges, your spamminess is zero. However, if your account is newly created it get a little spam bump.

## Wrapping it up

While certainly cool to know, you may find that the topics that I brought today are no game-changer.

I mean, if someone came here expecting tips to game the feed algorithm I'm sure that this person will leave quite disappointed. 😄

What I really hope, though, is that this article sparked an interest in looking through Forem. I have zero experience with Ruby/Rails and it is being an interesting learning platform.

As a final thought, imagine how wonderful it would be if we could do that with every app that we use every day?

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
