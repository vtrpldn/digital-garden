SVG can be super-duper fast _and_ accessible [you know that](https://css-tricks.com/accessible-svgs/).

And the coolest thing about SVG in webdev is that CSS simply works with it, so you can do stuff like:

```css
path {
  fill: red;
}
```

and _bam_, your icon is red.

Need it to be bigger or smaller? Well, the S on SVG literally stands for "scalable", so you can just go ahead and _pow_ make your icons [as big as your browser can handle](https://stackoverflow.com/questions/16637530/whats-the-maximum-pixel-value-of-css-width-and-height-properties).

```css
svg {
  width: 33554400px;
  height: 33554400px;
}
```

However, we might have a problem here, this post is about React but individually importing SVG files in React is a pain... 😩

# There's a better way

You can leverage the CSS styling features of SVG with React components by using a library called `react-svg`. This library works by fetching, caching and inlining your SVG icons so you only need to worry about styling them.

Here's the step by step guide on how to create an Icon component that, trust me, is a real pleasure to use.

1 - Create an /icons folder and stuff it with all your favorite icons

2 - Create an Icon component that wraps ReactSVG:

```jsx
import React from "react";
import ReactSVG from "react-svg";

const Icon = (props) => {
  return <ReactSVG src="YOUR_PATH/icons/${props.name}.svg" />;
};

export default Icon;
```

3 - Import your Icon component and use it like so:

```jsx
import React from "react";
import Icon from "./Icon";

const IconList = () {
  return (
    <div>
      <Icon name="user" />
      <Icon name="calendar" />
      <Icon name="phone" />
      <Icon name="email" />
    </div>
  );
}

export default IconList;
```

Can you see the beauty of it? No more fumbling with icon imports every time you need a new icon. Just add the file to the icon folder, pass its name as a prop to your brand new Icon component and call it a day.

Now, let's go a bit further with this Icon component thingy and make it even more useful.

# Give it some style

Did you see how we are using the `name` prop to fetch the right icon file? We can do the same thing for picking the right color and size of that icon.

All we need is a CSS-in-JS library to act as a glue between our SVG files and our Icon component, we are using Styled Components in the example below but any other library would serve.

Here, take a look. The embed space is pretty limited so feel free to click the "Open Sandbox" button and play with it for a while, just remember to come back. 🙂

codesandboxEmbed cpw5j view=split

Pretty nice, huh? What I like the most about this approach is that after some initial setup, adding a new icon is as simple as dragging the SVG file to the icon folder. And being able to style it directly in the component props is definitely a plus.

So that's it! Thanks [Harpal Singh](https://unsplash.com/@aquatium) on Unsplash for the cover photo.

If you have any questions about the example please share it in the comments!

---

## Hey, let's connect 👋

[Follow me on Twitter](https://twitter.com/paladini_dev) and let me know you liked this article!

And if you _really_ liked it, make sure to share it with your friends, that'll help me a lot 😄
