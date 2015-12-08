Taffy Sass
=========

A sweet responsive grid.

## Overview
Taffy is a gutter-less flex based grid system that only outputs the CSS that you use. It uses a combination of flex and calc to ensure accuracy, rather than use hard coded percentages with floating points. Taffy also includes offsets and breakpoints.

## Mixins
```scss
@include item($breaks, [$name]);
@include offset($breaks, [$name]);
@include break($break, [$name]) {
  // ...
}
```

## Grids
Grids contain items. All it does is initiate flex.

```html
<div class='grid'>
  <!-- items -->
</div>
```

## Items
Items go inside grids. Items wrap to a new line when the limit has been reached.

```html
<div class='grid'>
  <div class='item'></div>
  <div class='item'></div>
  <!-- break -->
  <div class='item'></div>
  <div class='item'></div>
</div>
```

To make an item, use the `item` mixin. This item allows two per line before it wraps to the next line. Items are automatically extended so you don't need to worry about bloated output.

```scss
.item {
  @include item(2);
}
```

This item is the same as the previous example, but adds media queries. Each item will allow two items per line until the browser width exceeds the sixth break. After the sixth break each item will allow four items per line before wrapping to the next line. Items are also extended within media queries so you don't need to worry about bloated output here either.

```scss
.item {
  @include item(2 '6:4');
}
```

## Offsets
Offsets work the same as items but use margins instead of flex. Offsets are classes attached to items and occupy the space normally occupied by items.

```html
<div class='grid'>
  <div class='item.offset'></div>
  <!-- break -->
  <div class='item.offset'></div>
</div>
```

You make an offset the same way you'd make an item but with the `offset-left` and `offset-right` mixins.

```scss
.offset {
  @include offset-left(2 '6:4');
}
```

## Breaks
Breaks use a similar syntax to items and offsets. Breaks create media queries for styles passed to them.

```scss
.break {
  @include break(4) {
    // styles
  }
}
```

## Custom grids
If for some reason you want to use more or less than 12 items not globally, use the `taffy-generator` mixin.

```scss
@include taffy-generator($name, $amount);
```

To use a custom grid pass your custom grid name to the mixins as the a second argument.

```scss
@include item(6 '6:4', 'custom-name');
@include offset(6 '6:4', 'custom-name');
@include break(4, 'custom-name') {
  // ...
}
```
