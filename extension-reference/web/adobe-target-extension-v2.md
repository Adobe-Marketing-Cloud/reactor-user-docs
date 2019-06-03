# Adobe Target v2 Extension

Use this reference for information about the options available when using this extension to build a rule.

## Configure the Adobe Target v2 extension

**Important:** The Adobe Target extension requires At.js 2.x.

If the Adobe Target extension is not yet installed, open your property, then click **Extensions &gt; Catalog**, hover over the Target extension, and click **Install**.

To configure the extension, open the Extensions tab, hover over the extension, and then click **Configure**.

![](../../.gitbook/assets/targetv2config.png)

### at.js settings

All of your at.js settings, with the exception of the Timeout, are automatically retrieved from your at.js configuration in the Target user interface. The extension only retrieves settings from the Target user interface when it is first added, so all settings should be managed in the Launch interface if additional updates are needed.

The following configuration options are available:

#### Client Code

The client code is Target’s account identifier. This should almost always be left as the default value.

Can be changed using data elements.

#### Organization ID

This ID ties your implementation to your Adobe Experience Cloud account. This should almost always be left as the default value.

Can be changed using data elements.

#### Server Domain

The domain where Target requests are sent. This should almost always be left as the default value.

#### GDPR Opt-In

When enabled, Adobe Target provides opt-in functionality to help support your consent management strategy. Opt-in functionality lets customers control how and when the Target tag is fired.  For more information about Adobe Opt-in, see [Privacy and General Data Protection Regulation \(GDPR\)](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation.html).

#### Timeout \(ms\)

If the response from Target is not received within the defined period, the request times out and default content is displayed. Additional requests continue to be attempted during the visitor's session. The default is 3000ms, which might be different from the Timeout configured in the Target user interface.

For more information about how the Timeout setting works, refer to the [Adobe Target help](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/deploy-at-js/implementing-target-without-a-tag-manager.html).

## Target extension action types

This section describes the action types available in the Target extension.

The Target extension provides the following actions in the Then portion of a rule:

### Load Target

Add this action to your Launch rule where it makes sense to load Target in the context of your rule. This loads the at.js library into the page. In most implementations, Target should be loaded on every page of your site.

No configuration is needed.

### Add Params to All Requests

Add parameters to all Target requests. The Load Target action must be used earlier.

1. Specify the name and value of any parameter you want to add.
2. Click the add icon to add more parameters.

### Add Params to Page Load Request

Add parameters only to your page load requests. The Load Target action must be used earlier.

1. Specify the name and value of any parameter you want to add.
2. Click the add icon to add more parameters.

### Fire Page Load Request

Fire a Target request when your page loads. The Load Target action must be used earlier.

Specify whether to enable body hiding to prevent flickering, and the style used when hiding your body element.

The following options are available:

* **Body Hiding:** You can enable or disable this setting. The default value is Enabled, which means HTML BODY is hidden.
* **Body Hidden Style:** The default value is body{opacity:0}. This value can be changed to something different, like body{display:none}.

For more information, refer to the [Target online help documentation](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/mbox-implement/advanced-mboxjs-settings.html).

### Trigger View

Trigger a view for your Single Page Applications.

1. Specify the view name that must be triggered.
2. Specify whether the triggering of the view should be attributed to an impression for reporting by checking the Page checkbox. If the view is correlated to a component that is re-rendered and does not attribute to an impression for reporting then leave the Page checkbox unchecked.

For more information about triggering a view, please refer to the [`triggerView()` help documentation](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/adobe-target-triggerview-atjs-2.html).

## Adobe Target basic deployment

Once the Target Extension is installed, create at least one rule to properly deploy it. You first need to load the Target library \(at.js\), specify the parameters you want to use with the page load request, and fire the page load request.

A Target rule with this basic implementation looks like this:

![](../../.gitbook/assets/targetv2deploy.png)

Once you have saved this rule, you'll need to add it to a Library and build/deploy so that you can test the behavior.

## Adobe Target extension with an asynchronous deployment

Launch can be deployed asynchronously. If you are loading the Launch library asynchronously with Target inside it, then Target will also be loaded asynchronously. This is a fully supported scenario, but there is one additional consideration that must be handled.

In asynchronous deployments, it is possible for the page to finish rendering the default content before the Target library is fully loaded and has performed the content swap. This can lead to what is known as "flicker" where the default content shows up briefly before being replaced by the personalized content specified by Target. If you want to avoid this flicker, we suggest you use a pre-hiding snippet and load the Launch bundle asynchronously to avoid any content flicker.

Here are some things to keep in mind when using the pre-hiding snippet:

* The snippet must be added before loading the Launch header embed code.
* This code can't be managed by Launch, so it must be added to the page directly.
* The page displays when the earliest of the following events occur:
  * When the page load response has been received
  * When the page load request times out
  * When the snippet itself times out
* The "Fire Page Load Request” action should be used on all pages using the pre-hiding snippet to minimize the duration of the pre-hiding.

The pre-hiding code snippet is as follows and can be minified. The configurable options are at the end:

```text
;(function(win, doc, style, timeout) {
  var STYLE_ID = 'at-body-style';

  function getParent() {
    return doc.getElementsByTagName('head')[0];
  }

  function addStyle(parent, id, def) {
    if (!parent) {
      return;
    }

    var style = doc.createElement('style');
    style.id = id;
    style.innerHTML = def;
    parent.appendChild(style);
  }

  function removeStyle(parent, id) {
    if (!parent) {
      return;
    }

    var style = doc.getElementById(id);

    if (!style) {
      return;
    }

    parent.removeChild(style);
  }

  addStyle(getParent(), STYLE_ID, style);
  setTimeout(function() {
    removeStyle(getParent(), STYLE_ID);
  }, timeout);
}(window, document, "body {opacity: 0 !important}", 3000));
```

By default, the snippet pre-hides the whole HTML BODY. In some cases, you might want to pre-hide only certain HTML elements and not the entire page. You can achieve that by customizing the style parameter. Replace it with something that pre-hides only particular regions of the page.

For example, if you have two regions identified by IDs container-1 and container-2, the style can be replaced with the following:

```text
#container-1, #container-2 {opacity: 0 !important}
```

Instead of default:

```text
body {opacity: 0 !important}
```

By default, the snippet times out at 3000ms or 3 seconds. This value can be customized.











