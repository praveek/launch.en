---
title: Adobe Target v2 Release Notes
seo-title: Adobe Target v2 Release Notes in Adobe Experience Platform Launch
description: Release notes for Adobe Target v2 extension in Adobe Experience Platform Launch
seo-description: Release notes for Adobe Target v2 extension in Adobe Experience Platform Launch
---

# Adobe Target v2 Extension Release Notes

## March 25, 2020

### Adobe Target v2 Extension 0.13.0

* Updated at.js to v2.3.
* Added Target Global Mbox support in adobe.target.getOffer API
* Fixed an issue where params and page load params were not processed correctly


## October 10, 2019

### Adobe Target v2 Extension 0.12.0

* Updated at.js to v2.2.
* Improved performance for integrations between Experience Cloud ID library (ECID) v4.4 and at.js 2.2.
* Previously, the ECID library made two blocking calls before at.js could fetch experiences. This has been reduced to a single call, which significantly improves performance.

>[!NOTE]
>Please upgrade your ECID Launch Extension to v4.4.1 to take advantage of this performance enhancement.

## July 31, 2019

### Adobe Target v2 Extension 0.11.1

* Updated extension version to use at.js 2.1.1
* Added a fix for handling parameters

## June 3, 2019

### Adobe Target v2 Extension 0.11.0

* New Adobe Launch extension to support at.js 2.1
