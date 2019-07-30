---
title: Release notes
seo-title: Adobe Launch Release notes
description: Adobe Launch release notes
seo-description: Adobe Launch release notes
---

# Release notes

## June 18, 2019

### Updates

* Libraries that use the [!DNL Managed by Adobe] host and a non-archived environment will now reference all sub files directly with `https://` instead of inheriting the underlying page protocol.  This enables you to use [!DNL Launch] in embedded HTML scenarios (mobile and set-top-box environment in particular) without self-hosting.
* You can now unset your Working Library.
* The Edit Library screen now has a button to [!UICONTROL Remove All Resources].
* The size of the click target has increased to remove individual resources from a library

### Bug Fixes

* Fixed a bug in [!DNL Safari] that caused the [!UICONTROL Add Resource] buttons on the Library Edit page to show in the wrong place.
* Fixed a bug with validating uppercase domains on the Property Edit screen.
* Fixed a bug that caused some buttons to be available when they should not be.

## June 13, 2019

### Updates

* Error messages now provide much more detail about the error that occurred (for those who want to look).  They also provide an easy way to log tickets and some key identifiers that will help [!DNL Adobe] to troubleshoot any issues.  And they've moved to the bottom center of the page to comply with the latest [!DNL Adobe] styles.
* The [!UICONTROL Add Resource] buttons on the Library Edit page now float as you scroll up and down so they are always visible.
* The URLS for Resource Comparison are more informative (and useful for debugging purposes).

## Bug Fixes

* Fixed a bug in Edge on Windows 10 that wouldn't let you promote libraries in Edge on Windows 10.
* Fixed a bug in Edge on Windows 10 that prevented library resources from being displayed on the Library edit page.
* Fixed a bug that was showing scroll bars in unnecessary places.
* Fixed several broken links that were scattered about.
* Fixed several non-scrollable areas for iOS browsers.


## June 15, 2019

### Updates

* Archive packages on SFTP Hosts will now be delivered to the root patch specified by the Host instead of being delivered two subdirectories deep (which is how all other builds are delivered).  This was change because of permissions issues creating subdirectories on some SFTP servers.

## June 11, 2019

### Updates

* Archive packages now use relative symlinks instead of absolute ones.

### Bug Fixes

* You can no longer delete a Host that is being used by an environment.

## May 8, 2019

The [!DNL Reactor] API that powers [!DNL Launch] is officially reaching 1.0 status today.  This comes with a commitment to maintaining backwards compatibility within this major version (the 1.x series).  To get started working with the [!DNL Reactor] API, please visit [https://developer.adobelaunch.com/api/\#](https://developer.adobelaunch.com/api/#).

### Updates

* A number of API changes have been made for this 1.0 release.  API release notes will be posted with the API documentation at [https://developer.adobelaunch.com/api/release\_notes/2019-release-notes/](https://developer.adobelaunch.com/api/release_notes/2019-release-notes/).
* `Adapter` has been renamed to `Host`. Audit events will contain the following items related to this change.
  * For each adapter, you'll see a `Host.created` event.
  * For each environment, you'll see an `Environment.updated` event to remove the relationship with the adapter and add the relationship to the host.
  * For each adapter, you'll see an `Adapter.deleted` event.

### Bug Fixes

* Fixed some inconsistencies with the Regular Expression tester used by various extensions.

## April 8, 2019

### Bug Fixes

* Improved a few build error messages
* Better reporting for failed SFTP Hosts

### Other

* Updated the way that rule components and data elements relate to extensions.  When you delete an extension and reinstall an extension, you no longer have to manually update your resources to point to the newly installed extension.
* Rule components are now under Property instead of Rule.  This lays a foundation for future enhancements to rule components.

## March 20, 2019

### Updates

* Visual updates to the resource copy tool, including status indicators and a cancel button.

## March 5, 2019

### Bug Fixes

* Builds stored on Akamai will use a new folder structure.  Embed codes do not change. This will mediate many issues we've seen with builds to Akamai.

## February 20, 2019

### Updates

* Support for custom code has been added to Compare View.

### Bug fixes

* The cross-property workflow is now a bit smoother.

## February 12, 2019

### Features

* Cross-property Copy - You can now copy resources from one property to another.  After selecting a resource and clicking the **[!UICONTROL Copy]** button, you can select a target property to copy to.  This is available on extensions, data elements, and rules.  Read more about copying resources [here](../launch-reference/managing-resources/copying-resources.md).

## January 29, 2019

### Features

* Revision Compare - You can now compare one version of a resource with older versions.  This is available on extensions, data elements, and rules.  Read more about this new feature [here](../launch-reference/managing-resources/compare-resource-revisions.md).

## January 17, 2019

### Updates

* Builds should be running ~15% faster than before.  Large builds (hundreds of resources) will have more dramatic improvements.

## January 8, 2019

### Core Extension 1.4.2

* The `Enters Viewport` event is now configurable to trigger each time that the element enters the viewport instead of just the first time.
* Custom Events can now contain extra contextual data that can be used in conditions and actions.
* Link Delay on the Click event will now trigger on descendants of the anchor and not just the anchor itself.

### Updates

* Properties that are configured for Extension Development now have a small tag next to the Property Name.
* OrgID is now available on the \_satellite object.
* Use of the [!DNL Launch] UI is no longer supported in IE 11, you'll receive a warning if you login with IE 11.

### Bug fixes

* Better support for long library names in your Active Library and the Publishing view.
* In certain scenarios, when you saved a library, the dependency checker would prompt you to add a new revision of an extension that was already in your library. It doesn't do that anymore.
* Tooltips will now reliably show up in Safari.
* Searches in the search bar will now trigger a bit faster than before.

