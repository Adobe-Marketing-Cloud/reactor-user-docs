# Retrieving Stored Identifiers in Android

This information helps you retrieve the locally stored Adobe Experience Cloud Platform SDKs identities from your Android app and with GDPR data access requests.

**Important**: The `getSdkIdentities` method retrieves identities stored in the SDK. You must call this method **before** the user opts-out.

SDK identities \(as applicable\) are locally stored and returned in a JSON string, which might contain:

* Company Context - IMS Org IDs
* User IDs
* Marketing Cloud ID \(MCID\)
* Integration Codes \(ADID, Push ID\)
* Data Source IDs \(DPID, DPUUID\)
* Analytics IDs \(AVID, AID, VID, and associated RSIDs\)
* Target Legacy IDs \(TNTID, TNT3rdpartyID\)
* Audience Manager ID \(UUID\)

Here is an example of the `MobileCore.getSdkIdentities()` method in Android:

```java
MobileCore.getSdkIdentities(new AdobeCallback<String>() {
    @Override
    public void call(String value) {
        // handle the json string
    }
});
```

