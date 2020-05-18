---
title: Adobe Experience Platform Web Extension
seo-title: Adobe Experience Platform Web Extension in Adobe Experience Platform Launch
description: Adobe Experience Platform Web Extension in Adobe Experience Platform Launch
seo-description: Adobe Experience Platform Web Extension in Adobe Experience Platform Launch
---

# AEP Extension Release Notes

## May 4, 2020

### AEP Extension 0.1.2

#### Features

* Renamed `configId` to `edgeConfigId`.
* Renamed `viewStart` to `renderDecisions`, set to false by default. If set to true, Personalization offers are fetched and auto-rendered.
* Changes related to `Get Decisions`:
  * Removed the `getDecisions` command.
  * Added a `scopes` option to the `sendEvent` command. Decisions are returned in the `sendEvent` resolved promise.
  * Added a built-in `__view__` scope which will result in returning page/view wide offers. (VEC offers in Target for example.)
Those decisions return from the `sendEvent` command only if `renderDecisions` is set to false.
  * Added a `Decisions Received` event, which fires when decisions become available. 
* Combined multiple Personalization notifications under a single server call.
* Fixed issue in Event Merge ID where it was being reset every time the data element was referenced.
* Renamed the `setCustomerIds` action to `syncIdentity`.
* Added a `getIdentity` command. This can be consumed via custom code only for now.
* Enabling debug using `_satellite` now enables debugging in the AEP Extension.
* Added support for typed values in the XDM Object: Booleans, Numbers and Decimals.

## March 16, 2020

### AEP Extension 0.0.10

#### Features

* Combined the concepts of Opt-In & Opt-Out under `Consent`, and added a new `setConsent` command.
* Added a new Data Element of type `XDM Object` which allows mapping from JavaScript/JSON to XDM.

## February 18, 2020

### AEP Extension 0.0.7

#### Features

* Removed idSyncContainerId, datasetId, schemaId, urlDestinationsEnabled, and cookieDestinationsEnabled options
* Added support for hyphens in edgeDomain option value
* Request made during ID migration is sent to demdex endpoint to improve cross-domain identification when demdex cookie is not set
* Request made during ID migration always expects a response to ensure identity cookie gets set
* When executing an invalid command, a list of valid command names will be logged in the console
* Added checkbox for toggling third-party cookie support to the Launch extension. This disables calls to demdex.net

## December 20, 2019

### AEP Extension 0.0.5

#### Features 

* Add Activity Tracker configs to Launch Extension
* Expose EventType and EventMergeId on event command
* Add onBeforeEventSend config to Launch Extension
* Add edgeBasePath config to Launch Extension

#### Update to Alloy v. 0.0.10 which includes the following changes:

* Implement Client Storage: State and cookies logic moved to the server
* Expose EventType and EventMergeId on event command
* Use sendBeacon for link tracking other than exit links
* Bring back ID Syncs minus checking for expiry
* setCustomerIds command not hashing ids on non-SSL (http) pages
* Pass the APEX domain to the server to be used when setting state/cookies
* Pick up the ECID from the response using a new handle type
* Remove defaults for Activation & Identity configs
* Rename + move query options to meta
* Legacy ECID Migration

#### Bug Fixes

* On unexpected status code, parse and format response body for error message
* Running debug command or using alloy_debug gets overwritten by configuration

## November 25, 2019

### AEP Extension 0.0.3

#### Features 

* New Merge ID and Type fields on the Send Event action. Merge ID maps to `xdm.eventMergeID` in the XDM schema and Type maps to `xdm.eventType` in the XDM schema. 
* Improved error handling and reporting
* Now uses `sendBeacon` for all links

#### Bug Fixes

* Fixed an issue where toggling debugging through a query string parameter or the `debug` command wouldn't persist through the session.

## November 18, 2019

### AEP Extension 0.0.2

#### Features

* Extension winked into existence
* ECID support with no additional libraries or networks calls
* Opt-in support
* Support sending XDM to AEP
* First-party domain support
* Automatically collect browser context
* Fully open source ([extension](https://github.com/adobe/reactor-extension-alloy), [SDK](https://github.com/adobe/reactor-extension-alloy))
* Detailed logging
* Ability to hide errors in production
