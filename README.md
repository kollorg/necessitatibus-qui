# @kollorg/necessitatibus-qui <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES spec-compliant `Array.prototype.forEach` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-@kollorg/necessitatibus-qui).

Because `Array.prototype.forEach` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @kollorg/necessitatibus-qui
```

## Usage/Examples

```js
var forEach = require('@kollorg/necessitatibus-qui');
var assert = require('assert');

var arr = [1, [2], [], 3, [[4]]];
var counter = 0;
var increaseCounter = function (x) { counter += 1; };

assert.equal(forEach(arr, increaseCounter), undefined);
assert.equal(counter, arr.length);
```

```js
var forEach = require('@kollorg/necessitatibus-qui');
var assert = require('assert');
/* when Array#forEach is not present */
delete Array.prototype.forEach;
var shimmed = forEach.shim();
var counter = 0;

assert.equal(shimmed, forEach.getPolyfill());
assert.equal(arr.forEach(increaseCounter), forEach(arr, increaseCounter));
assert.equal(counter, arr.length * 2);
```

```js
var forEach = require('@kollorg/necessitatibus-qui');
var assert = require('assert');
/* when Array#forEach is present */
var shimmed = forEach.shim();
var counter = 0;

assert.equal(shimmed, Array.prototype.forEach);
assert.equal(arr.forEach(increaseCounter), forEach(arr, increaseCounter));
assert.equal(counter, arr.length * 2);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@kollorg/necessitatibus-qui
[npm-version-svg]: https://versionbadg.es/kollorg/necessitatibus-qui.svg
[deps-svg]: https://david-dm.org/kollorg/necessitatibus-qui.svg
[deps-url]: https://david-dm.org/kollorg/necessitatibus-qui
[dev-deps-svg]: https://david-dm.org/kollorg/necessitatibus-qui/dev-status.svg
[dev-deps-url]: https://david-dm.org/kollorg/necessitatibus-qui#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@kollorg/necessitatibus-qui.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@kollorg/necessitatibus-qui.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@kollorg/necessitatibus-qui.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@kollorg/necessitatibus-qui
[codecov-image]: https://codecov.io/gh/kollorg/necessitatibus-qui/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/kollorg/necessitatibus-qui/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/kollorg/necessitatibus-qui
[actions-url]: https://github.com/kollorg/necessitatibus-qui
