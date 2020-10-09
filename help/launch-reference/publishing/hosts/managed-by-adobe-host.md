---
title: Managed by Adobe Hosts
seo-title: Managed by Adobe Hosts in Adobe Experience Platform Launch
description: Adobe Experience Platform Launch hosts
seo-description: Adobe Experience Platform Launch hosts
---

# Adobe-managed hosts

Hosts which are managed by Adobe are the default host setting for deploying your library builds in Adobe Experience Platform Launch, with the other option being [SFTP hosts](./managed-by-adobe-host.md). When you create a new property through the Launch user interface, a default Adobe-managed host is created for you. 

With Adobe-managed hosts, library builds are delivered to a third-party content delivery network (CDN) that Adobe has contracted with. These CDNs operate independently from Adobe, so even when Launch is undergoing maintenance or is otherwise down, your deployed code will continue to function as normal on your sites and applications. The embed code for an Adobe-managed host references the main library file on the CDN so a client device can retrieve the files at runtime.

This document provides an overview of Adobe-managed hosts in Launch, including important considerations that should be made when using this option as well as how to create a new Adobe-managed host in the UI.

<!-- 
>[!NOTE]
>
>For Adobe-managed hosts, the very first published library to any new environment can take up to five minutes to propagate out to the global CDN. 
-->

## About Akamai

Currently, the primary CDN provider for Adobe is [Akamai](https://www.akamai.com/). Akamai's robust CDN is built to serve content to a global, high-volume audience of web visitors. The CDN runs redundant networks of load-balanced, geo-optimized nodes in order to serve content as quickly as possible to visitors located throughout the world.

Specifically, Akamai runs more than 137,000 servers in 87 countries within more than 1,150 networks. In terms of redundancy, the CDN not only routes from one server to another, but can also route from one node of servers to another node of servers as needed. In other words, each node consists of multiple servers, so that one server going down never becomes an issue as the other servers on the same node can take over.

If an entire node goes down, Akamai serves from the next-closest node with the same cached content. Nodes are dynamically selected based on visitor location, traffic load, and other factors so that content is consistently served from the best local node for each visitor.

Akamai also has access to edge nodes in China, so end-users in China get traffic from nodes that are geographically close to them.

Files hosted on Akamai have a domain of `assets.adobedtm.com`. This can be referenced securely or not (`http://` or `https://`) based on how it is called within in your `<script>` code.

<!-- 
### Can I avoid errors in case of CDN unavailability?

No. Launch can do nothing if the library is unavailable from the Akamai network. -->

## Embed code caching

When using Adobe-managed hosts, your CDN embed code is cached for your application in two locations:

* [Edge caching](#edge)
* [Browser caching](#browser)

### Edge caching {#edge}

Copies of your build are cached on many different edge nodes around the world so that they can be served to end-users as quickly as possible.

When an edge node receives a request for a specific file, the node first checks the the time-to-live (TTL) on the file. If the TTL has not expired, the edge node serves the cached version. If the TTL has expired, then the edge node requests a new copy from the nearest origin, serves that refreshed copy, and then caches the refreshed copy with a new TTL.

#### Edge cache invalidation {#invalidation}

When you upload a new library build, Launch invalidates the caches on all applicable edge nodes, which means that each node considers its cached version to be invalid, regardless of the how recently it retrieved a fresh copy. The next time an edge node receives a request for that file, the node retrieves a fresh copy from the origin.

Because Akamai has multiple origin servers that replicate files between each other, and because there is no way of knowing which origin received your file first, it is possible for these node requests to hit an origin that does not have the latest version, and then cache the older version again. To prevent this from occurring, Launch performs multiple cache invalidations for each new build on the following intervals:

* Immediately after upload
* 5 minutes after upload
* 60 minutes after upload

These staggered cache invalidations give the origin server groups time to replicate the latest version of the file between themselves so they all have the latest when the the file is retrieved.

### Browser caching {#browser}

The CDN embed code is also cached on the browser through the use of the `cache-control` HTTP header. When using Adobe-managed hosts, you do not have control over the headers returned in API responses, so the Adobe default for caching is used. In other words, you cannot utilize custom headers for Adobe-managed hosts. If you require a custom `cache-control` header, you may want to consider [self-hosting](self-hosting-libraries.md) instead.

The time-to-live (TTL) for your browser-cached embed code (determined by the `cache-control` header) will vary depending on the environment you are using:

| Environment | `cache-control` value |
| --- | --- |
| Development | `max-age=0, no-cache, no-store` |
| Staging | `max-age=0, no-cache, no-store` |
| Production | `max-age=3600` |

As the table above indicates, browser caching is not supported on development and staging environments. As such, you should not use the development or staging embed codes in high-traffic or production contexts.

Cache control headers are only are only applied for the main library build. Any sub-resources below the main library are always considered net-new, and therefore there is no need to cache them on the browser.

## How to use managed hosting

To have Adobe manage your hosting, you need to create a Managed by Adobe host, then assign your environments to use this host.

## Create Managed by Adobe host

1. Open the [!UICONTROL Hosts] tab.
1. Create the new host.
1. Name the host.
1. Select **[!UICONTROL Managed by Adobe]** as the host type.
1. Click **[!UICONTROL Save]**.
