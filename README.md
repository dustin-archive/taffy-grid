Grid
===

> Sweet responsive grids

## Why?
+ Only outputs only the CSS you use
+ Uses a combination of flex and calc to ensure accuracy
+ Keeps output small by extending classes, even within media queries
+ Uses Taffy's Break, a breakpoint system created for syncing grids and breakpoints
+ Includes a `$grid-fixed` variable to enable a responsive product grid style layout

## Getting Started
+ Install with Bower
+ Import dependencies

```
$ bower install --save taffy-grid
```

```scss
@import 'bower_components/fizz-sass/scss/main';
@import 'bower_components/taffy-break/scss/main';
@import 'bower_components/taffy-adapt/scss/main';
@import 'bower_components/taffy-grid/scss/main';
```
