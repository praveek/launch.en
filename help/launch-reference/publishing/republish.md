---
title: Republish Library
seo-title: Republishing Libraries in Adobe Experience Platform Launch
description: Adobe Experience Platform Launch library republish
seo-description: Adobe Experience Platform Launch library republish
---

# Republish Library

The most recent 5 Libraries that have been published to your production environment on a Web property are available for later retrieval.  

We developed this feature to support the the scenario when you say something like "Oh no, I just found a bug in my production library.  I don't have time to find it and fix it, I need to rollback to a known good state immediately."

The retrieval process will depend on your environment settings at the time that the library was originally published.  This is important to know, because retrieving an archived library will not change anything on your live site, while retrieving an regular library would.

1. Host: Managed by Adobe, Archive: Off - If you are using the Managed by Adobe host and you are not archiving your library, you can republish these older libraries.
2. Host: Managed by Adobe, Archive: On - If you are using the Managed by Adobe host and you are archiving your library, then you can download these older libraries.
3. Host: SFTP, Archive: On or Off - If you are using the SFTP host, we assume that you have your own archival strategies in place and no retrieval options are available.

Retrieval options for Mobile properties are not yet available.

## Republishing

Each Launch environment provides you with a link you to a Launch library file.  Any library that you build in that environment is referenceable with that link.

When you do a build to a development or a staging environment, the old build is cleaned up and the new build is deployed.  For your production environment, this link is updated to point to the latest build, but the latest five builds are kept around before they are cleaned up.

These most recent five builds in your production environment are the ones that are available for retrieval.

When you republish an older library, behind the scenes Launch is simply updating the environment link to point to one of these older builds that hasn't been cleaned up yet.  Launch will also issue a purge request to the CDN edge nodes cache to indicate that the library has been updated and they should retrieve a fresh copy from the origin.

This means that when you republish an older library:

1. No changes are made to any of the resources (or historical revisions) in your Launch property
2. The way that development and staging environments calculate what is upstream will not change

Consider the scenario when you rollback back because of a problem with a specific rule.  The rule revision that is now in production is three revisions old (for example).  When you view that rule in the Launch UI to fix it, it will still reflect the latest changes saved rather than what is currently in production.

For this reason, Launch will notify you that a property is in a republished state as a reminder that what you're seeing in the UI is a little farther removed from Production than usual.  This notification is dismissable and will appear once per browser session the first time that you view the property.

### How to Republish an older library

![Republish a library](/help/assets/retrieve_republish.png)

From the Publishing screen:

1. Find the library in the Published column that you'd like to republish
2. Click the triple-dots in the upper right of the Library card
3. Click Republish

## Download

Downloading an Archived library is more straightforward.  You aren't directly referencing these .zip files on anywhere anyway, so you can simply download the older library to your computer and run your usual process.

### How to Download and older library

![Download a library](/help/assets/retrieve_download.png)

From the Publishing screen:

1. Find the library in the Published column that you'd like to download
2. Click the triple-dots in the upper right of the Library card
3. Click Download
