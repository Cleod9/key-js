# key-js

Simple library for JavaScript key code constants and a utility to check key press state. It is a port of my [KeyAS3](https://github.com/Cleod9/KeyAS3) library.

Many existing libraries expose key code values in strange ways (such as requiring function calls that took string values). This library provides a simple static object containing the key codes, and comes with an additional utility function for checking the pressed state of keys. The API is heavily influenced by  the `Key` class from the olden days of ActionScript 2.0.

## Usage

### CommonJS

```js
var KeyJS = require('key-js');
```

### `<script>` Tag

When loaded through a `<script>` tag in the browser, `KeyJS` will become a global variable on the `window` object.

### Retrieving Key Code Constants

The `KeyJS` object exposes the key code values as values attached to the object itself. See below:

```js
console.log(KeyJS.A); // 65
console.log(KeyJS.ENTER); // 13
console.log(KeyJS.SPACEBAR); // 32
```

See [key.js](key.js) for a full list of all the constants

### Checking the state of the Keyboard

By default `KeyJS` will not listen for Keyboard events. You can use the function `KeyJS.startCapture()` to start the listeners. The full API can then be accessed as outlined below:

`KeyJS.startCapture(target = null)` - Starts listening for keyboard events on the `target` DOM element. By default this will be set to the `window` object. Note that keyboard events are only tracked while the `target` has focus. This means you don't have to worry about key presses becoming "stuck" in the pressed state when focus is lost.

`KeyJS.endCapture()` - Stops listening for keyboard events.

`KeyJS.isDown(keyCode)` - Checks the "pressed" state of the specified key specified by its key code.

#### Example Code

```js
var KeyJS = require('key-js');
KeyJS.startCapture();

setInterval(function () {
  // Check console to see when spacebar is pressed
  console.log('Spacebar pressed: ' + KeyJS.isDown(KeyJS.SPACEBAR));
}, 100);

```