# Setting the User's Opt Status in Android

This information helps you with a GDPR data deletion request.

You can control whether the Analytics, Target, and Audience Manager activity is allowed on a device by using the following settings:

* `global.privacy` in the [Sample JSON File](https://github.com/jiabingeng/sdk-v5-docs/tree/8509ef7d0edcdccfdae5a521cb1fe94693581dba/sdk-core/sdk-core/sample-json-file.md).

  This setting controls the initial setting that persists until it is changed in the code.

* The `MobileCore.setPrivacyStatus` method.

After the privacy setting is changed by using this method, this change remains effective until you change it again, or when you uninstall and reinstall the app. For more information about the methods, see [Configuration Methods in Android](https://github.com/jiabingeng/sdk-v5-docs/tree/8509ef7d0edcdccfdae5a521cb1fe94693581dba/sdk-core/sdk-coare/configuration-methods-in-android/README.md).

Here is some information about each privacy status:

**Opt in**

* Analytics: Hits are sent.
* Target: Mbox requests are sent.
* Audience Manager: Signals and ID syncs are sent.
* Value in the JSON Config: `optedin`
* Value in setPrivacyStatus: `MOBILE_PRIVACY_STATUS_OPT_IN`

**Opt Out**

* Analytics: Hits are discarded.
* Target: Mbox requests are not sent.
* Audience Manager: Signals and ID syncs are not allowed.
* Value in the JSON Config file: `optedout`
* Value in setPrivacyStatus: `MOBILE_PRIVACY_STATUS_OPT_OUT`

**Unknown**

* Analytics: If offline tracking is enabled, hits are saved until the privacy status changes to opt-in \(hits are sent\) or opt-out \(hits are discarded\).  If offline tracking is not enabled, hits are discarded until the privacy status changes to opt-in.
* Target: Mbox requests are not sent, and the default content will be returned.
* Audience Manager: Signals and ID syncs are saved until the privacy status changes to `opt-in` \(hits are sent\) or `opt-out` \(hits are discarded\).
* Value in the JSON Config file: `optunknown`
* Value in setPrivacyStatus: `MOBILE_PRIVACY_STATUS_UNKNOWN`
