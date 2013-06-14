sass-unity 
============================
Got units? Find unity.

A framework for working with numbers and units.

But wait, there's more -- a grid that ties it all together.


Usage for dimension functions
--------------------------

####Easily normalize units:

	body {
		font-size: rem(12px);
		padding: px(1rem 2em 14px 1em); //Convert all values to px.
	}
	
	div.rounded {
		border-radius: unity(1rem 12px 1em 1); //Convert all values to the same unit as the first value.
	}

####Use the "rem" mixin to create px fallbacks for older browsers:
	
	body {
		@include rem(font-size 12px, padding 1rem);
	}
	
####Add or subtract:
	
	$baseline: 16px; //Define the baseline for our rem unit.
	$grid-width: 1120px;
	$grid-padding: 0 1rem;
	
	div.container {
		width: plus($total-width);
	}
	
	


Usage for grid
--------------------------

####A few globals

	$grid-width: 320px; //The width of the grid, not including its padding
	$grid-columns: 12; //The number of columns
	$grid-column-width: 68px; //The width of a single column
	$grid-gutter-width: auto; //The width of a single gutter

####Use multiple grids

	@include grid(12, static, 62px, auto){
		//All rules within this @include are subject to the grid settings.
		#container {width: container-width(); }
	}

####Grid helpers

These helpers have many parameters, but will use the current grid context if none are passed.

	grid-width(); //The total width of your grid, not including its padding
	column-width(); //The static width of a column
	gutter-width(); //The static width of a gutter
	container-width(); //The static total width of your container, which is the grid-width plus its padding.

#####Breakpoint helpers

These helpers accept a breakpoint list or a breakpoint handle. If neither is passed, it uses the current global $grid-breakpoint.
	
	grid-breakpoint($handle);
	grid-breakpoint-columns(); //Get the current breakpoint's columns, or pass a handle, ie. grid-brea
	grid-breakpoint-handle($breakpoint)
	grid-breakpoint-min();
	grid-breakpoint-max();
	
	
####Easy breakpoints:

	$grid-breakpoints: grid-breakpoints(
		(four 4 0 4), //This is a small-down breakpoint. The base global breakpoint is already four columns.
		(eight 8), //format is ("handle" "columns" "min" "max") -- without quotes, where "min" and "max" are the visible ranges. If neither are entered, "min" is set to "columns".
		(twelve 12),
		(sixteen 16)
	);

	@include grid-breakpoint(four){
		body {color: blue;}
		#container {@include container;}
	}

	@include grid-breakpoint(eight){
		body {color: green;}
		#container {@include container;}
	}

	@include grid-breakpoint(twelve){
		body {color: purple;}
		#container {@include container;}
	}

	@include grid-breakpoint(sixteen){
		body {color: black;}
		#container {@include container;}
	}

