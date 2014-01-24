Gridster.js
===========

This is a fork that allows you to set relative column sizes and have the layout update on window resize. It's work in progress and highly untested, but works for widths right now. It's based on the work done by others in [this gh issue thread](https://github.com/ducksboard/gridster.js/pull/77/files).

To set relative sizes, you need to calculate the column width based on screen width, number of columns, and gutter width:

````
var maximumColumns = 6;
var widgetMargin = 5;

var widgetWidth= Math.floor(($(".gridster > ul").width() / maximumColumns) - (widgetMargin * 2));

gridster = $(".gridster > ul").gridster({
    widget_margins: [widgetMargin, widgetMargin],
    widget_base_dimensions: [widgetWidth, 100]
}).data('gridster');
````

Then there's a new `gridster.resizeGridster(widgetWidth, widgetHeight)` function that takes your target width and height and then redraws the grid with new, resized widgets. You should recalculate your desired column width on resize and then pass that to `resizeGridster`. Debouncing is a good idea, too:

````
$(window).resize(function() {
  var widgetWidth= Math.floor(($(".gridster > ul").width() / maximumColumns) - (widgetMargin * 2));
  gridster.resizeGridster(widgetWidth, 100);
});
````

## Original readme follows:

Gridster is a jQuery plugin that makes building intuitive draggable
layouts from elements spanning multiple columns. You can even
dynamically add and remove elements from the grid.

More at [http://gridster.net/](http://gridster.net/).

[Releases](https://github.com/ducksboard/gridster.js/releases)

[CHANGELOG](https://github.com/ducksboard/gridster.js/blob/master/CHANGELOG.md)

Gridster is maintained by Ducksboard occasionally but not actively.
@dustmoo and @pushmatrix have also write permissions as Gridster maintainers
they are. Thank you guys!

## Forks

Mr @dustmoo (maintainer of Gridster) has his own fork of gridster.js
with some new interesting features like widget-swapping and static widgets.

Can be found here: [dustmoo/gridster.js](https://github.com/dustmoo/gridster.js)

@dustmoo is working in his spare time to merge all these changes into
ducksboard/gridster.js

If anyone would like to help @dustmoo improve his fork and reconcile
it with the main library he would be happy for the help.


## Contributing to this project

Anyone and everyone is welcome to contribute. Please take a moment to review the guidelines for contributing.

* [Bug reports](CONTRIBUTING.md#bugs)
* [Feature requests](CONTRIBUTING.md#features)
* [Pull requests](CONTRIBUTING.md#pull-requests)


## License

Distributed under the MIT license.

## Whodunit

Gridster is built by [Ducksboard](http://ducksboard.com/) with the help of all
these [wonderful people](https://github.com/ducksboard/gridster.js/graphs/contributors).
