# Retrieving Stored Identifiers in iOS

This information helps you retrieve locally stored, the Adobe Cloud Platform SDKs identities from your iOS app and with GDPR data access requests.

For more information about GDPR, see [GDPR and Your Business](https://www.adobe.com/privacy/general-data-protection-regulation.html).

**Important**: The `getSdkIdentities` method retrieves identities stored in the Adobe Cloud Platform SDKs. You must call this method **before** the user opts-out.

The Adobe Cloud Platform SDKs identities \(as applicable\) are locally stored and returned in a JSON string, which might contain:

* Company Context - IMS Org IDs
* User IDs
* Marketing Cloud ID \(MCID\)
* Integration Codes \(ADID, Push ID\)
* Data Source IDs \(DPID, DPUUID\)
* Analytics IDs \(AVID, AID, VID, and associated RSIDs\)
* Target Legacy IDs \(TNTID, TNT3rdpartyID\)
* Audience Manager ID \(UUID\)

Here is an example of the `[ACPCore getSdkIdentities:]` method in iOS:

```text
[ACPCore getSdkIdentities:^(NSString * _Nullable content){
    NSLog(content);
}];
```

