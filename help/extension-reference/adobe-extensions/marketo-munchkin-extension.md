---
title: Marketo Munchkin Extension
seo-title: Marketo Munchkin Extension for Adobe Experience Platform Launch
description: Information about configuring the Marketo Munchkin Extension, and the options available when using this extension to build a rule
seo-description: Marketo Munchkin Extension for Adobe Experience Platform Launch
---

# Marketo Munchkin Extension

Use this extension to integrate [!DNL Marketo Munchkin] JavaScript tracking code with your property. [!DNL Marketo Munchkin] JavaScript allows for tracking of end-user page visits and clicks to your Marketo landing pages and external web pages.

## Install Marketo Munchkin Extension

If [!DNL Marketo Munchkin] extension is not yet installed, open your property, then click **[!UICONTROL Extensions > Catalog]**, hover over the [!DNL Marketo Munchkin] extension, and click **[!UICONTROL Install]**.

This extension has no configuration necessary.

## Marketo Munchkin Extension action types

This section describes the action types available in [!DNL Marketo Munchkin] extension.

### Initialize

![](/help/assets/munchkin-Init.png)

#### Munchkin ID: (required) Munchkin Account ID found under Admin > Integration > Munchkin menu.
#### Configurations: All configurable parameters are documented at https://developers.marketo.com/javascript-api/lead-tracking/configuration/

### Visit Web page

![](/help/assets/munchkin-Init.png)

#### url: (required) The URL file path used to record a page visit.
#### params: A querystring of the desired parameters to be recorded.
#### name: The custom name of the web page asset.

### Click Clink

![](/help/assets/munchkin-Init.png)

#### href: (required) The URL file path used to record a link click.


### Associate Lead

#### attributes: Comma-separated key:value pairs to associate lead with.

