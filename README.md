# [e-spres-oh] BEM

This page contains a list of Frontend Best Practices and Coding Guidelines used at [e-spres-oh].
It also explains our internal CSS naming conventions, using a combination of BEM, SMACCS and OOCSS.

### General Guidelines

> __DON'T apply CSS styles on HTML tags__<br>
> We should decouple mark-up from styling, meaning that if you change the mark-up, it shouldn't have any impact over the CSS.

> __DON'T apply CSS styles on IDs__<br>
> They don't scale up. This can only be done if you are 110% sure that the element will remain unique until the _End-of-All-Frickin'-Times_.

> __DON'T apply CSS styles on JS triggered elements__<br>
> We should decouple behavior from styling and from mark-up. 

# BEM Methodology

BEM method prevents specificity nightmare on long term projects.

### Block

Any re-usable block of mark-up, along with its styling, should be consider a __"Block"__. Blocks can contain other Blocks. Blocks have the __"b-"__ prefix, so they can be easily indentified.

```html
<div class="b-blockname"> ... </div>
```

### Element

Any element inside a Block, that cannot exist outside the block, is an __"Element"__. Elements have the __"\_\_"__ separator, so they can be easily indentified.

It is required that the full name of the element contains also the name of the Block he is attached to.

The Block and Element should have the same specifity.

```html
<div class="b-blockname">
  <span class="b-blockname__elementname"> ... </span>
</div>
```

```css
.b-blockname {
  ...
}
  .b-blockname__elementname {
    ...
  }
```

### Modifier

If you need to re-use a certain Block or Element, but with a different styling, you can apply a __"Modifier"__. Modifiers should only be used for visual purposes.

Modifiers have the __"--"__ separator, so they can be easily indentified. It is required that the Modifier overwrites the other classes, and doesn't over specifies the rules.

The Modifier should have the same specifity as the Block or Element they modify.

```html
<div class="
  b-blockname
  b-blockname--modifiername
">
  <span class="
      b-blockname__elementname
      b-blockname__elementname--modifiername
  "> ... </span>
</div>
```

```css
.b-blockname {
  ...
}
  .b-blockname__elementname {
      ...
  }

.b-blockname--modifiername {
  /* overwrites */
}
  .b-blockname__elementname--modifiername {
    /* overwrites */
  }
```

# Other naming conventions

We have also borrowed some concepts from SMACCS.

### State

A State defines a special modifier, that can change dynamically (from server, or client). It is the ONLY category of CSS classes that can have CSS styles applied and JavaScript hooks aswell. States have the __"is-"__ prefix, so they can be easily indentified.

```html
<div class="is-hidden"> ... </div>
<span class="is-disabled"> ... </span>
```

### JavaScript Hook

No JavaScript Events should be applied to BEM classes. JavaScript Hooks have the __"js-"__ prefix, so they can be easily indentified.

```html
<div class="js-add-item"> ... </div>
```
