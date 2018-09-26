# Analytics Methods in Android

## trackAction

Actions are the events that occur in your Android app that you want to measure. Each action has one or more corresponding metrics that are incremented each time the event occurs. For example, you might send a `trackAction` call for each new subscription each time an article is viewed, or each time a level is completed.

You must call `trackAction` when an event that you want to track occurs. In addition to the action name, you can send additional context data with each track action call. This method sends an Analytics action tracking hit with optional context data.

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

## trackState

States are the different screens or views in your application. Each time a new state is displayed in your application, for example, when a user navigates from the home page to the news feed, a `trackState` call should be sent. In Android, `trackState` is typically called each time a new activity is loaded. This method sends an Analytics state tracking hit with optional context data.

**Tip**: Calling this API increments page views.

### **Syntax**

```java
public static void trackState(final String state, final Map<String, String> contextData)
```

### Example

```java
Map<String, String> additionalContextData = new HashMap<String, String>();         
additionalContextData.put("customKey", "value");         
MobileCore.trackState("homePage", additionalContextData);
```

## getTrackingIdentifier

Retrieves the analytics tracking identifier generated for this app/device instance.

This is an app-specific, unique visitor ID that is generated at the initial launch and is stored and used after the initial launch.The ID is preserved between app upgrades and is removed when the app is uninstalled.

### Syntax

```java
 public static void 
 getTrackingIdentifier(final AdobeCallback<String> callback)
```

### **Example**

```java
AdobeCallback<String> trackingIdentifierCallback = new AdobeCallback<String>() {
    @Override
    public void call(final String trackingIdentifier) {
        // check the trackingIdentifier value
    }
};
Analytics.getTrackingIdentifier(analyticsTrackingIdentifierCallback);
```

## sendQueuedHits

Forces the library to send all queued hits regardless of the current batch options.

### **Syntax**

```java
public static void sendQueuedHits()
```

### **Example**

```java
Analytics.sendQueuedHits();
```

## clearQueue

Clears all unsent Analytics hits from the tracking queue.

### **Syntax**

```java
public static void clearQueue()
```

### **Example**

```java
Analytics.clearQueue();
```

**Warning:** Use caution when manually clearing the queue. This process cannot be reversed.

## getQueueSize

Retrieves the total number of Analytics hits In the tracking queue.

### Syntax

```java
 public static void getQueueSize(final AdobeCallback<Long> callback)
```

### Example

```java
Analytics.getQueueSize(new AdobeCallback<Long>() {
            @Override
            public void call(final Long queueSize) {
                // handle the queueSize
            }
        });
```

