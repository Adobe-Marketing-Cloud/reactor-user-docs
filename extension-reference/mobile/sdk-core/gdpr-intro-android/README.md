# Privacy and General Data Protection Regulation

The Adobe Experience Cloud Platform SDKs provide General Data Protection Regulation \(GDPR\)-ready APIs for Controllers that allow users to retrieve locally stored identities and set opt status flags for data collection and transmission.

When Adobe provides software and services to an enterprise, Adobe acts as a data processor for any personal data it processes and stores as part of providing these services. As a data processor, Adobe processes personal data in accordance with your company’s permission and instructions \(for example, as set out in your agreement with Adobe\).

As a data controller, you can use the Adobe Experience Cloud Platform SDKs to support GDPR retrieve and delete requests from your mobile apps.

For the Adobe Experience Cloud Platform SDK portions of your mobile apps, you can use the following settings and methods:

* To retrieve data from the SDKs, and send this data to your servers, use the `getSdkIdentities` method.

  For more information, see [Retrieving Stored Identifiers In Android](https://github.com/jiabingeng/sdk-v5-docs/tree/8509ef7d0edcdccfdae5a521cb1fe94693581dba/sdk-core/sdk-core/retr-stored-ids-android.md) or [Retrieving Stored Identifiers in iOS](https://github.com/jiabingeng/sdk-v5-docs/tree/8509ef7d0edcdccfdae5a521cb1fe94693581dba/sdk-core/sdk-core/retr-stored-ids-ios.md).

* To set your opt status and help you with a GDPR data deletion request, use the following settings:

  * `global.privacy` in the ADBMobileConfig.json configuration file
  * `setPrivacyStatus` API method.

  For more information, see [Setting the User's Opt Status in Andriod](https://github.com/jiabingeng/sdk-v5-docs/tree/8509ef7d0edcdccfdae5a521cb1fe94693581dba/sdk-core/sdk-core/set-user-opt-status-android.md) or [Setting the User's Opt Status in iOS](set-user-opt-status-ios.md).

## Additional Information

* For more information about GDPR, see [GDPR and Your Business](https://www.adobe.com/privacy/general-data-protection-regulation.html).
* To see the GDPR API documentation, go to [General Data Protection Regulation API](https://adobe.io/apis/cloudplatform/gdpr.html).

