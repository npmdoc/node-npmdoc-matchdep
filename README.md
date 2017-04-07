# api documentation for  [matchdep (v1.0.1)](https://github.com/tkellen/node-matchdep)  [![npm package](https://img.shields.io/npm/v/npmdoc-matchdep.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-matchdep) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-matchdep.svg)](https://travis-ci.org/npmdoc/node-npmdoc-matchdep)
#### Use globule to filter npm module dependencies by name.

[![NPM](https://nodei.co/npm/matchdep.png?downloads=true)](https://www.npmjs.com/package/matchdep)

[![apidoc](https://npmdoc.github.io/node-npmdoc-matchdep/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-matchdep_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-matchdep/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-matchdep/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-matchdep/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Tyler Kellen",
        "url": "http://goingslowly.com/"
    },
    "bugs": {
        "url": "https://github.com/tkellen/node-matchdep/issues"
    },
    "dependencies": {
        "findup-sync": "~0.3.0",
        "micromatch": "^2.3.7",
        "resolve": "~1.1.6",
        "stack-trace": "0.0.9"
    },
    "description": "Use globule to filter npm module dependencies by name.",
    "devDependencies": {
        "grunt": "~0.4.1",
        "grunt-contrib-jshint": "~0.11.3",
        "grunt-contrib-nodeunit": "~0.4.1"
    },
    "directories": {},
    "dist": {
        "shasum": "a57a33804491fbae208aba8f68380437abc2dca5",
        "tarball": "https://registry.npmjs.org/matchdep/-/matchdep-1.0.1.tgz"
    },
    "engines": {
        "node": ">= 0.10.0"
    },
    "gitHead": "c0eb918c1838c89b6bdf5ce4295f3ec37398f7b0",
    "homepage": "https://github.com/tkellen/node-matchdep",
    "keywords": [
        "package.json",
        "dependencies",
        "devDependencies",
        "peerDependencies"
    ],
    "license": "MIT",
    "main": "lib/matchdep",
    "maintainers": [
        {
            "name": "phated",
            "email": "blaine@iceddev.com"
        },
        {
            "name": "tkellen",
            "email": "tyler@sleekcode.net"
        }
    ],
    "name": "matchdep",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/tkellen/node-matchdep.git"
    },
    "scripts": {
        "test": "grunt"
    },
    "version": "1.0.1"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module matchdep](#apidoc.module.matchdep)
1.  [function <span class="apidocSignatureSpan">matchdep.</span>filter (pattern, config)](#apidoc.element.matchdep.filter)
1.  [function <span class="apidocSignatureSpan">matchdep.</span>filterAll (pattern, config)](#apidoc.element.matchdep.filterAll)
1.  [function <span class="apidocSignatureSpan">matchdep.</span>filterDev (pattern, config)](#apidoc.element.matchdep.filterDev)
1.  [function <span class="apidocSignatureSpan">matchdep.</span>filterPeer (pattern, config)](#apidoc.element.matchdep.filterPeer)



# <a name="apidoc.module.matchdep"></a>[module matchdep](#apidoc.module.matchdep)

#### <a name="apidoc.element.matchdep.filter"></a>[function <span class="apidocSignatureSpan">matchdep.</span>filter (pattern, config)](#apidoc.element.matchdep.filter)
- description and source-code
```javascript
filter = function (pattern, config) {
  config = loadConfig(config, props);
  var search = props.reduce(function(result, prop) {
    return result.concat(config[prop]);
  }, []);
  return micromatch(search, pattern);
}
```
- example usage
```shell
...

## Examples

'''js
var matchdep = require('matchdep');

// Filter dependencies (by autoloading nearest package.json)
matchdep.filter('mini*');

// Filter devDependencies (with config string indicating file to be required)
matchdep.filterDev('grunt-contrib-*', './package.json');

// Filter peerDependencies (with config string indicating file to be required)
matchdep.filterPeer('foo-{bar,baz}', './some-other.json');
...
```

#### <a name="apidoc.element.matchdep.filterAll"></a>[function <span class="apidocSignatureSpan">matchdep.</span>filterAll (pattern, config)](#apidoc.element.matchdep.filterAll)
- description and source-code
```javascript
filterAll = function (pattern, config) {
  config = loadConfig(config, props);
  var search = props.reduce(function(result, prop) {
    return result.concat(config[prop]);
  }, []);
  return micromatch(search, pattern);
}
```
- example usage
```shell
...
// Filter devDependencies (with config string indicating file to be required)
matchdep.filterDev('grunt-contrib-*', './package.json');

// Filter peerDependencies (with config string indicating file to be required)
matchdep.filterPeer('foo-{bar,baz}', './some-other.json');

// Filter all dependencies (with explicit config provided)
matchdep.filterAll('*', require('./yet-another.json'));

// Filter all dependencies, exclude grunt (multiple matching patterns)
matchdep.filterAll(['*','!grunt']);
'''

## Usage
...
```

#### <a name="apidoc.element.matchdep.filterDev"></a>[function <span class="apidocSignatureSpan">matchdep.</span>filterDev (pattern, config)](#apidoc.element.matchdep.filterDev)
- description and source-code
```javascript
filterDev = function (pattern, config) {
  config = loadConfig(config, props);
  var search = props.reduce(function(result, prop) {
    return result.concat(config[prop]);
  }, []);
  return micromatch(search, pattern);
}
```
- example usage
```shell
...
'''js
var matchdep = require('matchdep');

// Filter dependencies (by autoloading nearest package.json)
matchdep.filter('mini*');

// Filter devDependencies (with config string indicating file to be required)
matchdep.filterDev('grunt-contrib-*', './package.json');

// Filter peerDependencies (with config string indicating file to be required)
matchdep.filterPeer('foo-{bar,baz}', './some-other.json');

// Filter all dependencies (with explicit config provided)
matchdep.filterAll('*', require('./yet-another.json'));
...
```

#### <a name="apidoc.element.matchdep.filterPeer"></a>[function <span class="apidocSignatureSpan">matchdep.</span>filterPeer (pattern, config)](#apidoc.element.matchdep.filterPeer)
- description and source-code
```javascript
filterPeer = function (pattern, config) {
  config = loadConfig(config, props);
  var search = props.reduce(function(result, prop) {
    return result.concat(config[prop]);
  }, []);
  return micromatch(search, pattern);
}
```
- example usage
```shell
...
// Filter dependencies (by autoloading nearest package.json)
matchdep.filter('mini*');

// Filter devDependencies (with config string indicating file to be required)
matchdep.filterDev('grunt-contrib-*', './package.json');

// Filter peerDependencies (with config string indicating file to be required)
matchdep.filterPeer('foo-{bar,baz}', './some-other.json');

// Filter all dependencies (with explicit config provided)
matchdep.filterAll('*', require('./yet-another.json'));

// Filter all dependencies, exclude grunt (multiple matching patterns)
matchdep.filterAll(['*','!grunt']);
'''
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
