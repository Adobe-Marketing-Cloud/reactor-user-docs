# Generic APIs in the Core Extension

`ACPCore` on iOS and `MobileCore` on Android provide some APIs that generate events that are dispatched to the Adobe Core eventhub. These APIs provide a standard way to perform the corresponding actions by usng an extension that supports these actions.

By default, the APIs listed here will only generate events. To perform the corresponding action, you need to include and register an extension that supports these events/actions.

## Track Action

The APIs for the corresponding platforms dispatch an event that notifies the Adobe SDK, and any extensions, that you might have enabled a track action, which is being requested. If an extension supports this event, the functionality will be carried out.

### Android

{% tabs %}
{% tab title="Android" %}
213245324234
{% endtab %}

{% tab title="iOS" %}
Sample COnt
{% endtab %}
{% endtabs %}

### Syntax

```java
public static void trackAction(final String action, final Map<String, String> contextData)
```

### Example

```java
Map<String, String> additionalContextData = new HashMap<String, String>();
additionalContextData.put("customKey", "value");
MobileCore.trackAction("loginClicked", additionalContextData);
```

### Android Adobe Extensions that support this API

Ensure that the Analytics extension and the Identity extension are registered **before** this API is called:

```java
Identity.registerExtension();
Analytics.registerExtension();
```

The Analytics extension supports this API.

### iOS

### Syntax

```objectivec
+ (void) trackAction: (nullable NSString*) action data: (nullable NSDictionary*) data;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
 [ACPCore trackAction:@"action name" data:@{@"key":@"value"}];
```

**Swift**

```swift
ACPCore.trackAction("action name", data: ["key": "value"])
```

### iOS Adobe Extensions that support this API

Ensure that the Analytics extension and the Identity extension are registered **before** this API is called:

```text
[ACPIdentity registerExtension];
[ACPAnalytics registerExtension];
```

The Analytics extension supports this API.

## Track State

The APIs for the corresponding platforms dispatch an event that notifies the Adobe SDK, and any extensions, that you might have enabled a track state, which is now being requested. If an extension supports this event, the functionality will be carried out.

### Android

### Syntax

```java
public static void trackState(final String state, final Map<String, String> contextData)
```

### Example

```java
Map<String, String> additionalContextData = new HashMap<String, String>();         
additionalContextData.put("customKey", "value");         
MobileCore.trackState("homePage", additionalContextData);
```

### Android Adobe Extensions that support this API

Ensure that the Analytics extension and the Identity extension are registered **before** this API is called:

```java
Identity.registerExtension();
Analytics.registerExtension();
```

The Analytics extension supports this API.

### iOS

### Syntax

```objectivec
+ (void) trackState: (nullable NSString*) state data: (nullable NSDictionary*) data;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
 [ACPCore trackState:@"state name" data:@{@"key":@"value"}];
```

**Swift**

```swift
ACPCore.trackState("state name", data: ["key": "value"])
```

### iOS Adobe Extensions that support this API

Ensure that the Analytics extension and the Identity extension are registered **before** this API is called:

```text
[ACPIdentity registerExtension];
[ACPAnalytics registerExtension];
```

The Analytics extension supports this API.

## collectPII

The APIs for the corresponding platforms dispatch an event that notifies the Adobe SDK, and any extensions, that you might have enabled a collect PII action to be requested. If an extension supports this event, the functionality will be carried out.

### Android

### Syntax

```java
public static void collectPii(final Map<String, String> data);
```

### Example

```java
Map<String, String> data = new HashMap<String, String>();
data.put("firstname", "customer");
//The rule to trigger a PII needs to be setup for this call
//to result in a network send
MobileCore.collectPii(data);
```

### Android Adobe Extensions that support this API

Ensure that the `Signal` extension is registered before this API is called:

```java
Signal.registerExtension();
```

The Signal extension supports this API.

### iOS

### Syntax

```objectivec
+ (void) collectPii: (nonnull NSDictionary<NSString*, NSString*>*) data;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
 [ACPCore collectPii:@{@"firstname":@"customer"};
```

**Swift**

```swift
let data: NSDictionary = ["firstname": "customer"]
//The rule to trigger a PII needs to be setup for this call
//to result in a network send
ACPCore.collectPii(data as! [String : String])
```

### iOS Adobe Extensions that support this API

Ensure that the `ACPSignal` extension is registered **before** this API is called:

```text
[ACPSignal registerExtension];
```

The Signal extension supports this API.

## Lifecycle Start

The APIs for the corresponding platforms dispatch an event that notifies the Adobe SDK and any extensions that you might have enabled that a application lifecycle start action is being performed. If an extension supports this event, the functionality will be carried out.

