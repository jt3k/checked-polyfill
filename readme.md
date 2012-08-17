# Checked polyfill

This code adds support for the :checked pseudo-class on browsers that don't natively support it. More precisely, it adds a .checked class that behaves like the :checked psuedo selector. If you use the "for" attribute on your label, it will also apply the .checked class to your label. That helps work around the [buggy sibling selector support in IE7](http://oncemade.com/adjacent-sibling-selector-bug-in-ie7).

This tool is a work in progress. The documentation is limited, and there's no demo yet. There may be bugs. If you see anything that could be better, please let me know!

Written by [Ryan DeBeasi](http://www.ryandebeasi.com/) of [352 Media Group](http://www.352media.com/).

##Usage

Grab Modernizr, and then tell it how to detect :checked support:

```javascript
Modernizr.addTest('checkedselector',function(){
  return selectorSupported(':checked');
});
```

Then, have it run the test and load this script if the test fails. If you are only styling some inputs, feel free to limit the jQuery selector to just those.

```javascript
Modernizr.load([
	{
		test: Modernizr.checkedselector,
		nope: 'js/checked-polyfill.js',
		callback: function() {
			jQuery(function(){
				$('input:radio').checkedPolyfill();
			});
		}
	}
]);
```

Finally, use :checked and .checked to style your radio buttons. You'll get native support in modern browsers, and JS-based support in IE7 and IE8. Put these selectors on separate lines.

```css
.myStyledLabels label.checked {
	background-color: #ccc;	
}

..myStyledLabels input[type="radio"]:checked + label {
	background-color: #ccc;
}

```

##License

Checked polyfill is licensesed under the MIT License, and is free for commercial or personal use.

Copyright &copy; 2012 352 Media Group

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.