[![build status](https://secure.travis-ci.org/jharding/boomerang.png?branch=master)](http://travis-ci.org/jharding/boomerang)

Boomerang
=========
 

Download
--------

* [boomerang.js v0.1.0][boomerang.js]

Usage
-----

### API

#### boomerang.mixin(obj)

Adds the `on`, `off`, and `trigger` methods to `obj`.

#### boomerang#on(event, callback, context)

Binds `callback` to the object. `callback` will be invoked when `event`
is triggered. If `context` is set, that is the context `callback` will 
be invoked in.

#### boomerang#off(event)

Removes previously-bound callbacks.

#### boomerang#trigger(event, [,args])

Triggers previously registered callbacks for `event`. Additional
arguments will be passed to the callbacks when invoked.

Example
-------

```js
var asyncEventEmitter = boomerang.mixin({}), testVal;

asyncEventEmitter.on('event', callback).trigger('event', 42);

assert(testVal === undefined);
setTimeout(function() { assert(testVal === 42); }, 100);

function callback(event, val) {
  assert(event === 'event'); 
  testVal = val;
}
```

Testing
-------

Tests are written using [Jasmine][jasmine] and ran with [Karma][karma]. 
To run Boomerang's test suite with PhantomJS, run `npm test`.

Issues
------

Found a bug? Create an issue on GitHub.

https://github.com/jharding/boomerang/issues

Versioning
----------

For transparency and insight into the release cycle, releases will be numbered with the follow format:

`<major>.<minor>.<patch>`

And constructed with the following guidelines:

* Breaking backwards compatibility bumps the major
* New additions without breaking backwards compatibility bumps the minor
* Bug fixes and misc changes bump the patch

For more information on semantic versioning, please visit http://semver.org/.

License
-------

Copyright (c) 2013 [Jake Harding](http://thejakeharding.com)  
Licensed under the MIT License.

[boomerang.js]: https://raw.github.com/jharding/boomerang/master/boomerang.js 
[jasmine]: http://pivotal.github.com/jasmine/
[karma]: http://karma-runner.github.io
