# Content Security Policy \(CSP\)

The primary goal of a Content Security Policy \(CSP\) is to prevent cross site scripting attacks \(XSS\).  This happens when the browser is tricked into running malicious content that appears to come from trusted source, but is really coming from somewhere else.

CSP is implemented by adding the `Content-Security-Policy` HTTP header to your server responses. You can read more about CSP on the Mozilla Developer Network site: [https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)

## The Problem

Strict security policies can be problematic for Launch implementations because Launch frequently relies on dynamically loading other JavaScript onto the page in order to execute the actions that you've defined in your rules.

If you have a strict CSP, these dynamically loaded scripts are blocked by the browser and your actions will not execute as you'd expect.

## Options

### unsafe-inline

Currently, if you want to use Launch on a site with a Content Security Policy, you'll need to add the `unsafe-inline` source to your `Content-Security-Policy` HTTP header.  It is also a good idea to specify the domain that is allowed to load inline scripts.  As an example, if you have Adobe host your Launch library, your header might look something like this:

`script-src 'self' 'unsafe-inline' assets.adobedtm.com`

### unsafe-eval

If you're using Adobe Target, you should also be aware that at.js 1.X uses the `eval()` function.  If you are using the Adobe Target extension, you will also need to add the `unsafe-eval` source to your CSP.

at.js 2.X does not use `eval()`.

## Future Options

The Launch team is currently working with Adobe's security team to evaluate an alternate approach that would use a `nonce` to validate inline scripts.  More details will be forthcoming if that approach pans out.

