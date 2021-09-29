<!-- basic rules for resetting -->

- in the universal selector: margin, padding & box-sizing: border-box

- global font-related properties: place them in the body. All other elements that inherit font-related proprties will inherit this rules.

- line-height: 1.7  it recieves different untits. It is preferred to use a number without unit. This will be intepreted as a multiplier of the font-size value.


<!-- formatting elements -->

- 95vh: this relative unti will be computed 95% of the viewport height


<!-- image sizes -->

all we need to do is specify the height. The width will scale accordingly. This is the defualt behaviour


<!-- natural order -->

follow the natural order of the html element when styling them. Put the styles in the same order as they are defined in the html


<!-- animations (@keyframes) & browser performance -->

it is better to only animate two different properties: opacity & transform. But it turns out that with transform we can do a lot.

  animation: moveInBottom 5s ease-out .75s;
.75s is the animation-delay property

  animation-fill-mode: backwards;
this applies the values defined in the animation **before the animation starts**


<!-- the 'initial' value -->

a special css value that holds the element value when it was first loaded


<!-- links and pseudo selectors -->

:link is the initial state


<!-- pseudo-elements & pseudo-selectors -->

- the order as always is important -> .btn:hover::after {}
- if you have to use them in a rule, remember that the pseudo-elements are always placed AFTER the pseudo-selectors.


<!-- transform: scale() -->

you can use scaleX, scaleY or use scale(valueX, valueY), or scale(value)


<!-- three pillars of web design -->

responsive design - maintanable & scalable code - web performance

- responsive design: fluid layouts, media queries, responsive widths, correct units, desktop-first vs mobile-first

- maintanable & scalable code: clean, easy to understand, reusable, how to name classes, how to structure html

- web performance: less http requests, less code, compress code, less images, compress images


<!-- loading css when the browser is loading a web page -->

the browser start by parsing the html and building the DOM

then it parses the css by resolving the possible conflicts in declarations by overwriting the values that are set each time they are set: the CASCADE

after all of the rules and values are set, the css is stored in a tree-like structure, the CSSOM, similar to the DOM

these two parts is what is know as the **RENDER TREE**, and with all of this, we can render the page.

in order to render the page, the browser uses something called the **visual formatting model**. It is important to know how it is defined because our code will affect how the browser actually renders the page

with all this processes done, the page is finally rendered


<!-- how css is parsed -->

the browser combine styles from three sources: author - user - browser (user agent)

the rule is: **IMPORTANCE > SPECIFICITY > SOURCE ORDER**

IMPORTANCE:
1. user !important declarations
2. author !important declarations
3. author declarations
4. user declarations
5. default browser declarations

SPECIFICTY:
1. inline styles
2. ids
3. classes, pseudo-classes, attributes
4. elements, pseudo-elements

ORDER:
if more than one declaration have the same importance and speceficity, the declaration that was declared last is the one that applies

- the universal selector (*) has no specificity value
- the css declarations that have !important have the highest priority
- but inline styles will always have prioroty over styles in external stylesheets
- rely on order when using 3rd party stylesheets. always put your author stylesheet last
- if a rule don't apply, among other things, check if there's another rule that has higher specificity


<!-- how css values are processed -->

each element has to have a value, even if it is not declared. This is the process of how the browser finally determines it:

1. declared value: author declaration
2. cascaded value: after cascade
3. specified value: defaulting to a initial one that prvides the browser if there's no cascade value
4. computed value: converting relative values to aboslute
5. used value: final calculations, based on layout
6. actual value: broswer and device restrictions


<!-- how units are converted from relative to absolute (px) -->

the percentage (%) for fonts - the percentage (%) for lengths are treated differently

fonts: parent computed font-size
lengths: parent computed **width**

the em for fonts - the em for lengths are treated differently

fonts: parent computed font-size
lengths: current element computed **font-size** (OJO-CUIDAO!)

the em for fonts - the em for lengths are treated differently

fonts: :root element font-size
lengths: :root element font-size


<!-- viewport-based units -->
vh: viewport height
vw: viewport width


<!-- inheritance in elements -->

some properties, like the ones related to text, INHERIT the computed value from its parent elements. Some others, not.

what is inherited is the computed value, not the specified value

other properties, like margin, padding.. aren't because styling like this would be so much tedious

inheritance only works if no one declares a value, of if its declared to the keyword 'inherit'


you must specify in the universal selector ::before and ::after, otherwise the 'reset' rules doesn't apply to them

<!-- the root element -->

the root element in an html document is html


