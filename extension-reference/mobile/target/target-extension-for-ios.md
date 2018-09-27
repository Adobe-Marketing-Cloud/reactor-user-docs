# Target Extension for iOS

## Enabling the Target extension for your app

1. Add the Target library to your project via your `Podfile` by adding `pod 'ACPTarget'`
2. Import the Target and Identity library.   
   This can be done in the bridging header if building in Swift.

   ```objectivec
   #import <ACPCore_iOS/ACPCore_iOS.h>
   #import <ACPTarget_iOS/ACPTarget_iOS.h>
   #import <ACPIdentity_iOS/ACPIdentity_iOS.h>
   ```

**Important**: Target depends on the Identity extension. The Identity extension is automatically included in the Mobile Core extension.

## Register the Target and Identity extensions

**Required**: You must complete the following steps in the app before calling other Target APIs.

1. In your app's `didFinishLaunchingWithOptions` function register the Target and Identity extensions:

```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
  [ACPIdentity registerExtension];
  [ACPTarget registerExtension];

  // Override point for customization after application launch.
  return YES;
}
```

## ACPTargetPrefetchObject

This class contains the name of the Target location/mbox and parameter dictionary for mbox parameters, product parameters, and order parameters that will be used in a prefetch:

```objectivec
@interface ACPTargetPrefetchObject : NSObject

///< The name of the Target location/mbox
@property(nonatomic, strong, nullable) NSString* name;

///< Dictionary containing key-value pairs of mbox parameters
@property(nonatomic, strong, nullable) NSDictionary<NSString*, NSString*>* mboxParameters;

///< Dictionary containing key-value pairs of product parameters
@property(nonatomic, strong, nullable) NSDictionary<NSString*, NSString*>* productParameters;

///< Dictionary containing key-value pairs of order parameters
@property(nonatomic, strong, nullable) NSDictionary* orderParameters;
@end
```

The following method can be used to create an instance of a Target prefetch object that might be used to make a batch request to the configured Target server to prefetch content for mbox locations:

```objectivec
+ (nonnull instancetype) prefetchObjectWithName: (nonnull NSString*) name
                                 mboxParameters: (nullable NSDictionary*) mboxParameters;
```

## ACPTargetRequestObject

This class extends `ACPTargetPrefetchObject` by adding default content and a function pointer property that will be used as a callback when requesting content from Target:

```objectivec
@interface ACPTargetRequestObject : ACPTargetPrefetchObject

///< The default content that will be returned if Target servers are unreachable    
@property(nonatomic, strong, nonnull) NSString* defaultContent;

///< Optional. When batch requesting Target locations, callback will be invoked when content is available for this location.
@property(nonatomic, strong, nullable) void (^callback)(NSString* __nullable content);

@end
```

The following method can be used to create an instance of a Target prefetch object that might be used to make a batch request to the configured Target server to prefetch content for mbox locations:

```objectivec
+ (nonnull instancetype) requestObjectWithName: (nonnull NSString*) name
                                defaultContent: (nonnull NSString*) defaultContent
                                mboxParameters: (nullable NSDictionary<NSString*,                                                                     NSString*>*) mboxParameters
                                      callback: (nullable void (^) (NSString* __nullable content)) callback;
```

