# Acquisition Methods in Android

## startCampaign

Allows developers to start an app acquisition campaign as if the user clicked a link. You can create manual acquisition links and handle the app store redirect.

Processes the acquisition campaign start event for the given application ID.

### Syntax

```java
public static void startCampaign(String applicationID, Map<String, String> additionalData)
```

### Example

```java
Acquisition.startCampaign("appId", new HashMap<String, String>() {
    {
        put("key", "value");
    }
});
```

## trackAdobeDeepLink

Allows you to track an Adobe deep link URI.

### Syntax

```java
public static void trackAdobeDeepLink(Uri deepLink);
```

### Example

```java
Uri testUri = new Uri.Builder()
        .appendQueryParameter("a.deeplink.id", "test_deeplinkId")
        .build();
Acquisition.trackAdobeDeepLink(testUri);
```

