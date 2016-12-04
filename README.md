Grid
===

> Sweet responsive grids

## Rationale
+ Only outputs the CSS you use
+ Uses a combination of flex and calc to ensure accuracy
+ Keeps output small by extending classes, even within media queries
+ Uses `taffy-break` for syncing grids and breakpoints
+ Includes optional responsive product grid layout
+ Includes optional work arounds for Internet Explorer 10

## Installation
+ Install with NPM
+ Import dependencies

```
$ npm install --save taffy-grid
```

```scss
@import '../node_modules/taffy-util/main';
@import '../node_modules/taffy-break/main';
@import '../node_modules/taffy-adapt/main';
@import '../node_modules/taffy-grid/main';
```

## Usage

### `%grid`

Grid placeholder for items

#### Example

```scss
.taffy-grid {
  @extend %grid;
}
```

```html
<div class='taffy-grid'> ... </div>
```

### `@include item($item [($break $item) ($break $item) ($break $item) ...])`

Extends item placeholders that are generated on import and qualified by `%grid`

#### Parameters
+ `$item`: width of the column <sup>1</sup>
+ `$break`: point at which `$item` is applied as the width of the column <sup>1</sup>

> <sup>1</sup> between `1` and [`$break-amount`](www.google.com)

#### Example

```scss
.taffy-item {
  @include item(2 (6 4) (8 6));
}
```

```html
<div class='taffy-grid'>
  <div class='taffy-item'> ... </div>
  <div class='taffy-item'> ... </div>
  <div class='taffy-item'> ... </div>
</div>
```

### `$grid-fixed`

Enables a consistent item width layout when set to `true`

#### Example

```scss
$grid-fixed: true;
```

### `$grid-ie10`

Enables IE10 work arounds when set to true

#### Example

```scss
$grid-ie10: true;
```
