---
title: Release notes
seo-title: Adobe Launch Release notes
description: Adobe Launch release notes
seo-description: Adobe Launch release notes
---

# Release notes

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
