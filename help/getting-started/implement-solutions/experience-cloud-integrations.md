---
title: Experience Cloud integrations
seo-title: Experience Cloud integrations in Adobe Experience Platform Launch
description:  review the key integrations between Adobe Experience Platform Launch and the solutions you have implemented
seo-description: Review the key integrations between Adobe Experience Platform Launch and the solutions you have implemented
---

# Experience Cloud integrations

This tutorial reviews the key integrations between the solutions you have implemented. If you have completed the earlier tutorials, you have already implemented the code-aspects of the integrations. You don't need to do any additional work in this tutorial besides reading and validating.

## Objectives

At the end of this lesson, you will be able to:

* Explain the use cases for Audience Sharing, [!DNL Analytics for Target (A4T)], and Customer Attributes integrations
* Validate the basic client-side implementation aspects of these integrations

## Prerequisites

You should complete all of the previous [!DNL Launch] implementation tutorials before following the instructions in this tutorial.

>[!NOTE]  There are many user-permissions requirements, account configurations, and provisioning steps that are required to fully use these integrations and which are beyond the scope of this tutorial. If you are not already using these integrations in your current implementation of the [!DNL Experience Cloud], you should consider the following:

* Review the full requirements of the [Core Services integrations](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html)
* Review the full requirements of the [Analytics for Target integration](https://marketing.adobe.com/resources/help/en_US/target/a4t/c_before_implement.html)
* Have an Administrator of your [!DNL Experience Cloud] Organization [request provisioning of these integrations](https://www.adobe.com/go/audiences)

## Audiences

[Audiences](https://marketing.adobe.com/resources/help/en_US/mcloud/audience_library.html) are part of the People core service. They allow you to share audiences between solutions. For example, you can create an audience in [!DNL Audience Manager] and use it to deliver personalized content with [!DNL Target].

The main requirements to implement A4T, which you have already done, are to:

* Implement the [!DNL Experience Cloud Id Service]
* Implement [!DNL Audience Manager]
* Implement other solutions that you would like to receive or create audiences, such as [!DNL Target] and [!DNL Analytics]

### Validate the audiences integration

The best way to validate the audiences integration is to build an audience, share it to another solution, and then use it in the other solution. For example, confirm that a visitor who qualifies for an [!DNL AAM] segment can qualify for a [!DNL Target] activity targeted to that segment. However, this is beyond the scope of this tutorial.

These validation steps focus on the critical part visible in the client-side implementation: the Visitor ID.

1. Open the [We.Retail site](https://aem.enablementadobe.com/content/we-retail/us/en.html).
1. Make sure the [!DNL Debugger] is mapping the [!DNL Launch] property to your Development environment, as described in the earlier lesson.

   ![](/help/assets/switchenvironments-debuggeronweretail21.png)

1. Go to the Network tab of the [!DNL Debugger], then click **[!UICONTROL Clear All Requests]** to clean things up.
1. Reload the We.Retail page, making sure that you see both the [!DNL Target] and [!DNL Analytics] requests in the [!DNL Debugger].
1. Reload the We.Retail page again. You should now see four requests in the Network tab of the [!DNL Debugger]—two for [!DNL Target] and two for [!DNL Analytics].
1. Look in the row labeled "[!DNL Experience Cloud Visitor ID]." The IDs in every request by every solution should always be the same.

   ![](/help/assets/integrations-matchingecids.png)

   The IDs are unique per visitor, which you can confirm by asking a co-worker to repeat these steps.

## Analytics for Target (A4T)

The [Analytics for Target (A4T)](https://marketing.adobe.com/resources/help/en_US/target/a4t/a4t.html) integration allows you to leverage your [!DNL Analytics] data as the source for reporting metrics in [!DNL Target].

The main requirements to implement [!DNL A4T], which you have already done, are to:

* Implement the [!DNL Experience Cloud ID Service]
* Fire the global mbox before the [!DNL Analytics] page view beacon

[!DNL A4T] works by stitching together a server-side request from [!DNL Target] to [!DNL Analytics] with the [!DNL Analytics] page view beacon, referred to as "hit-stitching." Hit-stitching requires that the [!DNL Target] request that delivers the activity (or increments a [!DNL Target]-based goal metric) have a parameter that matches a parameter in the [!DNL Analytics] page view beacon. This parameter is called the supplemental data ID (SDID).

### Validate the A4T Implementation

The best way to validate the [!DNL A4T] integration is to build a [!DNL Target] activity using [!DNL A4T] and validate the reporting data. This is beyond the scope of this tutorial. This tutorial shows how to confirm that the supplemental data IDs match between the solution calls.

1. Open the [We.Retail site](https://aem.enablementadobe.com/content/we-retail/us/en.html).
1. Make sure the [!DNL Debugger] is mapping the [!DNL Launch] property to your Development environment, as described in the earlier lesson.

   ![](/help/assets/switchenvironments-debuggeronweretail21.png)

1. Go to the [!UICONTROL Network] tab of the [!DNL Debugger].
1. Click **[!UICONTROL Clear All Requests]** to clean things up.
1. Reload the We.Retail page, making sure that you see both the [!DNL Target] and [!DNL Analytics] requests in the [!DNL Debugger].
1. Reload the We.Retail page again. You should see four requests in the [!UICONTROL Network] tab of the [!DNL Debugger], two for Target and two for Analytics.
1. Look in the row labeled "Supplemental Data ID."

   The IDs from the first page load should match between [!DNL Target] and [!DNL Analytics]. The IDs from the second page load should also match, but be different from the first page load.

   ![](/help/assets/integrations-matchingsdids.png)

If you make additional [!DNL Target] requests in the scope of a page load (not including single-page apps) that are part of [!DNL A4T] activities, give them unique names (not target-global-mbox) so that they continue to have the same SDIDs of the initial [!DNL Target] and [!DNL Analytics] requests.

## Customer attributes

[Customer Attributes](https://marketing.adobe.com/resources/help/en_US/mcloud/attributes.html) are a part of the People core service that allows you to upload data from your customer relationship management (CRM) database and leverage it in [!DNL Adobe Analytics] and [!DNL Adobe Target].

The main requirements to implement Customer Attributes, which you have already done, are to:

* Implement the [!DNL Experience Cloud ID Service]
* Set Customer IDs via the [!DNL Id Service] before [!DNL Target] and [!DNL Analytics] fire their requests, which you accomplished using the rule ordering feature in [!DNL Launch]

### Validate the Customer Attributes implementation

You validated that the Customer IDs are passed to both the [!DNL ID Service] and to [!DNL Target] in earlier tutorials. You can also validate the Customer ID in the [!DNL Analytics] hit as well. At this time, the Customer ID is one of the few parameters that does not show up in the [!DNL Experience Cloud Debugger], but you can use the browser's JavaScript Console to view it.

1. Open the We.Retail site.
1. Open your browser's developer tools.
1. Go to the [!UICONTROL Network] tab.
1. In the filter field, type b/ss, which limits what you see to the [!DNL Adobe Analytics] requests.

   ![](/help/assets/aam-openthejsconsole.png)

1. Click the **[!UICONTROL LOGIN]** link in the top right corner of the site, enter `test@adobe.com` as the username, and enter `test` as the password, then click **[!UICONTROL Login]**.

   You are returned to the home page, which triggers a beacon that you can see in the developer tools.

1. Click on the request and select the [!UICONTROL Headers] tab.
1. Scroll down until you see some nested parameters:
   * `cid`: The standard delimiter for the Customer ID portion of the request
   * `crm_id`: The custom integration code, which you specified in the [!DNL ID Service] lesson
   * `id`: The Customer ID value coming from your Email (Hashed) data element
   * `as`: The Authentication State, with "1" meaning logged in

![](/help/assets/integrations-analyticscustomeridvalidation.png)
