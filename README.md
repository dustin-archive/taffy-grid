Taffy Sass
=========

A sweet responsive grid.

## Mixins
```scss
@include grid($breaks, [$name]);
@include column($breaks, [$name]);
@include offset($breaks, [$name]);
@include break($break, [$name]);
```

## Using taffy
Taffy is set up to work right out of the box. By default Taffy uses 12 columns, a gutter width of 1em, and a gutter height of 2em.

### Grid classes
To start we'll create a grid class. Grids must start with `grid`. Any class that starts with `grid` is assumed to be a grid. Grids contain columns and determine when the columns will break to a new row.

This grid will break the columns it contains to a new row every 2 columns.

```scss
.grid-foobar {
  @include grid(2);
}
```

This grid will break the columns it contains to a new row every 2 columns, until it reaches the 6th break point. After the 6th break it will break to a new row every 4 columns.

```scss
.grid-foobar {
  @include grid(2 '6:4');
}
```

### Column and offset classes
Columns must start with `column`. Any class that starts with `column` is assumed to be a column. Columns are contained within grids and will break to a new row according to the grid they are contained inside.

This column will span half of the grid.

```scss
.column-foobar {
  @include column(2);
}
```

This column will span half the grid, until the width of the browser reaches the 6th break point. After the 6th break it will span one fourth the grid.

```scss
.column-foobar {
  @include column(2 '6:4');
}
```

## Generating custom grids
Generating grids is a big deal. I'd only recommend generating a custom grid when absolutely necessary. If done improperly you could end up with thousands of bloated Sass placeholders and you might even crash your compiler. Generating many custom grids or grids with more than 12 columns will increase your compile time dramatically. If you must generate a new grid, all you need to do is call the `taffy-generator` mixin with the following parameters.

```scss
@include taffy-generator($name, $gutter-width, $gutter-height, $amount);
```

## Using custom grids
Just pass a second parameter of your custom grid name to one of the mixins.

```scss
@include grid(6, 'custom-grid-name');
@include column(6, 'custom-grid-name');
@include offset(6, 'custom-grid-name');
@include break(6, 'custom-grid-name') {
  // ...
}
```
