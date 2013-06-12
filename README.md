sass-dimension
============================
Some functions and mixins for SASS dimensions.

Considering renaming to sass-unity...


Usage for dimension functions
--------------------------

Easily normalize units:

	body {
		font-size: rem(12px);
		padding: px(1rem 2em 14px 1em); //Convert all values to px.
	}
	
	div.rounded {
		border-radius: unity(1rem 12px 1em 1); //Convert all values to the same unit as the first value.
	}

Use the "rem" mixin to create px fallbacks for older browsers:
	
	body {
		@include rem(font-size 12px, padding 1rem);
	}
	
Add or subtract:
	
	$baseline: 16px; //Define the baseline for our rem unit.
	$grid-width: 1120px;
	$grid-padding: 0 1rem;
	
	div.container {
		width: plus($total-width);
	}
	
	


Usage for grid
--------------------------

A few global defaults:

	$grid-width: 960px;
	$grid-columns: 12;
	$grid-column-width: 68px;
	$grid-gutter-width: auto;

Easy breakpoints:

	$grid-breakpoints: grid-breakpoints(
		(small 1 4), //This is basically a small-down breakpoint
		(medium 8),
		(large 12),
		(xlarge 16)
	);

	@include grid-breakpoint(small){
		body {color: blue;}
		#container {@include container;}
	}

	@include grid-breakpoint(medium){
		body {color: green;}
		#container {@include container;}
	}

	@include grid-breakpoint(large){
		body {color: purple;}
		#container {@include container;}
	}

	@include grid-breakpoint(xlarge){
		body {color: black;}
		#container {@include container;}
	}
