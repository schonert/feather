# Feather

[![Travis branch](https://img.shields.io/travis/feathericons/feather/master.svg?style=flat-square)](https://travis-ci.org/feathericons/feather)
[![npm downloads](https://img.shields.io/npm/dm/feather-icons.svg?style=flat-square)](https://npm-stat.com/charts.html?package=feather-icons&from=2017-06-01)
[![npm version](https://img.shields.io/npm/v/feather-icons.svg?style=flat-square)](https://www.npmjs.com/package/feather-icons)
[![CDNJS version](https://img.shields.io/cdnjs/v/feather-icons.svg?style=flat-square)](https://cdnjs.com/libraries/feather-icons)

## What is Feather?

Feather is a collection of simply beautiful open source icons. Each icon is designed on a 24x24 grid with an emphasis on simplicity, consistency and readability.

https://feathericons.com

```sh
npm install feather-icons
```

**Sponsored by**

<a href="https://stdlib.com">
  <img src="https://stdlib.com/static/images/stdlib-logo-wordmark-128.png" width="128" />
</a>

## Table of Contents

* [Quick Start](#quick-start)
* [Usage](#usage)
  * [Client-side](#client-side)
  * [Node](#node)
  * [SVG Sprite](#svg-sprite)
* [API Reference](#api-reference)
	* [`feather.icons`](#feathericons)
	* [`feather.icons[name].toSvg()`](#feathericonsnametosvgattrs)
	* [`feather.replace()`](#featherreplaceattrs)
	* [(DEPRECATED) `feather.toSvg()`](#deprecated-feathertosvgname-attrs)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [Related Projects](#related-projects)
* [License](#license)

## Quick Start

Start with this [CodePen Template](https://codepen.io/pen?template=WOJZdM) to begin prototyping with Feather in the browser.

Or copy and paste the following code snippet into a blank `html` file.

```html
<!DOCTYPE html>
<html lang="en">
  <title></title>
  <script src="https://unpkg.com/feather-icons/dist/feather.min.js"></script>
  <body>

    <!-- example icon -->
    <i data-feather="circle"></i>

    <script>
      feather.replace()
    </script>
  </body>
</html>
```

## Usage

At its core, Feather is a collection of [SVG](https://svgontheweb.com/#svg) files. This means that you can use Feather icons in all the same ways you can use SVGs (e.g. `img`, `background-image`, `inline`, `object`, `embed`, `iframe`). Here's a helpful article detailing the many ways SVGs can be used on the web: [SVG on the Web – Implementation Options](https://svgontheweb.com/#implementation)

The following are additional ways you can use Feather.

### Client-side

#### 1. Install

> **Note:** If you intend to use Feather with a CDN, you can skip this installation step.

Install with [npm](https://docs.npmjs.com/getting-started/what-is-npm).

```
npm install feather-icons --save
```

Or just copy [`feather.js`](https://unpkg.com/feather-icons/dist/feather.js) or [`feather.min.js`](https://unpkg.com/feather-icons/dist/feather.min.js) into your project directory. You don't need both `feather.js` and `feather.min.js`.

#### 2. Include

Include `feather.js` or `feather.min.js` with a `<script>` tag. These files are located in the `dist` directory of the npm package.

```html
<script src="path/to/dist/feather.js"></script>
```

Or load the script from a CDN provider.

```html
<!-- choose one -->
<script src="https://cdn.jsdelivr.net/npm/feather-icons/dist/feather.min.js"></script>
<script src="https://unpkg.com/feather-icons/dist/feather.min.js"></script>
```

After including the script, `feather` will be available as a global variable.

#### 3. Use

To use an icon on your page, add a `data-feather` attribute with the icon name to an element.

```html
<i data-feather="circle"></i>
```

See the complete list of icons at [feathericons.com](https://feathericons.com).

#### 4. Replace

Call the `feather.replace()` method.

```html
<script>
  feather.replace()
</script>
```

All elements that have a `data-feather` attribute will be replaced with SVG markup corresponding to their `data-feather` attribute value. See the [API Reference](#api-reference) for more information about `feather.replace()`.

### Node
#### 1. Install

Install with [npm](https://docs.npmjs.com/getting-started/what-is-npm).

```
npm install feather-icons --save
```

#### 2. Require

```javascript
const feather = require('feather-icons')
```

#### 3. Use

```js
feather.icons.x
// {
//    name: 'x',
//    contents: '<line ... /><line ... />`,
//    tags: ['cancel', 'close', 'delete', 'remove'],
//    attrs: {
//      class: 'feather feather-x',
//      xmlns: 'http://www.w3.org/2000/svg',
//      width: 24,
//      height: 24,
//      viewBox: '0 0 24 24',
//      fill: 'none',
//      stroke: 'currentColor',
//      'stroke-width': 2,
//      'stroke-linecap': 'round',
//      'stroke-linejoin': 'round',
//    }
// }

feather.icons.x.toSvg()
// <svg class="feather feather-x" ...><line ... /><line ... /></svg>

feather.icons.x.toSvg({ class: 'foo bar', 'stroke-width': 1, color: 'red' })
// <svg class="feather feather-x foo bar" stroke-width="1" color="red" ...><line ... /><line ... /></svg>
```

See the [API Reference](#api-reference) for more information about the available properties and methods of the `feather` object.

### SVG Sprite
A SVG Sprite is also provided, which can be used as following:
```html
<svg class="feather feather-[iconName]"
  width="24"
  height="24"  
  fill="none"
  stroke="currentColor"
  stroke-width="2"
  stroke-linecap="round"
  stroke-linejoin="round"
>
  <use xlink:href="feather-sprite.svg#[iconName]"/>
</svg>
```
Where `iconName` is the name of the icon you want to display.

Same result but using a CSS class:
```css
.feather {
  width: 24px; 
  height: 24px; 
  stroke: currentColor; 
  stroke-width: 2; 
  stroke-linecap: round; 
  stroke-linejoin: round; 
  fill: none;
}
```
```html
<svg class="feather feather-[iconName]">
  <use xlink:href="feather-sprite.svg#[iconName]"/>
</svg>
```
Prefer using CSS classes to keep things organized.

## API Reference

### `feather.icons`

An object with data about every icon.

#### Usage

```js
feather.icons.x
// {
//    name: 'x',
//    contents: '<line ... /><line ... />',
//    tags: ['cancel', 'close', 'delete', 'remove'],
//    attrs: {
//      class: 'feather feather-x',
//      xmlns: 'http://www.w3.org/2000/svg',
//      width: 24,
//      height: 24,
//      viewBox: '0 0 24 24',
//      fill: 'none',
//      stroke: 'currentColor',
//      'stroke-width': 2,
//      'stroke-linecap': 'round',
//      'stroke-linejoin': 'round',
//    }
// }

feather.icons.x.toString()
// '<line ... /><line ... />'
```

[View Source](https://github.com/colebemis/feather/blob/master/src/icons.js)

---

### `feather.icons[name].toSvg([attrs])`

Returns an SVG string.

#### Parameters

| Name      | Type   | Description |
| --------- | ------ | ----------- |
| `attrs` (optional) | Object |  Key-value pairs in the `attrs` object will be mapped to HTML attributes on the `<svg>` tag (e.g. `{ foo: 'bar' }` maps to `foo="bar"`). All default attributes on the `<svg>` tag can be overridden with the `attrs` object. |

#### Usage

```javascript
feather.icons.circle.toSvg()
// '<svg class="feather feather-circle" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>'

feather.icons.circle.toSvg({ 'stroke-width': 1 })
// '<svg class="feather feather-circle" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>'

feather.icons.circle.toSvg({ class: 'foo bar' })
// '<svg class="feather feather-circle foo bar" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>'
```

[View Source](https://github.com/colebemis/feather/blob/master/src/icon.js)

---

### `feather.replace([attrs])`

Replaces all elements that have a `data-feather` attribute with SVG markup corresponding to the element's `data-feather` attribute value.

#### Parameters

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| `attrs` (optional)  | Object | Key-value pairs in the `attrs` object will be mapped to HTML attributes on the `<svg>` tag (e.g. `{ foo: 'bar' }` maps to `foo="bar"`). All default attributes on the `<svg>` tag can be overridden with the `attrs` object. |

#### Usage

> **Note:** `feather.replace()` only works in a browser environment.

Simple usage:
```html
<i data-feather="circle"></i>
<!--
<i> will be replaced with:
<svg class="feather feather-circle" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>
-->

<script>
  feather.replace()
</script>
```

You can pass `feather.replace()` an `attrs` object:
```html
<i data-feather="circle"></i>
<!--
<i> will be replaced with:
<svg class="feather feather-circle foo bar" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>
-->

<script>
  feather.replace({ class: 'foo bar', 'stroke-width': 1 })
</script>
```

All attributes on the placeholder element (i.e. `<i>`) will be copied to the `<svg>` tag:

```html
<i data-feather="circle" id="my-circle" class="foo bar" stroke-width="1"></i>
<!--
<i> will be replaced with:
<svg id="my-circle" class="feather feather-circle foo bar" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>
-->

<script>
  feather.replace()
</script>
```

[View Source](https://github.com/colebemis/feather/blob/master/src/replace.js)

---

### `feather.append([attrs])`

Appends the svgs to the element, instead of replacing the element.
_changes the `data-feather-append` to `data-feather-appended` to prevent prepending multiple svgs_

#### Parameters

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| `attrs` (optional)  | Object | Key-value pairs in the `attrs` object will be mapped to HTML attributes on the `<svg>` tag (e.g. `{ foo: 'bar' }` maps to `foo="bar"`). All default attributes on the `<svg>` tag can be overridden with the `attrs` object. |

#### Usage

> **Note:** `feather.append()` only works in a browser environment.

Simple usage:
```html
<i data-feather-append="circle"></i>
<!--
<i> will result in:
<i data-feather-appended="circle">
  <svg class="feather feather-circle" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>
</i>
-->

<script>
  feather.append()
</script>
```

[View Source](https://github.com/colebemis/feather/blob/master/src/append.js)

---

### `feather.prepend([attrs])`

Prepends the svgs to the element, instead of replacing the element.
_changes the `data-feather-prepend` to `data-feather-prepended` to prevent prepending multiple svgs_

#### Parameters

| Name       | Type   | Description |
| ---------- | ------ | ----------- |
| `attrs` (optional)  | Object | Key-value pairs in the `attrs` object will be mapped to HTML attributes on the `<svg>` tag (e.g. `{ foo: 'bar' }` maps to `foo="bar"`). All default attributes on the `<svg>` tag can be overridden with the `attrs` object. |

#### Usage

> **Note:** `feather.prepend()` only works in a browser environment.

Simple usage:
```html
<i data-feather-prepend="circle"></i>
<!--
<i> will result in:
<i data-feather-prepended="circle">
  <svg class="feather feather-circle" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>
</i>
-->

<script>
  feather.prepend()
</script>
```

[View Source](https://github.com/colebemis/feather/blob/master/src/append.js)

---

### (DEPRECATED) `feather.toSvg(name, [attrs])`

> **Note:** `feather.toSvg()` is deprecated. Please use `feather.icons[name].toSvg()` instead.

Returns an SVG string.

#### Parameters

| Name      | Type   | Description |
| --------- | ------ | ----------- |
| `name`    | string | Icon name   |
| `attrs` (optional) | Object |  Key-value pairs in the `attrs` object will be mapped to HTML attributes on the `<svg>` tag (e.g. `{ foo: 'bar' }` maps to `foo="bar"`). All default attributes on the `<svg>` tag can be overridden with the `attrs` object. |

#### Usage

```javascript
feather.toSvg('circle')
// '<svg class="feather feather-circle" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>'

feather.toSvg('circle', { 'stroke-width': 1 })
// '<svg class="feather feather-circle" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>'

feather.toSvg('circle', { class: 'foo bar' })
// '<svg class="feather feather-circle foo bar" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle></svg>'
```

[View Source](https://github.com/colebemis/feather/blob/master/src/to-svg.js)

## Roadmap

- [ ] Write icon design guidelines
- [ ] Track code coverage
- [ ] Improve SVG accessibility
- [ ] Handle usage of custom icons
- [ ] Add usage examples
- [ ] Make `<feather-icon>` web component

## Contributing

For more info on how to contribute please see the [contribution guidelines](https://github.com/colebemis/feather/blob/master/CONTRIBUTING.md).

Caught a mistake or want to contribute to the documentation? [Edit this page on Github](https://github.com/colebemis/feather/blob/master/README.md)

## Related Projects

 - [angular-feather](https://github.com/michaelbazos/angular-feather) - Feather icons for Angular applications
 - [elm-feather](https://github.com/1602/elm-feather) - Feather icons for Elm applications
 - [react-feather](https://github.com/carmelopullara/react-feather) - Feather icons as React components
 - [sketch-feather](https://github.com/odmln/sketch-feather) - Feather icons as a Sketch library
 - [vue-feather-icon](https://github.com/mage3k/vue-feather-icon) - Feather icons as Vue components

## License

Feather is licensed under the [MIT License](https://github.com/colebemis/feather/blob/master/LICENSE).
