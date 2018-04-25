# Adobe Target Extension

Use this reference for information about the options available when using this extension to build a rule.

## Configure the Adobe Target extension

Important: The Adobe Target extension requires at.js. It does not support mbox.js.

If the Adobe Target extension is not yet installed, open your property, then click Extensions &gt; Catalog, hover over the Target extension, and click Install.

To configure the extension, open the Extensions tab, hover over the extension, and then click Configure.

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/ext-target-config.png)

### at.js Settings

Configure your at.js settings. The following configuration options are available:

#### Client Code

The client code is a client-specific sequence of characters often required when using the Target APIs.

Can be changed using data elements.

#### Organization ID

This ID ties your implementation to your Adobe Experience Cloud account.

Can be changed using data elements.

#### Server Domain

The domain where Target requests are sent. This should almost always be left as the default value.

#### Cross Domain

Determines where Target sets cookies in the browsers.

* **Disabled:** Sets the cookies on the first-party domain only. This is the typical setting.
* **Enabled:** Sets cookies on both the first-party domain and the third-party Target domain \(the "Server Domain"\).

#### Timeout \(ms\)

If Target does not respond with content within the defined period, the server call times out and default content is displayed. Additional calls continue to be attempted during the visitor's session. The default is 3000ms.

For more information about how the Timeout setting works, refer to the [Adobe Target help](https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-advanced-settings.html).

#### Global Mbox Name

Shows the name of your global mbox. By default, this name is target-global-mbox.

Can be changed using data elements.

## Target extension action types

This section describes the action types available in the Target extension.

The Target extension provides the following actions in the Then portion of a rule:

### Load Target

**Description**

Add this action to your Launch rule where it makes sense to load Target in the context of your rule. This loads the at.js library into the page. In most implementations, Target should be loaded on every page of your site.

**Settings**

No configuration is needed.

### Load Target Async

**Description**

Add this action to your Launch rule where it makes sense to load Target asynchronously in the context of your rule. This loads the at.js library into the page. In most implementations, Target should be loaded on every page of your site.

**Settings**

No configuration is needed.

### Add Mbox Params

**Description**

Add parameters to your mbox configuration.

**Settings**

Specify the name and value of any parameter you want to add.

Click the Plus icon to add more parameters.

### Add Global Mbox Params

**Description**

Add parameters to your global mbox configuration.

**Settings**

Specify the name and value of any parameter you want to add.

Click the Plus icon to add more parameters.

### Fire Global Mbox

**Description**

Fire the global mbox on your page.

**Settings**

Specify whether to enable body hiding to prevent flickering, and the style used when hiding your body element.

The following options are available:

* **Body Hiding:** You can enable or disable this setting. The default value is Enabled, which means HTML BODY is hidden.
* **Body Hidden Style:** The default value is `body{opacity:0}`. This value can be changed to something different, like `body{display:none}`.

For more information, refer to the [Target online help documentation](https://marketing.adobe.com/resources/help/en_US/target/ov/r_advanced_mboxjs_settings.html).

### Fire Global Mbox Async

**Description**

Fire the global mbox asynchronously on your page.

**Settings**

Specify whether to enable body hiding to prevent flickering, and the style used when hiding your body element.

The following options are available:

* **Body Hiding:** You can enable or disable this setting. The default value is Enabled, which means HTML BODY is hidden.
* **Body Hidden Style:** The default value is `body{opacity:0}`. This value can be changed to something different, like `body{display:none}`.

For more information, refer to the [Target online help documentation](https://marketing.adobe.com/resources/help/en_US/target/ov/r_advanced_mboxjs_settings.html).

Note: You cannot combine Load Target \(sync\) action with Fire Global Mbox Async action or vice-versa. Use either sync or async actions.

## Adobe Target extension with an asynchronous deployment

Launch supports asynchronous deployment.

To use the Adobe Target extension with an asynchronous deployment, we suggest you use a pre-hiding snippet and load the Launch bundle asynchronously to avoid any content flicker.

* A pre-hiding snippet should be loaded _before_ the Launch bundle, to ensure there is no flicker.

  Important: This code can't be managed by Launch, so it must be added to the page directly.

* To avoid hiding the whole page, the pre-hiding snippet should hide a container element that will be personalized.

  The CSS selector used in the pre-hiding snippet can be customized, so you can pre-hide more than one element. By default, the snippet tries to load the whole page.

| Pre-hiding Snippet | Launch Bundle | Body Hiding Inside fireGlobalMbox Action | Target Actions |
| --- | --- | --- | --- |
| True | Async | Prehiding snippet hides body or other elements. Without prehiding snippet, flicker occurs. | Sync |
| False | Sync | Body hiding enabled. | Async |

The snippet must be added before loading at.js. The pre-hiding code snippet is as follows:

```javascript
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

By default the snippet pre-hides the whole HTML BODY. In some cases, you may only want to pre-hide certain HTML elements and not the entire page. You can achieve that by customizing the style parameter. It can be replaced with something that pre-hides only particular regions of the page.

For example, you have two regions identified by IDs container-1 and container-2, then the style can be replaced with the following:

```css
#container-1, #container-2 {opacity: 0 !important}
```

Instead of default:

```css
body {opacity: 0 !important}
```

