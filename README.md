# to-arg [![NPM version](https://badge.fury.io/js/to-arg.svg)](http://badge.fury.io/js/to-arg)  [![Build Status](https://travis-ci.org/jonschlinkert/to-arg.svg)](https://travis-ci.org/jonschlinkert/to-arg) 

> Create a command-line argument from a string or string (key) and value.

## Install with [npm](npmjs.org)

```bash
npm i to-arg --save
```

## Usage

```js
var toArg = require('to-arg');

toArg('abc');
//=> '--abc'

toArg('abc', true);
//=> '--abc'

toArg('abc', 'xyz');
//=> '--abc=xyz'

toArg('abc', 'true');
//=> '--abc=true'

toArg('abc', 10);
//=> '--abc=10'
```

**casing**

Keys that are camelcase or contain spaces will be dash-cased:

```js
toArg('fooBar');
//=> '--foo-bar'

toArg('a b c');
//=> '--a-b-c'

toArg('A');
//=> '--a'
```

## Usage example

```js
var obj = {
  foo: 'bar',
  abc: true,
  xyz: 10,
  one: false
};

var args = Object.keys(obj).map(function (key) {
  return toArg(key, obj[key]);
});
//=> ['--foo=bar', '--abc', '--xyz=10', '--no-one']
```

## Options

### invert

When the value is `false` an inverted flag is created by default:

```js
toArg('a', false);
//=> '--no-a'
```

To disable inversion, pass `false` on the options:

```js
toArg('a', false, {invert: false});
//=> '--a'
```

## Other awesome libs
 * [option-cache](https://github.com/jonschlinkert/option-cache): Simple API for managing options in JavaScript applications.
 * [config-cache](https://github.com/jonschlinkert/config-cache): General purpose JavaScript object storage methods.

## Run tests
Install dev dependencies:

```bash
npm i -d && npm test
```

## Contributing
Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/to-arg/issues)

## Author

**Jon Schlinkert**

+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert) 

This was inspired by [grunt.option](https://github.com/gruntjs/grunt/blob/master/lib/grunt/option.js#L40).

## License
Copyright (c) 2015 Jon Schlinkert  
Released under the MIT license

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on April 17, 2015._
