# Identity Methods in iOS

## syncIdentifer

Updates the provided customer ID with the Adobe Experience Cloud ID Service.

This API synchronizes the provided customer identifier type key and value with the provided [authentication state](identity-methods-in-ios.md#adbmobilevisitorauthenticationstate) to the Adobe Experience Cloud ID Service. If this customer ID type exists in the service, this type is updated with the new ID and authentication state. Otherwise a new customer ID is added. This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall. If the current SDK privacy status is `optedout`, calling this method results in no operations being performed.

### **Syntax**

```objectivec
+ (void) syncIdentifier: (nonnull NSString*) identifierType
             identifier: (nonnull NSString*) identifier
         authentication: (ADBMobileVisitorAuthenticationState) authenticationState;
```

### **Examples**

#### Objective-C

```objectivec
[ACPIdentity syncIdentifier:@"idType" identifier:@"idValue" authentication:ACPMobileVisitorAuthenticationStateUnknown];
```

#### Swift

```swift
ACPIdentity.syncIdentifier("idType", identifier: "idValue", authentication: ACPMobileVisitorAuthenticationState.unknown)
```

## syncIdentifiers

Updates the provided customer IDs with the Adobe Experience Cloud ID Service.

This API synchronizes the provided customer identifiers to the Adobe Experience Cloud ID Service. If a customer ID type matches an existing ID type, it is updated with the new ID value and [authentication state](identity-methods-in-ios.md#adbmobilevisitorauthenticationstate). New customer IDs are added. These IDs are preserved between app upgrades, are saved and restored during the standard application backup process, and are removed at uninstall. If the current SDK privacy status is `optedout`, calling this method results in no operations being performed.

**Tip**: The `identifiers` dictionary contains IDs with the Identifier type as the key, and the string identifier as the value.

### **Syntax**

```text
+ (void) syncIdentifiers: (nullable NSDictionary*) identifiers;
```

### **Examples**

#### Objective-C

```objectivec
NSDictionary *ids = @{@"idType":@"idValue"};
[ACPIdentity syncIdentifiers:ids];
```

#### Swift

```swift
let identifiers : [String: String] = ["idType1":"idValue1", "idType2":"idValue2"];
ACPIdentity.syncIdentifiers(identifiers)
```

## syncIdentifiers \(overloaded\)

Updates the provided customer IDs with the Adobe Experience Cloud ID Service.

This API synchronizes the provided customer identifiers to the Adobe Experience Cloud ID Service. If a customer ID type matches an existing ID type, the customer ID is updated with the new ID value and [authentication state](identity-methods-in-ios.md#adbmobilevisitorauthenticationstate). New customer IDs are added. These IDs are preserved between app upgrades, are saved and restored during the standard application backup process, and are removed at uninstall. If the current SDK privacy status is `optedout`, calling this method results in no operations being performed.

**Tip**: The `identifiers` dictionary contains IDs with the Identifier type as the key, and the string identifier as the value.

### **Syntax**

```text
+ (void) syncIdentifiers: (nullable NSDictionary*) identifiers
          authentication: (ACPMobileVisitorAuthenticationState) authenticationState;
```

### **Examples**

#### Objective-C

```objectivec
NSDictionary *ids = @{@"idType":@"idValue"};
[ACPIdentity syncIdentifiers:ids authentication:ACPMobileVisitorAuthenticationStateAuthenticated];
```

#### Swift

```swift
let identifiers : [String: String] = ["idType1":"idValue1", "idType2":"idValue2"];
ACPIdentity.syncIdentifiers(identifiers, authentication: ACPMobileVisitorAuthenticationState.authenticated)
```

## appendToURL

Appends Adobe visitor data to a URL.

If the provided URL is nil or empty, it is returned as is. Otherwise, the following information is added to the url string that is returned via the callback:

* The adobe\_mc attribute is an URL encoded list containing:
  * Experience Cloud ID \(ECID\)
  * Experience Cloud Org ID
  * A timestamp taken when this request was made
* The optional `adobe_aa_vid` attribute is the URL-encoded Analytics Custom Visitor ID, if available.

### **Syntax**

```text
+ (void) appendToUrl: (nullable NSURL*) baseUrl withCallback: (nullable void (^) (NSURL* __nullable urlWithVisitorData)) callback;
```

### **Examples**

#### Objective-C

```objectivec
NSURL* url = [[NSURL alloc] initWithString:@"www.myUrl.com"];
[ACPIdentity appendToUrl:url withCallback:^(NSURL * _Nullable urlWithVisitorData) {
    // handle the appended url here
}];
```

#### Swift

```swift
ACPIdentity.append(to:URL(string: "www.myUrl.com"), withCallback: {(appendedURL) in
    // handle the appended url here
});
```

## getIdentifiers

Returns all customer identifiers which were previously synced with the Adobe Experience Cloud.

### **Syntax**

```text
+ (void) getIdentifiers: (nonnull void (^) (NSArray<ADBMobileVisitorId*>* __nullable visitorIDs)) callback;
```

### **Examples**

#### Objective-C

```objectivec
[ACPIdentity getIdentifiers:^(NSArray<ACPMobileVisitorId *> * _Nullable retrievedVisitorIds) {
    // handle the retrieved Identifiers here     
}];
```

#### Swift

```swift
ACPIdentity.getIdentifiers { (retrievedVisitorIds) in
    // handle the retrieved Identifiers here        
}
```

## getExperienceCloudId

Retrieves the Adobe Experience Cloud Visitor ID from the Adobe Experience Cloud ID Service.

The Experience Cloud ID is generated at initial launch and is stored and used from that point. This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall.

### **Syntax**

```text
+ (void) getExperienceCloudId: (nonnull void (^) (NSString* __nullable experienceCloudId)) callback;
```

### **Examples**

#### Objective-C

```objectivec
[ACPIdentity getExperienceCloudId:^(NSString * _Nullable retrievedCloudId) {
    // handle the retrieved Id here    
}];
```

#### Swift

```swift
ACPIdentity.getExperienceCloudId { (retrievedCloudId) in
    // handle the retrieved Id here    
}
```

## setAdvertisingIdentifier

This API is part of the ACPCore extension. Adobe Identity extension supports the API and sets the advertising identifier in the SDK.

If the IDFA was set in the SDK, the IDFA will be sent in lifecycle. It can also be accessed in Signals \(Postbacks\). This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall.

Remember, if the current SDK privacy status is `optedout`, the advertising identifier is not set.

### **Syntax**

```text
+ (void) setAdvertisingIdentifier: (nullable NSString*) adId;
```

### **Examples**

#### Objective-C

```objectivec
[ACPCore setAdvertisingIdentifier:@"AdvertisingId"];
```

#### Swift

```swift
ACPCore.setAdvertisingIdentifier("AdvertisingId")
```

## setPushIdentifier

This API is part of the ACPCore extension. Adobe Identity extension supports the API, and sets the device token for push notifications in the SDK. If the current SDK privacy status is `optedout`, the push identifier is not set.

### **Syntax**

```java
+ (void) setPushIdentifier: (nullable NSData*) deviceToken;
```

### **Examples**

#### Objective-C

```objectivec
// Set the deviceToken that the APNS has assigned to the device
[ACPCore setPushIdentifier:deviceToken];
```

#### Swift

```swift
// Set the deviceToken that the APNs has assigned to the device
ACPCore.setPushIdentifier(deviceToken)
```

## Identity Service Classes

### ACPMobileVisitorId

An identifier to be used with the Experience Cloud Visitor ID Service.

Contains the origin, the type, a value, and the authentication state of the visitor ID.

```objectivec
@interface ACPMobileVisitorId : NSObject

@property(nonatomic, strong, nullable) NSString* idOrigin;
@property(nonatomic, strong, nullable) NSString* idType;
@property(nonatomic, strong, nullable) NSString* identifier;
@property(nonatomic, readwrite) ACPMobileVisitorAuthenticationState authenticationState;

@end
```

### ACPMobileVisitorAuthenticationState

Used to indicate the authentication state for the current `VisitorID`.

```objectivec
typedef NS_ENUM(NSUInteger, ADBMobileVisitorAuthenticationState) {
    ACPMobileVisitorAuthenticationStateUnknown          = 0,
    ACPMobileVisitorAuthenticationStateAuthenticated    = 1,
    ACPMobileVisitorAuthenticationStateLoggedOut        = 2  
};
```

