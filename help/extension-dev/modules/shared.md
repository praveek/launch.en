---
title: Shared modules
seo-title: Shared modules
description: Shared modules
seo-description: Shared modules
---

# Shared modules

A shared module is a mechanism by which you can communicate with other extensions.

For example, you can create a module that loads a user ID asynchronously and then shares the user ID with any other extension via a [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise):

```javascript
var userIdPromise = new Promise(/* load user id, then resolve promise */);
module.exports = userIdPromise;
```

In the [extension manifest](../manifest.md) you have to provide a name for this shared module. If you name it `user-id-promise`, a different extension could then access this shared module as follows:

```javascript
var userIdPromise = turbine.getSharedModule('user-extension', 'user-id-promise');
```

Shared modules can be anything you would typically be able to export from a CommonJS module (such as functions, objects, strings, numbers, or booleans).
