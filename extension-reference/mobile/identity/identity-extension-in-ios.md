# Identity Extension in iOS

The Experience Cloud ID service provides a universal visitor ID across Experience Cloud solutions. The ID service is required by Analytics for Target, video heartbeat, and so on.

**Tip**: You do not need to populate this ID unless you are using the Experience Cloud ID service. For more information, see [Experience Cloud ID Service](https://marketing.adobe.com/resources/help/en_US/mcvid/).

**Important:** This functionality requires the Adobe Cloud Platform SDKs.

To enable the Experience Cloud ID:

1. Add the library to your project
2. Import the library \(Obj-C\):

   `#import <ACPIdentity_iOS/ACPIdentity_iOS.h>`

3. Register Identity extension in your app's `didFinishLaunchingWithOptions` function:

   ```text
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
     [ACPIdentity registerExtension];

     // Override point for customization after application launch.
     return YES;
   }
   ```

4. Verify that the app configuration contains the experienceCloud org:

   `"experienceCloud.org" : "YOUR-MCORG-ID"`

Experience Cloud organization IDs uniquely identify each client company in the Adobe Experience Cloud and are similar to the following value:

`016D5C175213CCA80A490D05@AdobeOrg`

**Important:** You must include `@AdobeOrg`.

After the configuration is complete, an Experience Cloud ID is generated and is included on all hits. Other IDs, such as custom and automatically-generated IDs, continue to be sent with each hit.

