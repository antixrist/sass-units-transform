# SASS/SCSS Relative Units
## Functions
### EM/REM to PX
```scss
@function px ($input, $font-size: $base-font-size) {}
```
Calculate ```$input``` to ```px``` units.
```scss
$list-int			: 24 25 26 27;
$list-px			: 24px 25px 26px 27px;
$list-em			: 24em 25em 26em 27em;
$list-rem			: 24rem 25rem 26rem 27rem;
$list-mixed			: 24 25px 26em 27rem;
$list-mixed-zero	: 0 0px 0em 0rem;
$base-font-size		: 12px;
#test11 { border-width : px($list-int); }
#test12 { border-width : px($list-px); }
#test13 { border-width : px($list-em, $base-font-size); }
#test14 { border-width : px($list-rem); } // based on $base-font-size
#test15 { border-width : px($list-mixed, $base-font-size); }
#test16 { border-width : px($list-mixed-zero, $base-font-size); }
```
return:
```css
#test11 { border-width: 24px 25px 26px 27px; }
#test12 { border-width: 24px 25px 26px 27px; }
#test13 { border-width: 288px 300px 312px 324px; }
#test14 { border-width: 288px 300px 312px 324px; }
#test15 { border-width: 24px 25px 312px 324px; }
#test16 { border-width: 0px 0px 0px 0px; }
```

### PX/REM to EM
```scss
@function em ($input, $font-size: $base-font-size) {}
```
Calculate ```$input``` to ```em``` units.
```scss
$list-int			: 24 25 26 27;
$list-px			: 24px 25px 26px 27px;
$list-em			: 24em 25em 26em 27em;
$list-rem			: 24rem 25rem 26rem 27rem;
$list-mixed			: 24 25px 26em 27rem;
$list-mixed-zero	: 0 0px 0em 0rem;
$font-size			: 16px;
#test11 { padding : em($list-int, $font-size); }
#test12 { padding : em($list-px, $font-size); }
#test13 { padding : em($list-em, $font-size); }
#test14 { padding : em($list-rem, $font-size); }
#test15 { padding : em($list-mixed, $font-size); }
#test16 { padding : em($list-mixed-zero, $font-size); }
```
return:
```css
#test11 { padding: 24em 25em 26em 27em; }
#test12 { padding: 1.5em 1.5625em 1.625em 1.6875em; }
#test13 { padding: 24em 25em 26em 27em; }
#test14 { padding: 18em 18.75em 19.5em 20.25em; }
#test15 { padding: 24em 1.5625em 26em 20.25em; }
#test16 { padding: 0em 0em 0em 0em; }
```


### PX/EM to REM
```scss
@function rem ($input, $font-size: $base-font-size) {}
```
Calculate ```$input``` to ```rem``` units.
```scss
$list-int			: 24 25 26 27;
$list-px			: 24px 25px 26px 27px;
$list-em			: 24em 25em 26em 27em;
$list-rem			: 24rem 25rem 26rem 27rem;
$list-mixed			: 24 25px 26em 27rem;
$list-mixed-zero	: 0 0px 0em 0rem;
$base-font-size		: 12px;
$font-size			: 16px;
#test11 { margin : rem($list-int); }
#test12 { margin : rem($list-px); }
#test13 { margin : rem($list-em, $font-size); }
#test14 { margin : rem($list-rem); }
#test15 { margin : rem($list-mixed); }
#test16 { margin : rem($list-mixed-zero); }
```
return:
```css
#test11 { margin: 24rem 25rem 26rem 27rem; }
#test12 { margin: 2rem 2.08333rem 2.16667rem 2.25rem; }
#test13 { margin: 32rem 33.33333rem 34.66667rem 36rem; }
#test14 { margin: 24rem 25rem 26rem 27rem; }
#test15 { margin: 24rem 2.08333rem 26rem 27rem; }
#test16 { margin: 0rem 0rem 0rem 0rem; }
```
## Mixins
### PX/REM to EM
```scss
@mixin em ($property, $value, $font-size: $base-font-size) {}
```
```scss
$list-int			: 24 25 26 27;
$list-px			: 24px 25px 26px 27px;
$list-em			: 24em 25em 26em 27em;
$list-rem			: 24rem 25rem 26rem 27rem;
$list-mixed			: 24 25px 26em 27rem;
$list-mixed-zero	: 0 0px 0em 0rem;
$base-font-size		: 12px;
#test17 {
	@include em(margin, $list-int);
	@include em(padding, $list-px);
	@include em(border-width, $list-em);
	@include em(outline-width, $list-rem);
}
	#test17-2 {
		@include em(padding, $list-mixed);
		@include em(margin, $list-mixed-zero);
	}
```
return:
```css
#test17 {
  margin: 24em 25em 26em 27em;
  padding: 2em 2.08333em 2.16667em 2.25em;
  border-width: 24em 25em 26em 27em;
  outline-width: 24em 25em 26em 27em;
}
#test17-2 {
  padding: 24em 2.08333em 26em 27em;
  margin: 0em 0em 0em 0em;
}
```

