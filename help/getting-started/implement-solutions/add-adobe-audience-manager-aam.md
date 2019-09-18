---
title: Add Adobe Audience Manager (AAM)
seo-title: Add Adobe Audience Manager (AAM) in Adobe Experience Platform Launch
description: enable Adobe Audience Manager in Adobe Experience Platform Launch using Server-Side Forwarding
seo-description: enable Adobe Audience Manager in Adobe Experience Platform Launch using Server-Side Forwarding
---

# Add Adobe Audience Manager (AAM)

This tutorial guides you through the steps to enable [!DNL Adobe Audience Manager] using Server-Side Forwarding.

[Adobe Audience Manager](https://marketing.adobe.com/resources/help/en_US/aam/) ([!DNL AAM]) provides industry-leading services for online audience data management, giving digital advertisers and publishers the tools they need to control and leverage their data assets to help drive sales success.

## Objectives

At the end of this lesson, you will be able to:

* Describe the two main ways to implement [!DNL Audience Manager] on a website
* Add [!DNL Audience Manager] using Server-Side Forwarding of the [!DNL Analytics] beacon
* Validate the [!DNL Audience Manager] implementation

## Prerequisites

To complete this lesson, you need the following:

* Complete the lessons in Configure [!DNL Launch], Add [!DNL Adobe Analytics], and Add the ID Service.
* Admin access to [!DNL Adobe Analytics] so you can enable Server-Side Forwarding for the report suite you are using for this tutorial.

  Alternatively, you can ask an existing admin at your organization to do this for you, following the instructions below.

* Your “[!DNL Audience Manager] Subdomain” (also known as the “Partner Name” “Partner ID,” or “Partner Subdomain”).

  If you already have [!DNL Audience Manager] implemented on your website, the easiest way to obtain this is to go to your actual website and open the [!DNL Debugger]. The subdomain is available on the [!UICONTROL Summary] tab, in the [!DNL Audience Manager] section:

![](/help/assets/aam-debugger-partner.png)

## Implementation options

There are two ways to implement [!DNL Audience Manager] in a website:

* **Server-Side Forwarding (SSF):** For customers with [!DNL Adobe Analytics], this is the easiest and recommended way to implement. [!DNL Adobe Analytics] forwards data to [!DNL AAM] on [!DNL Adobe's] backend, allowing for one less request on the page. This also enables key integration features and conforms with the best practices for [!DNL Audience Manager] code implementation and deployment.
* **Client-Side DIL:** This approach is for customers who do not have [!DNL Adobe Analytics]. DIL code (Data Integration Library Code, the [!DNL AAM] JavaScript configuration code) sends data directly from the web page into [!DNL Audience Manager].

Because you have already deployed [!DNL Adobe Analytics] in these tutorials, you can deploy [!DNL Audience Manager] using Server-Side Forwarding. For a complete description and requirements list for Server-Side Forwarding, review the [documentation](https://marketing.adobe.com/resources/help/en_US/reference/ssf.html) so you can be familiar with how it works, what is required, and how to validate.

## Enable Server-Side Forwarding

There are two main steps when implementing Server-Side Forwarding:

1. Turn on a "switch" in the [!DNL Analytics] [!UICONTROL Admin Console] to forward data from [!DNL Analytics] to [!DNL Audience Manager] per the report suite.
1. Put the code in place via [!DNL Launch].

   For this to work correctly, you need to install the [!DNL Experience Cloud ID Service] extension, as well as the [!DNL Analytics] extension. You will actually not need the [!DNL AAM] extension, which is explained below.

### Enable Server-Side Forwarding in the Analytics Admin Console

A configuration in the [!DNL Adobe Analytics] [!UICONTROL Admin Console] is required to start forwarding data from [!DNL Adobe Analytics] to [!DNL Adobe Audience Manager]. Because it can take up to four hours to start forwarding the data, you should do this step first.

1. Log in to [!DNL Analytics] via the [!DNL Experience Cloud] UI.

   If you don't have Admin access to [!DNL Analytics], ask your [!DNL Experience Cloud] or [!DNL Analytics] admin to assign you access or to complete these steps for you.

   ![](/help/assets/aam-logintoanalytics.png)

1. From the top navigation in [!DNL Analytics], choose **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]**, and from the list, select the report suites that you want to forward to [!DNL Audience Manager].

   ![](/help/assets/aam-analyticsadminconsolereportsuites.png)

1. From the [!UICONTROL Report Suites] screen and with the report suites selected, choose **[!UICONTROL Edit Settings]** > **[!UICONTROL General > Server-Side Forwarding]**.

   ![](/help/assets/aam-selectssfmenu.png)

   >[!NOTE]  As stated above, you will need to have administrator privileges to see this menu item.

1. Once you are on the [!UICONTROL Server-Side Forwarding] page, read the info and check the box to **[!UICONTROL Enable Server-Side Forwarding]** for the report suite(s).
1. Click **[!UICONTROL Save]**.

>[!NOTE]  Because SSF needs to be enabled per report suite, make sure you repeat this step for your real report suites when you deploy SSF on your own site's report suite. If the SSF option is grayed out, you need to map the report suites to your [!DNL Experience Cloud] Org to enable the option. This is explained in [the documentation](https://marketing.adobe.com/resources/help/en_US/mcloud/map-report-suite.html).

Once this step has been completed, and if you have the [!DNL Experience Cloud ID Service] enabled, data is forwarded from [!DNL Analytics] to [!DNL AAM]. However, to complete the process so the response comes back correctly from [!DNL AAM] to the page (and to [!DNL Analytics] via the Audience Analytics feature), you must complete the following step in [!DNL Launch] as well.

### Enable Server-Side Forwarding in Launch

1. Go to **[!UICONTROL Extensions]** > **[!UICONTROL Installed]** and click to configure the [!DNL Analytics] extension.

   ![](/help/assets/aam-configanalyticsextension.png)

1. Expand the [!UICONTROL Adobe Audience Manager] section, then check the box to **[!UICONTROL Automatically share Analytics Data with Audience Manager]**.

   This adds the [!DNL Audience Manager] module (code) to the [!DNL Analytics] AppMeasurement.js implementation.

1. Add your [!DNL Audience Manager] Subdomain, also known as the Partner Name, Partner ID, or Partner Subdomain.
1. Click **[!UICONTROL Save to Library and Build]**.

### Validate the Server-Side Forwarding

The main way to validate that the Server-Side Forwarding is up and running is to look at the response to any of your [!DNL Adobe Analytics] hits. First, though, check a couple other things that can help make sure that it is working the way you want it to.

#### Verify that the code loads correctly

The code that [!DNL Adobe Experience Platform Launch] installs to handle the forwarding, and especially the response from [!DNL AAM] to the page, is called the [!DNL Audience Manager] Module. Use the [!DNL Experience Cloud Debugger] to ensure that it has loaded.

1. Open the We.Retail site.
1. Click the [!UICONTROL debugger] icon in your browser to open the [!DNL Experience Cloud Debugger].
1. On the [!UICONTROL Summary] tab, scroll down to the [!DNL Analytics] section.
1. Verify that "AudienceManagement" is listed under the [!UICONTROL Modules] section.

   ![](/help/assets/aam-verifyaammodule.png)

#### Verify the Partner ID in the Debugger

Next, verify that the [!DNL Debugger] is picking up the right partner ID from the code.

1. In the [!DNL Debugger], on the [!UICONTROL Summary] tab, scroll down to the [!DNL Audience Manager] section.
1. Verify your Partner ID/Subdomain under Partner.

   ![](/help/assets/aam-verifypartnerid.png)

>[!NOTE]  The [!DNL Audience Manager] section of the [!DNL Debugger] refers to "DIL", which is the Data Integration Library that typically refers to a client-side implementation, as opposed to the server-side approach used here. The [!DNL AAM] Module used in this SSF approach uses much of the same code as the client-side DIL library, so the [!DNL Debugger] repors it as such. If you have followed the steps in this tutorial, and the rest of the items in this validation section are correct, be assured that server-side forwarding is working.

#### Verify the Analytics request and response

If you are not doing server-side forwarding of data from [!DNL Analytics] to [!DNL Audience Manager], then there is no response to the [!DNL Analytics] beacon (besides a 2x2 pixel). However, if you are doing SSF, then there are items that you can verify in the [!DNL Analytics] request and response that let you know that it is working correctly. Unfortunately, at this time, the [!DNL Experience Cloud Debugger] does not support showing the response to the beacons. Therefore, you should use another debugger/packet sniffer, like [!DNL Charles Proxy] or the browser's Developer Tools.

1. Open the Developer Tools in your browser and go to the [!UICONTROL Network] tab.
1. In the [!UICONTROL Filter] field, type b/ss, which limits what you see to the [!DNL Adobe Analytics] requests.
1. Refresh the page to see the [!DNL Analytics] request.

   ![](/help/assets/aam-openthejsconsole1.png)

1. In the [!DNL Analytics] beacon (request), look for a "callback" parameter. This parameter is set to something like this: `s_c_il[1].doPostbacks.`

   ![](/help/assets/aam-callbackparam.png)

This is a response to the [!DNL Analytics] beacon. It contains references to `doPostbacks`, as called in the request. Most importantly, it should see a `stuff` object. This is where [!DNL AAM] segment IDs are sent back to the browser. If you have the `stuff` object, SSF is working.

![](/help/assets/aam-stuffobjectinresponse.png)

>[!IMPORTANT]  Beware the false "Success." If there is a response, and everything seems to be working, make sure you have that `stuff` object. If you don't, you might see a message in the response that says "status":"SUCCESS".

![](/help/assets/aam-responsefalsesuccess.png)

Despite its appearance, this is actually proof that it is **not** working correctly. If you see this, it means that you have completed this second step (the code in [!DNL Launch]), but that the forwarding in the [!DNL Analytics] [!UICONTROL Admin Console] (first step of this section) has not yet completed. In this case, verify that you have enabled SSF in the [!DNL Analytics] [!UICONTROL Admin Console]. If you have, and it hasn't been four hours yet, be patient.
