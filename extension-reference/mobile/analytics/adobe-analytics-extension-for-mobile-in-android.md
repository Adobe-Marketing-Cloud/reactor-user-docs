---
description: >-
  This section helps app developers understand how the Mobile Services SDKs for
  Android interact with Adobe Analytics.
---

# Analytics Extension for Mobile in Android

## Tracking App States in Android

States are the different screens or views in your application. Each time a new state is displayed in your application, for example, when a user navigates from the home page to the news feed, a`trackState()` call is sent.

1. Add the library to your project.
2. Import the library:

   `import com.adobe.marketing.mobile.*;`

3. Register both the Analytics and Identity extensions:

   ```java
   public class MobileApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Analytics.registerExtension();
            Identity.registerExtension();
        } catch (Exception e) {
            //Log the exception
        }
    }
   }
   ```

   **Important**: Analytics depends on the Identity extension and is automatically included in Core. When installing the SDK manually, ensure that you download and add the Identity extension to your project.

4. Call the `trackState()` method to send a hit for this state view:

   ```java
   MobileCore.trackState("homePage", null);
   ```

5. Send additional data.

   In addition to the state name, you can send additional context data with each track state call:

   ```java
     Map<String, String> additionalContextData = new HashMap<String, String>();         
     additionalContextData.put("customKey", "value");         
     MobileCore.trackState("homePage", additionalContextData);
   ```

## Tracking App Actions in Android

Actions are events that occur in your application that you want to measure. The corresponding metrics will be incremented each time the event occurs. For example, you might want to track when a user clicks the **Log in** button or when an article was viewed.

1. Add the library to your project.
2. Import the library:

   `import com.adobe.marketing.mobile.*;`

3. Register both the Analytics and Identity extensions:

   ```java
    Identity.registerExtension();
    Analytics.registerExtension();
   ```

   **Important**: Analytics depends on the Identity extension and is automatically included in Analytics.

4. When the action that you want to track occurs in your app, call `trackAction()` to send a hit for this action:

   ```java
   MobileCore.trackAction("loginClicked", null);
   ```

5. Send additional data.

   In addition to the action name, you can send additional context data with each track action call:

   ```java
   Map<String, String> additionalContextData = new HashMap<String, String>();
   additionalContextData.put("customKey", "value");
   MobileCore.trackAction("loginClicked", additionalContextData);
   ```

## Hit Batching in Android

Hit batching allows applications to hold hits from being sent until the number of hits in the queue have exceeded the configured limit.

**Tip**: To use hit batching, you must enable offline tracking.

To enable hit batching, update your configuration and specify a value for `batchLimit`:

```java
{ 
     "analytics.batchLimit”: 5,
      ...
}
```

When the value is greater than 0, the Adobe Experience Cloud Platform SDKs queue the number of hits equal to the `analytics.batchLimit` value. After this threshold is passed, all hits in the queue are sent.

The following methods are used with hit batching:

* `Analytics.getQueueSize` returns the total number of hits currently in the queue in a callback.
* `Analytics.sendQueuedHits` forces the library to send all hits in the queue no matter how many hits are currently queued.
* `Analytics.clearQueue` clears all hits from the queue without sending them.

## Video Analytics

The Adobe Experience Cloud Platform SDKs do not have milestone tracking. For more information about video analytics, see [Heartbeat Video Measurement](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/).

