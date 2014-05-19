Goals
* Make an understanding of how transitions work
* Provide a baseline code to get it started
* Provide inspiration and examples
* Provide learnings and tips from around the web
* Provide a gallery of good examples and an explanation of whats happening
* Make any code block a working snippet
* Deadline: Sunday, May 18.

# Transition and Animation Basics

The purpose of this document is to have a quick and simple guide into
CSS Transitions and Animations. It will include the following:

* Basics
* Best Practices
* Tips
* Tools


## Introduction
Now we can animate UI elements and events using only CSS. Before *animations* and
*transitions* were part of the CSS spec, we had to animate only using JavaScript.
*3D Tranforms* were also added to the spec, giving CSS devs more tools to bring
animations to life. As with any new spec implemented with web browsers, we had
to proceed with caution. Mainly for cross browser support and also for poor performance.
Thankfully, browser developers took a serious consideration to optimize this spec.

This document is intended to provide a clear understanding and implementation of
**CSS Transitions** and **CSS Animations**. You will find the basics to get it going,
tips from experts regarding how to implement motion to websites, performance tips
and others. You will also find my takeaway from the articles and tools listed.

**Note:** For the sake of ease of reading, I will be omitting the vendor prefixes.
Depending on your workflow, you can use [Autoprefixer](https://github.com/ai/autoprefixer),
which will parse your CSS and add the prefixes for you (highly recommended), or you
can add them yourself.

```css
-webkit-transition: ...;
   -moz-transition: ...;
     -o-transition: ...;
        transition: ...;
```

## Basics

### Transitions
We use transition when we want to have an animated transition between one state to
another. We would see use it on a `:hover` event, but it can be between an
appended CSS class (`.element.active`).

### Syntax

```css
transition-property: <property>; /* default: all */
transition-duration: <duration>; /* default: 0s */
transition-easing: <easing function>; /* default: ease */
transition-delay: <delay>; /* default: 0s */

/* shorthand for single transition */
transition: <property> <duration> <easing function> <delay>;
```

| Property        | Value(s)                                                      | Example          |
| --------------- | ------------------------------------------------------------- | ---------------- |
| property        | single CSS property or `all`                                  | `color`          |
| duration        | positive number in ms or s                                    | `1.2s`           |
| easing function | `ease`, `linear`, `easein`, `easeout`, `cubic-bezier(timing)` | `cubic-bezier()` |
| delay           | positive number in ms or s                                    | `500ms`          |

For more easing functions, you can find a collection of commonly used easings [here](http://easings.net/), or if
you want to build your own, you can try it [here](http://cubic-bezier.com/).

### Examples

**Basic Example:**

```css
.button {
  background-color: #0896FF;
  transition: all 500ms easein 250ms;
}

.button:hover {
  background-color: #39A38F;
}
```

**Multiple Transitions Example:**

If you wish to have multiple transitions on a single element, you declare a single
transition property, **separated by commas**:

```css
/* shorthand for multiple transitions */
.button {
  background-color: #0896FF;
  color: #333
  transition: background-color 500ms easein 250ms,
              color 250ms easeout 400ms;
}

.button:hover {
  background-color: #39A38F;
  color: #999;
}
```

## Tips
### Visual
* [The 12 Principles of Animation](http://www.subtraction.com/2014/05/04/the-12-principles-of-animation/): [here](https://vimeo.com/93206523) or [here](http://the12principles.tumblr.com/)
* [Nobody Expects 3D](http://aerotwist.com/tutorials/protip-nobody-expects-3d/)
  * TLDR: They 'umpf' your transitions on the screen.

### Performance
* <http://www.html5rocks.com/en/tutorials/speed/high-performance-animations/>

## Tools
* <http://framerjs.com/>
* <http://easings.net/>
* <http://cubic-bezier.com/>

### JavaScript
* <http://julian.com/research/velocity/>