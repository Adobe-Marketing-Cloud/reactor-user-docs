---
description: >-
  The Audience Manager extension enables data collection and data fetching of
  Adobe Audience Manager.
---

# Adobe Audience Manager

Applications can use this extension to update a user’s audience profile and retrieve the current segments into which a user has fallen. These segments will be shared with the parent application and published for other extensions that might use audience segments.

## Configuring the Audience Manager Extension in Adobe Launch

1. In Launch, click the **Extensions** tab.
2. On the **Installed** tab, locate the **Adobe Audience Manager** extension and click **Configure**.
3. Type the name of the Audience Manager server.
4. Click the up or down arrows and select a timeout value.
5. Click **Save**.

## Additional Information

Here is some additiona linformation:

* To install an extension, see [https://docs.adobelaunch.com/managing-resources/extensions](https://docs.adobelaunch.com/managing-resources/extensions).
* For more information rules and conditions, see [https://docs.adobelaunch.com/managing-resources/rules](https://docs.adobelaunch.com/managing-resources/rules).
* For more information about elements, see [https://docs.adobelaunch.com/managing-resources/data-elements](https://docs.adobelaunch.com/managing-resources/data-elements).
* For more information about builiding your own extension, see [Build your own Extension](../build-your-own-extension/). 
* For more information about events and shared states, see [Events and Shared States](../build-your-own-extension/events/) for each extension.

  **Tip**: The keys in the [Events](../build-your-own-extension/events/) section can be used as data elements.

## Integrating Audience Manager with Analytics

To share the Analytics data with Audience Manager, in the Launch UI in the Analytics extension, select **Automatically share Analytics Data with Audience Manager** and provide the Audience Manager subdomain.

As a prerequisite for using the server side forwarding of Analytics data, you should also have the Identity Service configured in your application configuration.

* For more information, see [Identity Configuration](../identity/).
* For more information about Audience Manager Service, see [Audience Manager](https://marketing.adobe.com/resources/help/en_US/aam/c_am_overview_intro.html).

