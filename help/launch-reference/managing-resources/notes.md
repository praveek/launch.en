---
title: Notes
seo-title: Notes in Adobe Experience Platform Launch
description: Adobe Experience Platform Launch notes
seo-description: Adobe Experience Platform Launch notes
---

# Notes

Notes are textual annotations that you can add to certain Launch resources.  Currently, the notes can be attached to the following resources:

* Extensions
* Data Elements
* Rules
* Rule Components
* Libraries
* Properties

Notes can contain up to 512 Unicode characters.  That is a little more than twice the length of a modern tweet.

Notes are comments that have no impact on the behavior of the resources they are attached to.  They are not emitted into built libraries.  You might use Notes to:

1. provide background information on a resource
2. function as a to-do list for future enhancements
3. pass along resource usage advice to other users
4. give instructions to other team members
5. record historical context
6. remind yourself what a resource does, why it was built the way it is, or where it gets used

## Create a Note

Noteable resources will now display a narrow rail on the right-hand side of the screen.  Within the right rail, there is an icon for Notes.  This icon will display the current number of notes attached to the resource.

Clicking on the Notes icon will expand the right rail to display the Notes with the most recent Notes at the top.  To add a new Note, simply enter your Note text in the box at the top and click [!UICONTROL Add Note].

## Other

Notes in Launch currently match the behavior of Notes in DTM, namely they are immutable and cannot be edited or deleted.

When viewing older revisions of a resource, only the Notes that were created prior to that revision's `created_at` date will be displayed.

When you delete a resource, all Notes attached to the resource are also deleted.