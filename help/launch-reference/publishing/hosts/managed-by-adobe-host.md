---
title: Managed by Adobe Hosts
seo-title: Managed by Adobe Hosts in Adobe Experience Platform Launch
description: Adobe Experience Platform Launch hosts
seo-description: Adobe Experience Platform Launch hosts
---

# Managed by Adobe Hosts

This host type is the default selection and is simplest to manage.

When you choose the Adobe-managed option, libraries that Launch builds are delivered to a 3rd-party CDN that Adobe has contracted with. These CDNs operate independently from Adobe, so even when Launch has maintenance or downtime, the code deployed to your sites and applications continues to function as normal. The embed code references the main library file on the CDN so a client device can retrieve the files at run-time.

Currently, the primary CDN provider is Akamai. Files hosted on Akamai have a domain of [assets.adobedtm.com](https://assets.adobedtm.com). This can be referenced securely or not (`http://` or `https://`) based on how you call it in your `<script>` code.

When you create a new property through the Launch UI, a default host of this type is created for you. Note that with this host type, the very first published library to any new environment can take up to five minutes to propagate out to the global CDN.

## About Akamai

Akamai is robust when serving content to a global, high-volume audience of web visitors. Akamai runs redundant networks of load-balanced, geo-optimized nodes to serve content as quickly as possible to visitors wherever they are located throughout the world.

Specifically, Akamai runs more than 137,000 servers in 87 countries within more than 1,150 networks. In terms of redundancy, Akamai does not just route from one server to another. Akamai routes from one node of servers to another node of servers as needed. In other words, each node consists of multiple servers for redundancy within a node, so a server going down is not an issue because the other servers in the node take over. If a node goes down, Akamai serves from the next closest one, with the same cached content. Nodes are dynamically selected based on visitor location, traffic load, and other factors, so content is consistently served from the best local node for each visitor.

Akamai also has access to edge nodes in China, so end-users in China get traffic from nodes that are geographically close to them.

### Can I avoid errors in case of CDN unavailability?

No. Launch can do nothing if the library is unavailable from the Akamai network.

### CDN cache control headers

When you choose to have Adobe manage your hosting, you do not have control over the headers on the response, so the Adobe default is used. There is no way to get custom headers when you have Adobe manage your hosting.

As of September 25, 2019, there is a 24-hour TTL on all builds managed by Adobe.  If you require different cache control headers, you need to host your own files.  Please see the [Self-hosting Guide](/help/launch-reference/publishing/hosts/self-hosting-libraries.md) for more info.

>[!NOTE]  It is up to browsers to receive and respect the cache control headers. Some browsers might ignore them.

### Cache Invalidations {#cache-invalidation}

Copies of your build are cached on many different *edge nodes* around the world so that they can be served to end-users as quickly as possible.  When edge nodes field a request for a specific file, they check the TTL on the file.  If the file has not expired, the edge nodes serve the cached version.  If the TTL has expired, then it requests a new copy from the nearest *origin*, serve that refreshed copy, and then cache the refreshed copy with the defined TTL.

When you upload a new build, Launch invalidates the edge caches, which means that each edge node considers its cached version to be invalid, regardless of how recently it retrieved a fresh copy.  The next time it fields a request for that file, it retrieves a fresh copy from origin.

Because Akamai has multiple origin servers that replicate files between themselves, and because there is no way of knowing which origin got your file first, it is possible for these new requests to hit an origin that does not have the latest version and then cache the older version again.  For this reason, Launch performs multiple cache invalidations for each new build on the following interval:

* Immediately
* 5 Minutes
* 60 Minutes

This is done to give the origin groups time to replicate the latest version of the file between themselves so they all have the latest when the cache invalidations are performed.

## How to use managed hosting

To have Adobe manage your hosting, you need to create a Managed by Adobe host, then assign your environments to use this host.

## Create Managed by Adobe host

1. Open the [!UICONTROL Hosts] tab.
1. Create the new host.
1. Name the host.
1. Select **[!UICONTROL Managed by Adobe]** as the host type.
1. Click **[!UICONTROL Save]**.
