Test Snippet
===
[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Coverage Status][codecov-image]][codecov-url] [![Dependencies][dependencies-image]][dependencies-url]

> Creates a test file.


## Installation

``` bash
$ npm install @kgryte/test-snippet
```


## Usage

``` javascript
var cp = require( '@kgryte/test-snippet' );
```

#### cp( dest[, opts ][, clbk ] )

Asynchronously create a file in a specified `destination` directory.

``` javascript
cp( 'path/to/a/directory', onCreate );

function onCreate( error ) {
	if ( error ) {
		throw error;
	}
	console.log( 'Success!' );
}
```

The function accepts the following `options`:
*	__template__: snippet template name. Default: `'mocha'`.
*	__title__: test title. Default: `''`.

By default, a `mocha` template is used. To specify a different snippet template, set the `template` option.

``` javascript
cp( 'path/to/a/directory', {
	'template': 'mocha'
});
```

To specify snippet fields, set the corresponding `options`.

``` javascript
cp( 'path/to/a/directory', {
	'title': 'beep-boop'
});
```



#### cp.sync( dest[, opts] )

Synchronously create a file in a specified `destination` directory.

``` javascript
cp.sync( 'path/to/a/directory' );
```

The function accepts the same `options` as the asynchronous version.


## Notes

* 	Supported templates may be found in the `./lib` directory and are named according to the directory name.


## Examples

``` javascript
var mkdirp = require( 'mkdirp' ),
	path = require( 'path' ),
	cp = require( '@kgryte/test-snippet' );

var dirpath = path.resolve( __dirname, '../build/' + new Date().getTime() );

mkdirp.sync( dirpath );
cp.sync( dirpath, {
	'template': 'mocha',
	'title': 'beep-boop'
});
```

To run the example code from the top-level application directory,

``` bash
$ node ./examples/index.js
```

---
## CLI


### Installation

To use the module as a general utility, install the module globally

``` bash
$ npm install -g @kgryte/test-snippet
```


### Usage

``` bash
Usage: test-snippet [options] [destination]

Options:

  -h,    --help                Print this message.
  -V,    --version             Print the package version.
  -tmpl  --template [name]     Template name. Default: 'mocha'.
         --title [title]       Test title. Default: ''.
```


### Examples

``` bash
$ cd ~/my/project/directory
$ test-snippet
# => creates a file in the current working directory
```

To specify a destination other than the current working directory, provide a `destination`.

``` bash
$ test-snippet ./../some/other/directory
```



---
## Tests

### Unit

Unit tests use the [Mocha](http://mochajs.org/) test framework with [Chai](http://chaijs.com) assertions. To run the tests, execute the following command in the top-level application directory:

``` bash
$ make test
```

All new feature development should have corresponding unit tests to validate correct functionality.


### Test Coverage

This repository uses [Istanbul](https://github.com/gotwarlost/istanbul) as its code coverage tool. To generate a test coverage report, execute the following command in the top-level application directory:

``` bash
$ make test-cov
```

Istanbul creates a `./reports/coverage` directory. To access an HTML version of the report,

``` bash
$ make view-cov
```


---
## License

[MIT license](http://opensource.org/licenses/MIT).


## Copyright

Copyright &copy; 2015. Athan Reines.


[npm-image]: http://img.shields.io/npm/v/@kgryte/test-snippet.svg
[npm-url]: https://npmjs.org/package/@kgryte/test-snippet

[travis-image]: http://img.shields.io/travis/kgryte/test-snippet/master.svg
[travis-url]: https://travis-ci.org/kgryte/test-snippet

[codecov-image]: https://img.shields.io/codecov/c/github/kgryte/test-snippet/master.svg
[codecov-url]: https://codecov.io/github/kgryte/test-snippet?branch=master

[dependencies-image]: http://img.shields.io/david/kgryte/test-snippet.svg
[dependencies-url]: https://david-dm.org/kgryte/test-snippet

[dev-dependencies-image]: http://img.shields.io/david/dev/kgryte/test-snippet.svg
[dev-dependencies-url]: https://david-dm.org/dev/kgryte/test-snippet

[github-issues-image]: http://img.shields.io/github/issues/kgryte/test-snippet.svg
[github-issues-url]: https://github.com/kgryte/test-snippet/issues
