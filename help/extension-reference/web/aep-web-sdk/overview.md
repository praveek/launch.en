---
title: Adobe Experience Platform Web Extension
seo-title: Adobe Experience Platform Web Extension in Adobe Experience Platform Launch
description: Adobe Experience Platform Web Extension in Adobe Experience Platform Launch
seo-description: Adobe Experience Platform Web Extensionin Adobe Experience Platform Launch
---

# Adobe Experience Platform Extension

The Adobe Experience Platform Extension sends data to the Adobe Experience Platform from web properties. The AEP extension allows for streaming data into platform, syncing identities, opt-in and automatically collected context data. 

## Configure the AEP extension

This section provides a reference for the options available when configuring the AEP extension.

If the AEP Web SDK extension is not yet installed, open your property, then click **[!UICONTROL Extensions > Catalog]**, hover over the AEP Web SDK extension, and click **[!UICONTROL Install]**.

To configure the extension, open the Extensions tab, hover over the extension, and then click **[!UICONTROL Configure]**.

![](/help/assets/ext-aep-config.png)

### Instance Name

The AEP extension support multiple instances on the page. This is used to send data to multiple organizations with a single launch configuration. The **[!UICONTROL Name]** will default to Alloy however you may change the instance name to any valid javascript object name. The AEP extension requires that you each instance have a different **[!UICONTROL Config ID]** and a different **[!UICONTROL Organization ID]**. 

## **[!UICONTROL Config ID]**

The **[!UICONTROL Config ID]** is what tells AEP where the data should be routed and what configurations should be used on the server. This is required for the AEP extension to work. You can obtain a configuration ID by contacting client care. 


### **[!UICONTROL Organization ID]**

The **[!UICONTROL Organization ID]** is the Organization that you would like the data sent to at Adobe. Most of the time you will want to use the defualt that is autopopulated. When you have multiple instances on the page you will want to populate this with the value of the second organization you want to send data to. 

### **[!UICONTROL Edge Domain]**

The **[!UICONTROL Edge Domain]** is the domain that the AEP will send and receive data from. The AEP extension requires that you use a 1st party CNAME for production traffic (the default 3rd party domain will work for development environments). Instructions on how to setup a first party CNAME are listed [here](https://docs.adobe.com/content/help/en/core-services/interface/ec-cookies/cookies-first-party.html). 

### **[!UICONTROL Enable Errors]**

By default if there is an error with the AEP extension it will log the error will be logged to the console. If you would like to hide the errors in a production environment you can uncheck the **[!UICONTROL Enable Errors]** checkbox. Errors will still be printed out when debugging is turned on in Launch. 

### **[!UICONTROL Enable Opt-in]**

If **[!UICONTROL Enable Opt-in]** is enabled AEP extension can hold hits until opt-in is recieved. The extension exposes an action to set the opt-in preferences. 

### **[!UICONTROL Enable Migrate ECID]**

The AEP extension uses a new cookie to store the ECID cookie. This setting enables compatibility between the new cookie and the old cookie for migration purposes. We highly recommend this be enabled, unless you have no existing visitors in ECID. 

### **[!UICONTROL Context]**

The AEP Extension collects information automatically about the context of the reqeust (e.g. details about the URL and the browser). This can be disbaled by selecting specific purposes. 

- **[!UICONTROL web]** - Details about the webpage such as url, referrer, etc. 
- **[!UICONTROL device]** - Details about the device such as the screen orientation, screen height and screen width.
- **[!UICONTROL environment]** - Information about the computing environment (e.g. Browser, connection, etc)
- **[!UICONTROL loacation]** - Limited information about the location of the user

## AEP Extension Action Types

### Send Event

Sends an event to AEP so that AEP can collect the data you send and act on that information. You must select an instance (if you have more than one). If the event happens at the beginning of a page load or during a view change in a single page application select the **[!UICONTROL Occurs at teh start of a view]**. 

Any data that you want to send can be sent in the **[!UICONTROL XDM Data]** field. This should be a JSON object that conforms to the structure of your XDM schema. This object can either be created on your page or through a **[!UICONTROL Custom Code]** **[!UICONTROL Data Element]**.

### Set Opt-in Preferences

There are currently two option for opt-in. **[!UICONTROL All purpose]** which will send data to AEP and **[!UICONTROL No purposes]**, in which no data will be sent. These can either be set on the event or pull from a **[!UICONTROL Data Element]**. 