### PX/EM to REM
```scss
@mixin rem ($property, $value, $font-size: $base-font-size, $with-fallback: true) {}
```
```scss
$list-int			: 24 25 26 27;
$list-px			: 24px 25px 26px 27px;
$list-em			: 24em 25em 26em 27em;
$list-rem			: 24rem 25rem 26rem 27rem;
$list-mixed			: 24 25px 26em 27rem;
$list-mixed-zero	: 0 0px 0em 0rem;
$base-font-size		: 12px;
#test18 {
	@include rem(margin, $list-int);
	@include rem(padding, $list-px, $with-fallback: false);
	@include rem(border-width, $list-em);
	@include rem(outline-width, $list-rem);
}
	#test18-2 {
		@include rem(padding, $list-mixed, $with-fallback: false);
		@include rem(margin, $list-mixed-zero);
	}
```
return:
```css
#test18 {
  margin: 24px 25px 26px 27px;
  margin: 24rem 25rem 26rem 27rem;
  padding: 2rem 2.08333rem 2.16667rem 2.25rem;
  border-width: 288px 300px 312px 324px;
  border-width: 24rem 25rem 26rem 27rem;
  outline-width: 288px 300px 312px 324px;
  outline-width: 24rem 25rem 26rem 27rem;
}
#test18-2 {
  padding: 24rem 2.08333rem 26rem 27rem;
  margin: 0px 0px 0px 0px;
  margin: 0rem 0rem 0rem 0rem;
}
```

## Helper functions

### Clear unit
```scss
@function clear-unit ($value) {}
```
Remove unit from input number.
```scss
#test1 { line-height : clear-unit(1.2); }
#test2 { line-height : clear-unit(1.2px); }
#test3 { line-height : clear-unit(1.2em); }
#test4 { line-height : clear-unit(1.2rem); }
```
return:
```css
#test1 {
  line-height: 1.2;
}
#test2 {
  line-height: 1.2;
}
#test3 {
  line-height: 1.2;
}
#test4 {
  line-height: 1.2;
}
```

### Make unit
```scss
@function make-unit ($value, $unit: px) {}
```
Replace unit of ```$value``` to target unit.
```scss
$var-int    : 24;
$var-px  	: 24px;
$var-em		: 24em;
$var-rem	: 24rem;
#test {
	top			: make-unit($var-int, px);
	right		: make-unit($var-px, px);
	bottom		: make-unit($var-em, px);
	left		: make-unit($var-rem, px);
}
#test2 {
	top			: make-unit($var-int, em);
	right		: make-unit($var-px, em);
	bottom		: make-unit($var-em, em);
	left		: make-unit($var-rem, em);
}
#test3 {
	top			: make-unit($var-int, rem);
	right		: make-unit($var-px, rem);
	bottom		: make-unit($var-em, rem);
	left		: make-unit($var-rem, rem);
}
```
return:
```css
#test {
  top: 24px;
  right: 24px;
  bottom: 24px;
  left: 24px;
}
#test2 {
  top: 24em;
  right: 24em;
  bottom: 24em;
  left: 24em;
}
#test3 {
  top: 24rem;
  right: 24rem;
  bottom: 24rem;
  left: 24rem;
}
```

## Convert functions

