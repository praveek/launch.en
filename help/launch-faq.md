---
title: [!DNL Launch] FAQ
seo-title: [!DNL Launch] FAQ in [!DNL Adobe Experience Platform Launch]
description: [!DNL Adobe Experience Platform Launch] FAQ
seo-description: [!DNL Adobe Experience Platform Launch] FAQ
---

# Adobe Experience Platform Launch FAQ

Frequently asked questions about Launch, by Adobe, announced in March 2017.

## What is Launch?

[!DNL Launch] is the next-generation of the [!DNL Adobe] tag-management capability, built into the [!DNL Adobe Cloud Platform]. [!DNL Launch] enables clients to:

* Deploy client-side web products using integrations called _extensions_
* Consistently capture, define, manage, and share data between marketing and advertising products from other vendors and from [!DNL Adobe]

[!DNL Launch] is an advanced JavaScript delivery system that evaluates conditions and executed actions to efficiently and effectively deploy client-side libraries and products. It provides a highly scalable approach to managing and building extensions, together with a robust set of APIs for programmatic interaction with the [!DNL Adobe Cloud Platform].

## Is Launch just an updated DTM?

No. [!DNL Launch] is an entirely new product with a new code base. The system has been redesigned from scratch using modern front-end development practices and an API-first approach. Everything is built on a robust set of APIs, which makes the system very powerful and highly flexible.

## Will the current DTM product remain available?

Yes, legacy [!DNL DTM] (the existing production version) will continue to be supported for the foreseeable future. [!DNL Adobe] will continue to fix any significant bugs and ensure consistent performance. At this time, no major feature enhancements are planned for legacy [!DNL DTM].

The [!DNL Launch] team is working to make the migration process from legacy [!DNL DTM] to [!DNL Launch] as easy as possible so customers can take advantage of more than twenty new features, extensions, and APIs that [!DNL Launch] provides.

## How much does Launch cost?

There is no additional charge for [!DNL Launch]. It is available for any [!DNL Adobe Experience Cloud] customer.

## Do I have to change the embed codes in my current DTM implementation?

