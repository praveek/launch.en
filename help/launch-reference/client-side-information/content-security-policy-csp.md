---
title: Content Security Policy (CSP)
seo-title: Content Security Policy (CSP) in Adobe Experience Platform Launch
description: Content Security Policy (CSP) in Adobe Experience Platform Launch
seo-description: Content Security Policy (CSP) in Adobe Experience Platform Launch
---

# Content Security Policy (CSP)

A Content Security Policy (CSP) is a security feature that helps prevent cross-site scripting attacks (XSS). This happens when the browser is tricked into running malicious content that appears to come from a trusted source, but is really coming from somewhere else. CSPs allow the browser (on behalf of the user) to verify that the script is actually coming from a trusted source. CSPs are implemented by adding a `Content-Security-Policy` HTTP header to your server responses.

>[!NOTE]
>
> For more detailed information on CSP, refer to the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP).

As a tag management system, Adobe Experience Platform Launch is designed to dynamically load scripts on your website. A default CSP blocks these dynamically loaded scripts due to potential security problems. This document provides guidance on how to configure your `Content-Security-Policy` header to allow dynamically loaded scripts from [!DNL Launch].

## Issues to overcome

If you want [!DNL Launch] to work with your CSP, there are two main challenges to overcome:

- **The source for your [!DNL Launch] library must be trusted.** If this condition is not met, the [!DNL Launch] library and other required JavaScript files are blocked by the browser and will not load on the page.
- **Inline scripts must be allowed.** If this condition is not met, custom scripts are blocked on the page and will not execute properly.

If you want to use [!DNL Launch] and have a CSP in place, you have to address both of these issues without incorrectly marking other scripts as safe. The rest of this document provides guidance on how to achieve this.

## Add [!DNL Launch] as a trusted source

When using a CSP, you must include any trusted domains within the value of the `Content-Security-Policy` header. The value you must provide for [!DNL Launch] will vary depending on the type of hosting you are using.

### Self-hosting

If you are [self-hosting](../publishing/hosts/self-hosting-libraries.md) your library, then the source for your library is probably your own domain. You can specify that the host domain is a safe source by using the following header:

`Content-Security-Policy: script-src 'self'`

### Adobe-managed hosting

If you are using an [Adobe-managed host](../publishing/hosts/managed-by-adobe-host.md), then your library is maintained on `assets.adobedtm.com`. In this case, you should use the following header:

`Content-Security-Policy: script-src 'self' assets.adobedtm.com`

You should specify `self` as a safe domain so that any scripts that you are already loading continue to work, but you also need `assets.adobedtm.com` to be listed as safe or your [!DNL Launch] library won't load on the page.

## Inline scripts

CSP disallows inline scripts by default, and therefore must be manually configured to allow them. You have two options to allow inline scripts:

- [Allow by nonce](#nonce) (good security)
- [Allow all inline scripts](#unsafe-inline) (least secure)

>[!NOTE]
>
>The CSP specification has details for a third option using hashes, but this approach is not feasible to use with tag management systems like [!DNL Launch]. For more information on the limitations of using hashes in [!DNL Launch], see the [Subresource Integrity (SRI) guide](./sri.md).

### Allow by nonce {#nonce}

This method involves generating a cryptographic nonce and adding it to your CSP and every inline script on your site. When the browser receives an instruction to load an inline script with a nonce on it, the browser compares the nonce value to what is contained within the CSP header. If it matches, the script is loaded. This nonce should be changed with each new page load.

>[!IMPORTANT]
>
>In order to use this method, you must load the [!DNL Launch] library asynchronously. This does not work with a synchronous load of the [!DNL Launch] library, which results in console errors and rules not executing properly. See the guide on [asynchronous deployment](./asynchronous-deployment.md) for more information.

The examples below show how can add your nonce to the CSP header.

**Self-hosting**

`Content-Security-Policy: script-src 'self' 'nonce-2726c7f26c'`

**Adobe-managed hosting**

`Content-Security-Policy: script-src 'self' assets.adobedtm.com 'nonce-2726c7f26c'`

You must then tell [!DNL Launch] where to find the nonce when loading an inline script. For [!DNL Launch] to use the nonce when loading the script, you must:

1. Create a data element that references where the nonce is located within your data layer.
2. Configure the Core Extension and specify which data element you used.
3. Publish your data element and Core Extension changes.

>[!NOTE]
>
>The above process only handles loading your custom code, not what that custom code does. If an inline script contains custom code that is not compliant with your CSP, the CSP takes precedence. For example, if you use custom code to load an inline script by appending it to the DOM, [!DNL Launch] cannot find that or add the nonce correctly, so that particular custom code action will not work as expected.

### Allow all inline scripts {#unsafe-inline}

If using nonces does not work for you, you can configure your CSP to allow all inline scripts. This is the least secure option, but is also easier to implement and maintain.

The examples below show how can allow all inline scripts in the CSP header.

**Self-hosting**

`Content-Security-Policy: script-src 'self' 'unsafe-inline'`

**Adobe-managed hosting**

`Content-Security-Policy: script-src 'self' assets.adobedtm.com 'unsafe-inline'`

## Next steps

By reading this document, you should now understand how to configure your CSP header to accept the [!DNL Launch] library file and inline scripts.

As an additional security measure, you may also opt to use Subresource Integrity (SRI) to validate fetched library builds. However, this feature has some major limitations when used with tag management systems like [!DNL Launch]. See the guide on [SRI compatibility in [!DNL Launch]](./sri.md) for more information.