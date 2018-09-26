# Analytics Methods in iOS

## trackAction

Actions are the events that occur in your Android app that you want to measure. Each action has one or more corresponding metrics that are incremented each time the event occurs. For example, you might send a `trackAction` call for each new subscription, each time an article is viewed, or each time a level is completed.

You must call `trackAction` when an event that you want to track occurs. In addition to the action name, you can send additional context data with each track action call. This method sends an Analytics action tracking hit with optional context data.

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

## trackState

States are the different screens or views in your application. Each time a new state is displayed in your application, for example, when a user navigates from the home page to the news feed, a `trackState` call should be sent. The tracking state name is typically called from a `UIViewController` in the `viewDidLoad` method. This method sends an Analytics state tracking hit with optional context data.

**Tip**: Calling this API will increment page views.

### Syntax

```objectivec
+ (void) trackState: (nullable NSString*) state data: (nullable NSDictionary*) data;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```text
 [ACPCore trackState:@"state name" data:@{@"key":@"value"}];
```

**Swift**

```swift
ACPCore.trackState("state name", data: ["key": "value"])
```

## clearQueue

Clears all hits from the tracking queue and removes the hits from the database.

**Warning**: Use caution when clearing the queue manually because this process cannot be reversed.

### Syntax

```objectivec
+ (void) clearQueue;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPAnalytics clearQueue];
```

**Swift**

```swift
ACPAnalytics.clearQueue()
```

## getQueueSize

Forces the library to send all queued hits regardless of the current batch options.

### Syntax

Here are examples in Objective-C and Swift:

```objectivec
+ (void) getQueueSize: (nonnull void (^) (NSUInteger queueSize)) callback;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPAnalytics getQueueSize: ^(NSUInteger queueSize) {
    // use queue size
}];
```

**Swift**

```swift
ACPAnalytics.getQueueSize({queueSize in
    // use queue size   
})
```

## getTrackingIdentifier

Retrieves the analytics tracking identifier.

### Syntax

```objectivec
+ (void) getTrackingIdentifier: (nonnull void (^) (NSString* __nullable trackingIdentifier)) callback;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPAnalytics getTrackingIdentifier:^(NSString * _Nullable trackingIdentifier) {
    // use returned tracking id
    NSLog(@"Tracking ID : %@", trackingIdentifier);
}];
```

**Swift**

```swift
ACPAnalytics.getTrackingIdentifier({trackingIdentifier in
    // use returned tracking id
}
```

## sendQueuedHits

Regardless of how many hits are currently queued, this method forces the library to send all hits in the offline queue.

**Warning:** Use caution when manually clearing the queue. This process cannot be reversed.

### Syntax

```objectivec
+ (void) sendQueuedHits;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPAnalytics sendQueuedHits];
```

**Swift**

```swift
ACPAnalytics.sendQueuedHits()
```

