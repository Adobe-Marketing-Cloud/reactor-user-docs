---
description: >-
  This section helps app developers understand how the Mobile Services SDKs for
  Android interact with Adobe Profile Extension.
---

# Usage Examples for Profile in iOS

## Creating a User Attribute

For example, you want to update the `userID` of a user that was obtained in the log in page:

**Objective-C Example**

```objectivec
[ACPUserProfile updateUserAttribute:@"userID" withValue:@"Tustin_Jimberlake"];
```

**Swift Example**

```swift
ACPUserProfile.updateUserAttribute("userID", withValue: "Tustin_Jimberlake");
```

## Creating a Batch of User Attributes

For example, a video streaming service wants to store the details of the last watched video of the user:

**Objective-C Example**

```objectivec
NSMutableDictionary *lastSeenVideo = [NSMutableDictionary dictionary];
[lastSeenVideo setObject:@"Unbreaking Good" forKey:@"VideoName"];
[lastSeenVideo setObject:@(5) forKey:@"Episode"];
[lastSeenVideo setObject:@(false) forKey:@"DidComplete"]; 

[ACPUserProfile updateUserAttributes:lastSeenVideo];
```

**Swift Example**

```swift
var lastSeenVideo = [AnyHashable: Any]()
lastSeenVideo["Unbreaking Good"] = "VideoName"
lastSeenVideo["Episode"] = 5
lastSeenVideo["DidComplete"] = false
ACPUserProfile.updateUserAttributes(lastSeenVideo)
```

## Updating a User Attribute

Updating a user attribute can be done by calling the public API with the update value for the same key.

For example, a music service wants to update the user type from unsubscribed to premium:

**Objective-C Example**

```text
// Creating a user attribute
[ACPUserProfile updateUserAttribute:@"UserType" withValue:@"Unsubscribed"];


// Updating a user attribute
[ACPUserProfile updateUserAttribute:@"UserType" withValue:@"Premium"];
```

**Swift Example**

```text
// Creating a user attribute
ACPUserProfile.updateUserAttribute("UserType", withValue: "Unsubscribed");

// Updating a user attribute
ACPUserProfile.updateUserAttribute("UserType", withValue: "Premium");
```

## Removing an User Attribute

To remove an user attribute that has been already set, select one of the following options:

* Option 1: Use the `removeUserAttribute` API with the attribute key that needs to be removed. 
* Option 2: Update the user attribute key with a nil/null value. 

For example, a retail appilication wants to remove the `itemsAddedToCart` user data after the product is purchased:

**Objective-C Example**

```text
// Creating a user attribute
[ACPUserProfile updateUserAttribute:@"itemsAddedToCart" withValue:@"Book: Learn C++ in 5 days"];


// Deleting a user attribute
[ACPUserProfile removeUserAttribute:@"itemsAddedToCart"];
[ACPUserProfile updateUserAttribute:@"itemsAddedToCart" withValue:nil];
```

**Swift Example**

```objectivec
// Creating a user attribute
ACPUserProfile.updateUserAttribute("itemsAddedToCart", withValue: Book: Learn C++ in 5 days);


// Deleting a user attribute
ACPUserProfile.removeUserAttribute("itemsAddedToCart");
ACPUserProfile.updateUserAttribute("itemsAddedToCart", withValue: nil);
```