<!-- a good practice for setting units -->

set the font-size to 62.5%, so now the rest of unit declarations that uses rem, which should be the majority, will be much more easier for us to think and set, because they are multiples of 10, which is the final computed value

you use percentages because this way you don't override the user font-size that may have set in their browser. By using 10px would you lock this ability


<!-- old browsers and rem -->

they are not supported in old browsers


<!-- box-sizing in the root element -->

in the universal selector you set it to 'inherit' because by default it is not inherited and then put it in the body selector and set it to 'border-box' again.

now we're forcing inheritance.


<!-- the visual formating model -->

is an algorithm that calculates boxes and determines the layout of theese boxes, for each element in the render tree, in order to determine the final layout of hte page

it takes into account:
- dimensions of boxes: the box model
- box type: inline - block - inline-block
- position scheme: floats and positioning


<!-- block-level boxes -->

- are elements formatted visually as blocks.
- occupy 100% of parent's width. As much as space as possible
- are placed VERTICALLY one after another
- box-model applies as showed


<!-- inline-level boxes -->

- height & width don't apply
- their content es distributed in lines
- occupy only content's space
- no line breaks
- no heights nor widths
- padding & margins only horizontal


<!-- inline-block boxes -->

- occupies only content space
- no line breaks
- box-model applies as showed


<!-- stacking contexts -->

z-index is the most known property that creates new stacking context, but there's other properties that do this: opacity different than 1, a transform, a filter or other properties also create new stacking contexts


<!-- BEM, BABY!! -->

- think > build > architect

- block__element-modifier

- you set names based on if the element is a standalone block, not related to its parent, possibly used in other part of the page

<!-- the 7.1 pattern -->

- there are 7 different folders for partial sass file,

- and 1 main sass file to import all other files into a compiled css stylesheet. the foders are:
- base: basic project definitions
- components: one file per each component
- layout: the layout of the project
- pages: styles for specific pages of the project
- themes: different visual themes
- abstracts: code that doesn't output any css, like variables or mixins
- vendors: third-party css


<!-- main sass features -->

- list of features: variables - nesting - operators - partials & imports - mixins - functions - extends

- line comments are allowed in sass

- sass & scss are two syntaxes. scss stands for sassy css, and is the same css syntax but with the added css features, while in sass you don't use brackets, and the indentation is interpreted as nesting


<!-- sass: variables -->

name of the variable preceded by $. Like in $color-primary. You put them outside of any selector (in global space)


<!-- is it better to write a:link instead of a? -->

not really. It is more correct though. it is how it was defined its first state, :link.


<!-- nesting is awesome but beware! -->

'&' represents the current selector, like in this situation, and it's ussually used in pseudo-classes. So, don't forget!

.navigation {
  list-style: none;

  li {
    display: inline-block;
    margin-left: 30px;

    &:first-child {
      margin: 0;
    }
  }
}


<!-- floats -->

if you use float: right in a group of elements and float: left in an another adjacent group, it will trigger is a collapse, and the child elements will lose its height.


<!-- add a clearfix -->

to solve the issue of collapsed heights, you use the clearfix method. you put a clearfix class in the parent container and in the scss file you put this

.clearfix::after {
  content: '';
  clear: both;
  display: table;
}


<!-- color functions -->

darken($color-secondary, 50%)


<!-- mixins -->

think of them as a group of variables. A piece of repeatable css, like this:

@mixin clearfix {
  &::after {
    content: "";
    clear: both;
    display: table;
  }
}

and you add it by using the keyword '@include', like this

nav {
  margin: 30px;
  background-color: red;

  @include clearfix;
}

**you can pass arguments to mixins!!**

@mixin style-link-text($color) {
  text-decoration: none;
  text-transform: uppercase;
  color: $color;
}

.highlighted {
  @include style-link-text(red)
}


<!-- sass functions -->

not really that much used. Like this:

@function add($a, $b) {
  @return @a + @b
}

nav {
  margin: add(30, 2) * 1px; // you need to multiply by 1px in order to sass to add the unit
  background: red;
}


<!-- sass extends -->

extends are meant as common placeholders. again, not really not that much used.

When to use mixins and when extends? actually both are capable of doing the same job, but **if you don't want to repeat compiled css code, use extends**, when the elements you are extending are pretty related.



<!-- setting colors in sass  -->

you can set them by assigning a color and then the opacity, in rgba()
  rgba($color-primary-light, 0.8),



<!-- sass is awesome for writing nesting selectors -->

you can convert this:

