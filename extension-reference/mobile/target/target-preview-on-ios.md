# Target Preview on iOS

Target Preview allows you to easily perform end-to-end QA for Target activities and preview these activities on your device.

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://marketing.adobe.com/resources/help/en_US/target/target/target-mobile-preview.html).

## setPreviewRestartDeepLink

Sets an app deepLink that will be triggered when preview selections are applied in the Preview mode.

### Syntax

```objectivec
+ (void) setPreviewRestartDeepLink: (nonnull NSURL*) deepLink;
```

### Examples

Here are some examples using Objective-C and Swift:

**Objective-C**

```objectivec
[ACPTarget setPreviewRestartDeepLink:@"myApp://HomePage"];
```

**Swift**

```swift
ACPTarget.setPreviewRestartDeepLink("myApp://HomePage")
```

