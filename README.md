# simplex-noise.js

simplex-noise.js is a fast simplex noise implementation in Javascript. It works in the browser and on nodejs.

## Requirements

It requires typed arrays, if you want to use it in browsers without support
you will need to use a polyfill like [typedarray.js](http://www.calormen.com/polyfill/typedarray.js).

## Demo
Simple 2D plasma demo on [jsfiddle.net](http://jsfiddle.net/9f8fV/).
A more complex [3D voxel world generation](http://29a.ch/sandbox/2012/voxelworld/) example

## Usage

```javascript
// initializing a simplex instance
// do this only once it's relatively expensive
var simplex = new SimplexNoise(),
    value2d = simplex.noise2D(x, y),
    value3d = simplex.noise3D(x, y, z),
    value4d = simplex.noise4D(x, y, z, w);
```

You can also pass an alternative random function to the constructor that is
used to build the permutation table:

```javascript
var simplex = new SimplexNoise(Math.random),
    value2d = simplex.noise2D(x, y);
```

## node.js

Node.js is also supported, you can install the package using [npm](https://npmjs.org/package/simplex-noise).

```javascript
var SimplexNoise = require('simplex-noise'),
    simplex = new SimplexNoise(Math.random),
    value2d = simplex.noise2D(x, y);
```

## Benchmarks

- [Comparison between 2D and 3D noise](http://jsperf.com/simplex-noise/2)
- [Comparison with simplex implementation in three.js](http://jsperf.com/simplex-noise-comparison)

For development you can open `perf/index.html` and watch the console or run `node perf/benchmark.js` in a shell.
There is also a rake task for comparing your current changes can also run `make compare`.
The command works using git stash.

## Tests

There are some simple buster.js tests for this library to run them first install buster.js and jshint:
```shell
npm install buster.js
# if you haven't done so already
npm install -g jshint
make tests
```

## Changelog

### master
- Small performance improvement for 2D noise

### 2.1.1
- Increased entropy by fixing a little initialization issue.

### 2.1.0
- AMD support

### 2.0.0
- Changed node.js api, SimplexNoise is now exported directly.
- Added unit tests

### 1.0.0
- Initial Release

## Credits

This is mostly a direct javascript port of the [Java implementation](http://webstaff.itn.liu.se/~stegu/simplexnoise/SimplexNoise.java)
by Stefan Gustavson and Peter Eastman.
