---
description: This information can help you understand the Identity Extension.
---

# Adobe Identity

The Identity extension allows your app to communicate with the Experience Cloud ID Service, and this interaction will primarily be in sync with the customer identifiers.

## Configuring the Identity Extension in Adobe Launch

1. In Launch, click the Extensions tab.
2. On the **Installed** tab, locate the **Identity** extension and click **Configure**.
3. Select the Advertising ID Enabled checkbox. 
4. Type the name of your Experience Cloud Server.
5. Verify that your Experience Cloud ID is correct. 
6. Click **Save**.

## Additional Information

Here is some additional information:

* To install an extension, see [https://docs.adobelaunch.com/managing-resources/extensions](https://docs.adobelaunch.com/managing-resources/extensions).
* For more information rules and conditions, see [https://docs.adobelaunch.com/managing-resources/rules](https://docs.adobelaunch.com/managing-resources/rules).
* For more information about elements, see [https://docs.adobelaunch.com/managing-resources/data-elements](https://docs.adobelaunch.com/managing-resources/data-elements).
* For more information about building your own extension, see [Build your own Extension](../build-your-own-extension/). 
* For more information about events and shared states, see [Events and Shared States](../build-your-own-extension/events/) for each extension.

**Tip**: The keys in the [Events](../build-your-own-extension/events/) section can be used as data elements.

## Integrating with Analytics

For Analytics to use the ID generated for Experience Cloud, the Experience Cloud ID Service extension needs to be configured in the Launch UI. This integration will enable the SDK to send the Experience Cloud Organization ID and any customer identifiers with your Analytics hits.

