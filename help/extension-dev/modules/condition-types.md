---
title: Condition types
seo-title: Condition types
description: Condition types
seo-description: Condition types
---

# Condition types

A condition type library module has one goal: evaluate whether something is true or false. What it evaluates is up to you.

For example, if you wanted to evaluate whether the user is on the host `example.com`, your module may look like this:

```js
module.exports = function(settings) {
  return document.location.hostname === 'example.com';
};
```

Now, consider a situation where you want to make the hostname configurable by the Adobe Experience Platform Launch user. You may allow the user to input a hostname and then save the hostname to the settings object. The object might look something like this:

```js
{
  "hostname": "example.com"
}
```

In order to operate on the user-defined hostname, your module would need to change to this:

```js
module.exports = function(settings) {
  return document.location.hostname === settings.hostname;
};
```

## Contextual event data

A second argument is passed to your module which contains contextual information regarding the event that fired the rule. It may be beneficial in certain cases and can be accessed as follows:

```js
module.exports = function(settings, event) {
  // event contains information regarding the event that fired the rule
};
```

The `event` object must contain the following properties:

| Property | Description |
| --- | --- |
| `$type` | A string describing the extension name and event name, joined using a period. For example, `youtube.play`. |
| `$rule` | An object containing information about the currently executing rule. The object must contain the following sub-properties:<ul><li>`id`: The ID of the currently executing rule.</li><li>`name`: The name of the currently executing rule.</li></ul> |

The extension providing the event type that triggered the rule may optionally add any other useful information to this `event` object.