### PX to EM
```scss
@function pxtoem ($value, $font-size: $base-font-size) {}
```
Convert ```$value``` to ```px``` unit, then calculate to ```em``` (based on ```$font-size```).
```scss
$var-int  	    : 24;
$var-px			: 24px;
$var-em			: 24em;
$var-rem		: 24rem;
$font-size	    : 16px;
#test5 {
	top			: pxtoem($var-int, $font-size);
	right		: pxtoem($var-px, $font-size);
	bottom		: pxtoem($var-em, $font-size);
	left		: pxtoem($var-rem, $font-size);
}
```
return:
```css
#test5 {
  top: 1.5em;
  right: 1.5em;
  bottom: 1.5em;
  left: 1.5em;
}
```

### EM to PX
```scss
@function emtopx ($value, $font-size: $base-font-size) {}
```
Convert ```$value``` to ```em``` unit (based on ```$font-size```), then calculate ```px```.
```scss
$var-int        : 24;
$var-px			: 24px;
$var-em			: 24em;
$var-rem		: 24rem;
$font-size	    : 16px;
#test6 {
  top		: emtopx($var-int, $font-size);
  right		: emtopx($var-px, $font-size);
  bottom	: emtopx($var-em, $font-size);
  left		: emtopx($var-rem, $font-size);
}
```
return:
```css
#test6 {
  top: 384px;
  right: 384px;
  bottom: 384px;
  left: 384px;
}
```

### PX to REM 
```scss
@function pxtorem ($value) {}
```
Convert ```$value``` to ```px``` unit, then calculate to ```rem``` (based on ```$base-font-size```).
```scss
$var-int        : 24;
$var-px			: 24px;
$var-em			: 24em;
$var-rem		: 24rem;
$font-size	    : 16px;
$base-font-size : 12px
#test7 {
  top       : pxtorem($var-int);
  right		: pxtorem($var-px);
  bottom	: pxtorem($var-em);
  left		: pxtorem($var-rem);
}
```
return:
```css
#test7 {
  top: 2rem;
  right: 2rem;
  bottom: 2rem;
  left: 2rem;
}
```

### REM to PX
```scss
@function remtopx ($value) {}
```
Convert ```$value``` to ```rem``` unit (based on ```$base-font-size```), then calculate to ```px```.
```scss
$var-int        : 24;
$var-px  		: 24px;
$var-em			: 24em;
$var-rem		: 24rem;
$font-size	    : 16px;
$base-font-size : 12px
#test8 {
  top			: remtopx($var-int);
	right		: remtopx($var-px);
	bottom		: remtopx($var-em);
	left		: remtopx($var-rem);
}
```
return:
```css
#test8 {
  top: 288px;
  right: 288px;
  bottom: 288px;
  left: 288px;
}
```

### EM to REM
```scss
@function emtorem ($value, $font-size: $base-font-size) {}
```
Convert ```$value``` to ```em``` unit (based on ```font-size```), then calculate to ```rem``` (based on ```$base-font-size```).
```scss
$var-int        : 24;
$var-px    	: 24px;
$var-em			: 24em;
$var-rem		: 24rem;
$font-size	    : 16px;
$base-font-size : 12px
#test9 {
  top			: emtorem($var-int, $font-size);
	right		: emtorem($var-px, $font-size);
	bottom		: emtorem($var-em, $font-size);
	left		: emtorem($var-rem, $font-size);
}
```
return:
```css
#test9 {
  top: 32rem;
  right: 32rem;
  bottom: 32rem;
  left: 32rem;
}
```

### REM to EM
```scss
@function remtoem ($value, $font-size: $base-font-size) {}
```
Convert ```$value``` to ```rem``` unit (based on ```$base-font-size```), then calculate to ```em``` (based on ```$font-size```).
```scss
$var-int        : 24;
$var-px      : 24px;
$var-em			: 24em;
$var-rem		: 24rem;
$font-size	    : 16px;
$base-font-size : 12px
#test10 {
  top			: remtoem($var-int, $$-font-size);
	right		: remtoem($var-px, $font-size);
	bottom		: remtoem($var-em, $$-font-size);
	left		: remtoem($var-rem, $font-size);
}
```
return:
```css
#test10 {
  top: 18em;
  right: 18em;
  bottom: 18em;
  left: 18em;
}
```