### Android

### Syntax

```java
public static void lifecycleStart(final Map<String, String> additionalContextData)
```

### Example

```java
Map<String, String> additionalContextData = new HashMap<String, String>();
additionalContextData.put("myapp.type", "example");
MobileCore.lifecycleStart(additionalContextData);
```

### Android Adobe Extensions that support this API

Ensure that the Lifecycle extension is registered **before** this API is called:

```java
Lifecycle.registerExtension();
```

The `Lifecycle` extension supports this API.

### iOS

### Syntax

```objectivec
+ (void) lifecycleStart: (nullable NSDictionary<NSString*, NSString*>*) additionalContextData;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
NSDictionary* additionalContextData = @{@"myapp.type":@"example"};
[ACPCore lifecycleStart:additionalContextData];
```

**Swift**

```swift
var additionalContextData = [String: String]()
additionalContextData["myapp.type"] = "example"
ACPCore.lifecycleStart(additionalContextData)
```

### iOS Adobe Extensions that support this API

Ensure that the Lifecycle extension is registered **before** this API is called:

```text
[ACPLifecycle registerExtension];
```

The Lifecycle extension supports this API.

## Lifecycle Pause

The APIs for the corresponding platforms dispatch an event that notifies the Adobe SDK, and any extensions, that you might have enabled a application lifecycle pause action is to be performed. If an extension supports this event, the functionality will be carried out.

### Android

### Syntax

```java
public static void lifecyclePause()
```

### Example

```java
MobileCore.lifecyclePause();
```

### Android Adobe Extensions that support this API

Ensure that the Lifecycle extension is registered **before** this API is called:

```java
Lifecycle.registerExtension();
```

The Lifecycle extension supports this API.

### iOS

### Syntax

```objectivec
+ (void) lifecyclePause;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPCore lifecyclePause];
```

**Swift**

```swift
ACPCore.lifecyclePause()
```

### iOS Adobe Extensions that support this API

Ensure that the Lifecycle extension is registered **before** this API is called:

```text
[ACPLifecycle registerExtension];
```

The Lifecycle extension supports this API.

## Set Advertising Identifier

The APIs for the corresponding platforms dispatch an event that notifies the Adobe SDK, and any extensions, that you might have enabled a platform advertising identifier to be available. If an extension supports this event, the the identitifer will be used according to the extension.

### Android

### Syntax

```java
public static void setAdvertisingIdentifier(final String advertisingIdentifier);
```

### Example

```java
MobileCore.setAdvertisingIdentifier("advertising_identifier");
```

### Android Adobe Extensions that support this API

Ensure that the Identity extension is registered **before** this API is called:

```java
Identity.registerExtension();
```

The Identity extension supports this API.

### iOS

### Syntax

```objectivec
+ (void) setAdvertisingIdentifier: (nullable NSString*) adId;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPCore setAdvertisingIdentifier:@"AdvertisingId"];
```

**Swift**

```swift
ACPCore.setAdvertisingIdentifier("AdvertisingId")
```

### iOS Adobe Extensions that support this API

Ensure that the `Identity` extension is registered **before** this API is called:

```java
[ACPIdentity registerExtension];
```

The Identity extension supports this API.

## Set Push Identifier

The APIs for the corresponding platforms dispatch an event that notifies the Adobe SDK and any extensions that you might have enabled that a platform push identifier is available. If an extension supports this event then, the the identitifer will be used as per the extension.

### Android

### Syntax

```java
public static void setPushIdentifier(final String pushIdentifier);
```

### Example

```java
//Retrieve the token from either GCM or FCM, and pass it to the SDK
MobileCore.setPushIdentifier(token);
```

### Android Adobe Extensions that support this API

The `Identity` extension supports this API. Ensure that the `Identity` and `Analytics` extensions are registered before this API is called:

```java
Identity.registerExtension();
Analytics.registerExtension();
```

### iOS

### Syntax

```objectivec
+ (void) setPushIdentifier: (nullable NSData*) deviceToken;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
// Set the deviceToken that the APNS has assigned to the device
[ACPCore setPushIdentifier:deviceToken];
```

**Swift**

```swift
// Set the deviceToken that the APNs has assigned to the device
ACPCore.setPushIdentifier(deviceToken)
```

### iOS Adobe Extensions that support this API

Ensure that the `Identity` and `Analytics` extensions are registered **before** this API is called:

```java
[ACPIdentity registerExtension];
[ACPAnalytics registerExtension];
```

The Identity extension supports this API.

