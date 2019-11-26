---
title: Adobe Experience Platform Web Extension
seo-title: Adobe Experience Platform Web Extension in Adobe Experience Platform Launch
description: Adobe Experience Platform Web Extension in Adobe Experience Platform Launch
seo-description: Adobe Experience Platform Web Extensionin Adobe Experience Platform Launch
---

# AEP Extension Release Notes

## November 25, 2019

### AEP Extention 0.6

#### Features 

* New Merge ID and Type fields on the Send Event action. Merge ID maps to `xdm.eventMergeID` in the XDM schema and Type maps to `xdm.eventType` in the XDM schema. 
* Improved error handling and reporting
* Now uses `sendBeacon` for all links

#### Bug Fixes

* Fixed and issue where toggling debugging through a query string parameter or the `debug` command wouldn't persist through the session.

## November 18, 2019

### AEP Extention 0.5

#### Features

* Extension winked into existance
* ECID support with no additional libraries or networks calls
* Opt-in support
* Support sending XDM to AEP
* First-party domain support
* Automatically collect browser context
* Fully open source ([extension](https://github.com/adobe/reactor-extension-alloy), [SDK](https://github.com/adobe/reactor-extension-alloy))
* Detailed logging
* Ability to hide errors in production
