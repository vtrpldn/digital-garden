---
title: Hooked on Hooks! A Late Introduction to My Favorite Thing in React
date: 2020-06-30
tags:
  - react
  - javascript
  - webdev
  - frontend
layout: layouts/post.njk
---

_This article was [originally published](https://dev.to/vtrpldn/hooked-on-hooks-a-late-introduction-to-my-favorite-thing-in-react-1nfe) in the DEV Community._

---

Having launched in Feb 2019, it is safe to say hooks aren't a new, shiny, feature anymore.

Since then hooks made working with React so much easier and fun that I couldn't help but write some words about it. But, at the time of writing this paragraph, I've realised that despite knowing _how_ to use it on my projects, I understand very little _about_ the subject itself.

So, two birds one stone, the idea of this article is to teach you more about hooks while I also teach _myself_ about hooks.

I'm assuming in this article that you have some experience with React and understand core concepts like state and the component life-cycle, ok?

If you're not familiar with these concepts already you can always save it and come back later. 🙂

So, let's learn something new together. Check out the questions below, reference links at the end of the post.

Off we go!

## From the beginning, what are hooks?

A hook, as a programming concept, is "a software or hardware feature included in order to simplify later additions or changes by a user".[1]

With that in mind, you can think of hooks as a way for pieces of code, like functions, to interact with already implemented segments of code in a predictable, predefined way.

WordPress, for instance, relies heavily on its own kind of hooks for plugin and theme APIs.

The deal of hooks is _extensibility_ and making future changes easier. You can say that React Hooks extend your function components with cool new stuff the same way that plugins and themes extend the default WordPress experience.

## Ok, cool, but why did React switch to hooks?

Well, React didn't _switch_ to Hooks, you can still use the ol' class-based components just fine. Hooks simply improve function components with some features that once were only available on class-based.

However, _in my personal opinion_, I believe hooks are the way to go and _probably_ future documentation and examples will prioritize hooks.

But opinions aside, React docs has a whole segment on the team's motivations for hooks [2] but here's how I'd summarize it:

1. When you work on something for five years straight, some improvements start to become clear
2. React's way of sharing stateful logic across components -- render props and higher-order components -- would get complicated and hard to follow as the codebase grew
3. Hooks allowed handling side-effects in an isolated, feature specific way, instead of forcing multiple features logic to split based based on component lifecycle methods
4. Function components with hooks are just straight up easier to understand than class-based components

## That's nice, but what can I do with hooks?

Well I thought you'd never ask!

For one, hooks make your components code much simpler and easy to understand. And in order to prove that I'm going to shamelessly copy and paste an example from the React docs. [3]

**Class-based component**

```jsx
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    );
  }
}
```

**Functional component with hooks**

```jsx
import React, { useState } from "react";

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

Ah, much leaner and easier to understand. So refreshing...

Ok, back to what hooks are good for.

The React docs highlight two major hooks and, considering that this is an intro to the subject, we'll leave the additional hooks and custom hooks to another time.

You can check how to use both of those hooks below. You'll definitely need the additional hooks in the future but these two are certainly the ones you'll use the most.

Please be aware that this post will get a little dense from now on, so feel free to save it for later or stare at this relaxing campfire for a couple minutes. Just remember to get back here when you're done.

youtubeEmbed EqqpcFj8G-s

## Use useState() when you need to use state

The `useState` hook is your function component alternative to `this.state` and `this.setState()` so if you're familiar with how state works the change is relatively simple to understand.

However, if you've just switched from Class-based components you might be tempted to just go ahead and do something like `const [state, setState] = useState()`, but you need to be aware of an _important difference_!

As you might know, `this.setState()` changes _only the property that you specified_ in the object.

```jsx
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
      name: "Vitor Paladini",
      email: "vitor@paladini.dev",
    };
  }

  render() {
    return (
      // this.setState will only change state.count and leave other properties intact
      <button onClick={() => this.setState({ count: this.state.count + 1 })}>
        Click me
      </button>
    );
  }
}
```

However, if you initialize `useState` with an object, be aware that every change on that state variable will override the whole object.

```jsx
import React, { useState } from "react";

