Taffy
=====

## A sweet responsive grid.
### ...with grid based breakpoints.

## Overview
Taffy is a grid system that only outputs the CSS you need and automatically extends classes when possible. By default Taffy uses flex and calc to ensure accuracy according to the browser, rather than use percentages with floating points. Taffy also includes grid based breakpoints and a fixed grid option (still responsive) that works well for product grid style layouts.

## Grids
Grids contain items. All this class does is initiate flex.

```html
<div class='grid'>
  <!-- items -->
</div>
```

## Breaks
Breaks create media queries based on item widths. This break will be activated when the browser width exceeds the 4th break, which is equivalent to the width of 4 out of 12 items. This is based on the `max-width` and `taffy-amount` variables.

```scss
.break {
  @include break(4) {
    // ...
  }
}
```

## Items
Items go inside grids. Items wrap to a new line when the item limit has been reached.

```html
<div class='grid'>
  <div class='item'></div>
  <div class='item'></div>
  <!-- break -->
  <div class='item'></div>
  <div class='item'></div>
</div>
```

To make an item, use the `item` mixin. This item allows 2 per line before it wraps to the next line. Items are automatically extended so you don't need to worry about bloated output.

```scss
.item {
  @include item(2);
}
```

## Item breaks
This feature is syntactic sugar to make it easier to use multiple breaks for items.

Each item will allow 2 items per line until the browser width exceeds the 6th break, which is equivalent to the width of 6 out of 12 items. After the 6th break each item will allow 4 items per line before wrapping to the next line and so on. Items are also extended within media queries so you don't need to worry about bloated output here either.

```scss
.item {
  @include item(2 '6:4' '8:6');
}
```

## Custom grids
If you want to use more or less than 12 items or breaks and/or enable a fixed grid in a separate instance, use the `taffy-generator` mixin.

```scss
@include taffy-generator($name, $amount, $fixed);
```

To use a custom grid pass your custom grid name to the mixins as the second argument.

```scss
@include item(6 '6:4' '8:6', 'custom-name');
@include break(4, 'custom-name') {
  // ...
}
```
