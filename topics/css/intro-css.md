# Introduction to CSS

Last class you learned how to add HTML content to a page, and hopefully you feel comfortable adding content to a blog post. But in order to jazz it up and style it some up, you will need CSS _Cascading stylesheets_.

## How CSS works

Generally, your style rules will live in a separate file from your HTML. This is because HTML was not designed to hold the rules for styling up pages. So CSS was invented as a quick, powerful way of formatting a page. HTML and CSS were designed to complement each other, so a lot of the same logic applies.

### How to write CSS

The syntax of CSS is easy and straight forward once you get a hang of it. We start with a selector, this can be any of the tags that we have in our `<body>` section.
So for example, we can select our title `<h1>`, by removing the <> symbols on either side. We then write the style rules or _properties_ between two curly brackets like so:

`h1 {`  
 `color: purple;`  
 `border: 2px solid black;`  
`}`

So with those four lines, we just changed the color of text to purple, and added a 2 pixel thick border around our heading. We chose our h1, but we could have stuck chosen any tag like our `<h2>`, `<p>`, `<img>` or several. But we'll get to that later, for now let's move on to adding a dash of color to our page.

There are hundreds of different properties that we can use, a good resource to find these is:  
[W3Schools](https://www.w3schools.com/css/default.asp)

## Adding some color

Last class we briefly covered the `<body>` tag, the tag that holds all the content that appears on the page. Let's start with that as an example. If we open our CSS file , all we have to do is write:

`body {`  
 `color: red;`  
 `background-color: green;`  
`}`

Here we have selected our body tag, changed the background color to green and the text color to red. The last property is an important aspect of CSS, when we say _cascading_ we mean that rules can cascade down to tags inside of tags.

**Colors**  
You can write the name of a color, like we have above, or you can use a color code like a hex code, or rgb code. If you want to find more colors you can use a color picker like:
[Google's color picker](https://www.google.se/search?q=color+picker&ie=&oe=)

## Structural elements

So far we have mainly focused on _semantic elements_, that is to say elements with set rules with some rules attached like paragraphs, headings, and images. These are incredibly helpful, but there are some times when you need a tag without any rules pre-attached.

The most common of these _structural elements_ is the `<div>` or _divider_. If you add one to your html page, you won't be able to see any changes. But the humble `<div>` is a very useful element all the same. One of its main uses is positioning. Let's try it out.

## Positioning elements

Let's try it to make reading our page a bit easier, first let's wrap all of our elements in a `<div>`. That will allow us to instead of having to target each individual element to only style up our new `<div>` tag.

After you have added the `<div>` to the page, then let's style up. First, we are going to want to change the width of the div, so that text doesn't span the entire page.

`div {`  
 `width: 800px;`  
`}`

Now your text should be 800 pixels wide, but it's aligned to one corner and is still not great for reading. So let's fix that using `margins` , margins are the spaces outside of an element, these can be written as pixels, percent and several other units. But because we want to align the reading view in the center of the screen, let's add the `margin: auto;` rule to our CSS, like so:

`div {`  
 `width: 800px;`  
 `margin: auto;`  
`}`

Now our text will be easier to read! **Why don't you experiment with adding a `margin-top` property below the other margin property and trying out different pixel (px) values to see what looks good?**

## Classes and ids

Right now, we have a very short html page. There is not a lot there. But eventually, it will grow and we will have multiple elements of the same type that should look different. For example we might have two different `<div>` elements on a page, and we want to make one a nice red circle while the other is the reading view we just styled up.

To do that we use classes and ids. Both classes and ids are _attributes_ that can be added to any structural or semantic html tag. Classes and ids differ in one key way, which is that an id can only be used once, whereas classes can be re-used.

So for example for our page, we can add an id to the article wrapper `<div>`:

**HTML**

`<div id='main-article'>`
*Article in here*
`</div>`

`<div class="circle"></div>`  
`<div class="circle"></div>`

And then all we have to do in our CSS is switch over the rules we had for div to the id, which we symbolize with a hash symbol:

~~div~~ `#main-article {`  
 `width: 800px;`  
 `margin: auto;`  
`}`

And let's style up our two circles, using the period sign to choose classes.

`.circle {`  
 `width: 50px;`  
 `height: 50px;`  
 `border-radius: 100%;`  
 `background-color: tomato;`  
`}`

The `border-radius` property allows us to choose how round an element should be, by setting it to 100% we are effectively rounding each corner as much as possible. You might have to add margins to make it look good, but you should have two tomato colored circles below your article.

## Getting jiggy with it

Hopefully you feel that you have a grasp of basic CSS now, but not much is happening on our page. Just for fun, let's play around with some more advanced selectors. Let's try to make our pretty circles react to being hovered over, to do this, it's relatively simple! Leaving the old rules we wrote, all we have to do is add a few more lines of code with the `:hover` selector, like so:

`.circle:hover {`  
 `background-color: blue;`  
`}`

Now, when we hover our circles they should become blue. But it would be nice if there was a transition between the colors, instead of it being instant like it is now. Simple! We can use the `transition` property to make it happen, so let's add `transition: 1s;` to our `.circle` block. We just added a 1 second transition to our element so that when you hover over it, it should gradually change from a tomato to blue.

## Animations

Great! We have our two tomatoes, but even with :hover states, they aren't that exciting. Let's throw in some animations!
Animations in CSS are done with keyframes, that work similarly to most animation software. So if you've worked with animations before, this will feel very similar.

Let's make our tomatoes bounce!

To do that, let's introduce you to a few new properties and another selector, similar to the `:hover` selector.

`.circle:first-child {`  
 `animation-name: bounce;`  
 `animation-duration: 1s;`  
 `animation-iteration-count: infinite;`  
`}`

First, we have chosen the first element with the class name of `.circle` by using the `:first-child` selector. Then we have defined the name of our animation, the amount of time (duration) before the animation is complete, and then the amount of times (iterations) it runs, in this case infinite times. Next, we have to define what our animation, named _bounce_ actually does. To do that we use the keyframe syntax in CSS:

`@keyframes bounce {`  
 `0% {`  
 `opacity: 0.2;`  
 `transform: translateY(50px);`  
 `}`  
`50% {`  
 `opacity: 1;`  
`transform: translateY(-20px);`  
`}`  
`}`

So here, we have defined our animation named _bounce_, `@keyframes`, inside of the @keyframes declaration we can stick the actual keyframes of the animations. So at 0% of the animation our circle is going to have an opacity of 0.2 (20%) so it's going to be fairly transparent, and we are using the `transform: translateY()` property to place it 50 pixels below where it starts. Then at 50% we have made the circle fully opaque, meaning solid, and we've added a negative value into our `transform: translateY()` which means that it will travel upwards 20 pixels, from where it started. So hopefully, we'll have a circle that starts a bit see-through, flies upwards, and then bounces downwards.

It's not the most exciting animation, **so why not try to make it look a bit more happening?**, you can animate almost any property, including all the ones we've learned so far, and you can add many more keyframes, why not add a 75% block? Maybe get it to pulse a certain color? Points for creativity here.

**Transforms**
One of the most useful properties in CSS is the `transform` property. It allows you to transform the look and layout of html elements. You can do everything from translating (moving), rotating, skewing, scaling, and perspective.
[W3Schools on Transforms](https://www.w3schools.com/cssref/css3_pr_transform.asp)

Here are some that you can try instead of just translateY():

`transform: scale(3);`  
`transform: skew(17deg);`  
`transform: rotate(32deg);` // You won't be able to see this one, unless you set `border-radius` to something lower than, 50%, remember we have a perfect circle.

## Flexing our muscles

So far, we have only used `margin` to position elements on the page, but there is an incredibly powerful set of rules called `flex`. [W3Schools](https://www.w3schools.com/cssref/css3_pr_flex.asp).

**Tell us when you get here, and we'll have a class walkthrough.**  
Also, kudos on being first!

# Class Challenge: _Make a snowman_

This is entirely for fun, and not at all necessary, but the person who can make the best snowman using the skills learned in this class, will win a prize.
