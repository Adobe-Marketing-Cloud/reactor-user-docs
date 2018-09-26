# Profile Methods in iOS

# Enabling the UserProfile extension for your app

1. Add the UserProfile library to your project via your `Podfile` by adding `pod 'ACPUserProfile'`

2. Import the UserProfile and Identity library. This can be done in the bridging header if building in Swift.

   ```
   #import <ACPCore_iOS/ACPCore_iOS.h>
   #import <ACPUserProfile_iOS/ACPUserProfile_iOS.h>
   ```

# Register the UserProfile 

**Required**: You must complete the following steps in the app before calling other UserProfile APIs.

1. In your app's `didFinishLaunchingWithOptions` function register the UserProfile  extension.

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  [ACPUserProfile registerExtension];
  // Override point for customization after application launch.
  return YES;
}
```

# Public API

Here are the public API for UserProfile extension:

## updateUserAttribute

Sets the user profile attributes key and value and allows you to create or update a user profile attribute.

Remember the following information:

* If the attribute does not exist, it will be created.
* If the attribute already exists, then the value will be updated.
* A null attribute value will remove the attribute.

### Syntax

```objectivec
+ (void) updateUserAttribute: (nonnull NSString*) attributeName withValue: (nullable NSString*) attributeValue;
```

### Example

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
[ACPUserProfile updateUserAttribute:@"username" withValue:@"Will Smith"];
```

**Swift**

```swift
ACPUserProfile.updateUserAttribute("username", withValue: "Will Smith");
```

## updateUserAttributes

Sets the user profile attributes key and value.

Allows to create/update a batch of user profile attributes:

* String, Integer, Boolean, Double, Array, Map are valid type of user profile attributes.
* We do not allow custom objects to be saved as a `UserProfile` attribute.
* If the attribute already exists, then the value will be updated.
* If the attribute does not exist, it will be created.

A null attribute value will remove the attribute.

### Syntax

```objectivec
+ (void) updateUserAttributes: (nonnull NSDictionary*) attributeMap
```

### **Examples**

Here are examples in Objective-C and Swift:

**Objective-C**

```objectivec
NSMutableDictionary *profileMap = [NSMutableDictionary dictionary];
[profileMap setObject:@"username" forKey:@"will_smith"];
[profileMap setObject:@"usertype" forKey:@"Actor"];
[ACPUserProfile updateUserAttributes:profileMap];
```

**Swift**

```swift
var profileMap = [AnyHashable: Any]()
profileMap["username"] = "will_smith"
profileMap["usertype"] = "Actor"
ACPUserProfile.updateUserAttributes(profileMap)
```

## removeUserAttribute

Removes the user profile attribute for the given key.

### Syntax

```objectivec
+ (void) removeUserAttribute: (nonnull NSString*) key
```

### Example

Here are examples in Objective-C and Swift:

#### Objective-C

```objectivec
[ACPUserProfile removeUserAttribute:@"itemsAddedToCart"];
```

#### Swift

```swift
ACPUserProfile.removeUserAttribute("itemsAddedToCart");
```

