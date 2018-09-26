# Target Methods in iOS

## getThirdPartyId

Gets the custom visitor ID for Target. The callback will be invoked to return the `thirdPartyId` value, or if no third-party ID is set, `nil` is returned.

### Syntax

```objectivec
+ (void) getThirdPartyId: (nonnull void (^) (NSString* __nullable thirdPartyId)) callback;
```

### Examples

Here are the examples in Objective C and Swift:

#### **Objective C**

```objectivec
[ACPTarget getThirdPartyId:^(NSString *thirdPartyId){
       // read thirdPartyId
  }];
```

#### **Swift**

```swift
ACPTarget.getThirdPartyId({thirdPartyID in   
    // read thirdPartyId
 })
```

## setThirdPartyId

Sets the custom visitor ID for Target. This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall or when `resetExperience` API is called.

### Syntax

```objectivec
+ (void) setThirdPartyId: (nullable NSString*) thirdPartyId;
```

### Examples

Here are some examples in Objective-C and Swift:

#### **Objective-C**

```objectivec
[ACPTarget setThirdPartyId:@"third-party-id"];
```

**Swift**

```swift
ACPTarget.setThirdPartyId("third-party-id")
```

## resetExperience

Resets the user's experience by removing the visitor identifiers. This method also removes previously set third-party and Target IDs from persistent storage.

### Syntax

```text
+ (void) resetExperience;
```

### Examples

Here are some examples in Objective-C and Swift:

#### **Objective-C**

```objectivec
[ACPTarget resetExperience];
```

#### **Swift**

```swift
ACPTarget.resetExperience()
```

## getTntId

Gets the Target user identifier. The callback will be invoked to return the `tntId` value, or if no Target ID is set, `nil` is returned.

Target returns `tntId` upon a successful call to `loadRequests` or `prefetchContent`. Once set in SDK, this ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall or when `rResetExperience` API is called.

### Syntax

```objectivec
+ (void) getTntId: (nonnull void (^) (NSString* __nullable tntId)) callback;
```

### **Examples**

Here are some examples in Objective-C and Swift:

#### **Objective-C**

```objectivec
[ACPTarget getTntId:^(NSString *tntId){
       // read target's tntId
  }];
```

#### **Swift**

```swift
ACPTarget.getTntId({tntId in   
    // read target's tntId
 })
```

## loadRequests

Sends a batch request to your configured Target server for multiple mbox locations that are specified in the`ACPTargetRequestObject` array. Each object in the array contains a callback function, which will be invoked when content is available for its given mbox location.

### Syntax:

```objectivec
+ (void) loadRequests: (nonnull NSArray<ACPTargetRequestObject*>*) requests
      withProfileParameters: (nullable NSDictionary<NSString*, NSString*>*) profileParameters;
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

ACPTargetRequestObject *request1 = [ACPTargetRequestObject requestObjectWithName:@"logo" defaultContent:@"BlueWhale" mboxParameters:mboxParameters1 callback:^(NSString *content){
        // do something with the received content
  }];
request1.productParameters = productParameters1;
request1.orderParameters = orderParameters1;


ACPTargetRequestObject *request2 = [ACPTargetRequestObject requestObjectWithName:@"buttonColor" defaultContent:@"red" mboxParameters:mboxParameters2 callback:^(NSString *content){
        // do something with the received content
}];
request2.productParameters = productParameters1;
request2.orderParameters = orderParameters1;

// create request object array
NSArray *requestArray = @[request1,request2];

// Creating Profile parameters
NSDictionary *profileParameters = @{@"age":@"20-32"};

// Call the API
[ACPTarget loadRequests:requestArray withProfileParameters:profileParameters];
```

## locationClicked

Sends a click notification to configured Target server for a prefetched or regular mbox location. Click metric should be enabled for the provided location name in Target. If notification is sent for a prefetched mbox, its contents should already have been requested with `loadRequests` indicating that the mbox was viewed.

### Syntax:

```objectivec
+ (void) locationClickedWithName: (nonnull NSString*) name mboxParameters: (nullable NSDictionary<NSString*, NSString*>*) mboxParameters productParameters: (nullable NSDictionary<NSString*, NSString*>*) productParameters orderParameters: (nullable NSDictionary*) orderParameters profileParameters: (nullable NSDictionary<NSString*, NSString*>*) profileParameters;
```

### Example

```objectivec
// Define Mbox parameters
NSDictionary *mboxParameters = @{@"membership":@"prime"};

// Define Product parameters
NSDictionary *productParameters = @{@"id":@"CEDFJC",
                                    @"categoryId":@"Electronics"};
// Define Order parameters
NSDictionary *orderParameters = @{@"id":@"NJJICK",
                                    @"total":@"650",
                                    @"purchasedProductIds":@"81, 123, 190"};

// Define Profile parameters
NSDictionary *profileParameters = @{@"ageGroup":@"20-32"};

[ACPTarget locationClickedWithName:@"cartLocation" mboxParameters:mboxParameters productParameters:productParameters orderParameters:orderParameters profileParameters:profileParameters];
```