function Example() {
  const [state, setState] = useState({
    count: 0,
    name: "Vitor Paladini",
    email: "vitor@paladini.dev",
  });

  // Oh no, this will update the whole
  // state object and remove name and email properties from it
  return (
    <button
      onClick={() =>
        setState({
          count: state.count + 1,
        })
      }
    >
      Click me
    </button>
  );
}
```

To prevent that kind of scenario, it would be better to create state variables for every object key like this:

```jsx
const [count, setCount] = useState(0);
const [name, setName] = useState("");
const [email, setEmail] = useState("");
```

Or, if you really need it to be an object, you could safely update it like so:

```jsx
import React, { useState } from "react";

function Example() {
  const [state, setState] = useState({
    count: 0,
    name: "Vitor Paladini",
    email: "vitor@paladini.dev",
  });

  // This will only update count
  // while name and email stay intact
  return (
    <button
      onClick={() =>
        setState({
          ...state,
          count: state.count + 1,
        })
      }
    >
      Click me
    </button>
  );
}
```

But other than that, `useState` is a very straight forward hook that I see as a direct improvement over `this.setState()` syntax.

Just be aware that the argument that you pass to `useState` will be the initial value of that state variable.

For instance, on `const [potato, setPotato] = useState("Tasty");` the `potato` value will initially be equal to `"Tasty"`.

Next hook!

## Use useEffect when you need some side-effects

_(If you repeat that three times with the terminal on fullscreen, Dan Abramov will appear next to you and help you debug your React code)_

In order to understand the `useEffect` hook and why it replaces component lifecycle methods, first you need to be familiar with the concept of side-effects. Let's talk briefly about that.

You can think of side-effects as anything that happens whenever you ask your computer to do something and it does that thing, but also something else unrelated. This unrelated thing is a side-effect and I strongly encourage you to read more into it.

With that in mind, a side-effect in Reactland is everything that your component does other than returning the component itself. So if you need to interact with the DOM in any way or fetch data from a server, `useEffect` is the place to start.

Basically, `useEffect` hook will take any code you give it and execute it on specific times. In the example below, `useEffect` will fire an alert whenever the the component _mounts_, or shows up on the screen.

```jsx
import React, { useEffect } from "react";

function Example() {
  useEffect(() => {
    alert("Hello! 👋");
  }, []);

  return <>// Component jsx goes here...</>;
}
```

Not only that, you can make pieces code be executed when the component _unmounts_, or goes away. You just need to also return a function on the first argument, here's an example:

```jsx
import React, { useEffect } from "react";

function Example() {
  useEffect(() => {
    alert("Hello! 👋");
    return () => {
      alert("Goodbye! 😢");
    };
  }, []);

  return <>// Component jsx goes here...</>;
}
```

These two examples already cover the `ComponentWillMount` and `ComponentWillUnmount` life-cycle methods. But did you see in the examples that we've used an empty array as a second parameter on our effect hooks?

That array is telling the effect hook that the code inside it doesn't depend on any prop or state, so it will only run once on mount and once on unmount.

But there are times that you really need for your side-effects to _react_ to your app. And you can do that by adding any state variable or prop to that array, and whenever that state or prop changes, the function inside `useEffect` will be executed again!

Here's a slightly modified example from React docs in case things are starting to get confusing:

```jsx
import React, { useState, useEffect } from "react";

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // This will run on mount...
    alert("Hello! 👋");
    return () => {
      // This will run on unmount...
      alert("Goodbye! 😢");
    };
  }, []);

  useEffect(() => {
    // This will run whenever count changes!
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

See how with that second argument we can get more control of when the side-effect gets executed? With that small change you can replicate the `ComponentDidUpdate` life-cycle method!

Just remember that if you skip this second argument the code inside `useEffect` will run whenever any prop or state changes (!) and that may significantly impact your app's performance, so remember to use it whenever possible!

## Final words

And that's a wrap! This article got somewhat bigger than I initially expected but I think it was for the best. 😄

I hope this introduction to React hooks serves you well, and good luck on your front-end journey.

Comments and feedback are super welcome!

## References

[1] http://www.catb.org/jargon/html/H/hook.html
[2] https://reactjs.org/docs/hooks-intro.html#motivation
[3] https://reactjs.org/docs/hooks-state.html

## Thanks

Photo by [Ivar Asgaut](https://unsplash.com/@bo99) on Unsplash
Draft feedbacks by [Cezar Augusto](https://twitter.com/cezaraugusto) and [Christian Kaisermann](https://twitter.com/kiwistian)

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
