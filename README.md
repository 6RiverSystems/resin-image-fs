resin-image-fs
--------------

[![npm version](https://badge.fury.io/js/resin-image-fs.svg)](http://badge.fury.io/js/resin-image-fs)
[![dependencies](https://david-dm.org/resin-io/resin-image-fs.png)](https://david-dm.org/resin-io/resin-image-fs.png)
[![Build Status](https://travis-ci.org/resin-io/resin-image-fs.svg?branch=master)](https://travis-ci.org/resin-io/resin-image-fs)
[![Build status](https://ci.appveyor.com/api/projects/status/86bot1jaepcg5xlv?svg=true)](https://ci.appveyor.com/project/jviotti/resin-image-fs)

Resin.io image filesystem manipulation utilities.

Role
----

The intention of this module is to provide low level utilities to Resin.io operating system data partitions.

**THIS MODULE IS LOW LEVEL AND IS NOT MEANT TO BE USED BY END USERS DIRECTLY**.

Installation
------------

Install `resin-image-fs` by running:

```sh
$ npm install --save resin-image-fs
```

Documentation
-------------


* [imagefs](#module_imagefs)
  * [.read(definition)](#module_imagefs.read) ⇒ <code>Promise.&lt;ReadStream&gt;</code>
  * [.write(definition, stream)](#module_imagefs.write) ⇒ <code>Promise</code>
  * [.copy(input, output)](#module_imagefs.copy) ⇒ <code>Promise</code>

<a name="module_imagefs.read"></a>
### imagefs.read(definition) ⇒ <code>Promise.&lt;ReadStream&gt;</code>
**Kind**: static method of <code>[imagefs](#module_imagefs)</code>  
**Summary**: Read a device file  
**Returns**: <code>Promise.&lt;ReadStream&gt;</code> - file stream  
**Access:** public  

| Param | Type | Description |
| --- | --- | --- |
| definition | <code>String</code> | device path definition |

**Example**  
```js
imagefs.read('/foo/bar.img(4:1):/baz/qux').then (stream) ->
		stream.pipe(fs.createWriteStream('/bar/qux'))
```
<a name="module_imagefs.write"></a>
### imagefs.write(definition, stream) ⇒ <code>Promise</code>
**Kind**: static method of <code>[imagefs](#module_imagefs)</code>  
**Summary**: Write to a device file  
**Access:** public  

| Param | Type | Description |
| --- | --- | --- |
| definition | <code>String</code> | device path definition |
| stream | <code>ReadStream</code> | contents stream |

**Example**  
```js
imagefs.write('/foo/bar.img(2):/baz/qux', fs.createReadStream('/baz/qux'))
```
<a name="module_imagefs.copy"></a>
### imagefs.copy(input, output) ⇒ <code>Promise</code>
**Kind**: static method of <code>[imagefs](#module_imagefs)</code>  
**Summary**: Copy a device file  
**Access:** public  

| Param | Type | Description |
| --- | --- | --- |
| input | <code>String</code> | input device type definition |
| output | <code>String</code> | output device type definition |

**Example**  
```js
imagefs.copy('/foo/bar.img(2):/baz/qux', '/foo/bar.img(4:1):/baz/hello')
```

Support
-------

If you're having any problem, please [raise an issue](https://github.com/resin-io/resin-image-fs/issues/new) on GitHub and the Resin.io team will be happy to help.

Tests
-----

Run the test suite by doing:

```sh
$ gulp test
```

Contribute
----------

- Issue Tracker: [github.com/resin-io/resin-image-fs/issues](https://github.com/resin-io/resin-image-fs/issues)
- Source Code: [github.com/resin-io/resin-image-fs](https://github.com/resin-io/resin-image-fs)

Before submitting a PR, please make sure that you include tests, and that [coffeelint](http://www.coffeelint.org/) runs without any warning:

```sh
$ gulp lint
```

License
-------

The project is licensed under the MIT license.