```css
header {
  height: 95vh;
  background-image: linear-gradient(
    to right bottom,
  rgba($color-primary-light, 0.8),
  rgba($color-primary-dark, 0.8)
  ),
    url(../img/hero.jpg);
  background-size: cover;
  background-position: top;

  clip-path: polygon(0 0, 100% 0, 100% 75vh, 0% 100%);
  position: relative;
}

.header__text-box {
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}
```

to this:
```scss
header {
  height: 95vh;
  background-image: linear-gradient(
    to right bottom,
  rgba($color-primary-light, 0.8),
  rgba($color-primary-dark, 0.8)
  ),
    url(../img/hero.jpg);
  background-size: cover;
  background-position: top;

  clip-path: polygon(0 0, 100% 0, 100% 75vh, 0% 100%);
  position: relative;

  &__logo-box {
    position: absolute;
    top: 4rem;
    left: 4rem;
  }
}
```

*use the power of th '&' operator!*


<!-- partials -->

partial files always start with _


<!-- responsive design basics (RDB): fluid grids and layouts -->

use % rather than px for all layout-related lengths

images behave differently than text content, and so we need to ensure that they also adapt nicely to the current viewport. This is achieved usually by using %. But we'll expand this later.

to apply different styles to the same html elements depending on certain viewport widths or much more, we use media queries



<!-- layout types -->

float - flex - grid


<!-- LAYING OUT WITH FLOATS  /////////////////////////////////////-->

```scss
.row {
  width: 114rem;
}

/* the process is: I want 1140px. So I divide it by 10 so I can transform it to rem. But we're not finished yet. We swap max-width for width. This property tells the browser: 'if you have enough space, take the value I set. If not, take the available space. That is, 100% of the available space'.


*/
```


```scss
.row {
  width: $grid-width;
  background-color: #eee;
  margin: 0 auto;
  margin-bottom: $gutter-vertical;

  &:not(:last-child) {

  }
}
// with &:not(:last-child) {} we're selecting everything that's not the last-child within a .row

*/
```

not always have to rely on the power of sass. There are already existing css functionalities that are really powerful, like the attribute selector

[class^="col-"] {} ^= means 'starts with "col-"'

[class$="col-"] {} *= means 'ends with "col-"'

[class*="col-"] {} *= means 'contains "col-"'


<!-- how to build an architect mindset -->

you start by creating the html element tree, then you style it

try not to mentally calculate too often, and let the browser lift that weight for you. Try to keep in mind the heights - widths - respecitve units of the elements, and add-substract them, always in a relative unit


<!-- how to use utility classes -->

utlity classes are classes used all around the project, that are made to be very reusable


<!-- how to use background-clip -->

if you want to generate text with a gradient as a color fill, you put a background-clip with the desired gradient, then 'background-clip: text', then color: transparent -> so you can see the gradient, not the text color.


<!-- how to transform properties simlutaneously -->

you can put multiple transform in one sigle property definition, like this:

transform: scale(1.2) rotate(30deg) translate(20% 0)

observe that the different transforms are separated JUST **BY A SPACE** character


<!-- how to use outline-offset together with outline -->

