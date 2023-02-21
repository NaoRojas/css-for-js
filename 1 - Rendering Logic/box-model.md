# The Box Model

The `box-sizing` CSS property allows us to change the rules for size calculations. The default value (content-box) only takes the inner content into account, but it offers an alternative value: border-box.

<section class="example-1">
  <p>Hello World</p>
</section>

<style>
section.example-1 {
  width: 150px;
}


section.example-1 p {
  width: 100%;
  padding: 16px;
  border: 2px solid;
  /* Toggle this on and off! */
  box-sizing: border-box;
}

</style>

A new default
Instead of having to remember to swap box-sizing on every layout element, we can set it as the default value for all elemcxzents with this handy CSS snippet:

`
*,
*::before,
*::after {
  box-sizing: border-box;
}
`