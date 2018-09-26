# Identity Extension in Android

The Experience Cloud ID service provides a universal visitor ID across Experience Cloud solutions. The ID service is required by Analytics for Target, video heartbeat, and so on.

**Tip**: You do not need to populate this ID unless you are using the Experience Cloud ID service. For more information, see the [Experience Cloud ID Service](https://marketing.adobe.com/resources/help/en_US/mcvid/) documentation.

## Configuring Identity in Android

**Important:** This functionality requires SDK Core version 1.0 or later.

**Required:** The `setApplication()` method must be called once in the `onCreate()` method of your main activity. For more details, see [Initial Configuration](https://launch.gitbook.io/marketing-mobile-sdk-v5-by-adobe-documentation/sdk-core/configuration-methods-in-android)

To enable the Experience Cloud ID:

1. Add the library to your project
2. Import the library:

   `import com.adobe.marketing.mobile.*;`

3. Register the Identity extension.

   ```java
   public class MobiletApp extends Application {
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        try {
            Identity.registerExtension();
        } catch (Exception e) {
            //Log the exception
        }
    }
   }
   ```

4. Verify that the app configuration contains the experienceCloud org:

   `"experienceCloud.org" : "YOUR-MCORG-ID"`

Experience Cloud Organization IDs uniquely identify each client company in the Adobe Experience Cloud. Here an example value of `YOUR-MCORG-ID`:`016D5C175213CCA80A490D05@AdobeOrg`

**Important:** You must include `@AdobeOrg`.

After the configuration is complete, an Experience Cloud ID will be generated and, where applicable, be included on all Analytics and Audience Manager hits. Other IDs, such as custom and automatically-generated IDs, will continue to be sent with each hit.

