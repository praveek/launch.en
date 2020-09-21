---
title: Experience Platform Launch Server Side Overview
seo-title: Experience Platform Launch Server Side overview
description: Experience Platform Launch Server Side overview
seo-description: Experience Platform Launch Server Side overview
---

# Experience Platform Launch Server Side overview

Adobe Experience Platform Launch Server Side decreases web page and app weight by using Adobe Experience Platform Edge Network to execute tasks normally done on the client. Launch Server Side rules can transform and send data to new destinations without changing client-side implementations.

Experience Platform Launch Server Side makes it possible to:

* Make a single call from the page that contains a payload of data and then federate this data server-side to reduce client-side network traffic and deliver a faster experience for customers, and boost conversion rates.

* Decrease the amount of time it takes for webpages to load so your site conforms to industry best practices around performance.

* Increase transparency and control over which types of data are sent where, across all client-side properties.

* Protect marketing data and campaigns through first-party tracking so data can still be delivered when browsers block cookies.

* Create a server-side rule to send previously collected data to a new destination.

## Improved performance

In an increasingly competitive environment, businesses must prioritize performance to maintain market share.Experience Platform Launch Server Side improves Website and app performance across mobile, IoT, and OTT devices. Website conversion rates increase due to faster load times, mobile apps don't drain batteries as quickly, and OTT apps feel as responsive as those same apps running on mobile devices. As performance increases, so do conversion rates. 

## Better data governance

As the technology stack grows and data is sent to more and more destinations, the challenge to control what data is sent where becomes more difficult. The normalization of regulations like GDPR and CCPA force companies to exert more control over a data problem that’s increasingly becoming harder.

Experience Platform Launch Server Side helps marketing teams grow their business while controlling data. It decreases the number of technologies that marketers need to use to reach their target market. This makes it easier for implementation teams to deploy this technology.   

## Reduced need for cookies and local storage

As more and more consumers block third-party cookies, businesses struggle to hit performance indicators as the top of their marketing funnel contracts. Web browsers are increasingly introducing default settings that block third-party cookies. Today, some customers see up to 15% of their traffic blocking third-party cookies, either by opt-in or default browser settings. Experience Platform Launch Server Side reduces the need to use third-party cookies. 

## Differences between Experience Platform Launch Server Side and Client Side

It is important to note the following differences between [!DNL Experience Platform Launch] Server Side and Client Side:

* Data element tokenization

    * Client Side: In a rule, data elements are tokenized with a `%` at the beginning and end of the data element name. For example, `%viewportHeight%`.

    * Server Side: In a rule, data elements are tokenized with `{{` at the beginning and `}}` at the end of the data element name. For example, `{{viewportHeight}}`.

* How data is referenced
    
    To reference data from the Edge network, the data element path must be `arc.event._<element>_`.
    
    `arc` stands for Adobe Response Context.

    For example: `arc.event.xdm.web.webPageDetails.URL`
    
    >[!IMPORTANT]
    >
    >If this path in specified incorrectly, data is not collected.
    

* Sequence of rule actions

    In the Action section of a rule, server-side rules are executed sequentially. The order cannot be changed. Make sure the order is correct when you create the rule. Behavior cannot be chosen like it can on the client side.

* Custom code JavaScript versions

    Experience Platform Launch Client Side uses JavaScript version es5. Server Side uses version es6.

<!--doc Adobe Cloud Connector extension, get from Jon>