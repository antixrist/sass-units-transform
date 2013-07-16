# SASS/SCSS Relative Units

## Helper functions

### Clear unit
```scss
@function clear-unit ($value) {}
```
Remove unit from input number.
```scss
#test1 {
  line-height : clear-unit(1.2);
}
#test2 {
  line-height : clear-unit(1.2px);
}
#test3 {
  line-height : clear-unit(1.2em);
}
#test4 {
  line-height : clear-unit(1.2rem);
}
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

