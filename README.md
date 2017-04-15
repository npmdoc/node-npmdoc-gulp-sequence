# api documentation for  [gulp-sequence (v0.4.6)](https://github.com/teambition/gulp-sequence)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-sequence.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-sequence) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-sequence.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-sequence)
#### Run a series of gulp tasks in order.

[![NPM](https://nodei.co/npm/gulp-sequence.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/gulp-sequence)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-sequence/build/screenCapture.buildCi.browser.apidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-sequence/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-gulp-sequence/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-gulp-sequence/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "authors": [
        "Yan Qing <admin@zensh.com>"
    ],
    "bugs": {
        "url": "https://github.com/teambition/gulp-sequence/issues"
    },
    "dependencies": {
        "gulp-util": ">=3.0.0",
        "thunks": "^4.5.1"
    },
    "description": "Run a series of gulp tasks in order.",
    "devDependencies": {
        "gulp": "^3.9.1",
        "standard": "^8.0.0"
    },
    "directories": {},
    "dist": {
        "shasum": "e388d64311046e05547af43035352d9495501c50",
        "tarball": "https://registry.npmjs.org/gulp-sequence/-/gulp-sequence-0.4.6.tgz"
    },
    "files": [
        "index.js"
    ],
    "gitHead": "484d711883102320166c452960cdfcc0309b961a",
    "homepage": "https://github.com/teambition/gulp-sequence",
    "keywords": [
        "gulpplugin",
        "sequence",
        "sync",
        "thunk",
        "thunks",
        "flow"
    ],
    "main": "index.js",
    "maintainers": [
        {
            "name": "zensh"
        }
    ],
    "name": "gulp-sequence",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/teambition/gulp-sequence.git"
    },
    "scripts": {
        "test": "gulp test"
    },
    "version": "0.4.6"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module gulp-sequence](#apidoc.module.gulp-sequence)
1.  [function <span class="apidocSignatureSpan"></span>gulp-sequence ()](#apidoc.element.gulp-sequence.gulp-sequence)
1.  [function <span class="apidocSignatureSpan">gulp-sequence.</span>toString ()](#apidoc.element.gulp-sequence.toString)
1.  [function <span class="apidocSignatureSpan">gulp-sequence.</span>use (gulp)](#apidoc.element.gulp-sequence.use)



# <a name="apidoc.module.gulp-sequence"></a>[module gulp-sequence](#apidoc.module.gulp-sequence)

#### <a name="apidoc.element.gulp-sequence.gulp-sequence"></a>[function <span class="apidocSignatureSpan"></span>gulp-sequence ()](#apidoc.element.gulp-sequence.gulp-sequence)
- description and source-code
```javascript
function gulpSequence() {
  if (!gulp) gulp = require('gulp')

  var BREAKER = {}
  var args = slice.call(arguments)
  var done = args[args.length - 1]

  if (typeof done === 'function') args.pop()
  else done = null

  if (!args.length) {
    throw new gutil.PluginError(packageName, 'No tasks were provided to gulp-sequence!')
  }

  var runSequence = thunk.seq(args.filter(function (taskName) {
    // filter falsely taskName
    return taskName
  }).map(function (task) {
    return function (callback) {
      if (!Array.isArray(task)) task = [task]

      function successListener (e) {
        var index = task.indexOf(e.task)
        if (index < 0) return
        task[index] = BREAKER
        for (var i = 0; i < task.length; i++) {
          if (task[i] !== BREAKER) return
        }
        removeListener()
        callback()
      }

      function errorListener (e) {
        if (!e.err || task.indexOf(e.task) < 0) return
        removeListener()
        callback(e.err)
      }

      function removeListener () {
        gulp.removeListener('task_stop', successListener)
          .removeListener('task_not_found', errorListener)
          .removeListener('task_recursion', errorListener)
          .removeListener('task_err', errorListener)
      }

      gulp
        .on('task_stop', successListener)
        .on('task_not_found', errorListener)
        .on('task_recursion', errorListener)
        .on('task_err', errorListener)
        .start(task.slice())
    }
  }))

  return done ? runSequence(done) : runSequence
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-sequence.toString"></a>[function <span class="apidocSignatureSpan">gulp-sequence.</span>toString ()](#apidoc.element.gulp-sequence.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.gulp-sequence.use"></a>[function <span class="apidocSignatureSpan">gulp-sequence.</span>use (gulp)](#apidoc.element.gulp-sequence.use)
- description and source-code
```javascript
use = function (gulp) {
  return sequence(gulp)
}
```
- example usage
```shell
...
'''js
var gulp = require('gulp')
var gulpSequence = require('gulp-sequence')

gulp.task('test', gulpSequence(['a', 'b'], 'c', ['d', 'e'], 'f'))
'''

### gulpSequence.use(gulp)
return a new gulpSequence function with the gulp. If you have some errors such as "task xxx is not defined", this will resolve it
.

'''js
var gulp = require('gulp')
var gulpSequence = require('gulp-sequence').use(gulp)

gulp.task('test', gulpSequence(['a', 'b'], 'c', ['d', 'e'], 'f'))
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
