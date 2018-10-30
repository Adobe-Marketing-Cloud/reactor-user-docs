---
description: 'The following Acquisition methods are provided by the iOS library:'
---

# Acquisition Methods in iOS

## startCampaign :withData:

Processes the acquisition campaign start event for the given application ID.

This method is provided as a way for you to create an acquisition link ad-hoc and is meant to support app-to-app acquisition. The `applicationId` should be that of the targeted destination app. For example, if you are calling this method in app "A", and you deeplink the user into your other app "B", you need to use the `applicationId` for app "B". This method is helpful for creating manual acquisition links and handling the app store redirect yourself, such as with an SKStoreView.

### Syntax

```text
+ (void) startCampaign: (nonnull NSString*) applicationId
    withData: (nullable NSDictionary<NSString*,NSString>) data;
```

### Example

Here are some examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPAcquisition startCampaign:@"testAppId" withData:@{@"a.referrer.campaign.name":@"name", @"a.referrer.campaign.source":@"source"
                                                                        }];
```

**Swift**

```swift
let dict = ["a.referrer.campaign.name":"name", "a.referrer.campaign.source":"source"]
ACPAcquisition.startCampaign("testAppId", withData:dict)
```

## collectLaunchInfo:

Provide user info to the SDK from various launch points in your application. This method should be called to support the following use cases:

* Tracking Deep Link click-throughs
  * From `application:didFinishLaunchingWithOptions`
  * Extract `userInfo` from `UIApplicationLaunchOptionsURLKey`
* Tracking Push Message click-throughs
  * From `application:didReceiveRemoteNotification:fetchCompletionHandler:`
* Tracking Local Notification click-throughs
  * From `application:didFinishLaunchingWithOptions`: \(pre iOS 10\)
    * Extract `userInfo` from `UIApplicationLaunchOptionsLocalNotificationKey`
  * \(pre-iOS 10\) From `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler`:

    If Analytics is enabled in your SDK, the collection of this launch data will result in an Analytics request being sent. Other modules in the SDK might use the collected data, for example, as a rule condition for an In-App Message.

### Syntax

```text
+ (void) collectLaunchInfo: (nonnull NSDictionary*) userInfo;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ADBMobileMarketing collectLaunchInfo:launchOptions];
```

**Swift**

```swift
ADBMobileMarketing.collectLaunchInfo(launchOptions)
```

## **trackAdobeDeepLink:**

Marshalls the provided deepLink and generates an event containing its data.

This method should be called in the `application:openURL:options: app` delegate method. If Analytics is configured in the SDK, calling this method with a valid URL will result in an Analytics request being sent.

### Syntax

```text
+ (void) trackAdobeDeepLink: (nonnull NSURL*) deepLink;
```

### Example

Here are some examples in Objective-C and Swift:

**Objective-C**

```text
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url options:(NSDictionary<NSString *, id> *)options {

    [ACPAcquisition trackAdobeDeeplink:url];
    return YES;
}
```

**Swift**

```swift
    func application(_ app: UIApplication, open url: URL, options: [UIApplicationOpenURLOptionsKey : Any] = [:]) -> Bool {
        ACPAcquisition.trackAdobeDeeplink(url)
    }
```

## **trackNotificationResponse:**

Marshalls the provided `UNNotificationResponse` and generates an event containing its data.

This method should be called to process a user's response to a notification. The SDK will determine if the notification was sent via Push or Local Notification and handle it accordingly. In your `UNUserNotificationCenterDelegate`, you should call this method in the implementation of the `userNotificationCenter:didReceiveNotificationResponse:withCompletionHandler:` delegate method. Though not required, it is recommended that your `UIApplicationDelegate` also be your `UNUserNotificationCenterDelegate`.

### Syntax

```text
+ (void) trackNotificationResponse: (nonnull UNNotificationResponse*) response;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```text
- (void) userNotificationCenter:(UNUserNotificationCenter *)center didReceiveNotificationResponse:(UNNotificationResponse *)response withCompletionHandler:(void (^)(void))completionHandler {
    [ACPAcquisition trackNotificationResponse:response];    
    completionHandler();
}
```

**Swift**

```swift
    func userNotificationCenter(_ center: UNUserNotificationCenter, didReceive response: UNNotificationResponse, withCompletionHandler completionHandler: @escaping () -> Void) {
        ACPAcquisition.trackNotificationResponse(response)
        completionHandler()
    }
```

