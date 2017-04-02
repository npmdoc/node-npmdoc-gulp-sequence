# api documentation for  [gulp-sequence (v0.4.6)](https://github.com/teambition/gulp-sequence)  [![npm package](https://img.shields.io/npm/v/npmdoc-gulp-sequence.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-gulp-sequence) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-gulp-sequence.svg)](https://travis-ci.org/npmdoc/node-npmdoc-gulp-sequence)
#### Run a series of gulp tasks in order.

[![NPM](https://nodei.co/npm/gulp-sequence.png?downloads=true)](https://www.npmjs.com/package/gulp-sequence)

[![apidoc](https://npmdoc.github.io/node-npmdoc-gulp-sequence/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-gulp-sequence_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-gulp-sequence/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-gulp-sequence/build/screen-capture.npmPackageListing.svg)



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
            "name": "zensh",
            "email": "admin@zensh.com"
        }
    ],
    "name": "gulp-sequence",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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
1.  [function <span class="apidocSignatureSpan">gulp-sequence.</span>use (gulp)](#apidoc.element.gulp-sequence.use)



# <a name="apidoc.module.gulp-sequence"></a>[module gulp-sequence](#apidoc.module.gulp-sequence)

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
