# Asynchronous Deployment

Performance and non-blocking deployment of the JavaScript libraries required by our products is increasingly important to Adobe Experience Cloud users. Tools like [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/) recommend that users change they way they deploy The Adobe libraries on their site. This article explains how to use the Adobe JavaScript libraries in an asynchronous fashion.

## Synchronous vs asynchronous

### Synchronous deployment

Often, libraries are loaded synchronously in the `<head>` tag of a page. For example:

```markup
<script src="example.js"></script>
```

By default, the browser parses the document and reaches this line, then starts to fetch the JavaScript file from the server. The browser waits until the file is returned, then it parses and executes the JavaScript file. Finally, it continues parsing the rest of the HTML document.

If the parser comes across the `<script>` tag before rendering visible content, content display is delayed. If the JavaScript file being loaded is not absolutely necessary to show content to your users, you are unnecessarily requiring your visitors to wait for content. For this reason, website performance benchmark tools like Google PageSpeed or Lighthouse often flag synchronously loaded scripts.

### Asynchronous deployment

To load the JavaScript file asynchronously, add an async attribute to the `<script>` tag:

```markup
<script src="example.js" async></script>
```

This indicates to the browser that when this script tag is parsed, the browser should begin loading the JavaScript file, but instead of waiting for the library to be loaded and executed, it should continue to parse and render the rest of the document.

## Drawbacks to asynchronous deployment

Although the goal is to display content to visitors faster, and asynchronously loading the JavaScript achieves that goal, asynchronous deployment requires careful consideration under certain circumstances.

### Personalized content

Note: The Target Extension does not currently support async deployments. Support is expected in an upcoming release.

Some products dynamically load personalized content at runtime. Typically, part or all of the body content is hidden until the personalized content displays. Otherwise, default content is displayed, then replaced by personalized content moments later. This is known as "flicker" and is undesirable for the user experience.

The Target and Launch teams are hard at work to solve this problem for async deployments of Target so that you can avoid this flicker. For now Target deployments should continue to be done synchronously.

### Page Bottom event type

Another consideration is that Launch has always provided a Page Bottom event type that allows users to fire a rule at the precise moment the bottom of the body tag is reached by the browser parser. Because the Launch runtime will likely finish loading after the page bottom has been reached, the Page Bottom event type may not fire associated rules at the time you may expect. For this reason, when loading Launch asynchronously, you should not use the Page Bottom event type. Instead, consider the Library Loaded, DOM Ready, Window Loaded, or other event types.

## Loading the Launch embed code asynchronously

Launch provides a toggle to turn on asynchronous loading when creating an embed code when you configure an [environment](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/67a59a7519514467a713016adfe46d999fe330d8/client-side-information/environment-overview.md). You can also configure asynchronous loading yourself:

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

