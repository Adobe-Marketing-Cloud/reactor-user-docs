---
description: >-
  This section helps app developers understand how the Mobile Services SDKs for
  iOS interact with Adobe Analytics.
---

# Adobe Analytics Extension for Mobile in iOS

## Tracking Apps States in iOS

States are the different screens or views in your application. Each time a new state is displayed in your application, for example, when a user navigates from the home page to the news feed, a track state call should be sent. In iOS, a state is typically tracked in the `viewDidLoad` method of each view.

1. Add the library to your project via your `Podfile` by adding:

   `pod 'ACPAnalytics'`

2. Import the Analytics and Identity library:

   ```objectivec
    #import <ACPCore_iOS/ACPCore_iOS.h>
    #import <ACPAnalytics_iOS/ACPAnalytics_iOS.h>
    #import <ACPIdentity_iOS/ACPIdentity_iOS.h>
   ```

   **Important**:  Analytics depends on the Identity extension and is automatically included in the Core pod. When installing manually, ensure that you have also added the `ACPIdentity.framework` to your project.

3. Register both the Analytics and Identity extensions in  your app's `didFinishLaunchingWithOptions` function.

   ```objectivec
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
       [ACPIdentity registerExtension];
   	[ACPAnalytics registerExtension];
   
     // Override point for customization after application launch.
     return YES;
   } 
   ```

4. Call `[ACPAnalytics trackState: data:]` to send a hit for the state view:

   ```objectivec
   [ACPCore trackState:@"test state" data:nil];
   ```

   The state name is reported in the _View State_ variable, and a view is recorded for each track state call. In other Analytics interfaces, **View State** is reported as **Page Name**, and state views are reported as page views.

5. Send additional data.

   In addition to the state name, you can send additional context data with each track state call:

   ```objectivec
    [ACPCore trackState:@"state name" data:@{@"key":@"value"}];
   ```

## Track App Actions in iOS

Actions are the events that occur in your app that you want to measure. Each action has one or more corresponding metrics that are incremented each time the event occurs. For example, you might track a new subscription, each time an article is viewed, or each time a level is completed. The corresponding metrics for these events are configured as subscriptions, articles read, and levels completed.

Actions are not tracked automatically, so to track an event, you must create call `ACPAnalytics trackAction: data:]` with an action name.

1. Add the library to your project via your `Podfile` by adding:

   `pod 'ACPAnalytics'`

2. Import the Analytics and Identity library:

   ```objectivec
    #import <ACPCore_iOS/ACPCore_iOS.h>
    #import <ACPAnalytics_iOS/ACPAnalytics_iOS.h>
    #import <ACPIdentity_iOS/ACPIdentity_iOS.h>
   ```

   **Important**: Analytics depends on the identity extension and is automatically included in the pod.

3. Register both the Analytics and Identity extensions:

   ```objectivec
    [ACPIdentity registerExtension];
    [ACPAnalytics registerExtension];
   ```

4. When the action that you want to track occurs in your app, call `trackAction` to send a hit for this action:

   ```objectivec
    [ACPCore trackAction:@"action name" data:@{@"key":@"value"}];
   ```

## Hit Batching in iOS

Hit batching allows applications to hold hits from being sent until the number of hits in the queue have exceeded the configured limit.

**Tip**: To use hit batching, you must enable offline tracking.

To enable hit batching, update your configuration and specify a value for `batchLimit`:

```java
{ 
     "analytics.batchLimit”: 5,
      ...
}
```

When the value is greater than 0, the Adobe Cloud Platform SDKs queue the number of hits equal to the `analytics.batchLimit` value. After this threshold is passed, all hits in the queue are sent.

The following methods are used with hit batching:

* `ACPAnalytics.getQueueSize: callback` returns a long with the number of hits currently in the hit batching queue.
* `ACPAnalytics.sendQueuedHits` forces the library to send all hits in the queue no matter how many hits are currently queued.
* `ACPAnalytics.clearQueue` clears all hits from the queue without sending them.

## Video Analytics

The Adobe Experience Cloud Platform SDKs do not have milestone tracking. For more information about video analytics, see [Heartbeat Video Measurement](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/).

