<!-- how easy it is -->

```scss
.container {
  display: grid;
  grid-template-columns: repeat(2, 60ch);
  grid-template-rows: repeat(2, 60ch);

  grid-column-gap: 1rem;
  grid-row-gap: 1rem;
  grid-gap: 1rem;
}
```

<!-- the fr unit -->

similar to flexbox, the fractional unit tries to occupy the available space

```scss
.container {
  display: grid;
  grid-template-columns: repeat(2, 60ch) 1fr; /* this will occupy the rest of the available space*/
  grid-template-rows: repeat(2, 60ch);

  grid-column-gap: 1rem;
  grid-row-gap: 1rem;
  grid-gap: 1rem;
}
```


<!-- other comments -->

using the fr in the template rows-columns, the grid-gap is taken into consideration. it's computed as row-column space.

<!-- how to place grid-item dffierently than its default place -->

```scss
  &--1 {
    background-color: $color--orange;
    grid-row-start: 2;
    grid-row-end: 3;
    grid-column-start: 2;
    grid-column-end: 3;
  }

  // or you can simply put:
  &--1 {
    grid-row: 2 / 3
    grid-column: 2 / 3
  }

  // there's more way to position items in grids, but this is ones are the most widely used
```

<!-- spanning grid items -->

you can achive that by increasing the grid-column start-end. Like this:
```scss
  &--1 {
    grid-row: 2 / 4
    grid-column: 2 / 3
  }
```
we can have multiple grid-items in the same cell
if you want to have visible the overlapped grid-item, set its z-index to a greater one than the "overlapper" grid-item

a better way to span items
```scss
  &--1 {
    grid-row: 2 / 4
    grid-column: 2 / -1 // this means "'til the end".
    grid-column: 2 / span 3 // this means "span 'til column 3".
  }
```

<!-- we can name the grid lines -->

we can name the grid lines, and not let the browser to name them. like this:
```scss
.container {
  padding-top: 2rem;
  width: 80rem;
  height: 60rem;
  margin: 0 auto;
  display: grid;

  grid-template-columns: [header-start] 1fr [header-start box-start] 1fr [box-start main-content-start] 1fr [main-content-end footer-start] 15rem [footer-end];
  grid-template-rows: 1fr 2fr 3fr 1fr;
  grid-gap: 2rem;
}
```
and then we use the names in grid-row and grid-column:
```scss
.sidebar {
  grid-row: box-start / box-end;
}
```
if we encounter the situation when you use the repeat function to define columns or rows, you can either way set each name. like this:


```scss
.container {
  padding-top: 2rem;
  width: 80rem;
  height: 60rem;
  margin: 0 auto;
  display: grid;

  grid-template-columns: repeat(3, [col-start] 1fr [col-end]) 2fr [grid-end];
  grid-template-rows: 1fr 2fr 3fr 1fr;
  grid-gap: 2rem;
}

.header {
  grid-column: col-start 1 / grid-end
}
```

<!-- naming grid areas -->

by using grid-template-areas when you define the areas, and by using grid-area for setting the area to a grid-item
```scss
.container {
  padding-top: 2rem;
  width: 80rem;
  height: 60rem;
  margin: 0 auto;
  display: grid;

  grid-template-columns:
    repeat(3, [col-start] 1fr [col-end]) 2fr [grid-end];
  grid-template-rows: 1fr 2fr 3fr 1fr;
  grid-gap: 2rem;

  grid-template-areas:
    "head head head head"
    "box box box side"
    "main main main side"
    "foot foot foot foot";
}

.header {
  grid-area: head
}
```

we can have empty cells by putting '.' instead of a name. like this:
```scss
.element {
    grid-template-areas:
    "head head head ."
    "box box box side"
    "main main main side"
    "foot foot foot foot";
}

```

justify-content exists too in grid as in flexbox. Their available value vary. But mildly
align-items exists too in grid as in flexbox

there are a few keyword associated with css grid that are worth to know:
min-content max-content and minmanx() function

max-content will set the width/height of a column/row to the content of the biggest column/row. and tries to not make any line-breaks

similar to max-content is min-content. Although it will try to make line-breaks

minmax() works by putting two values in which you want a grid-column/row to stay. like this:

```scss
.element {
  grid-template-columns: repeat(4, minmax(min-contnet, 30rem))
  grid-template-rows: 1fr 2fr 3fr 1fr;
  grid-gap: 2rem;

}
```


<!-- auto-fill and auto-fit -->

```scss
.element {
  grid-template-columns: repeat(auto-fill, 100px)
  // grid-template-columns: repeat(auto-fit, 100px) // it will create as much as tracks as necessary, but it will collapse the unused columns. combining it with minmax you have responsive layouts

  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr)) // THIS IS A HUGE TRICK TO BUILD RESPONSIVE LAYOUTS

  grid-template-rows: 1fr 2fr 3fr 1fr;
  grid-gap: 2rem;
}
```
this, depending on the amount of grid-items we have in the html and the width/height specified it will dynamically create columns/rows