No, you don't have to change your production embed codes if you're currently using the existing (legacy) [!DNL DTM] system. You can continue to work in your current [!DNL DTM] Company and Web Properties without worrying about changing that embed code. The product team is working to make the migration process as easy and automated as possible. For more details, see the [Launch help docs](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/embed-code-link.html), and this [blog post](https://medium.com/launch-by-adobe/migrating-from-dtm-to-launch-57548251a86d).

## I heard there are plug-ins now. What's that about?

[!DNL Launch] is built into the [!DNL Adobe Cloud Platform] and it is fully extensible. Customers, [!DNL Adobe] Partners, agencies, and marketing or advertising technology vendors can build [!DNL Launch] extensions that add new functionality or modify existing functionality. The system allows partners and clients to build, manage, and update their own integrations. This is just one way [!DNL Adobe] is opening up the [!DNL Adobe Cloud Platform] so customers and partners can build products and businesses on the Platform, and so everyone can more easily connect Adobe technology to the marketing and advertising technologies from other vendors. Over time, this will be the place for customers to install and configure all of their client-side technologies.

## Will all third-party extensions be available right away?

Extensions are available for [!DNL Adobe] solutions and for a select group of independent vendors. The product team is working closely with several technology partners to ensure the availability of these extensions. The product team continues to work to expand the number of extensions. Because extensions can be built, managed, and updated by the Extension developer, vendors don't have to wait for [!DNL Adobe] engineering to build them.

## When can clients or partners uild extensions?

[!DNL Launch] has opened its virtually self-service portal, which extension developers can use to build their own integrations with the [!DNL Adobe Cloud Platform].

## Does Launch meet my company's security standards?

[!DNL Launch] is SOC-2 and Gramm-Leach-Bliley Act ready. [!DNL Launch] also offers the capability of being self-hosted. The JavaScript libraries can be served from your own servers, or the CDN of your choice. For I.T. and security teams, this gives you the ability to run automated testing, to check the files into your own version control system, and to fully comply with any internal production migration processes, security-related or otherwise.

## When can I move to Launch?

If you are already using legacy [!DNL DTM], or are currently deploying [!DNL DTM], you can continue to do so. You can move your projects forward using the current [!DNL DTM]. Then, when you're ready to move to [!DNL Launch], the migration process makes it as easy and automated as possible (no on-page embed code changes, and automated migration of rules and data elements).

## Which capabilities exist in Launch that don't exist in legacy DTM?

[!DNL Launch] will offer four major capabilities that aren't comparable to legacy [!DNL DTM]:

* Deploy non-[!DNL Adobe] client-side browser technologies quickly and easily

  Using extensions, clients and partners can easily control in-browser technologies in the interface, without managing custom code.

* Enterprise-grade publishing

  Compartmentalize and control each piece of your libraries to deploy precisely what you need, where you need it, and when you need it.

* Robust approval workflows

  Flexible approval workflows allow custom processes to match your existing internal approval processes.

* Granular rights management

  Administrators will designate which extensions users can, and can't use. They will also control which areas within [!DNL Launch] are accessible to certain users.

## Does Launch support single page apps and my favorite framework?

Yes. [!DNL Launch] has capabilities to give users and extension developers flexibility in collecting, managing, and distributing data within single page application experiences or Ajax-heavy pages or sites. This applies regardless of your development framework preferences, whether that's Angular, React.js, Ember, Meteor, etc.

## Does Launch support dynamic data layers?

Yes. [!DNL Launch] includes an extension that specializes in listening for changes in dynamic data layers.

## Which event types does Launch support?

Event types are available through extensions. The pre-loaded [!DNL DTM] extension includes 30 built-in event types. Other extensions could add additional event types. For example, the YouTube extension includes four video event types: play, pause, end, and time played. Through extensions, [!DNL Launch] can support any other browser event types or synthetic event types, such as specific visitor activity sequences.

## Will Launch speed up (or slow down) my web site?

[!DNL Launch] is designed to deliver and run marketing and advertising technologies on your web site as efficiently as possible using today's best practices. When used properly, [!DNL Launch] has proven to improve performance of web sites over alternative methods of providing similar functionality.

## Which browsers does Launch support?

Browser support in the [!DNL Launch] client-side libraries:

* [!DNL Chrome] (latest)
* [!DNL Safari] (latest)
* [!DNL Firefox] (latest)
* [!DNL Microsoft Edge] (latest)
* [!DNL Internet Explorer] (10 and above)
* [!DNL iOS Safari] (latest)
* [!DNL Android Chrome] (latest)

Browser support in the [!DNL Launch] application interface:

* [!DNL Chrome] (latest)
* [!DNL Safari] (latest)
* [!DNL Firefox] (latest)
* [!DNL Internet Explorer] (11 and above)
* [!DNL Microsoft Edge] (latest)

Legacy [!DNL DTM] supported older versions of [!DNL Internet Explorer], but over the last few years, the percentage of overall web users with older, outdated browsers has dropped to a small segment for our clients. Most [!DNL Adobe] clients now leverage more modern web platform features in current browsers and create better user experiences, including single page applications and interactive Ajax-heavy web sites and pages. As most clients move to more modern approaches with their sites, they demand a solution like [!DNL Launch] that enables those approaches.

## Does Launch work on native mobile apps?

Yes! [!DNL Launch] now supports mobile properties and configuration for the new [!DNL Adobe Experience Platform] [Mobile SDKs](https://sdkdocs.com) to implement data collection and delivery in a native mobile app environment. Please visit [documentation](https://sdkdocs.com) to learn more.

## What if I have other questions?

These are the questions we've received most often from customers and partners since the [!DNL Launch] announcement. If you have other questions, please ask in the [!DNL Adobe] Community on the main Launch page located at [https://adobe.com/go/launchme](https://adobe.com/go/launchme).

[!DNL Launch] is just one example of where our platform is headed: more open, more integrated and as always dedicated to customer success.
