---
title: Release notes
seo-title: Adobe Launch Release notes
description: Adobe Launch release notes
seo-description: Adobe Launch release notes
---

# Release notes

## March 3, 2020

### Updates

* We've updated the Launch UI to bring dramatic improvements to the sign in and out process.  Switching between Launch and other Adobe products will also be much smoother now.  Finally, for those of you have a single account with rights to multiple companies, this is also dramatically improved.
* The structure of Launch URLs is now mor consistent with other Adobe products.  The new URL format replaces `https://launch.adobe.com` with `https://experience.adobe.com/#/@companyID/launch/`.  The old URLs will redirect to the new ones, but you'll want to update your bookmarks to save yourself a few seconds each time you go there.

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
