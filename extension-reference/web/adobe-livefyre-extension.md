# Adobe Livefyre Extension

 Configure the Adobe Livefyre Extension for Adobe Launch.

## Install Livefyre Extension

 Install the Livefyre Extension on a Launch Property. For information on creating Properties, see [Companies and Properties](../../administration/companies-and-properties.md).

1.  From the Adobe Experience Platform Launch home screen, click **Properties** in the left-hand rail.
2. Click the property in which you want to install the Livefyre extension.
3. Navigate to **Extensions &gt; Catalog**.
4. Locate the Livefyre extension, then click **Install**. ![](https://marketing-stage.adobe.com/resources/help/en_US/livefyre/images/launch_install_lf.png)
5. Enter your Livefyre network ID. For help configuring an extension, see [Configure Livefyre Extension](adobe-livefyre-extension.md#configure-livefyre-extension).
6. Click **Save**.

## Configure Livefyre Extension

Configure your existing Livefyre Extension.

**Note:** To access your Livefyre credentials, open Livefyre studio and navigate to **Settings &gt; Integration Settings &gt; Credentials**.

1. From the Adobe Experience Platform Launch home screen, click **Properties** in the left-hand rail.
2. Click the property containing the Livefye Extension you want to configure.
3. Click the **Extensions** tab.
4. Find the Livefyre Exension and click **Configure**.
5. Fill in the details:

   * **Livefyre network:** Enter your networkId as network.fyre.co. This enables other sections within the extension to process properly.
   * **Exclude specific paths:** Enter the name of any paths you want to exclude from using the Livefyre extension.

   ![](https://marketing-stage.adobe.com/resources/help/en_US/livefyre/images/launch-configure.png)

## Use Livefyre Extension with new or existing embeds on a page

After you add the Launch JavaScript to the page, all embeds that currently exist will continue to work and new ones can be added. Every page that the Launch JavaScript \(with Livefyre Extension\) is loaded on automatically loads external Livefyre JavaScript and attempts to load any app embeds that are on the page. If there are none, nothing happens aside other than the additional JavaScript being loaded. To exclude certain pages or groups of pages from automatically loading, use the **Exclude specific paths** option in the Livefyre Extension configuration.

Example of an existing App embed:

```text
<script type="text/javascript" src="https://cdn.livefyre.com/Livefyre.js">
</script><div class="lf-app-embed" data-lf-app="ae260092-4239-43d9-b403-
08b923136701/tagged/published" data-lf-env="qa" data-lf-read-only=""></div>
<script>Livefyre.require(["https://livefyre-cdn-
qa.s3.amazonaws.com/libs/app-embed/v1.0.10/app-embed.min.js"], function 
(appEmbed) {appEmbed.loadAll().done(function(embed) {embed = embed[0];if 
(embed.el.onload && embed.getConfig) 
{embed.el.onload(embed.getConfig());}});});</script>
```

 With the Livefyre Launch extension, this should be simplified to:

```text
<div class="lf-app-embed" data-lf-app="ae260092-4239-43d9-b403-
08b923136701/tagged/published" data-lf-env="prod" data-lf-read-only="">
</div>
```

The `Livefyre.js` script is included in the extension. The `Livefyre.js` script can find all of the embed elements on the page and instantiate the Apps for them.

For information on how to create an App in Adobe Livefyre, see [Create an App](https://marketing.adobe.com/resources/help/en_US/livefyre/c_create_an_app.html).

## Load app rule

1. Click the Property that has the Adobe Launch Livefyre Extension installed.
2. Click the **Rules** tab.
3. Click **Add Rule** \(or click a rule to edit it\).
4. Enter a name for your rule.
5. In the **Events** section, click **Add**.
6. Select **Core** for Extension and **Library Loaded \(Page Top\)** for Event Type.![](https://marketing-stage.adobe.com/resources/help/en_US/livefyre/images/livefyre-launch-rule-event.png)
7.  Click **Keep Changes**.
8. In the **Conditions** section, click **Add**.
9. Select **Regular** for Logic Type, **Core** for Event Type, and **Path Without Query String** for Condition Type.
10.  Specify the path for the page or pages you want the rule to load on.![](https://marketing-stage.adobe.com/resources/help/en_US/livefyre/images/livefyre-launch-rule-condition.png)
11.  Click **Keep Changes**.
12. In the **Actions** section, click **Add**.
13. Select **Adobe Livefyre** under Extension and **Load App** for Action Type.

    The Livefyre extension provides the following actions:

    * **App ID**: Enter the ID of the App to load. The App ID can be found in the Developer Info section of the App. For more information on creating and managing Livefyre Apps, see [Create an App](https://marketing.adobe.com/resources/help/en_US/livefyre/c_create_an_app.html).
    * **Selector**: Enter the CSS selector that identifies an element within the destination page where the app will be loaded.

    ![](https://marketing-stage.adobe.com/resources/help/en_US/livefyre/images/livefyre-launch-rule-action.png)

14. Click **Keep Changes**.
15. Enter a name for the Event Configuration and an order number. Rule order determines which rule runs first when an event is triggered. For more information, see [Rule ordering](../../managing-resources/rules.md#rule-ordering).
16.  Click **Save**.

## Livefyre Extension events

This section describes the event types available in the Livefyre extension.

The Livefyre extension provides the following events in the If portion of a rule:

* **App Initialized**: When an App is included on a page.
* **App Loaded**: When an App was loaded on a page regardless of position.
* **All User Interactions**: A consolidation of all events in the list that are actions users perform.
* **Show Modal**: When a user clicks to view Media Wall content in a larger modal window.
* **Request More Content**: When a user loads more content in an App.
* **Share Button Click**: Any time a user clicks on the share button on an App card.
* **Twitter Retweet Click**: When a user clicks the Twitter Retweet button from an App.
* **Share to Twitter**: When a user clicks the Twitter Like/Favorite button from an App.
* **Share URL**: When Share to URL text area is selected/copied from an App.
* **Twitter Like Click**: When a user clicks the Twitter Like/Favorite button from an App.
* **Twitter Reply Click**: When a user clicks the Twitter Reply button from an App.
* **Share to Facebook**: When Share to Facebook is clicked from an App.

## Enable an Adobe Analytics tracking rule

For more information on using Livefyre with Adobe Analytics and configuring eVars and events, see [Use Livefyre with Adobe Analytics and Dynamic Tag Manager](https://marketing.adobe.com/resources/help/en_US/livefyre/c_use_livefyre_with_adobe_analytics.html).

1. Add an App to a page.For more information on creating and managing Livefyre Apps, see [Create an App](https://marketing.adobe.com/resources/help/en_US/livefyre/c_create_an_app.html).
2. Choose or create a rule for your Property in the Adobe Launch Livefyre Extension to enable Adobe Analytics tracking.
3. Add a Livefyre event \(see list of events above\) which will trigger the Analytics handling.
4. Choose **Adobe Analytics &gt; Set Variables** to configure the Adobe Analytics actions that occur after the events are fired.
5. Set the values to use for eVars and events to determine how you want the reports to work.
6. Set the action to **Adobe Analytics &gt; Send Beacon**. **Note:** Choose `s.tl()` to not treat each triggered action as a page view to keep reported page views in accurate.

