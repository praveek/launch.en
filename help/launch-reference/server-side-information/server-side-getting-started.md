---
title: Getting started with Experience Platform Launch Server Side
seo-title: Getting started with Experience Platform Launch Server Side
description: Getting started with Experience Platform Launch Server Side
seo-description: Getting started with Experience Platform Launch Server Side
---

# Getting started with Experience Platform Launch Server Side (Beta)

>[!NOTE]
>
>This beta documentation desribed features that are not yet publicly available. It is subject to change and might not be complete or correct.

Data can be sent to Edge Network using one of three options:

* AEP Web SDK
* AEP Mobile SDK
* Server-to-Server API (coming soon)

>[!NOTE]
>
>The AEP Web SDK and AEP Mobile SDK do not require deployment through Experience Platform Launch Client Side. However, using Launch Client Side to deploy these SDKs is the recommended approach.

After you send data to the Edge network, you can toggle on Adobe solutions to send data there. To send data to a non-Adobe solution, you need to set that up in Launch Server Side.

## Prerequisites

* Adobe Experience Platform Launch Server Side
* AEP Web SDK extension in Experience Platform Launch, configured to send data to Edge network
* XDM

## Create a schema

In Adobe Experience Platform, create your schema.

1. Create a new schema by clicking “Create Schema” and selecting the `XDM ExperienceEvent` option.

1. Give the schema a name and short description.

1. You can add the “ExperienceEvent web details” mixin by clicking **[!UICONTROL Add]** next to **[!UICONTROL Mixins]**. 

    >[!NOTE]
    >
    >Multiple mixins can be added, if desired.

1. Save the schema and note the name you gave it.

For more information about schemas, see [Experience Data Model (XDM) System Help](https://docs.adobe.com/content/help/en/experience-platform/xdm/home.html).

## Create Launch Server Side property

In Experience Platform Launch, create a property of type "Edge."

1. Click **[!UICONTROL New property]**. 

1. Name the property. 

1. Choose the “Edge” platform type.

1. Click **[!UICONTROL Save]**.

After you create the property, go to the **[!UICONTROL Environments]** tab for the new property and make note of the Environment IDs. You can copy the Environment ID from the Environments tab to paste it when creating an Edge configuration.

## Create Edge Configuration

In AEP Edge Configuration, create your edge configuration. You will need the Environment ID generated when you created the server-side property.

1. Open the AEP Edge Configuration interface through Experience Platform Launch, from the link in the left rail.

1. Click **[!UICONTROL New Edge Configuration]**.

1. Name the configuration and provide an optional description. 
    The description helps to identify configurations ina  list of several configurations. 

1. Click **[!UICONTROL Save]**.



## Enable Launch Server Side.

Next, configure the ability to send data to Adobe Experience Platform and to Adobe Experience Cloud applications.

1. In the Edge Configuration UI, select the property you created.

1. Select the Development, Production, or Staging environment.

    Or, to send data to a Launch Server Side environment outside the Adobe org, click **[!UICONTROL Switch to Advanced Mode] and paste in an ID. The ID is provided when you create a Server Side property.

1. Toggle on the necessary tools and configure as required.

    * Adobe Analytics requires a report suite ID.

    * Server Side Launch requires an environment ID, which is the publish path from the Server Side Launch property.

After configuring, make note of the Environment IDs for the new property.

## Configure the Launch Client Side AEP Web SDK extension to send data to the Edge configuration that you created

In Client Side Launch, create your property, then use the AEP Web SDK extension to configure it.

1. Name the property.

    You can have multiple instances of Alloy. For example, you might have different pre- and post-paywall tracking properties.

1. Select the Org ID.

1. Select the Edge Domain.

See the [Web SDK extension documentation](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/aep-extension/overview.html) for more configuration options.

## Create a Launch Client Side rule to send data to AEP Web SDK

After all of the above is in place, you can build necessary data definitions, rules, and so on that leverage both server side and client side Launch, but that need only a single request from the page.

Create a new page load rule using the AEP Web SDK extension and the “Send Event” action type:

1. Open the **[!UICONTROL Rules]** tab, then click **[!UICONTROL Create New Rule]**.

1. Name the rule.

1. Click the **[!UICONTROL Events Add]** icon.

1. Choose your extension and one of the event types available for that extension, then configure the settings for the event. For example, select **[UICONTROL Core - Window Loaded]**.

1. In the action configuration on the right side of the screen, populate the **[UICONTROL XDM Data]** field using the XDM data element created in an earlier step.

1. The rest of the settings can be left as default for this example, so click **[UICONTROL Save]**.

For another example, you might create a rule that sends the data layer to Edge if the user hovers over a specified button.

## Summary

You should have the following in place:

* Adobe Experience Platform schema (Note the name you gave it.)
* Server Side Launch property (Keep track of the environment IDs.)
* AEP Edge Configuration (Note the environment ID.)
* Client Side Launch property


<!--
Additional info from PPT. Do we need any of this?

I’ll assume you’ve added this to a test page and won’t include any instructions on that here. If you haven’t, now’s the time...

Add and configure the AEP Web SDK extension:

If we’ve done everything right, the Edge Configuration we set up earlier should be available to pick from the drop down. If not, the values can be manually entered.

In Client Side Launch: XDM Data Element

Create a new Data Element using the AEP Web SDK extension and choosing “XDM Object” as the Data Element Type.
In the right half of the editor, choose the schema you created in in step one of this process. You should recognize the schema by its structure.
Take some time and click through the schema. This is where you’ll populate the parameters/keys that you send in the xdm event payload.



At present, the Server Side Launch beta has limited extension options, but enough to test out. Add the following extensions:

Adobe Cloud Connector
Google Analytics Measurement Protocol

Note: Do NOT use the “Send Beacon” extension. It is deprecated, doesn’t work, and is being removed.

Create a new rule:
There’s only one type of rule
Don’t add conditions, we want it to always fire
Add two (2) actions, each using the extensions added on the previous slide:
Adobe Cloud Connector / Send Beacon
Create a temp POST endpoint using https://webhook.site
Google Analytics Measurement Protocol / Send Data
Send data to a GA test environment

In Server Side Launch: Data Elements

To build a data element:
Note the location of the XDM key, beginning at the “events” level of the payload.
Create a new data element using the Core extension and the “Path” data element type.
Set the “Path” value to the payload path noted in #1 above.
Notes/Gotchas
Make sure to use “event” (singular) instead of “events” as shown in the example at right
Note: A _satellite.getVar() alternative is being developed for Server Side Launch: getDataElementValue()
Do not include the array index in the path
Do not include dots/periods or spaces in your data element name, doing so will cause errors when referencing the data element, and may well break the whole setup

As with Client Side Launch, Server Side Launch lets you manipulate data elements using custom javascript. When doing so, XDM paths can be referenced directly by adding “payload.” to the front of the reference as shown below:

``` javascript
var height = payload.event.xdm.device.screenHeight,
   width = payload.event.xdm.device.screenWidth;

var pixelCount = height * width;
return pixelCount;
```

## Testing

Install the Adobe Experience Platform Debugger and make use of the Edge Trace functionality found on the “Launch” tab:
-->
