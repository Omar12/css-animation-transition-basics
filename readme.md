# Transition and Animation Basics

## Introduction
Now we can animate UI elements and events using only CSS. Before *animations* and
*transitions* were part of the CSS spec, we had to animate only using JavaScript.
*3D Transforms* were also added to the spec, giving CSS devs more tools to bring
animations to life. As with any new spec implemented with web browsers, we had
to proceed with caution. Mainly for cross browser support and also for poor performance.
Thankfully, browser developers took a serious consideration to optimize this spec.

This document is intended to provide a clear understanding and implementation of
**CSS Transitions** and **CSS Animations**. You will find the basics to get it going,
tips from experts regarding how to implement motion to websites, performance tips
and others. You will also find my takeaway from the articles and tools listed.

**Note:** Vendor prefixes are being omitted.
I advise to integrate to your workflow [Autoprefixer](https://github.com/ai/autoprefixer),
it will parse your CSS and add the prefixes for you (highly recommended). Of course,
you can add them yourself.

```css
-webkit-transition: ...;
   -moz-transition: ...;
     -o-transition: ...;
        transition: ...;
```
## Transitions
Transtions are used when we want to animate from one state to
another. We would see use it on a `:hover` event, or with an appended CSS
class (`.element.active`).

### Syntax

```css
transition: <transition-property> <transition-duration> <transition-timing-function> <transition-delay>;
```

| Property                   | Value(s)                                                        | Example          |
| -------------------------- | --------------------------------------------------------------- | ---------------- |
| transition-property        | single CSS property or `all`                                    | `color`          |
| transition-duration        | positive number in ms or s                                      | `1.2s`           |
| transition-timing-function | `ease`, `linear`, `ease-in`, `ease-out`, `cubic-bezier(timing)` | `cubic-bezier()` |
| transition-delay           | positive number in ms or s                                      | `500ms`          |

*(For more information and the longhand format, [click here](https://developer.mozilla.org/en-US/docs/Web/CSS/transition))*

#### Timing Functions
* [Easings.net](http://easings.net/) - List of Easings functions and values.
* [Cubic-Bezier.com](http://cubic-bezier.com/) - Build and try your own easing.

### Examples

**Basic Example:**

```css
.button {
  background-color: #0896FF;
  transition: all 500ms ease-in 250ms;
}

.button:hover {
  background-color: #39A38F;
}
```

**Multiple Transitions Example:**

If you wish to have **multiple transitions** on a single element, you declare a single
transition property, **separated by commas**:

```css
/* shorthand for multiple transitions */
.button {
  background-color: #0896FF;
  color: #333
  /* transition background-color and color at different durations */
  transition: background-color 500ms ease-in 250ms,
              color 250ms easeout 400ms;
}

.button:hover {
  background-color: #39A38F;
  color: #999;
}
```

## Animations

### Syntax

```css
animation: <animation-name> <animation-duration> <animation-timing-function> <animation-delay> <animation-iteration-count> <animation-direction> <animation-fill-mode>;
```

| Property                    | Value(s)                                                      | Example           |
| --------------------------- | ------------------------------------------------------------- | ----------------- |
| `animation-name`            | name that matches the @keyframes name                         | `spinning`        |
| `animation-duration`        | positive number in ms or s                                    | `1.2s`            |
| `animation-timing-function` | `ease`, `linear`, `easein`, `easeout`, `cubic-bezier(timing)` | `cubic-bezier()`  |
| `animation-delay`           | positive number in ms or s                                    | `500ms`           |
| `animation-iteration-count` | `infinite`, number `1` or non-integer (`0.5`, `1.3`)          | `3`               |
| `animation-direction`       | `normal`, `reverse`, `alternate`, `alternate-reverse`         | `normal, reverse` |
| `animation-fill-mode`       | `none`, `forwards`, `backwards`, `both`                       | `both`            |

*(For more information and the longhand format, [click here](https://developer.mozilla.org/en-US/docs/Web/CSS/animation))*

**Keyframes and `<animation-name>`**

To properly use animation, you will need to define an animation by using the `@keyframes`
property and giving it a name.

```css
@keyframes to-from-anim {
  to {...}
  from {...}
}

@keyframes perc-anim {
  0% {...}
  25% {...}
  50% {...}
  100% {...}
}
```

### Examples

**Basic Example:**

```css
.loader {
  position: absolute;
  width: 2em;
  height: 2em;
  border-radius: 50%;
  animation-fill-mode: both;
  animation: circlemove 1.8s infinite ease-in-out;
}

@keyframes circlemove {
  0%,
  80%,
  100% {
    left: 0;
  }
  40% {
    left: 100%;
  }
}
```





## Tips
### Visual
* [The 12 Principles of Animation](http://www.subtraction.com/2014/05/04/the-12-principles-of-animation/): [here](https://vimeo.com/93206523) or [here](http://the12principles.tumblr.com/)
* [Nobody Expects 3D](http://aerotwist.com/tutorials/protip-nobody-expects-3d/)
  * TLDR: Tips to make your transitions buttery smooth.

### Performance
* <http://www.html5rocks.com/en/tutorials/speed/high-performance-animations/>
* <http://csstriggers.com/>

## Tools
* <http://framerjs.com/>
* <http://easings.net/>
* <http://cubic-bezier.com/>

### JavaScript
* <http://julian.com/research/velocity/>
