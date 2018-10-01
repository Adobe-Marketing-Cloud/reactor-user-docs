# Audience Manager Methods in Android

The Adobe Cloud Platform SDKs currently supports multiple Adobe Cloud Solutions, including Analytics, Target, Audience Manager, and the Experience Cloud ID Service.

If Audience Manager is configured in your JSON file, a signal that contains lifecycle metrics is sent with your lifecycle hit.

## Configuring Audience Manager in Android

**Required:** The `setContext()` method must be called once in the `onCreate()` method of your main activity. For more details, see [Initial Configuration](../../../client-side-information/mobile/sdk-core/configuration-methods-in-android.md)

**Tip**: If you already added this method call when you implemented Analytics or Target, you do not need to add it again.

1. Add the library to your project.
2. Import the library:

   `import com.adobe.marketing.mobile.*;`

3. Register both the Audience and Identity extensions:

   ```java
   public class AudiencetApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Audience.registerExtension();
            Identity.registerExtension();
        } catch (Exception e) {
            //Log the exception
        }
    }
   }
   ```

   **Important**: Audience Manager depends on the Identity extension and is automatically included in Core. When installing the SDK manually, ensure that you download and add the Identity extension to your project.

## Audience Manager Methods

### signalWithData

Sends a signal with traits to Audience Manager and gets the matching segments returned in a block callback.

Audience manager sends the UUID in response to initial signal call. The UUID is persisted in `SharedPreferences` and is sent by the SDK in all subsequent signal requests. If you are using the Experience Cloud ID Service, the Experience Cloud ID \(ECID\) and other `customerID`s for the same visitor are also sent in each signal request with the DPID and the DPUUID. The visitor profile that Audience Manager returns is saved in `SharedPreferences` and is updated with every signal call.

#### Syntax

```java
public static void signalWithData(final Map<String, String> data, final AdobeCallback<Map<String, String>> callback)
```

#### Example

```java
AdobeCallback<Map<String, String>> visitorProfileCallback = new AdobeCallback<Map<String, String>>() {
    @Override
    public void call(final Map<String, String> visitorProfile) {
        // your own customized code
    }
};

Map<String, String> traits = new HashMap<String, String>();
traits.put("trait", "xyz");
Audience.signalWithData(traits, visitorProfileCallback);
```

### reset

Resets the Audience Manager UUID and purges the current visitor profile. `reset` also clears the current in-memory DPID and DPUUID variables.

#### Syntax

```java
public static void reset()
```

#### Example

```java
Audience.reset();
```

### getVisitorProfile

Returns the visitor profile that was most recently obtained.

The visitor profile is saved in `SharedPreferences` for easy access across multiple launches of your app. If no audience signal has beed submitted, `null` is returned.

#### Syntax

```java
public static void getVisitorProfile(final AdobeCallback<Map<String, String>> adobeCallback)
```

#### Example

```java
AdobeCallback<Map<String, String>> visitorProfileCallback = new AdobeCallback<Map<String, String>>() {
    @Override
    public void call(final Map<String, String> visitorProfile) {
        // your own customized code
        }
    };
Audience.getVisitorProfile(visitorProfileCallback);
```

