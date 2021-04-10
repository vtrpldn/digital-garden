I don't know about you but I _love_ learning stuff in a silly way.

My 9 to 5 is much too serious already so whenever I'm programming for fun, I need to make it _fun_.

This means that for our second episode of "The react-three-fiber Zone" we are going to learn how to slap a floating rubber duck into a React app.

My objective today is to hook you in before introducing more theory in the next episodes.

You'll see how react-three-fiber makes it simple to add just a bit of 3D if you know some React already.

So anyway, here's a look of what we are going to build today:

codesandboxEmbed n33f2 view=preview

# How to?

> "If you wish to add a three-dimensional pink rubber duck to a website, you must first invent the universe." - Carl Sagan [sort of]

Ok, inventing the universe is quite a stretch but here are a few steps that we need to follow.

1. Create a React app
2. Add some website markup
3. Find a duck, import, color and rotate it
4. Add the duck to a Canvas element
5. Render it conditionally

Let's talk about how these things go together.

## 1. Create a React app

Here's the root of our example, the `App.js` component.

codesandboxEmbed n33f2 view=editor module=/src/App.js

You can see that it is pretty simple, it only loads a `<Website>` component, a `<Canvas>` component and uses some stateful logic to control if the `<Canvas>` should be rendered or not.

## 2. Add some website markup

We need a place for our duck to live on while it spins into eternity. This example features a simple `<Website>` component with static data.

We don't need anything fancy, just some boring UI to spice up with an unexpected three-dimensional bird.

Most of it is markup, the only interactive part of our website is the "Surprise" button which fires a state update on click.

Here, have a look a the `<Website/>` component:

codesandboxEmbed n33f2 view=editor module=/src/Website.js

Note that the `setShowCanvas` is a prop that comes from `App.js`.

```jsx
<button className="surprise" onClick={() => setShowCanvas(true)}>
  Surprise
</button>
```

## 3. Find a duck, import, color and rotate it

Or any funny 3D object, be creative.

I'm using [this one](https://free3d.com/3d-model/rubber-duck-v1--614347.html) in the example.

react-three-fiber makes it super easy to import objects. Let's see how by taking a peek into the `Duck.js` component.

Take a look at the comments in the implementation below.

codesandboxEmbed n33f2 view=editor module=/src/Duck.js

What I love the most about the react-three-fiber declarative approach to Three.js is that it makes importing objects _almost_ as simple as import images or CSS.

## 4. Add the duck to a Canvas element

`Canvas.js` is where react-three-fiber magic happens.

codesandboxEmbed n33f2 view=editor module=/src/Canvas.js

A few things that this file does:

1. Initialize the Canvas
2. Add some basic lighting spots
3. Import the `Duck.js` component and renders it inside Suspense - this is important because the `useLoader()` on Duck.js is async.

And that's pretty much everything this simple example needs. 🦆

## 5. Render it conditionally

This final part is as straightforward as it gets.

Let's have a quick look at `App.js` again.

```jsx
export default function App() {
  const [showCanvas, setShowCanvas] = useState(false);

  return (
    <div className="App">
      <Website setShowCanvas={setShowCanvas} />
      {showCanvas && <Canvas />}
    </div>
  );
}
```

We are using the `useState` hook to control the `showCanvas` variable. We initialize it with `false` because we only want to show our `<Canvas>` and therefore our `<Duck>` on click.

Then we pass `setShowCanvas` to the `<Website>` component, so the "Surprise" button can run it on click:

```jsx
<button className="surprise" onClick={() => setShowCanvas(true)}>
  Surprise
</button>
```

So when you click that button `showCanvas` is updated to `true` and React renders the `<Canvas />` component.

And _bam_, a spinning pink duck renders.

![A pink rubber duck rotates over a boring website UI](https://dev-to-uploads.s3.amazonaws.com/i/76l6tfdm6v9saugfpc83.gif)

Fan-tastic.

# Final words

I hope that this how-to sparkled some interest in react-three-fiber.

I strongly believe that this is _the tool_ that will make WebGL more accessible to front-end developers.

For some cool next steps, you should try [forking this CodeSandBox](https://codesandbox.io/s/how-to-add-a-three-dimensional-pink-rubber-duck-to-your-website-with-react-three-fiber-n33f2) and changing the object, or altering the example in any creative way.

Let me know if you need any help. Feedbacks are always welcome, we are learning together!

_Cover photo by [Marcus Lenk](https://unsplash.com/@marcuslenk?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on Unsplash_

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
