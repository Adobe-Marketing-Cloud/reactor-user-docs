# Asynchronous Deployment

Performance and non-blocking deployment of the JavaScript libraries required by our products is increasingly important to Adobe Experience Cloud users. Tools like [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/) recommend that users change they way they deploy the Adobe libraries on their site. This article explains how to use the Adobe JavaScript libraries in an asynchronous fashion.

## Synchronous vs asynchronous

### Synchronous deployment

Often, libraries are loaded synchronously in the `<head>` tag of a page. For example:

```markup
<script src="example.js"></script>
```

By default, the browser parses the document and reaches this line, then starts to fetch the JavaScript file from the server. The browser waits until the file is returned, then it parses and executes the JavaScript file. Finally, it continues parsing the rest of the HTML document.

If the parser comes across the `<script>` tag before rendering visible content, content display is delayed. If the JavaScript file being loaded is not absolutely necessary to show content to your users, you are unnecessarily requiring your visitors to wait for content. The larger the library, the longer the delay.  For this reason, website performance benchmark tools like Google PageSpeed or Lighthouse often flag synchronously loaded scripts.

Tag Management libraries can quickly grow large if you have a lot of tags to manage.

### Asynchronous deployment

You can load any library asynchronously by adding an `async` attribute to the `<script>` tag.  For example:

```markup
<script src="example.js" async></script>
```

This indicates to the browser that when this script tag is parsed, the browser should begin loading the JavaScript file, but instead of waiting for the library to be loaded and executed, it should continue to parse and render the rest of the document.

## Considerations to asynchronous deployment

As described above, in synchronous deployments, the browser pauses parsing and rendering the page while the Launch library is loaded and executed. In asynchronous deployments, on the other hand, the browser continues parsing and rendering the page while the library loads. The variability of when the Launch library might finish loading in relation to page parsing and rendering must be taken into consideration.

First, because the Launch library can finish loading before or after the bottom of the page has been parsed and executed, you should no longer call `_satellite.pageBottom()` from your page code \(`_satellite` won't be available until after the library has loaded\). This is explained in [Loading the Launch embed code asynchronously](asynchronous-deployment.md#loading-the-launch-embed-code-asynchronously).

Second, the Launch library can finish loading before or after the [`DOMContentLoaded`](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded) browser event \(DOM Ready\) has occurred.

Because of these two points, it's worth demonstrating how the [Library Loaded](../../extension-reference/web/core-extension/#library-loaded-page-top), [Page Bottom](../../extension-reference/web/core-extension/#page-bottom), [DOM Ready](../../extension-reference/web/core-extension/#page-bottom), and [Window Loaded](../../extension-reference/web/core-extension/#window-loaded) event types from the Core extension function when loading a Launch library asynchronously.

Let's assume your Launch property contains the following four rules:

* Rule A: uses the Library Loaded event type
* Rule B: uses the Page Bottom event type
* Rule C: uses the DOM Ready event type
* Rule D: uses the Window Loaded event type

Regardless of when the Launch library finishes loading, all the rules are guaranteed to be executed and they will be executed in the following order:

Rule A → Rule B → Rule C → Rule D

Although the order is always enforced, some rules might be executed immediately when the Launch library finishes loading, while others might be executed later. The following occurs when the Launch library finishes loading:

1. Rule A is executed immediately.
2. If the `DOMContentLoaded` browser event \(DOM Ready\) has already occurred, Rule B and Rule C are executed immediately. Otherwise, Rule B and Rule C are executed later when the [`DOMContentLoaded`](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded) browser event occurs.
3. If the [`load`](https://developer.mozilla.org/en-US/docs/Web/Events/load) browser event \(Window Loaded\) has already occurred, Rule D is executed immediately. Otherwise, Rule D will be executed later when the [`load`](https://developer.mozilla.org/en-US/docs/Web/Events/load) browser event occurs. Note that if you've installed the Launch library according to the instructions, the Launch library _always_ finishes loading before the [`load`](https://developer.mozilla.org/en-US/docs/Web/Events/load) browser event occurs.

When applying these principles to your own website, consider the following:

* **A rule using the Library Loaded event type might execute before your data layer is fully loaded.**  This can result in the rule's actions executing with missing data because the data was not yet available on the page. These types of issues can be mitigated by tweaking your rule configuration. As an example, instead of having a rule triggered by the Library Loaded event type, you could instead use the Custom Event or Direct Call event type that are triggered by your page code as soon as your data layer finishes loading.
* **The Page Bottom event type doesn't particularly provide value when the library is loaded asynchronously.**  Instead, consider the Library Loaded, DOM Ready, Window Loaded, or other event types.

If you see things occurring out of order, it is likely that you have some timing issues to work through. Deployments requiring precise timing might need to use event listeners and the Custom Event or Direct Call event type to make their implementations more robust and consistent.

## Loading the Launch embed code asynchronously

Launch provides a toggle to turn on asynchronous loading when creating an embed code when you configure an [environment](../publishing/environments.md). You can also configure asynchronous loading yourself:

1. Add an async attribute to the `<script>` tag to load the script asynchronously.

   For the Launch embed code, that means changing this:

   ```markup
   <script src="//www.yoururl.com/launch-EN1a3807879cfd4acdc492427deca6c74e.min.js"></script>
   ```

   to this:

   ```markup
   <script src="//www.yoururl.com/launch-EN1a3807879cfd4acdc492427deca6c74e.min.js" async></script>
   ```

2. Remove any code you may have previously added at the bottom of your tag:

   ```markup
   <script type="text/javascript">_satellite.pageBottom();</script>
   ```

   This code tells Launch that the browser parser has reached the bottom of the page. Since Launch likely will not have loaded and executed before this time, calling `_satellite.pageBottom()` results in an error and the Page Bottom event type may not behave as expected.

