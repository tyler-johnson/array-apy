# Array Spy

This library provides the means to observe changes to native JavaScript arrays. It does this by patching the core array methods (ie. `push`) and announcing every time they are called.

## Install

Download a UMD bundle from the [releases page](https://github.com/tyler-johnson/array-spy/releases). The variable `arraySpy` will be attached to `window`.

```html
<script type="text/javascript" src="array-spy.js"></script>
```

If using Browserify or Node.js, you can install via NPM.

```sh
$ npm install array-spy
```

## Usage

To use, call the `arraySpy()` method on any array.

```js
var arraySpy = require("array-spy");
var myarr = [];
arraySpy(myarr);
```

The array becomes patched, which adds an `observe()` method to it. Anytime the array is modified via one of the methods, the observe function is called with changes. The changes object will provide an index and the number of added and removed items.

```js
myarr.observe(function(chgs) {
	console.log(chgs);
});

myarr.push("some value");
```
