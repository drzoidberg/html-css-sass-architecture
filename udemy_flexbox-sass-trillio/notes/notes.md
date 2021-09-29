<!-- flexbox -->

the main idea behind flexbox is to give a container the ability to expand or shrink elements to best use all the available space

flexbox replaces floats using less & more readable code

if you set a flex-container with flex-direction: column, its flex-items will expand to occupy the available space, but if you set flex-direction: row it will behave like it was all inline

flex-grow - flex-shrink - flex-basis: it it sets the ability of a flex-item to grow/shrink... the final behaviour is the result of the computing of all grow/shrink... of all the flex-items. if a the majority of flex-items has flex: 1 and other has flex: 2, this one will occupy the double space.


<!-- occupy all space available -->

a trick for a flex-item to occupy as much space as it can (each one of them evenly) is set its flex: 1. If you set it just for one element in the flex-container, only this one will occupy its available space. The others occupy the rest of the space (if they have their own margin/padding...).

flex-basis set width based on percentage of the flex-container

even if we set flex-basis or flex-grow, if th space available gets lessen, it will. If we want to prevent this bevaviour, *we set flex-shrink to 0.*

align-items aligns the flex-items, but align-content aligns *rows* of content


<!-- the global reset -->
```scss
* {
  margin: 0;
  padding: 0;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}

html {
  box-sizing: border-box;
  font-size: 62.5%; // 1rem -> 10px
}
```

<!-- css custom properties -->

what's really cool about css variables is that they are accessible and set via javascript!

futhermore, this variables CASCADE and ARE INHERITED

**the :root pseudo-class is just like the html selector but with higher specificity.**

css custom properties have to be defined within a declaration block. And the usual one is the :root pseudo-class. By putting the css vars in the :root pseudoclass we ensure those will be available in the entire document

they can store all kinds of values


<!-- the shorthand for flex property order -->

flex: (flex-grow) (flex-shrink) (flex-basis)
usually is set like this:
flex: 0 0 18%, for example


<!-- svg files + sprites, baby!! -->

one single http request and then you fetch all images. All you have to do is focus on which part of the same image you want to render, with backgroound-position.


<!-- the best way to use svgs -->
```xml
<button class="search__button">
  <svg class="search__icon">
    <use xlink:href="img/sprite.svg#icon-magnifying-glass"></use>
  </svg>
</button>
```
one thing to keep in mind is, the method described here, using the xlink:href attribute, will only work on web servers. Having said that, it is the best way to handle svgs + sprites


<!-- other comments -->

```css
p.parrafazo {
  color: currentColor;
}
```
currentColor es una variable que se resuelve al valor seteado del propio elemento o de su elemento padre. it's rally well supported. it allows you to not reassign the same color value once the color is already set.

by default transform-origin is set to center

for and advanced use of trnasitions, you can set the shorthand transition property like this. <property> <duration> <timing-function> <delay>, like this:
```css
.navigation-item {
  transition:
    transform .2s,
    width .4s .2s;
}
```

z-index only works if the element has a position different than the initial specified.

css vars can contain other css vars

transitions doesn't work for background-images


<!-- margin: auto + flexbox -->

it aligns the content to where you set it, but the content will only occupy what's necessary for it. like this:

```scss
&__stars {
  // flex: 1;
  margin-right: auto;
  background-color: tomato;
}
```


<!-- css mask -->

still not widely accepted across browsers


<!-- as a rule of thumb for spacing with flexbox -->

use flex. Set the first box to 0 0 value, and the other to 1. Like this:

```scss
.primary-content {
  flex: 0 0 60%;
}

.secondary-content {
  flex: 1;
}

```

<!-- making list columns using flex is relatively easy -->

you have to 1. set display: flex, then set flex-wrap: wrap, then set its flex-items its flex: no grow, no shrink, and set its basis to 50% ot the amount of fixed space you want to set. like this:

```scss
.list {
  list-style: none;
  margin: 3rem 0;
  padding: 3rem 0;
  border-top: var(--line);
  border-bottom: var(--line);

  display: flex;
  flex-wrap: wrap;

  &__item {
    flex: 0 0 50%;
  }
}
```

masks are useful but poorly supported. mas-size is pretty useful.

remember: z-index only works when the element has set position

<!-- html entities in css -->

html entities in css are formatted differently than in html. We use the ISO formatting


<!-- how to make css queries that supports X feature -->

```css
  @supports (-webkit-mask-image: url()) or (mask-image: url()) {}
```

they have to have key - value pairs set.