# Messaging

In the Adobe Experience Cloud Platform SDKs, messaging is handled with the following components:

* **Rules Engine** Responsible for working with the current hit properties and parsing and handling the configuration file to see which rules matched. This acts as the only source of truth for any other module in the system taking any actions based on these rules being true.
* **Individual messaging modules** Individual modules responsible for handling different features when rules are matched. For example, Messages module will be responsible for actually showing the IAMs that have been triggered by rules.

To configure the Messaging extension in Adobe Launch, see the following sections:

* To install and configure extensions, see [https://docs.adobelaunch.com/managing-resources/extensions](https://docs.adobelaunch.com/managing-resources/extensions).
* For more information rules and conditions, see [https://docs.adobelaunch.com/managing-resources/rules](https://docs.adobelaunch.com/managing-resources/rules).
* For more information about elements, see [https://docs.adobelaunch.com/managing-resources/data-elements](https://docs.adobelaunch.com/managing-resources/data-elements).
* For more information about builidng your own extension, see [Build your own Extension](../build-your-own-extension/).  **Tip**: The keys in the [Events](../build-your-own-extension/events/) section can be used as data elements.

