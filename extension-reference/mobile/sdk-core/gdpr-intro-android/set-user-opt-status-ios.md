# Setting the User's Opt Status in iOS

This information helps you with a GDPR data deletion request.

You can control whether Analytics, Target, and Audience Manager activity is allowed on a device by using the following settings:

* `global.privacy` in the [Sample JSON File](https://github.com/jiabingeng/sdk-v5-docs/tree/8509ef7d0edcdccfdae5a521cb1fe94693581dba/sdk-core/sdk-core/sample-json-file.md).

  This setting controls the initial setting that persists until it is changed in code.

* `setPrivacyStatus` method.

After the privacy setting is changed by using this method, this change remains effective until you change it again, or when you uninstall and reinstall the app. For more information about the methods, see [Configuration Methods in iOS](https://github.com/jiabingeng/sdk-v5-docs/tree/8509ef7d0edcdccfdae5a521cb1fe94693581dba/sdk-core/sdk-coare/configuration-methods-in-ios/README.md).

The following table describes each privacy status:

**Opt in**

* Analytics: Hits are sent.
* Target: Mbox requests are sent.
* Audience Manager: Signals and ID syncs are sent.
* Value in the JSON Config: `optedin`
* Value in setPrivacyStatus: `ADBMobilePrivacyStatusOptIn`

**Opt Out**

* Analytics: Hits are discarded.
* Target: Mbox requests are not sent.
* Audience Manager: Signals and ID syncs are not allowed.
* Value in the JSON Config: `optedout`
* Value in setPrivacyStatus: `ADBMobilePrivacyStatusOptOut`

**Unknown**

* Analytics: If offline tracking is enabled, hits are saved until the privacy status changes to opt-in \(hits are sent\) or opt-out \(hits are discarded\).  If offline tracking is not enabled, hits are discarded until the privacy status changes to opt-in.
* Target: Mbox requests are not sent, and the default content will be returned..
* Audience Manager: Signals and ID syncs are saved until the privacy status changes to `opt-in` \(hits are sent\) or `opt-out` \(hits are discarded\).
* Value in the JSON Config file: `optunknown`
* Value in setPrivacyStatus: `ADBMobilePrivacyStatusOptUnknown`