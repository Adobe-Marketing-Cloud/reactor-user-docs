# Configuration Methods in iOS

## start

Start the Core processing. This should be called after the initial set of extensions have been registered. This call will wait for any outstanding registrations to complete and then start event processing. You can use the callback to kickoff additional operations immediately after any operations kicked off during registration.

### Syntax

```objective-c
+ (void) start: (nullable void (^) (void)) callback;
```

### Example

```objective-c
[ACPCore start:^{
   // do stuff after extensions has finished being registered
}];
```

## 

## configureWithAppID

Indicates to the Adobe Experience Cloud Platform SDKs that the configuration should be downloaded for the given app ID. Behind the scenes, the SDK retrieves configurations for each module as hosted by Adobe Server. After being downloaded, the configuration file is cached locally. Subsequent requests to this API will use the cached file unless an updated version of the config file is detected.

The app ID passed to this API is stored, so that at relaunch, the Adobe Experience Cloud Platform SDKs configuration is preserved. If the config file fails to load, no configuration changes are made.

A null app ID parameter has no effect.

### Syntax

```java
+ (void) configureWithAppId: (NSString* __nullable) appid;
```

### Example

```java
[ACPCore configureWithAppId :@"1423ae38-8385-8963-8693-28375403491d"];
```

## updateConfiguration

Allows the caller to pass a **NSDictionary** or `HashMap` of configuration key value pairs to override the existing configuration. Keys that are not found in the existing configuration are added. Null values are allowed and essentially remove the configuration parameter.

Values that are passed to `updateConfiguration` are always applied over the existing or new configuration. For example, calling `updateConfiguration` followed by `ConfigureWithAppId` will preserve the changes made in the first `updateConfiguration` call. The key-value pairs that are passed to `updateConfiguration` are stored in such a way so, at relaunch, the Adobe Experience Cloud Platform SDK configuration is preserved.

A null map parameter has no effect.

### Syntax

```java
+ (void) updateConfiguration: (NSDictionary* __nullable) config;
```

### Example

```java
NSMutableDictionary *updatedConfig = [NSMutableDictionary dictionary]; 
[contextData setObject:@"newrsid" forKey:@"analytics.rsid"]; 
[ACPCore updateConfiguration:updatedConfig];
```

## configureWithFileInPath

Allows the caller to pass a bundled path and file name that the Adobe Experience Cloud Platform SDKs uses to read and use a valid configuration. If the configuration file could not be loaded, no configuration changes are made.

A null file path parameter has no effect.

### Syntax

```java
+ (void) configureWithFileInPath: (NSString* __nullable) filepath;
```

### Example

```java
NSString *filePath = [[NSBundle mainBundle] pathForResource:@"ExampleJSONFile"ofType:@"json"]; 
[ACPCore configureWithFileInPath:filePath];
```



## setPrivacyStatus

Sets the privacy status for the current user to status.

You can set the privacy status to one of the following values:

* `ACPMobilePrivacyStatusOptIn`, hits are sent immediately.
* `ACPMobilePrivacyStatusOptOut` , hits are discarded.
* `ACPMobilePrivacyStatusUnknown`:
   * If offline tracking is enabled, hits are saved until the privacy status changes to opt-in, and the hits are sent. 

If the privacy status is opt-out, the hits are discarded. If offline tracking is disabled, hits are discarded until the privacy status changes to opt in. Calls to `setPrivacyStatus` have the same effects as a call to `updateConfiguration`. The value set here is stored so that, at relaunch, the privacy status setting is preserved.

### Syntax

```java
+ (void) setPrivacyStatus: (ACPMobilePrivacyStatus) status;
```

### Example

```text
[ACPCore setPrivacyStatus:ACPMobilePrivacyStatusOptIn
```



## getPrivacyStatus

Returns the enum representation of the privacy status for current user.

Here are the privacy status values:

* `ACPMobilePrivacyStatusOptIn`, hits are sent immediately.
* `ACPMobilePrivacyStatusOptOut`,  hits are discarded.
* ACPMobilePrivacyStatusUnknown:
  * If offline tracking is enabled, hits are saved until the privacy status changes to opt-in, and the hits are sent. 
  * If the privacy status is opt-out, the hits are discarded. If offline tracking is disabled, hits are discarded until the privacy status changes to opt in.

The default value is `ACPMobilePrivacyStatusUnknown`.

### Syntax

```java
+ (void) getPrivacyStatus: (nonnull void (^) (ACPMobilePrivacyStatus status)) callback;
```

### Example

```java
[ACPCore 
getPrivacyStatus:^(ACPMobilePrivacyStatus status) { 
     switch (status) { 
          case ACPMobilePrivacyStatusOptIn: NSLog(@"Privacy Status: Opt-In");               break; 
          } 
}];
```

