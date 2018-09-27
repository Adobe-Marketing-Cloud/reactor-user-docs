---
description: Here are the SDK Core methods that are available in Android.
---

# Configuration Methods in Android

## Initial Configuration

### start

Start the Core processing. This should be called after the initial set of extensions have been registered. This call will wait for any outstanding registrations to complete and then start event processing. You can use the callback to kickoff additional operations immediately after any operations kicked off during registration.

### Syntax

```java
public static void start(final AdobeCallback completionCallback)
```

### Example

```java
MobileCore.start(new AdobeCallback() {
    @Override
        public void call(Object value) {
        // do stuff after extensions have finished being registered
    }
});
```

### setApplication

This method must be called in the `onCreate` method of every entry activity, or called it once in the `onCreate` method of your custom Application class.

For example:

```java
public class MyApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        // Lets the Adobe SDK know of the application and initialize itself
        MobileCore.setApplication(this);

    }
}
```

## SDK Settings

### configureWithFileInPath

Allows the caller to pass in a bundled path and file name from which the Adobe Cloud Platform SDKs will attempt to read and use a valid configuration. If the configuration file does not load, no configuration changes are made.

A null file path parameter has no effect.

#### Syntax

```java
void configureWithFileInPath(final String filePath)
```

#### Example

```java
MobileCore.configureWithFileInPath("absolute/path/to/exampleJSONfile.json");
```

### configureWithAppID

After the configuration file is download, it is cached locally. Subsequent requests to this API will use the cached file unless an updated version is detected on the network. The app ID that is passed to this API is stored so that, at relaunch, the Adobe Cloud Platform SDKs configuration is preserved. If the configuration file does not load, no configuration changes are made. A null app ID parameter has no effect.

Indicates to the Adobe Cloud Platform SDKs that the configuration should be downloaded for the given app ID. Behind the scenes, the Adobe Cloud Platform SDKs will retrieve configurations for each module as hosted by Adobe Servers.

#### Syntax

```java
void configureWithAppID(final String appId)
```

#### Example

```java
MobileCore.ConfigureWithAppId("1423ae38-8385-8963-8693-28375403491d");
```

### updateConfiguration

Allows the caller to pass a map of the configuration key-value pairs to override the existing configuration. Keys that are not found in the existing configuration are added. Null values are allowed, and these values remove the configuration parameter.

Values passed to `updateConfiguration` are always applied over the existing or new configuration. For example, calling `updateConfiguration` followed by `ConfigureWithAppId` preserves the changes made in the first `updateConfiguration` call. The key-value pairs that are passed to `updateConfiguration` are stored so that, at relaunch, the SDK configuration is preserved.

A null map parameter has no effect.

#### Syntax

```java
void updateConfiguration(final Map configMap);
```

#### Example

```java
HashMap<String, Object> data = new HashMap<String, Object>();
data.put("global.ssl", true);
data.put("global.timezone", "PDT");
data.put("global.timeoneOffset", -420);
MobileCore.updateConfiguration(data);
```

### setPrivacyStatus

Sets the privacy status for SDK. The set privacy status is preserved and applied over any new configuration changes from calls to `configureWithAppID` or `configureWithFileInPath(String)` even across application restarts. Here are the privacy status values:

* `MobilePrivacyStatus.OPT_IN`, where the hits are sent immediately.
* `MobilePrivacyStatus.OPT_OUT`, where the hits are discarded.
* `MobilePrivacyStatus.UNKNOWN`, where if your report suite is timestamp enabled, hits are saved until the privacy status changes to opt-in \(hits are sent\) or opt-out \(hits are discarded\).

If your report suite is not timestamp enabled, hits are discarded until the privacy status changes to opt in. The default value is set in the ADBMobileConfig.json file.

#### Syntax

```java
public static void setPrivacyStatus(final MobilePrivacyStatus privacyStatus);
```

#### Example

```java
MobileCore.setPrivacyStatus(MobilePrivacyStatus.OPT_OUT);
```

### getPrivacyStatus

Returns the enum representation of the privacy status for current user.

Here are the privacy status values:

* `MobilePrivacyStatus.OPT_IN`, where the hits are sent immediately.
* `MobilePrivacyStatus.OPT_OUT`, where the hits are discarded.
* `MobilePrivacyStatus.UNKNOWN`, where if your report suite is timestamp enabled, hits are saved until the privacy status changes to opt-in \(hits are sent\) or opt-out \(hits are discarded\).

If your report suite is not timestamp enabled, hits are discarded until the privacy status changes to opt in. The default value is set in the ADBMobileConfig.json file.

#### Syntax

```java
void getPrivacyStatus(final AdobeCallback callback);
```

#### Example

```java
MobileCore.getPrivacyStatus(new AdobeCallback<MobilePrivacyStatus>() {
    @Override
    public void call(MobilePrivacyStatus value) {
          System.out.println("getPrivacyStatus: " + status);
    }
});
```

