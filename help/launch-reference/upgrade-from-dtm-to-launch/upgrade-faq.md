---
title: Upgrade FAQ
seo-title: Upgrade FAQ in Adobe Launch
description: 
seo-description: 
---

# Upgrade FAQ

## What does the Launch Upgrade do? {#what-does-the-launch-upgrade-do}

The Launch Upgrade reads your DTM property and attempts to make a complete copy of that property in Launch. The resulting Launch property mimics the on-page behavior of your DTM property as closely as possible. To read about differences in structure, see [Upgrade Preparation Guide](upgrade-preparation-guide.md).

When the upgrade is complete, a new property appears in Launch and a link to the new property is created. If the upgrade doesn't work, partially completed operations are deleted and an error message explains as much as possible about what went wrong. In some cases, error messages inform you that you can modify your DTM property and try the upgrade again.

The upgrade does not make any changes to your DTM property.

## How should I prepare to upgrade? {#how-do-i-prepare-to-upgrade}

Not everything you can do in DTM is compatible with Launch. A list of differences is available in the [preparation guide](upgrade-preparation-guide.md). Make any necessary changes to your DTM property before you attempt the upgrade.

## How do I start the upgrade? {#how-do-i-start-the-upgrade}

Log in to DTM through the Experience Cloud, select your DTM property, then click **Upgrade to Launch**.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LAxHla2X11_-j5Ak32l%2F-LFJyF3ou47m7oJeaH9w%2F-LFJyJz_MpGT-AtrmEOs%2Fupgrade_to_launch.png?alt=media&token=5f5d841c-dcd2-4e91-a748-716bdc82d584)

## Why is my upgrade button grayed out? {#why-is-my-upgrade-button-greyed-out}

If you mouse over the button, a message informs you why it is not available. There are a few typical reasons:

* Your Property is Disabled - Enable the DTM Property first before you try to Upgrade.
* You did not sign in through the Experience Cloud - Your DTM Company [must be connected](link-dtm-to-experience-cloud.md) to the same Experience Cloud Org as your Launch Company.  Log in through the Experience Cloud and try again.
* You are not a DTM Admin - You must be have the DTM Admin right granted to you through Admin Console.  Ask an Org Admin to grant you this right or find someone who already has it to perform the Upgrade for you.

## What does the recommended upgrade process look like? {#what-does-the-recommended-upgrade-process-look-like}

1. Complete the upgrade process in DTM.
1. Go to Launch and make a new Development library with all your new changes.
1. Test thoroughly in your Launch Development environment.
1. Adjust data elements and rules as desired.
1. Promote changes through to the Launch Production environment.
1. \(Optional\) Disable the DTM property any time after completing Step 1.

## What do I do if the upgrade doesn't work? {#what-do-i-do-if-the-upgrade-doesnt-work}

The upgrade is expected to succeed in nearly every scenario. There are a few reasons why it might fail, such as:

* You don't have the Manage Properties right in Launch.  Ask your Org Admin \(or a Launch Product Admin\) to add you to a Product Profile with the Manage Properties right.
* Your property has configuration issues.  If the upgrade fails for this reason, DTM informs you that you have property configuration issues. Please check the [Preparation Guide](upgrade-preparation-guide.md) and try again.

In the rare case that your upgrade fails for any other reason, please contact Client Care and provide your DTM Company and Property Name. Client Care will work with the Launch team to help you out.

