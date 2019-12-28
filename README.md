# SASS mixins
## RWD
### Description:
Basic mixin for simplified usage of CSS media queries (width breakpoints, touch & custom values).
Defaults to desktop-first*.

### Usage:
* Desktop-first breakpoint:
  ```
  @include rwd(xs) {
    font-size: x-small;
  }
  ```
  produces: 

  ```
  @media (max-width: 600px) {
    font-size: x-small;
  }
  ```
* Mobile-first breakpoint:
  ```
  @include rwd(l, true) {
    line-height: 2;
  }
  ```
  produces: 
  ```
  @media (min-width: 1601px) {
    line-height; 2;
  }
  ```
* Touch media query:
  ```
  @include rwd(touch) {
    padding: 2em;
  }
  ```
  produces:
  ```
  @media(pointer: coarse) {
    padding; 2em;
  }
  ```
* You can also use custom media queries. In this case: 
  ```
  @include rwd(666px) {
    color: #f00;
  }
  ```
  would produce:
  ```
  @media (max-width: 666px) {
    color: #f00;
  }
  ```

*\*) If you prefer to use mobile-first as default (as you should 🙄 - this is coming from a desktop-first project), change the `false` in the first line to `true` like so: `@mixin rwd($query, $mobileFirst: true) {// ...}`*

## Smooth shadow
### Description
Creates a smoother box shadow by overlaying five shadows with increasing radii and offsets combined with color with 20% opacitt

### Usage:
`@include shadow(horizontal offset, vertical offset, color);`
For example:
* `@include shadow(5px, 10px, #222);`
* `@include shadow(0, 1rem, $shadow-color);`
* `@include shadow(1ex, 2ch, var(--shadow-color);`
* and so on

## Linear gradient
### Description
Allows you to create a simple (horizontal, vertical or 45° diagonal) two-color gradient

### Usage:
`@include gradient(orientation, starting color, end color);`
Where `orientation` can be one of the following:
* `vertical`
* `horizontal`
* `diagonal-tl` (from top left to bottom right)
* `diagonal-tr` (from top right to bottom left)

So, for example, `@include gradient(diagonal-tl, #b00b1e, #bada55);` produces `background-image: linear-gradient(to bottom right, #b00b1e, #bada55);`
