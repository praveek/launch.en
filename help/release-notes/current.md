---
title: Release notes
seo-title: Adobe Launch Release notes
description: Adobe Launch release notes
seo-description: Adobe Launch release notes
---

# Release notes

## July 7th, 2020

### Features

* **Rule Component Sequencing:** Check **[!UICONTROL Run rule components in sequence]** in your property settings.  When enabled, the Launch runtime adds rule conditions and actions to a processing queue when the rule event is triggered.  The queue is processed on a FIFO basis with timeouts available on individual components.  See the [Rules page](../launch-reference/managing-resources/rules.md) for more information on available settings and details.
* **Promises in Core - Custom Code:** You can do asynchronous tasks in Core - Custom Code boxes.  In order to achieve this, you can return a Promise from your JavaScript custom code or use the new `onCustomCodeSuccess()` and `onCustomCodeFailure()` functions in HTML custom code.  More information is available in the [Core Extension reference](../extension-reference/web/core-extension/overview.md) doc.

## June 18th, 2020

### Features

* **Left-rail navigation:** The main pages for your day-to-day work within a property are moving from under the property name into a collapsible left-rail. These are nowbalso organized into some logical groups based on usage intent and patterns.
* **App breadcrumbs:** Breadcrumbs have been added throughout the app.  You should always have context now, regardless of what screen you're looking at.  This includes showing you rule names when you're modifying components, telling you how you got four levels deep in the compare screen you're looking at, and a few other things.  The top of the screen has been reorganized to maximize the amount of screen space you have for your day-to-day tasks.  You should still be able to find everything you're looking for with ease.
* **A new endpoint was added:** `{{extension_package_id}}/versions` allows API users to see all versions of extension packages that are public. API users can also see version information for extension packages that are in devlopment or private for orgs they belong to. See [https://developer.adobelaunch.com/api/reference/1.0/extension_packages/](https://developer.adobelaunch.com/api/reference/1.0/extension_packages/)

### Bug Fixes

* Notes now show show the name of the user who entered the note.
* In some cases, users were not able to download previous versions of archive production libraries due to a CORS issue. This has been fixed. 
* A `no-cache` header was added to the UI. Previously users had to hard refresh to get updates when JS files changed.

## June 9th, 2020

### Features

* Property Overview: the overview page was long overdue for an update.  Now after you select your property, we'll show you some some important information about your property including: the most recent production publish date, libraries that need approval, extensions that have available updates, and a list of your most recent activity within that property.  We've also got some helpful links and will use this page to notify you about product releases and technical advisories as needed.

## June 2nd, 2020

### Features

* **Discontinue Extension Packages:** Extension developers can now discontinue their extension packages.  A discontinued extension package is no longer available for new installations from the Launch catalog. However, existing installations continue to work as expected.  Please see [Discontinue an ExtensionPackage](https://developer.adobelaunch.com/api/reference/1.0/extension_packages/discontinue/) in the developer docs for more details.

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

* Rows per page: List pages now allow you to specify how many rows you'd like to see on each page.
* Pagination: List pages now have improved pagination that shows you how many pages are available and lets you jump to a specific page.  Page numbers are based on the number of rows per page

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
