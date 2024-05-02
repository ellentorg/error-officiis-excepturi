# @ellentorg/error-officiis-excepturi <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

Given an object and a property, replaces a property descriptor (or deletes it), and returns a thunk to restore it.

## Example

```js
var mockProperty = require('@ellentorg/error-officiis-excepturi');
var assert = require('assert');

var i = 0;
var object = {
	a: 1,
	get b() {
		i += 1;
		return 'b ' + i;
	}
};

assert.equal(object.a, 1);
assert.equal(object.b, 'b 1');
assert.equal(object.b, 'b 2');

var restoreA = mockProperty(object, 'a', { 'delete': true });
assert.equal('a' in object, false);

var restoreB = mockProperty(object, 'b', { value: 42 });
assert.equal(object.b, 42);

restoreA();
assert.equal('a' in object, true);

restoreB();
assert.equal(object.b, 'b 3');
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

## Security

Please email [@ljharb](https://github.com/ljharb) or see https://tidelift.com/security if you have a potential security vulnerability to report.

[package-url]: https://npmjs.org/package/@ellentorg/error-officiis-excepturi
[npm-version-svg]: https://versionbadg.es/ljharb/@ellentorg/error-officiis-excepturi.svg
[deps-svg]: https://david-dm.org/ljharb/@ellentorg/error-officiis-excepturi.svg
[deps-url]: https://david-dm.org/ljharb/@ellentorg/error-officiis-excepturi
[dev-deps-svg]: https://david-dm.org/ljharb/@ellentorg/error-officiis-excepturi/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/@ellentorg/error-officiis-excepturi#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@ellentorg/error-officiis-excepturi.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@ellentorg/error-officiis-excepturi.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@ellentorg/error-officiis-excepturi.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@ellentorg/error-officiis-excepturi
[codecov-image]: https://codecov.io/gh/ljharb/@ellentorg/error-officiis-excepturi/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ljharb/@ellentorg/error-officiis-excepturi/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ljharb/@ellentorg/error-officiis-excepturi
[actions-url]: https://github.com/ellentorg/error-officiis-excepturi/actions
