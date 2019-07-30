---
title: Switch Environments with the Experience Cloud Debugger
seo-title: Switch Environments with the Experience Cloud Debugger in Adobe Experience Platform Launch
description: Switch Environments with the Experience Cloud Debugger in Adobe Experience Platform Launch
seo-description: Switch Environments with the Experience Cloud Debugger in Adobe Experience Platform Launch
---

# Switch environments with the Experience Cloud Debugger

This tutorial shows how to use the [Adobe Experience Cloud Debugger extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) to replace the [!DNL Launch] property hardcoded on the [We.Retail demo site](https://aem.enablementadobe.com/content/we-retail/us/en.html) with your own property.

This technique is called environment switching. It will be helpful later, when you work with [!DNL Launch] on your own website. You can load your production website in your browser, but with your development [!DNL Launch] environment. This enables you to confidently make and validate [!DNL Launch] changes independently from your regular code releases. This separation of marketing tag releases from your regular code releases is one of the more common reasons why people use [!DNL Launch].

## Objectives

At the end of this lesson, you will be able to:

* Use the [!DNL Debugger] to load an alternate [!DNL Launch] environment
* Use the [!DNL Debugger] to validate that you have loaded an alternate [!DNL Launch] environment

## Get the URL of your Development environment

1. In your [!DNL Launch] property, open the [!UICONTROL Environments] page.
1. In the **[!UICONTROL Development]** row, click the **[!UICONTROL Install]** icon to open the modal.
1. Click **[!UICONTROL Copy]** to copy the embed code to your clipboard.
1. Click **[!UICONTROL Close]** to close the modal.

![](/help/assets/launch-copyinstallcode1.png)

## Replace the Launch URL on the We.Retail demo site

Open the [We.Retail demo site](https://aem100-us.adobevlab.com/content/we-retail/us/en.html) in your [!DNL Chrome] browser, then open the [Experience Cloud Debugger extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) by clicking the ![](/help/assets/icon-debugger.png) icon.

![](/help/assets/switchenvironments-opendebugger1.png)

Note that the currently implemented [!DNL Launch] property is shown on the [!UICONTROL Summary] tab.

![](/help/assets/switchenvironments-debuggeronweretail2.png)

Open the [!UICONTROL Tools] tab, then click **[!UICONTROL Adobe Launch]** > **[!UICONTROL Dynamically Insert Launch > Embed Code]** to open the text input field:

<!-- Scott - Check UI. Adobe Launch or Adobe Experience Platform Launch? -->

![](/help/assets/switchenvironments-debugger-editembedcode.png)

Make sure the [!DNL Chrome] tab with the We.Retail site is in focus behind the [!DNL Debugger] (not the tab with this tutorial or the tab with the [!DNL Launch] interface), then paste the embed code from your clipboard. Click the disk icon to save.

![](/help/assets/switchenvironments-debugger-save.png)

Reload the site and check the [!UICONTROL Summary] tab of the [!DNL Debugger]. Under the [!DNL Launch] section, you should see that your Development Property is being used. Confirm that the name of the property matches yours and that the environment says "development."

![](/help/assets/switchenvironments-debuggeronweretail.png)

>[!NOTE]  The [!DNL Debugger] saves this configuration and replaces the [!DNL Launch] embed codes whenever you come back to the We.Retail site. It does not impact other sites you visit in other open tabs. To stop the [!DNL Debugger] from replacing the embed code, click the X next to the embed code in the [!UICONTROL Tools] tab of the [!DNL Debugger].

Use this technique of mapping the We.Retail site to your own [!DNL Launch] property to validate your [!DNL Launch] implementation. When you start using [!DNL Launch] on your production website, you can use this same technique to validate changes you make to your Development and Staging environments before you publish them to Production.
