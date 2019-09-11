---
title: Content Security Policy (CSP)
seo-title: Content Security Policy (CSP) in Adobe Experience Platform Launch
description: Content Security Policy (CSP) in Adobe Experience Platform Launch
seo-description: Content Security Policy (CSP) in Adobe Experience Platform Launch
---

# Content Security Policy (CSP)

The primary goal of a Content Security Policy (CSP) is to prevent cross-site scripting attacks (XSS). This happens when the browser is tricked into running malicious content that appears to come from a trusted source, but is really coming from somewhere else. CSP allows the browser (on behalf of the user) to verify that the script is actually coming from a trusted source.

CSP is implemented by adding the `Content-Security-Policy` HTTP header to your server responses. You can read more about CSP on the Mozilla Developer Network site: [https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)

## Issues to Overcome

Tag management systems are designed to dynamically load scripts. CSP is designed to block these dynamically loaded scripts because they can cause security problems.

If you want Launch to work with your CSP, there are two main challenges to overcome:

* **The source for your Launch library must be trusted.** If this condition is not met, the Launch library and other required JavaScript files are blocked by the browser and won't load on the page.
* **Inline scripts must be allowed.** If this condition is not met, Custom Code rule actions are blocked on the page and won't execute properly.

If you want to use Launch _and_ have a CSP in place, you have to fix both of these problems without incorrectly marking other scripts as safe. Increasing security comes at the price of increasing the amount of work on your part.

## Trusted Sources

If you are self hosting your library, then the source for your library is probably your own domain. You can specify that the host domain is a safe source like this:

`script-src 'self'`

If you are having Adobe host the library (with the Managed by Adobe host), then your library is maintained on assets.adobedtm.com. In this case, you want your policy to look something like this:

`script-src 'self' assets.adobedtm.com`

You should specify `self` as a safe domain so you don't break any scripts that you are already loading, but you also need `assets.adobedtm.com` to be listed as safe or your Launch library won't load on the page.

You can read more about trusted sources on the [Mozilla Developer Network site](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP).

## Inline Scripts

Inline scripts present a challenge for CSP because they are disallowed by default. You have two options to allow inline scripts:

* Allow all inline scripts (least secure)
* Allow by nonce (good security)

The CSP specification has details for a 3rd option using hashes, but this approach is not feasible to use with a TMS of any kind for a number of reasons, some of them very complicated.

### Good Security - Nonces {#nonce}

This method involves generating a nonce and adding it to your CSP and to each inline script. When the browser receives an instruction to load an inline script with a nonce on it, compare the nonce value to what is contained within the CSP header. If it matches, the script is loaded.

This nonce should be changed with each new page load.

There is a very important prerequisite: You must load the Launch library [asynchronously](launch-reference/client-side-information/asynchronous-deployment.md). This does not work with a synchronous load of the Launch library (which results in console errors and rules not executing properly).

You can add your nonce to the above Adobe-hosted CSP example like this:

`script-src 'self' assets.adobedtm.com 'nonce-2726c7f26c'`

You must then tell Launch where to find the nonce. Launch uses it when loading an inline script. For Launch to use the nonce when loading the script, you must:

1. Create a data element that references your nonce (wherever you put it in your data layer).
2. Configure the Core Extension and specify which data element you used.
3. Publish your data element and Core Extension changes.

One additional note: This only handles loading of your custom code. It doesn't handle what you do in your custom code. It is possible for you to write custom code that is not compliant with your CSP, in which case the CSP has precedence. For example, if you use custom code to load an inline script by appending it to the DOM, Launch cannot find that or add the nonce correctly, so that particular custom code action will not work as expected.

### Low Security - Allow Inline {#unsafe-inline}

If the above option does not work for you, you can tell your CSP to allow all inline scripts. This is the least secure option, but is also easier to implement and maintain.

Again, assuming you are having Adobe manage the hosting and you mark assets.adobedtm.com domain as a trusted source, your CSP would look something like this:

`script-src 'self' assets.adobedtm.com 'unsafe-inline'`

For more information on allowing inline scripts, see [https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/script-src](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/script-src) on the MDN site.
