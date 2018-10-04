# Identity Methods in Android

## syncIdentifer

Updates the specified customer ID with the Adobe Experience Cloud ID Service.

This API synchronizes the provided customer identifier type key and value with the given [authentication state](identity-methods-in-android.md#authenticationstate) to the Adobe Experience Cloud ID Service. If the specified customer ID type exists in the service, this ID type is updated with the new ID and authentication state. Otherwise, a new customer ID is added. This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall. If the current SDK privacy status is `optedout`, calling this method results in no operations being performed.

### **Syntax**

```java
public static void syncIdentifier(final String identifierType,
                                      final String identifier,
                                      final VisitorID.AuthenticationState authenticationState);
```

### **Example**

```java
Identity.syncIdentifier("idType", "idValue", VisitorID.AuthenticationState.AUTHENTICATED);
```

## syncIdentifiers

Updates the specified customer IDs with the Adobe Experience Cloud ID Service.

This API synchronizes the provided customer identifiers to the Experience Cloud ID Service. If a customer ID type matches an existing ID type, the customer ID type is updated with the new ID value and [authentication state](identity-methods-in-android.md#authenticationstate). New customer IDs are added. These IDs are preserved between app upgrades, are saved and restored during the standard application backup process, and are removed at uninstall. If the current SDK privacy status is `optedout`, calling this method results in no operations being performed.

**Tip**: The `identifiers` map contains IDs with the Identifier type as the key, and the string identifier as the value.

### **Syntax**

```java
public static void syncIdentifiers(final Map<String, String> identifiers,
                                       final VisitorID.AuthenticationState authenticationState)
```

### **Example**

```java
Map<String, String> identifiers = new HashMap<String, String>();
identifiers.put("idType", "idValue");
Identity.syncIdentifier(identifiers, VisitorID.AuthenticationState.AUTHENTICATED);
```

## syncIdentifiers \(overloaded\)

Updates the given customer IDs with the Experience Cloud ID Service.

This API synchronizes the provided customer identifiers to the Experience Cloud ID Service. If a customer ID type matches an existing ID type, the ID type is updated with the new ID value and [authentication state](identity-methods-in-android.md#authenticationstate). New customer IDs are added.

**Tip**: All given customer IDs are given the default authentication state of `UNKNOWN`.

These IDs are preserved between app upgrades, are saved and restored during the standard application backup process, and are removed at uninstall. If the current SDK privacy status is `optedout`, calling this method results in no operations being performed.

**Tip**: The `identifiers` dictionary contains IDs with the Identifier type as the key, and the string identifier as the value.

### **Syntax**

```java
public static void syncIdentifiers(final Map<String, String> identifiers);
```

### Example

```text
Map<String, String> identifiers = new HashMap<String, String>();
identifiers.put("idType", "idValue");
Identity.syncIdentifier(identifiers);
```

## appendVisitorInfoForURL

Appends Adobe visitor data to a URL string. If the provided URL is null or empty, it is returned as is. Otherwise, the following information is added to the url string that is returned in the [AdobeCallback](identity-methods-in-android.md#adobecallback) instance:

* The `adobe_mc` attribute is an URL encoded list containing:
  * Experience Cloud ID \(ECID\)
  * Experience Cloud Org ID
  * A timestamp taken when this request was made
* The optional adobe\_aa\_vid attribute is the URL encoded Analytics Custom Visitor ID, if available

### **Syntax**

```java
public static void appendVisitorInfoForURL(final String baseURL, final AdobeCallback<String> callback);
```

### **Example**

```java
Identity.appendVisitorInfoForURL("http://myurl.com", new AdobeCallback<String>() {
    @Override
    public void call(String urlWithAdobeVisitorInfo) {
        //handle the new URL here
        //For example, open the URL on the device browser
        //
        Intent i = new Intent(Intent.ACTION_VIEW);
        i.setData(Uri.parse(urlWithAdobeVisitorInfo));
        startActivity(i);
    }
});
```

## getIdentifiers

Returns all customer identifiers which were previously synced with the Adobe Experience Cloud.

The values are returned through the [AdobeCallback](identity-methods-in-android.md#adobecallback).

### **Syntax**

```java
public static void getIdentifiers(final AdobeCallback<List<VisitorID>> callback);
```

### **Example**

```java
Identity.getIdentifiers(new AdobeCallback<List<VisitorID>>() {
    @Override
    public void call(List<VisitorID> idList) {
        //Process the IDs here
    }
});
```

## getExperienceCloudId

Retrieves the Experience Cloud ID from the Experience Cloud ID Service.

The Experience Cloud ID is generated at initial launch and is stored and used from that point forward. This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall. The values are returned via the [AdobeCallback](identity-methods-in-android.md#adobecallback).

### **Syntax**

```java
public static void getExperienceCloudId(final AdobeCallback<String> callback);
```

### **Example**

```java
Identity.getExperienceCloudId(new AdobeCallback<String>() {
    @Override
    public void call(String id) {
        //Handle the ID returned here
    }
});
```

## setAdvertisingIdentifier

This API is part of the MobileCore extension. Adobe Identity extension supports the API, and sets the advertising identifier in the SDK.

This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall.

Remember, if the current SDK privacy status is `optedout`, then the advertising identifier is not set.

### **Syntax**

```java
public static void setAdvertisingIdentifier(final String advertisingIdentifier);
```

### **Example**

```java
MobileCore.setAdvertisingIdentifier("advertising_identifier");
```

## setPushIdentifier

This API is part of the MobileCore extension. Adobe Identity extension supports the API, and sets the device token for push notifications in the SDK. If the current SDK privacy status is `optedout`, the push identifier is not set.

### **Syntax**

```java
public static void setPushIdentifier(final String pushIdentifier);
```

### **Example**

```java
//Retrieve the token from either GCM or FCM, and pass it to the SDK
MobileCore.setPushIdentifier(token);
```

## Identity Service Classes

### AdobeCallback

This class provides the interface to receive results when the async APIs perform the requested action. For more information about these methods, see [Identity Service methods in Android](identity-methods-in-android.md#identity-service-methods-in-android).

```java
public interface AdobeCallback<T> {
    void call(final T value);
}
```

### VisitorID

An identifier to be used with the Experience Cloud Visitor ID Service.

```java
public class VisitorID {
    //Constructor
    public VisitorID(String idOrigin, String idType, String id, VisitorID.AuthenticationState authenticationState);

    public VisitorID.AuthenticationState getAuthenticationState();

    public final String getId();

    public final String getIdOrigin();

    public final String getIdType();


}
```

### AuthenticationState

Used to indicate the authentication state for the current `VisitorID`.

```java
public enum AuthenticationState {
        UNKNOWN,
        AUTHENTICATED,
        LOGGED_OUT;
}
```

