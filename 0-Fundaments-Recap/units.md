
# Units

The most popular unit for anything size-related is the pixel:

## Pixel
`
.box {
  width: 1000px;
  margin-top: 32px;
  padding: 8px;
}
`

Pixels are nice because they correspond more-or-less with what you see on the screen*. It's a unit that many developers get comfortable with

## Ems
The `em` unit is an interesting fellow. It's a relative unit, equal to the font size of the current element.

If a heading has a font-size of 24px, and we give it a bottom padding of `2em`, we can expect that the element will have 48px of cushion underneath it (2 × 24px).

Here's a quick playground. Try tinkering with the font size to get a sense of how it works:

<p class="example-2">
  <span style="font-size: 1em">
    This
  </span>
  <span style="font-size: 0.8em">
    sentence
  </span>
  <span style="font-size: 0.64em">
    gets
  </span>
  <span style="font-size: 0.5em">
    quieter
  </span>
  <span style="font-size: 0.4em">
    and
  </span>
  <span style="font-size: 0.32em">
    quieter
  </span>
</p>

<style>
p.example-2 {
  /* Change me! */
  font-size: 24px;
}
</style>

## Rems
The `rem` unit is quite a lot like the em unit, with one crucial difference: it's always relative to the root element, the `html` tag.

All of the rems across your app will be taking their cues from that root HTML tag. By default, the HTML tag has a font size of `16px`, so `1rem` will be equal to `16px`.

Check out the following playground, and then change the html element's font size:

----
<h1>What's a staple? The list expands.</h1>
<h2>Jan. 1, 1991</h2>
<p>Conventional agricultural wisdom holds that only a handful of crop species -- as few as 7 and no more than 30, depending on different assessments -- account for most of the plant food consumed by humanity. But a new study says more than 100 species and possibly as many as 200 are important food sources.</p>

<style>
    html {
  font-size: 16px;
}

h1 {
  font-size: 2rem;
  margin: 0;
}

h2 {
  font-size: 1.25rem;
  margin-bottom: 1.5rem;
  color: gray;
}

p {
  font-size: 1rem;
}
</style>

Notice how all the text scales accordingly, when you change the root font size? That's why people like the rem unit. No matter where an element is in the DOM tree, the rem is consistent.

It behaves consistently and predictably, like pixels, but it respects user preferences when it comes to increasing/decreasing default font sizes.

Please note, you shouldn't actually set a px font size on the html tag. This will override a user's chosen default font size. The only reason we're doing it here is to demonstrate how the rem unit works, and to simulate a user changing their default font size.

If you really want to change the baseline font size for rem units, you can do that using percentages:

`
html {
  font-size: 120%;
}
`
## Percentages

The percentage unit is often used with width/height, as a way to consume a portion of the available space.

<div class="box">
  <div class="child"></div>
</div>

<style>
    .box {
  width: 250px;
  height: 250px;
  background-color: pink;
}

.child {
  width: 50%;
  height: 75%;
  background-color: gray;
}
</style>



## When should I use which unit?
I recently published a blog post, “The Surprising Truth about Pixels and Accessibility”. This blog post aims to answer the “pixels vs. rems” thing once and for all.

In the future, I plan on integrating this blog post into this course. For now, I strongly recommend that you check the blog post out. Consider it a bonus lesson from this course!

You can read it here:
https://www.joshwcomeau.com/css/surprising-truth-about-pixels-and-accessibility/