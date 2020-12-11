---
title: Core modules
seo-title: Core modules
description: Core modules
seo-description: Core modules
---

# Core modules

This document provides a list of core modules that you may use within your library modules. You may access these modules using `require('@adobe/reactor-name-of-module')`. 

## [!DNL @adobe/reactor-object-assign]

Mimics the native [`Object.assign`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) method by copying properties from source objects to a target object.

```javascript
var objectAssign = require('@adobe/reactor-object-assign');
var all = objectAssign({ a: 'a' }, { b: 'b' });
```

## [!DNL @adobe/reactor-cookie]

A utility for reading and writing cookies. See the [js-cookie npm package](https://www.npmjs.com/package/js-cookie) for more information.

```javascript
var cookie = require('@adobe/reactor-cookie');
cookie.set('foo', 'bar');
console.log(cookie.get('foo'));
cookie.remove('foo');
```

### [!DNL @adobe/reactor-document]

The [`document`](https://developer.mozilla.org/en-US/docs/Web/API/Document) object. This can be beneficial when testing the module by allowing tests to inject a mock `document` object using utilities like [`inject-loader`](https://www.npmjs.com/package/inject-loader).

```javascript
var document = require('@adobe/reactor-document');
console.log(document.location);
```

### [!DNL @adobe/reactor-query-string]

A utility for parsing and serializing [query strings](https://developer.mozilla.org/en-US/docs/Web/API/HTMLHyperlinkElementUtils/search).

```javascript
var queryString = require('@adobe/reactor-query-string');
var parsed = queryString.parse(location.search);
console.log(parsed.campaign);
var obj = {
  campaign: 'Campaign A'
};
var stringified = queryString.stringify(obj);
```

The utility has the following methods:

* `queryString.parse(string: String)`: Parses a query string into an object. Leading `?`, `#`, and `&` characters on the query string are ignored.
* `queryString.stringify(object: Object)`: Stringifies an object into a query string.

### [!DNL @adobe/reactor-load-script]

Loads a script when given a URL. A script tag will be created and placed within the `head` node of the document. A [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) will be returned which you may use to determine when loading of the script succeeds or fails.

```javascript
var loadScript = require('@adobe/reactor-load-script');
var url = 'http://code.jquery.com/jquery-3.1.1.js';
loadScript(url).then(function() {
  // Do something ...
})
```

### [!DNL @adobe/reactor-promise]

A constructor that mimics the [Promise API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) native in ECMAScript 6. If the native Promise API is available, it will be returned instead.

```javascript
var Promise = require('@adobe/reactor-promise');
new Promise(function(resolve) {
  resolve();
}, function(err) {
  console.error(err);
});
```

### [!DNL @adobe/reactor-window]

The [`window`](https://developer.mozilla.org/en-US/docs/Web/API/Window) object. This can be beneficial when testing the module by allowing tests to inject a mock `window` object using utilities like [`inject-loader`](https://www.npmjs.com/package/inject-loader).

```javascript
var window = require('@adobe/reactor-window');
console.log(window.document);
```
