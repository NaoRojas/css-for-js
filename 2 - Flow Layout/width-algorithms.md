# Width Algorithms

It's easy to assume that this means that they have a default width of 100%, but that wouldn't quite be right.

In the following playground, try toggling the width: 100% declaration in the devtools, to see how it affects the size of the heading:

<h1 class="example-1">
  Hello World
</h1>
<style>
    h1.example-1 {
  /* width: 100%;  */
  margin: 0 16px;
  background-color: purple;
}
</style>

---

When we enable width: 100%, we cause the heading to pop outside of our frame. This happens because of the margin.


When we use percentage-based widths, those percentages are based on the parent element's content space. If the body tag makes 400px of space available, any child with 100% width will become 400px wide, regardless of any other circumstances.

Block elements have a default width value of auto, not 100%. width: auto works very similar to margin: auto; it's a hungry value that will grow as much as it's able to, but no more. In the case above, our h1 will grow to consume (100% - 32px), since there is 16px of margin on either side.

It's a subtle but important distinction: by default, block elements have dynamic sizing. They're context-aware.

## Keyword values
Broadly speaking, there are two kinds of values we can specify for width:

- Measurements (100%, 200px, 5rem)
- Keywords (auto, fit-content)

Measurement-based values are either completely explicit (eg. 200px), or relative to the parent's available space (eg. 50%). Keywords, on the other hand, let us specify different sorts of behaviours depending on the context.

We've already seen how auto will let our element greedily consume the available space while respecting any constraints. Let's look at some of our other options!

### min-content

When we set width: min-content, we're specifying that we want our element to become as narrow as it can, based on the child contents. This is a totally different perspective: we aren't sizing based on the space made available by the parent, we're sizing based on the element's children!

This value is known as an intrinsic value, while measurements and the auto keyword are extrinsic. The distinction is based on whether we're focusing on the element itself, or the space made available by the element's parent.

<h1 class="example-2">
  This heading is shrunk down.
</h1>

<style>  
   h1.example-2{
  width: min-content;
  background-color: fuchsia;
}
</style>

### max-content

This value is similar in principle, but it takes an opposite strategy: it never adds any line-breaks. The element's width will be the smallest value that contains the content, without breaking it up:


<h1 class="example-3">
    This heading is constrained using max-content, which causes the line to extend far longer than it otherwise would!

</h1>

<style>  
   h1.example-3{
  width: max-content;
  background-color: purple;
}
</style>

As you can see, an element with width: max-content pays no attention to the constraints set by the parent. It will size the element based purely on the length of its unbroken children.


### fit-content
If these keywords were bowls of porridge, fit-content would be the one that Goldilocks declares "just right".

Here's how it works: like min-content and max-content, the width is based on the size of the children. If that width can fit within the parent container, it behaves just like max-content, not adding any line-breaks.

If the content is too wide to fit in the parent, however, it adds line-breaks as-needed to ensure it never exceeds the available space. It behaves just like width: auto.

Change the margin-left

<h2 class="example-4">Short</h2>
<h2 class="example-4">A mid-length heading</h2>
<h2 class="example-4">The longest heading you've ever seen in your life, will it ever end, ahhhhh ohmigod 😬😬😬😬😬😬😬</h2>
<h2 class="example-4">Short</h2>
<h2 class="example-4">A mid-length heading</h2>
<h2 class="example-4">The longest heading you've ever seen in your life, will it ever end, ahhhhh ohmigod 😬😬😬😬😬😬😬</h2>
<style>  
h2.example-4 {
  width: fit-content;
  margin-left: 12px;
  background-color: green;
  margin-bottom: 16px;
  padding: 8px;
}
</style>

### A thought experiment 
fit-content is a really cool new value, but does it offer truly unique functionality? Can it be replicated using other less-shiny CSS properties?

Take a few minutes and think about it. Play around and see if you can replicate the effect without using fit-content: