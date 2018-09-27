# Prefetch Offer Content in iOS

Adobe Target prefetch uses the Adobe Cloud Platform SDKs to fetch offer content as few times as possible by caching the server responses.

This process reduces the load time, prevents multiple network calls, and allows Adobe Target to be notified which mbox was visited by the mobile app user. All content will be retrieved and cached during the prefetch call, and this content will be retrieved from the cache for all future calls that contain cached content for the specified mbox name.

Prefetch content does not persist across launches. The prefetch content is cached as long as the application lives or until the `clearPrefetchCache()` function is called.

## prefetchContent

Sends a prefetch request to your configured Target server with the `ACPTargetPrefetchObject` array and specified `profileParameters`. The callback will be invoked when the prefetch is complete, which returns a success status for the prefetch request.

### Syntax

```objectivec
+ (void) prefetchContent: (nonnull NSArray<ACPTargetPrefetchObject*>*) targetPrefetchObjectArray
         withProfileParameters: (nullable NSDictionary<NSString*, NSString*>*) profileParameters
                      callback: (nullable void (^) (BOOL success)) callback;
```

### Example

```objectivec
NSDictionary *mboxParameters1 = @{@"status":@"platinum"};
NSDictionary *productParameters1 = @{@"id":@"24D3412",
                                        @"categoryId":@"Books"};
NSDictionary *orderParameters1 = @{@"id":@"ADCKKIM",
                                      @"total":@"344.30",
                                      @"purchasedProductIds":@"34, 125, 99"};

NSDictionary *mboxParameters2 = @{@"userType":@"Paid"};
NSDictionary *productParameters2 = @{@"id":@"764334",
                                         @"categoryId":@"Online"};
NSArray *purchaseIDs = @[@"id1",@"id2"];
NSDictionary *orderParameters2 = @{@"id":@"4t4uxksa",
                                       @"total":@"54.90",
                                       @"purchasedProductIds":purchaseIDs};

// Creating Prefetch Objects
ACPTargetPrefetchObject *prefetch1 = [ACPTargetPrefetchObject prefetchObjectWithName:@"logo" mboxParameters:mboxParameters1];
prefetch1.productParameters = productParameters1;
prefetch1.orderParameters = orderParameters1;

ACPTargetPrefetchObject *prefetch2 = [ACPTargetPrefetchObject prefetchObjectWithName:@"buttonColor" mboxParameters:mboxParameters2];
prefetch2.productParameters = productParameters2;
prefetch2.orderParameters = orderParameters2;

// Creating prefetch Array
NSArray *prefetchArray = @[prefetch1,prefetch2];

// Creating Profile parameters
NSDictionary *profileParameters = @{@"age":@"20-32"};

// Target API Call
[ACPTarget prefetchContent:prefetchArray withProfileParameters:profileParameters callback:^(BOOL isSuccess){
       // do something with the Boolean result
}];
```

## clearPrefetchCache

Clears the data that was cached by Target Prefetch.

### Syntax

```objectivec
+ (void) clearPrefetchCache;
```

### Example

```objectivec
[ACPTarget clearPrefetchCache];
```

