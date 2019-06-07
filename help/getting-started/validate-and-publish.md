---
title: Publish your Launch property
seo-title: Publish your Launch property in Adobe Launch
description: Publish your Launch property in Adobe Launch
seo-description: Publish your Launch property in Adobe Launch
---

# Publish your Launch property

After you have implemented some key solutions of the Adobe Experience Cloud in your Development environment, it's time to learn the publishing workflow.

## Objectives

At the end of this tutorial, you will be able to:

* Publish a Development library to the Staging environment
* Map a Staging library to your production website using the Debugger
* Publish a Staging library to the Production environment

## Publish to Staging

After you have created and validated your library in the Development environment, it is time to publish it to Staging.

1. Go to the **[!UICONTROL Publishing]** page.
1. Open the drop down next to your library and select **[!UICONTROL Submit for Approval]**.

   ![](/help/assets/publishing-submitforapproval.png)

1. Click **[!UICONTROL Submit]**.

   Your library appears in the Submitted column in an unbuilt state.

1. Open the drop down and select **[!UICONTROL Build for Staging]**.

   ![](/help/assets/publishing-buildforstaging.png)

Once the green-dot icon appears, the library can be previewed in the Staging environment.

In a real-life scenario, the next step in the process would typically be to have your QA team validate the changes in the Staging library. They can do this using the Debugger.

### Validate the changes in the Staging library

1. In your Launch property, open the Environments page.
1. In the Staging row, click the **[!UICONTROL Install]** icon.

   ![](/help/assets/publishing-getstagingcode.png)

1. Click the **[!UICONTROL Copy]** icon to copy the embed code to your clipboard, then click **[!UICONTROL Close]**.

   ![](/help/assets/publishing-copystagingcode.png)

1. Open the [We.Retail demo site](https://aem.enablementadobe.com/content/we-retail/us/en.html) in your Chrome browser.
1. Open the [Experience Cloud Debugger extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj).

   ![](/help/assets/switchenvironments-opendebugger.png)

1. Open the Tools tab and click **[!UICONTROL Adobe Launch]** > **[!UICONTROL Dynamically Insert Launch > Embed Code]** to open the text input field (it might currently have the URL of your Development embed code):

   ![](/help/assets/switchenvironments-debugger-editembedcode1.png)

1. Paste the Staging embed code that is in your clipboard, then click the disk icon to save.

   ![](/help/assets/switchenvironments-debugger-save1.png)

1. Reload and check the Summary tab of the Debugger. Under the Launch section, you should see that your Staging Property is implemented, showing your property name (for example, "Launch Tutorial" or whatever you named your property).

   ![](/help/assets/publishing-debugger-staging.png)

In real life, once your QA team has signed off by reviewing the changes in the Staging environment, it is time to publish to production.

## Publish to Production

1. Go to the Publishing page, then from the dropdown, click **[!UICONTROL Approve for Publishing]**:

   ![](/help/assets/publishing-approveforpublishing.png)

1. Click **[!UICONTROL Approve]**. The library appears in the Approved column in the unbuilt state (yellow dot).
1. Open the drop down and select **[!UICONTROL Build and Publish to Production]**:

   ![](/help/assets/publishing-buildandpublishtoproduction.png)

1. Click **[!UICONTROL Publish]**. The library appears in the Published column:

   ![](/help/assets/publishing-published.png)

You've completed the tutorial and published your first property in Launch.
