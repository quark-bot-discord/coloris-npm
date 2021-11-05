[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![npm version](https://badge.fury.io/js/@melloware%2Fcoloris.svg)](https://badge.fury.io/js/@melloware%2Fcoloris)
![Maven](https://img.shields.io/maven-central/v/org.webjars.npm/melloware__coloris)

# Coloris NPM

![Coloris in light, dark and polaroid themes](https://raw.githubusercontent.com/mdbassit/Coloris/gh-pages/images/coloris-light-dark-polaroid.jpg)

A lightweight and elegant JavaScript color picker written in vanilla ES6.
Convert any text input field into a color field.

**NOTE:** Forked from https://github.com/mdbassit/Coloris so we could provide TypeScript and NPM support.

[**View demo**](https://coloris.js.org/examples.html)

## Features

* Zero dependencies
* Very easy to use
* Customizable
* Dark theme
* Opacity support
* Color swatches
* Multiple color formats
* Touch support
* Fully accessible
* Works on all modern browsers (no IE support)
* TypeScript support

## Getting Started

### Basic usage

Download the [latest version](https://github.com/melloware/coloris-npm/releases/latest), and add the script and style to your page:

```html
<link rel="stylesheet" href="coloris.min.css"/>
<script src="coloris.min.js"></script>
```

Then just add the data-coloris attribute to your input fields:
```html
<input type="text" data-coloris>
```

That's it. All done!

### NPM

You can also download the color picker from NPM

```bash
# using NPM
npm install @melloware/coloris
# using Yarn
yarn add @melloware/coloris
```

And then use it within a module environment, e.g. with browserify, rollup,
webpack etc. In this case, you must initialize the color picker before its
first use (which has several side-effects such as adding DOM elements):

```javascript
import "@melloware/coloris/dist/coloris.css";
import Coloris from "@melloware/coloris";
Coloris.init();
Coloris({el: "#coloris"});
```

### AMD

The color picker also works with AMD / require.js:

```javascript
requirejs(['@melloware/coloris'], function (Coloris) {
  Coloris.init();
  Coloris({
    el: "#coloris",
  });
});
```

### Java / Maven

The colorpicker can also be downloaded as a Java JAR for use in Java web applicatons:

```xml
<dependency>
   <groupId>org.webjars.npm</groupId>
   <artifactId>melloware__coloris</artifactId>
   <version>0.6.0</version>
</dependency>
```

### Options

```js
Coloris({
  // The default behavior is to append the color picker's dialog to the end of the document's
  // body. but it is possible to append it to a custom parent instead. This is especially useful
  // if the color fields are in a scrollable container and you want color picker' dialog to stay
  // anchored to them. You will need to set the position of the container to relative or absolute.
  parent: '.container',

  // A custom selector to bind the color picker to. This must point to input fields.
  el: '.color-field',

  // The bound input fields are wrapped in a div that adds a thumbnail showing the current color
  // and a button to open the color picker (for accessibility only). If you wish to keep your
  // fields unaltered, set this to false, in which case you will lose the color thumbnail and
  // the accessible button (not recommended).
  wrap: true,

  // Available themes: light, dark, large, large-dark, polaroid, polaroid-dark.
  // More themes might be added in the future.
  theme: 'light',

  // The margin in pixels between the input fields and the color picker's dialog.
  margin: 2,

  // Set the preferred color string format:
  //  * hex: outputs #RRGGBB or #RRGGBBAA (default).
  //  * rgb: outputs rgb(R, G, B) or rgba(R, G, B, A).
  //  * hsl: outputs hsl(H, S, L) or hsla(H, S, L, A).
  //  * auto: guesses the format from the active input field. Defaults to hex if it fails.
  //  * mixed: outputs #RRGGBB when alpha is 1; otherwise rgba(R, G, B, A).
  format: 'hex',

  // Enable or disable alpha support.
  // When disabled, it will strip the alpha value from the existing color value in all formats.
  alpha: true,

  // Show an optional clear button and set its label
  clearButton: {
    show: true,
    label: 'Clear'
  },

  // An array of the desired color swatches to display. If omitted or the array is empty,
  // the color swatches will be disabled.
  swatches: [
    '#264653',
    '#2a9d8f',
    '#e9c46a',
    'rgb(244,162,97)',
    '#e76f51',
    '#d62828',
    'navy',
    '#07b',
    '#0096c7',
    '#00b4d880',
    'rgba(0,119,182,0.8)',
  ]
});
```

### Events

An "input" event is triggered on the bound input field whenever a new color is selected.
A "change" event is triggered when the color picker is closed and if the color has changed since it was opened.

### Closing the color picker

The color picker dialog can be closed by clicking anywhere on the page or by pressing the ESC on the keyboard. The later will also revert the color to its original value.

If you would like to close the dialog programmatically, you can do so by calling the close() method:
```js
// Close the dialog
Coloris.close();

// Close the dialog and revert the color to its original value
Coloris.close(true);
```

# TypeScript

This package includes TypeScript declarations. When you use it in a module
environment, just import it:

```typescript
import "@melloware/coloris/dist/coloris.css";
import Coloris from "@melloware/coloris";

Coloris.init();
Coloris({el: "#coloris"});
Coloris.close();
```

If you wish to write a global script file, use a triple slash reference:

```typescript
/// <reference types="@melloware/coloris" />
Coloris({
    el: "#coloris",
});
```

## Building from source

Clone the git repo:
```bash
git clone git@github.com:melloware/Coloris.git
```

Enter the Coloris directory and install the development dependencies:
```bash
cd Coloris && npm install
```

Run the build script:
```bash
npm run build
```
The built version will be in the `dist` directory in both minified and full copies.

Alternatively, you can start a gulp watch task to automatically build when the source files are modified:
```bash
npm run start
```

## Publishing

Adjust the version in the `package.json` if necessary, then

```bash
npm login
# This will run npm run build automatically
npm publish --access public
```

Then upload code to github, create tag & release.

## License

Copyright (c) 2021 Momo Bassit.
**Coloris** is licensed under the [MIT license](https://github.com/melloware/coloris-npm/blob/main/LICENSE).
