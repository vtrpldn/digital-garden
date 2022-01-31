---
title: How to Overcome Your TypeScriptoPhobia
date: 2022-02-02
tags:
  - typescript
  - codenewbie
  - tips
layout: post
---

Let's face it, TypeScript is kinda scary.

![scary typescript example](/img/scary-typescript-example.png)

Not too long ago, I used to dread the idea of having to learn and work with it every day.

I'd log off after a busy day at work and have a recurring nightmare where a mob of angry engineers forced me to either use it or face a slow, painful demise. I also couldn't run or fight in the dream, my punches were super slow, and all my teeth would crumble and fall...

Alright, I'm deviating here, but you get the idea.

And now, after a little more than a year of daily TypeScript exposure I... Kind of love it? I'm not sure if "love" is the right word here, but we're surely on amicable terms now.

Using it makes my job so much easier (after making it much harder for a while, let's be honest), and I regret not putting in the effort to learn it earlier in my career.

And that's the reason I'm here today. I want you to learn from my mistakes, eat that damn frog, and start putting some effort into learning TypeScript today!

🎵 [cue motivational song](https://www.youtube.com/watch?v=bWcASV2sey0) 🎵

_But first_, let's talk about why I avoided it so much.

## I used to hate the idea of using it

> Hate is a consequence of fear. Fear is a consequence of ignorance. - Albert Einstein ([not really](https://www.goodreads.com/quotes/8833090-ignorance-leads-to-fear-fear-leads-to-hatred-and-hatred))

As human beings, we have emotional responses for every stimulus, and _boy_, I used to have strong feelings right inside my gut whenever TypeScript popped up on my Twitter feed.

Back then, it looked like _one extra thing_ to learn atop a couple dozen new JS stuff, the syntax looked like something straight out of a [World War II cryptography machine](https://en.wikipedia.org/wiki/Enigma_machine), and it felt like I could accomplish the same thing with good old JS.

It all sounded like way too much effort. 😮‍💨

"It will just make me slower!", "It will be another dev dependency to go haywire and break my env!", "I could use that time to write tests!" - I thought.

There is _some_ truth to these thoughts, the syntax does indeed resemble an Enigma machine sometimes, and yes, _it is_ [one more thing to learn](https://medium.com/javascript-scene/why-im-thankful-for-js-fatigue-i-know-you-re-sick-of-those-words-but-this-is-different-296fae0c888f).

But at the deep end, I was simply afraid of the unknown, too comfortable with my JS-only experience, and very good at unconsciously coming up with excuses.

And all that prevented me from seeing the benefits it could bring to my workflow.

It's kind of like when you're meeting a new person but already have so many negative preconceptions that you instantly hate them. In my case, that person was called TypeScript, a funny name for a person to have if you ask me.

## Why I kind of love it now

I kind of love it for a few reasons, it makes my job easier, sure, but I only got to love it once I got to know it.

And I only got to know it because I put myself in a position where I was forced to use it every single day.

I mean, not really _forced_, but after applying and being hired to a TypeScript-heavy position, I had to damn well get rid of my TypeScriptoPhobia and learn it good.

And here's what I discovered along the way!

### TypeScript facilitates communication, like, a lot

TypeScript has a lot of advantages but the thing I like **the most** in using it is how it forces you to give good names to stuff, especially objects.

In the example below, you'd be able to say something like, "Hey Jess, this method takes a **User** as param" instead of "takes an object with id, name, and email as mandatory properties."

```js
function createUser({id, name, email}) {
	return fetch('https://example.com/user/create', {
	  method: 'POST',
	  body: JSON.stringify({id, name, email}),
    ...
	})
}
```

vs.

```ts
type User = {
	id: string
	name: string
	email: string
}

function createUser({id, name, email}: User) {
	return fetch('https://example.com/user/create', {
	  method: 'POST',
	  body: JSON.stringify({id, name, email}),
	  ...
	})
}
```

This single change in your team's workflow makes the implementation much more straightforward to discuss during code reviews, RFCs, and pair-programming sessions.

That also works very well when working with well-typed dependencies. For instance, when discussing a specific API method, you can say it accepts a [LatLngLiteral](https://developers.google.com/maps/documentation/javascript/reference/coordinates#LatLngLiteral) instead of "an object with lat and lng properties as `number`."

### It actually eases your mental workload over time

TS will make you slower before making you faster, and the sooner you accept that, the better.

But after going through an initial learning curve and type setup, you'll see how a robust type system and a reliable autocomplete saves you some critical mental bandwidth.

Your focus will no longer be interrupted by thoughts like "does this method take an object or an array of strings?" and "I'm not sure if I should explicitly set this argument as null or if I can leave it as undefined...".

TypeScript makes it so that you write the answers before _even thinking_ about the questions. If you try something that doesn't match your declared types, your code editor will let you know instantly.

**Here's another scenario:**

You're using a framework or dependency you're not super familiar with. You've been through the docs a couple of times but only learned about some key concepts.

Instead of rummaging through the API docs hundreds of times to see if a specific method is called `createUser()`, `createNewUser()`, or `createEntity('user', ...)` you can type down "create", let your editor autocomplete work for you and save countless alt+tabs to the docs page.

### It helps you sleep better at night

As your project grows, TypeScript makes it harder for you to shoot yourself in the foot. Harder but not impossible, as self-sabotage is a quintessential aspect of software engineering.

You know, your vanilla JS codebase might look cute and harmless now in its infancy, but you know that if left unattended for too long (or feed it after midnight), it will start to go wild.

![gizmo from gremlins](/img/gizmo.jpg)

It might be challenging to picture that scenario if you've never got close to a vast JS-only project, but trust me, things get _messy_.

I like TypeScript because it makes your codebase "tighter" in a good way.

It takes away some of that crazy flexibility and permissiveness of JavaScript and creates an environment where you _must_ think a little bit deeper about how you'll organize your data.

> After you put in the effort of learning TS, JS codebases feel like poorly built toy that does work, but rattles a lot when you pick it up and shake it close to your ear. You just don't trust it as much.

Every time you write and use a new type, you create a new constrain that prevents you from making bad decisions. And consequently, the trust you have in your own code increases.

Add that to a well-configured CI that checks for TS errors before build, and you'll have a safety net that prevents you from shipping embarrassing (and 100% avoidable) type errors.

Combine that with a well-tested application, and your sleep quality will improve ten-fold during release weeks.

## How and where to start

Now, you might not have that very strong "my new job literally depends on learning TypeScript" kind of motivation, so that's what this section is all about.

I'm confident that by now, I've at least made you consider trying it, so here are a few suggestions on how to start.

Just keep in mind that [sucking at something](https://www.youtube.com/watch?v=Gu8YiTeU9XU) is the first step toward being sorta good at something.

### 1. Sit down, grab a warm beverage, and read through the docs

This sounds obvious, but I'd like to stress how good [the TS intro material](https://www.typescriptlang.org/docs/) is. Really, it's got dedicated guides for new programmers, for people with some JS experience, for functional programmers, it is excellent.

Learning styles differ from person to person, but I'm sure that having the theory basics before getting down to business will help you immensely.

### 2. Start slow with a new project

A calculator, a to-do list, a neat project with Spotify API + react-three-fiber, a large-scale CRM to rival Salesforce's biggest efforts. It doesn't matter what it is as long as it is funny enough to keep you engaged.

Just run `$ yarn create next-app --typescript` and go to town!

There's one rule, though. Use `@ts-ignore` or type `any` and you lose. This will be the golden rule to keep you focused when TypeScript starts testing your faith.

And it will.

### 3. Gradually migrate a JS project to TypeScript

TypeScript came around when people already had a lot of JavaScript projects up and running. So it is no surprise that we can find a lot of migration tools and guides.

That said, a great way to start cracking some TypeScript is by cloning a JS repo and migrating it to TS. It can be some old project of yours or that small abandoned script on your company's GitHub page.

You can use AirBnb's [ts-migrate tool](https://github.com/airbnb/ts-migrate) or try a more direct tactic following the [Migrating from JavaScript](https://www.typescriptlang.org/docs/handbook/migrating-from-javascript.html) guide.

This approach is somewhat different from the previous suggestion as type `any` will be a good friend while you sort out a myriad of type errors. But you'll get there; you just gotta keep pushing forward.

## Some tips before you start

But wait, there's more!

This article is already getting a little on the longer side. I know, I know... But here are some lessons I learned after this intense year of TypeScript:

### 1. Take your time reading error messages

TS error messages are really something. They can look aggressively verbose and distract you from the problem at hand.

Try reading them bottom to top and make a solid effort to understand what is wrong before brute-forcing a solution (or giving up and leaving it `as any`).

### 2. TS will infer a lot of stuff, get to know how it works

You don't need to type every single line of your code. There's this thing called [Type Inference](https://www.typescriptlang.org/docs/handbook/type-inference.html) where TS makes an educated guess about types considering information it.

For instance, if you type an array, you won't need to type the argument of a filter or map function.

```ts
const potatoes: Array<string> = ["russet", "yukon gold", "la ratte"];

// no need to type the potato arg below 👇
const bestPotatoForMashedPotatoes = potatoes.filter(
  (potato) => potato === "la ratte"
);
```

> Unrelated cooking tip, La Ratte [is arguably the best potato](https://www.youtube.com/watch?v=-mJYyueZfd8) for mashed potatoes.

### 3. Always check for TypeScript support when adding a new dependency

Most big libraries have either their type definitions contained in the same package you installed or under [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped).

Make sure to always search for those type defs whenever you need them.

### 4. The extra syntax pops up like a sore thumb in the beginning

This is more of an attempt to bring you some comfort rather than an actual tip, but... Yeah, it is _a lot_ of new characters in your editor.

It will look overwhelming for a couple of weeks, but you'll get used to it sooner than you think.

## Conclusion

I'd rather not _have to_ use TypeScript.

It would be much easier to fling methods and variables left and right and hope for the best. Unfortunately, I lack the supernatural skill to always ship 100% bug-free code every time.

TypeScript helps be ship better, more reliable work, and I'm glad it exists. Getting acquainted with it was no small feat, but I'm a better engineer today because of it.

So yeah, give it a try if this article resonates with you. I hope it helped ease your TypeScriptoPhobia.

You may not like in the beginning -- or at all -- but it is like eating bitter greens or exercising, you might not enjoy it, but it will be good for you.
