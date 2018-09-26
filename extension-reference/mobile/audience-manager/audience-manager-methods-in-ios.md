# Audience Manager Methods in iOS

## Configuring Audience Manager in iOS

1. Add the library to your project via your `Podfile` by adding:

   `pod 'ACPAudience'`

2. Import the Audience and Identity library:

   ```objectivec
    #import <ACPCore_iOS/ACPCore_iOS.h>
    #import <ACPAudience_iOS/ACPAudience_iOS.h>
    #import <ACPIdentity_iOS/ACPIdentity_iOS.h>
   ```

   **Important**: Audience Manager depends on the Identity extension and is automatically included in the Core pod. When installing manually, ensure that you have also added the `ACPIdentity.framework` to your project.

3. Register both the Audience and Identity extensions in your app's `didFinishLaunchingWithOptions` function.

   ```objectivec
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
     [ACPIdentity registerExtension];
     [ACPAudience registerExtension];

     // Override point for customization after application launch.
     return YES;
   }
   ```

## getVisitorProfile

Returns the visitor profile that was most recently obtained.

The visitor profile is saved in `NSUserDefaults` for easy access across multiple launches of your app. If no signal has been submitted, `nil` is returned.

### Syntax

```objectivec
+ (void) getVisitorProfile: (nonnull void (^) (NSDictionary* __nullable visitorProfile)) callback;
```

### Example

```objectivec
[ACPAudience getVisitorProfile:^(NSDictionary* visitorProfile){
  // your customized code
}];
```

## reset

Resets the Audience Manager UUID, purges the current visitor profile from `NSUserDefaults`, `reset`, and clears the current in-memory DPID and DPUUID variables.

### Syntax

```objectivec
+ (void) reset;
```

### Example

```objectivec
[ACPAudience reset];
```

## signalWithData:callback:

Sends Audience Manager a signal with traits and returns the matching segments for the visitor in a callback.

Audience manager sends an AAM UUID in a response to the initial signal call. AAM UUID is persisted in `NSUserDefaults` and sent by the SDK in all subsequent signal requests. If available, an Experience Cloud ID \(ECID\) is also sent in each signal request with the DPID and DPUUID. The visitor profile that AAM returns is saved in `NSUserDefaults` and is updated with every signal call.

### Syntax

```objectivec
+ (void) signalWithData: (NSDictionary<NSString*, NSString*>* __nullable) data
                       callback: (nullable void (^) (NSDictionary* __nullable visitorProfile)) callback;
```

### Example

```objectivec
NSDictionary *traits = @{@"key1":@"value1",@"key2":@"value2"};
[ACPAudience signalWithData:traits callback:^(NSDictionary* visitorProfile){
  // your customized code
}];
```

