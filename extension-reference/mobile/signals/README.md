---
description: This information can help you understand Signals Extension.
---

# Adobe Signals

By leveraging the same triggers and traits that you use to display an in-app message, you can configure the SDK to send customized data to a third-party destination. Also, with the appropriate permissions and configurations, you can use the `collectPii` API to send personally identifiable information \(PII\) to a remote server.

Here are the implications of the privacy status for this extension:

* When the `global.privacy` configuration is set to `optedout`, the Signals extension clears all queued hits and drops future network send requests.
* If the configuration is `optunknown`, the network send requests will be queued on the SDK but are not sent out.
* If the configuration is `optedin`,  the network requests to a third-party destination are allowed, provided the trigger conditions match.

## Additional Information ##

Here is some additional information:

* To install an extension, see [https://docs.adobelaunch.com/managing-resources/extensions](https://docs.adobelaunch.com/managing-resources/extensions).
* For more information about rules and setting conditions, see [https://docs.adobelaunch.com/managing-resources/rules](https://docs.adobelaunch.com/managing-resources/rules).
* For more information about elements, see [https://docs.adobelaunch.com/managing-resources/data-elements](https://docs.adobelaunch.com/managing-resources/data-elements).
* For more information about building your own extension, see [Build your own Extension](../build-your-own-extension/).   
* For more information about events and shared states, see [Events and Shared States](../build-your-own-extension/events/) for each extension.

**Tip**: The keys in the [Events](../build-your-own-extension/events/) section can be used as data elements.

