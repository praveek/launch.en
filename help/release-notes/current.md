---
title: Release notes
seo-title: Adobe Launch Release notes
description: Adobe Launch release notes
seo-description: Adobe Launch release notes
---

# Release notes

## May 9th, 2020

### Bug Fixes

* When using Safari <= v12, users were not able to access Adobe Platform Launch due to an `X-FRAME-OPTIONS` header that was being set incorrectly.
* Notification messages were not displaying with the correct format in FireFox.

## April 24th, 2020

### Bug Fixes

* Error states on unselected library edit resources were not always cleared correctly. 

## April 13th, 2020

### Bug Fixes

* Tooltips on the Data Element Selector Dialog were not displaying correctly.

## March 18th, 2020

### Bug Fixes

* When a user tried to create a rule with a comma in the name, they would receive a false "duplicate name" error.

### Features

* When a rule component (event, condition, or action) is updated, the `updated_at` attribute for the rule it belongs to is also updated. This more accurately reflects that the behavior of the rule has changed by modifying one or more of its components. If you use callbacks for rules, you will see an increase in rule `updated_at` callbacks. See [https://developer.adobelaunch.com/api/reference/1.0/rule_components/](https://developer.adobelaunch.com/api/reference/1.0/rule_components/) for more information.

## March 3, 2020

### Updates

* The Launch sign-in and sign-out UI has been significantly improved. Switching between Launch and other Adobe products is now also much smoother. Finally, if you have a single account with rights to multiple companies, this is also dramatically improved.
* The structure of Launch URLs is now more consistent with other Adobe products. The new URL format replaces `https://launch.adobe.com` with `https://experience.adobe.com/#/@companyID/launch/`. The old URLs redirect to the new ones, but you should update your bookmarks to save a few seconds each time you access Launch.

## February 19, 2020

### Features

* Improved list view pagination:
** Users can jump to a specific page in a list
** Users can select the number of rows to display

## February 6, 2020

### Features

* The JavaScript runtime library has been updated to include version 2.2.1 of js-cookie. A vulnerability was discovered in version 2.1.4 that was previously deployed. The next time a library is built, this new version of js-cookie will be automatically included.
* Code minification errors of user defined custom code, which may occur while building a library, have been enhanced to give the user more context about the error.

## January 16, 2020

### Bug Fixes

* The republish library feature would sometimes not purge the Launch asset on Akamai properly and result in the original library still being served.

### Features

* Enhanced extension package validation is now performed at the time of upload.

## January 07, 2020

### Bug Fixes

* Property create no longer causes an erroneous 404 error. The property was still created and usable even though the error occurred.
