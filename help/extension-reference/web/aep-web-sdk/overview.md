---
title: Adobe Experience Platform Web SDK Extension
seo-title: Adobe Experience Platform Web SDK Extension in Adobe Experience Platform Launch
description: Adobe Experience Platform Web SDK Extension in Adobe Experience Platform Launch
seo-description: Adobe Experience Platform Web SDK Extension Adobe Experience Platform Launch
---

# Adobe Experience Platform Web SDK Extension

The AEP Web SDK Extension sends data to the Adobe Experience Cloud from web properties, through the Adobe Experience Platform Edge Network. The Adobe Experience Platform Web SDK extension allows for streaming data into platform, syncing identities, opt-in and automatically collecting context data. 

## Configure the AEP Web SDK extension

This section provides a reference for the options available when configuring the Adobe Experience Platform Web SDK extension.

If the Adobe Experience Platform Web SDK extension is not yet installed, open your property, then click **[!UICONTROL Extensions > Catalog]**, hover over the Adobe Experience Platform Web SDK extension, and click **[!UICONTROL Install]**.

To configure the extension, open the **[!UICONTROL Extensions]** tab, hover over the extension, and then click **[!UICONTROL Configure]**.

![](/help/assets/ext-aep-config.png)

### Instance Name

The AEP Web SDK extension supports multiple instances on the page. This is used to send data to multiple organizations with a single Adobe Experience Platform Launch configuration. The **[!UICONTROL Name]** defaults to alloy. However, you can change the instance name to any valid JavaScript object name. The Adobe Experience Platform extension requires that each instance have a different **[!UICONTROL Config ID]** and a different **[!UICONTROL Organization ID]**. 

## **[!UICONTROL Config ID]**

The **[!UICONTROL Config ID]** is what tells Adobe Experience Platform where the data should be routed and what configurations should be used on the server. This is required for the Adobe Experience Platform extension to work. You can obtain a configuration ID by contacting client care. 


### **[!UICONTROL Organization ID]**

The **[!UICONTROL Organization ID]** is the organization that you would like the data sent to at Adobe. Most of the time, you should use the default value that is autopopulated. When you have multiple instances on the page,  populate this with the value of the second organization you want to send data to. 

### **[!UICONTROL Edge Domain]**

The **[!UICONTROL Edge Domain]** is the domain that the Adobe Experience Platform extension sends and receives data from. The extension requires that you use a 1st-party CNAME for production traffic. The default 3rd-party domain works for development environments but is not suitable for production environments. Instructions on how to set up a first-party CNAME are listed [here](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.html). 

### **[!UICONTROL Enable Errors]**

By default, if there is an error with the extension, it logs the error to the console. If you want to hide the errors in a production environment, you can uncheck the **[!UICONTROL Enable Errors]** checkbox. Errors still print out when debugging is turned on in Platform Launch. 

### **[!UICONTROL Enable Opt-in]**

If **[!UICONTROL Enable Opt-in]** is enabled, AEP Web SDK extension can hold hits until opt-in is received. The extension exposes an action to set the opt-in preferences. 

### **[!UICONTROL Enable Migrate ECID]**

The AEP Web SDK extension uses a new cookie to store the ECID. This setting enables compatibility between the new cookie and the old cookie for migration purposes. Adobe highly recommends this be enabled, unless you have no existing visitors with an ECID. 

### **[!UICONTROL Use 3rd Party Cookies]**

The Adobe Experience Platform will store a cookie in the first party domain always. This option allows you to use a third-party cookie set on demdex.net in addition to the cookie on the first-party domain. This can be helpful when you have users that move between multiple domains. This will disable calls to demdex.net. 

### **[!UICONTROL Context]**

The extension collects information automatically about the context of the request (for example, details about the URL and the browser). This can be disabled by deselecting specific contexts. 

- **[!UICONTROL web]** - Details about the webpage such as url, referrer, etc. 
- **[!UICONTROL device]** - Details about the device such as the screen orientation, screen height and screen width.
- **[!UICONTROL environment]** - Information about the computing environment (Browser, connection, and so on)
- **[!UICONTROL location]** - Limited information about the location of the user

## Action Types

### Send Event

Sends an event to Adobe Experience Platform so that Adobe Experience Platform can collect the data you send and act on that information. You must select an instance (if you have more than one). If the event happens at the beginning of a page load or during a view change in a single page application, select **[!UICONTROL Occurs at the start of a view]**. 

Any data that you want to send can be sent in the **[!UICONTROL XDM Data]** field. This should be a JSON object that conforms to the structure of your XDM schema. This object can either be created on your page or through a **[!UICONTROL Custom Code]** **[!UICONTROL Data Element]**.

### Set Consent

After you have received consent from your user, this must be communicated to the AEP Web SDK. You do this by using the "Set Consent" action type. Currently, two types of standards are supported: "Adobe" and "IAB TCF." If using the Adobe standard, you can currently set the consent as "In," "Out," or you can provide it by using a data element. If using the IAB TCF standard, provide the version and value that you want to use, and additional information regarding GDPR. 

In this action you are also provided with an optional field to include an Identity Map so that identities can by synced once consent is received. This can be useful when the consent is configured as "Pending" because the consent call will likely be the first call to fire. 

### Reset Event Merge ID

If you would like to reset your event merge ID on your page you can do so with this action. To reset your ID you need to select the Merge ID you want to reset and fire the action as needed.

## Data Element Types

### Event Merge ID

This data element provides an event merge ID when used. No configuration is needed for this data element. The data element that is provided stays the same until the visitor leaves the page or until the "Reset Event Merge ID" action type is used.

### Identity Map

The identity map data element allows you to create identities from other data elements or other values that you specify. All identities that you create must be tied back to a corresponding namespace. This data element provides a dropdown that shows all the default namespaces, as well as any that you have created.   

![](/help/assets/identity-map-data-element.png)

### XDM Object

Any data that you send to the Adobe Experience Platform Web SDK should be in XDM format. Formatting your data is easier with the XDM object data element. When you first open this data element, select the correct Adobe Experience Platform sandbox and schema. After you have selected your schema you will see the structure of your schema, which you can easily fill out.

![](/help/assets/XDM-object.png)

Notice that when you open certain fields of your schema, such as `web.webPageDetails.URL`, that some items are automatically collected. Even though several items are automatically collected, you have the option to overwrite any, if needed. All the values can be filled in manually or using other data elements. 

>[!NOTE]
>
>You only need to fill in the pieces of information you are interested in collecting. Anything that is not filled in will be ommited when the data is sent to the solutions. 