you can make a block elemtent grow its 'border' (it's not its border, but its outline) by setting 'outline', and make it grow with outline-offset


<!-- how to style elements that are NOT hovered while other are -->

like this. this will select those whore aren't hovered. All of them:

.composition:hover composition__photo:not(:hover) {
  transform: scale(.95)
}

this will select the hovered:

.composition composition__photo:hover {
      transform: scale(1.05) translateY(-.5rem);
      box-shadow: 0 2.5rem 4rem rgba($color-black, .5);
      z-index: 20;
    }


<!-- other comments -->

BEM is used all around the projects. Keep in mind that the utility classes are treated as standalone elements.

you can just put really small values in px, since in order a value to grow in such a tiny proportion, the font-size should be much more larger: **3px is OK to be px, because in order it would like to change to 6px the root font-size would like to be 32px**

anyway, you're playing safe by putting as much as you can relative units

it is best practice to set image width values to percentages in order to scale them correctly depending on parent width

how to set something on top of others? with z-index. the parent set to one number and set to one greater when hover

the best way to move around a floated element is by using transform: translate() rather than positions/margins/paddings

if you want to remove some minor issues with animations, sometimes using backface-visibility: hidden solve these mionr problems

attribute order in HTML. first, the ones related to identify the element (class, id, name, data-*). then those that link its content, except for (src, for, type, href, value). then title - alt. and then the accessibility values
  - class
  - id, name
  - data-*
  - src, for, type, href, value
  - title, alt
  - role, aria-*

& is necessary for buttons that aren't links, because links have pseudo classes, but not regular buttons

if you want to make a line that takes all the space **THE CONTENT TAKES**, you can try display: inline-block

in order to transform-translate something, you have to first set the element to something different thant 'inline'

by styling a native html popup, we can put it wherever we want. It doesn't matter if it's on top of the document, in the middle or in the bottom.

if what we really want is two sibling elements sharing the SAME HEIGHT, we cannot use floats, we must use display: table-cell

I repeat: we have to merge the transforms. css nor sass will do it for us. The browser cannot merge two css transforms.

in the shorthand version of transition, the (optional) THIRD value is transition-delay

if during responsive adaptation you have issue, try to use !important. But don't abuse.

regarding media queries, it is considered bewst practice to first add @media only screen and ..., like this:
@media only screen and (max-width: 30rem) {}

regarding media queries too, if we want to target devices that doesnt accept hover behaviour, do this:
@media only screen and (hover: none) {}



<!-- how and when to use the direct child selector -->

when you want to select only the containers (direct children) of a parent, beacuse if you select all its children the effect applies to all of the children of the first parent. like this:

& * {} // this will probably not yield good results

first you skew all your content, then you "unskew" (skew in the opposite way and value) the elements you want to "restore"


<!-- another way on how to create 'skewed section' design -->

like this. all of direct children of a selector:
& > * {}

<!-- how to make a 'flip' transition -->

.card {
  background-color: orangered;
  height: 50rem;
  transition: all .5s;

  &:hover {
    transform: rotateY(180deg);
  }
}


<!-- how to use 'perspective' -->

the lower the value, the more dramatic the flipping effect is


<!-- how to use background blend modes -->

is pretty self-explanatory: like in programs like photoshop, with it, you set how you want to blend your MULTIPLE backgrounds.


<!-- how and when to use 'box-decoration-break' -->

**LA MAGIA!!! como conseguir que un texto cortado por falta de espacio conserve o no su padding?**

box-decoration-break: clone

what it does is **apply the defined style to all of the boxes generated in the same element**. So if there's a line of thext that is broken/split in two or more boxes for whatever reason, it will treat each box as a different element.


<!-- clarifications about the BEM methodology -->

it may seems that it does, but actually there's **NO ELEMENT NAME NESTING**. If there's no depedency between elements, the name doesn't have to reflect it. **BUT! IT DOES HAVE TO REFLECT IT with the block part, though!**. Like this:

<div class="card">
  <div class="card__side card__side--front">
    <div class="card__picture"></div>
  </div>
</div>


<!-- vendor prefixing React components -->

don't worry too much. styled-components automatically prefixes the styles


<!-- how to make text flow around shapes using shape-outside & float -->

in order to accoplimsh this, ou have to have defined the width, height and the element must be floated


<!-- how to apply filter to images -->

you can have multiple filters applied, separated only by a space character. No comma. Like in the multiple transforms.


<!-- multiple values in properties -->

for box-shadow: ','
for border: ','
for filter: ' '
for transform: ' '
for defining steps, after the color: ' '
for separating whole steps in linear gradients: ','


<!-- how to create a background video covering an entire section -->

in order to d that, you must put the video element the first tag of the container


<!-- how to use the video element -->

intead of using the src attribute like in the img tag, we use the <source> tag inside the video element

if for whatever reason the tag is not supported, the text contents of th video element will render

some nice options are autoplay - muted - loop


<!-- how and when to use the object-fit property -->

object-fit: cover is similiar to background-size: cover. It allows to fit the entire element while preserving its aspect ratio. it works with imgs too. object-fit is more versatile and more available across browsers

<!-- backgrouns-size: cover -->

background-size: cover and background-size: 100% means the same thing. It's 100% of the width. It 'covers' the entire (100%) width of the element

<!-- how to implement 'solid color gradients' gradients in-depth & how to create a shadow effect in an element with a background-image -->

experiment with steps in gradients. It will generate cool effects. The whole step colors are defined by a color followed by an (optional) percentage after the color, separated by a space (' ') character. each step is separated by a comma. like this:
```scss
.book {
  background-image:
    linear-gradient(
      105deg,
      rgba($color-white, 0.9) 0%,
      rgba($color-white, 0.9) 50%,
      transparent 50%,
      rgba(black, .1) 50%,
      transparent 52%,
    ),
}
```
look at rgba(black, .1) 50%, transparent 52%... it creates a shadow effect using a background-image!

<!-- how the general and adjacent sibling selectors work and why we need them -->

general sibling selector (~) and adjacent, the direct one, sibling selector (+). like this:
```scss
&__input:placeholder-shown + &__label {}
```

OJO! the order of the elements matters a lot. Select them in the same order they appear in the html. otherwise it won't work!


<!-- how to use the ::input-placeholder pseudo element -->

(not actually that much used..)


<!-- how and when to use the :focus, :invalid, :placeholder-shown and :checked pseudo classes-->

in forms, it becumes really useful. like this:
```scss
&:focus:invalid {}
```


<!-- some techniques to build custom radio buttons -->

the trick is to create three elements: input:radio - label - span

you hide the radio button, connect the label with the radio button, and style the span

when styling the rbutton, you make useof the ::after element for styling the :clicked behaviour

you have to set the element to inline-block, and position: absolute


<!-- how to translate this sass architecture to a React project while using styled-components (or not) -->

the process is pretty straightforward: you keep the same structure you've learned, but you change the path where you store the component and page (sometimes known as 'container') styles. Those styles will be managed by styled-components now.

If you use only sass, use it in an external scss file and place it along the same directory (individual directory) of each component. Then, reference it in the main.scss file for node-sass being able to process it.

create-react-app is preconfigured so you can write and use sass by default. It automatically detects sass changes and compiles the files.


<!-- some browser behaviour -->

browsers by default doesn't preserve the inheritance of font properties set by the user. You have to manually reset them.


<!-- opacity: 0 vs display: none vs visibility: hidden -->

opacity: 0 preserves space but not visible
visibility hidden not preserve space not visible
display none element is not rendered

in animations it is useful. Yuo cannot animate visibility nor display. But you can animate opacity


<!-- form creation basics -->

in order the browser to consider a group radio buttos an actually radio group, you have to set their attribute name at the same value


<!-- what the 'checkbox hack' is and how ot works -->

it's similar to the 'radiobutton hack' for styling radiobutton forms. 3 steps:
1. have a hidden checkbox
2. have a label connected to that checkbox
3. reveal the entire navigation in the background

We start by putting the navigation **ON TOP OF EVERYTHING ELSE**


<!-- hide overlapping elements -->

you can do it with opacity: 0 and then width: 0, because if you don't set the width, the elements are still selectable in the ui


<!-- how to create custom animation timing functions using cubic bezier curves -->

using cubic-bezier instead of ease-in/ease-in-out amd so on...


<!-- how to animate 'solid color gradients' -->

by animating its background-size, by using linear-gradients


<!-- how to animate a hamburguer icon -->

by playing with a box that resembles a stroke. You then play with ::after and before pseudoelements, by removing them and transforming them using animations @keyframes.


<!-- how and why to use transform-origin -->

you could actually use this property, but we didn't have to use it because we achieved our goal by using top: 0;

transform-origin is self-explanatory. Indicates de point where the animation will start applying


<!-- how to use the :target pseudo-class -->


1. we set the popup to opacity: 0, visibility: hidden & transition: whatever
2. we set the element:target to opacity: 1 & visibility: visible
3. we create a 'close popup' element (a cross icon for instance). we style it & we set its target to another element. by doing this the pseudo-class:target is no longer applied, and the popup dissapears.

<!-- how to create boxes with equal height using display: table-cell -->
<!-- how to create css text columns -->

using column-count and column-gap. Like this:
```scss
  &__text {
    font-size: 1.4rem;
    margin-bottom: 4rem;

    column-count: 2;
    column-gap: 2em;

  }
```
<!-- how to automaically hyphenate words using hyphens -->

an interesting note about hyphens is, supposedly, that it will break and words hyphenate them properly, **based on the language of the page**!! it's pretty well adopted by the majority of browser. But don'tcount too much on it.

column-gap is still not well adopted.


<!-- responsive design strategies -->

like in the rest of the css rules, it still aplies the same property comflicting strategy. So in media-queries is as much as important the order on we specify them. And because of this, we write the media queries at the end of the stylesheet.


<!-- deciding the website breakpoints -->

you can decide it based on breakpoint already set by frameworks, like Bootstrap. But even better, you set breakpoints based on your specific design. You set a breakpoint when your design breaks, or starts to look wrong. You set the breakpoint and correct the design. And iterate, until the design feels right for the entire range of device-widths.

either way, you must select at least four breakpoints: phone - protrait tablets - landscape tablets - desktop - (even another) big desktop

in the desktop-first approach: max-width
in the mobile-first approach: min-width

usual breakpoints:
in a desktop-first approach we'll write max-width for all four breakpoints, and a min-width for the last one
1. 0 - 600 phone
2. 600 - 900 tablet portrait
3. 900 - 1200 tablet landscape & desktop
4. 1200 - 1800 ----> where our normal styles apply
5. 1800 big desktop

<!-- how to write mixins to write all of our media queries into one single mixin -->



<!-- how to use the @content and @if directives -->

@content allows you to pass entire blocks of code to your mixin. This is very useful to write and apply media-queries.

actually, a combination of @content and @if makes powerful media-query manager

```scss
/* $breakpoint argument choices
  phone
  tab-port
  tab-land
  big-desktop
*/
@mixin responsive($breakpoint) {
  @if ($breakpoint == 'phone') {
    @media (max-width: 600px) { @content; };
  }

  @if ($breakpoint == 'tab-port') {
    @media (max-width: 900px) { @content; };
  }

  @if ($breakpoint == 'tab-land') {
    @media (max-width: 1200px) { @content; };
  }

  @if ($breakpoint == 'big-desktop') {
    @media (min-width: 1800px) { @content; };
  }
}

ONE IMPORTANT THING, the ems and rems specified in media-queries are not dynamic to what the user ends up setting them, but what the browser set their font-size. So, if the final user who consumes the web have the browser preferences a font-size value of 20px, THAT will be their base for rems and ems, not the one tht user (webdev) specifies in the stylesheet.a1

Because of this the conclusion is: better use ems. Because is probably set always to 16px and the final user doesn't bother in changing the font-size and still is a dynamic value.

as said before, in media queries, IN DESKTOP-FIRST approach, place larger media queries first, like this:

```scss
html {
  font-size: 62.5%; // this defines what 1 rem is

  @include responsive(tab-land) { // width < 1200
    font-size: 56.25%; // 1rem = 9px -> 9/16 = 56.25%
  }

  @include responsive(tab-port) { // width < 900
    font-size: 50%; // 1rem = 8px -> 8/16 = 50%
  }

  @include responsive(phone) { // width < 600
    font-size: 43.25%; // 1rem = 7px -> 7px/16px = 43.25%
  }

  @include responsive(big-desktop) { // width > 1200
    font-size: 75%; // 1rem = 12px -> 12/16 = 75%
  }

}
```
why is that the order? imagine you have a *700px* device width. The rule that is applied is the LAST DECLARED. So there's two media-queries that trigger here: < 900 and < 1200, and we want the media query that's *closer to the device width*. The order inverts when we adopt a mobile-first approach.


<!-- PROTOCOL FOR IMPLEMENTING MEDIA-QUERIES -->
1. base & typography
2. general layout & grid
3. page layout
4. components


<!-- reponsive images -->

load images based on 3 different use cases:
resolution switching: decrease resolution based on device resolution
density switching: decrease resolution based on device pixel density
art direction: load different but context similar images, usually lighter ones

all of them use html manipulation


<!-- using desity switching images -->

if the device where the page renders has a low-demsity screen, load 1x. and so on. like this:
<img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" alt="Full logo" class="footer__logo">


<!-- using resolution switching images -->

you set picture, you set source. On source, you establish srcset and media attributes. You add the media query. You force the browser to use one srcset based on the media query you specify.
<picture class="footer__logo">
  <source
    srcset="img/logo-green-1x-small.png 1x, img/logo-green-2x-small.png 2x"
    media="(max-width: 37.5em)"
  >
  <img
    srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x"
    alt="Full logo"
    class="footer__logo"
  >
</picture>


<!-- how to implement responsive images in css -->

it can be achieved by using media queries, such as min-resolution. but it's not widely accepted.


<!-- media queries power -->

you can use logic operators and make powerful media query rules. like this

// 192dpi is the iphone resolution
// the comma means here the OR operator

@media (min-resolution: 192dpi) and (min-width: 600px), (min-width: 2000px) {}


<!-- testing if a property is supported and useful degradation -->

you can test if a property is supported using @supports. If you want to still use the top-notch capabilities of the latest browser and still provide a nice experience por the older ones, use this query. like this:

@supports (-webkit-backdrop-filter: blur(12px)) or (backdrop-filter: blur(12px)) {
  -webkit-backdrop-filter: blur(12px);
  backdrop-filter: blur(12px);
  background-color: rgba(red, .3);
}

