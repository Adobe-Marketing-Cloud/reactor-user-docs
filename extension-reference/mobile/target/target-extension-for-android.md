# Target Extension for Android

## Enabling the Target Extension for your App

1. Add the Target library to your project using the app's gradle file.
2. Import the Target library \(and any other SDK library\) in your application's main activity.

   ```java
   import com.adobe.marketing.mobile.*;
   ```

**Important**: Target depends on the Identity extension, and the Identity extension is automatically included in the Mobile Core extension.

## Set the Application Context and Register the Target and Identity Extensions

**Required:** The `setApplication()` method must be called once in the `onCreate()` method of your main activity. For more details, see [Initial Configuration](../sdk-core/configuration-methods-in-android.md)

1. The Target and Identity extensions must be registered with the SDK core before calling any Target API.

   This may be done after calling the `setApplication()` method in the `onCreate()` method. Here is code sample which calls these setup methods:

   ```java
   public class TargetApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);

        try {
            Target.registerExtension();
            Identity.registerExtension();
        } catch (Exception e) {
            //Log the exception
        }
    }
   }
   ```

## Public Classes

Here are the public classes in the Target extension:

### TargetRequest

Here is a code sample for this class in Android:

```java
public class TargetRequest extends TargetObject {

    private TargetRequest() {}

    /**
    * Builder used to construct a TargetRequest object.
    */
    public static class Builder {
        private TargetRequest targetRequest;

        /**
         * Create a TargetRequest Builder.
         *
         * @param mboxName String mbox name for this request
         * @param defaultContent String default content for this request
         */
        public Builder(final String mboxName, final String defaultContent);

        /**
         * Set mbox parameters for this request.
         *
         * @param mboxParameters Map<String, String> mbox parameters
         * @return this builder
         */
        public Builder setMboxParameters(final Map<String, String> mboxParameters);

        /**
        * Set order parameters for this request.
        *
        * @param orderParameters Map<String, Object> order parameters
        * @return this builder
        */
        public Builder setOrderParameters(final Map<String, Object> orderParameters);

        /**
         * Set profile parameters for this request.
         *
         * @param productParameters Map<String, String> product parameters
         * @return this builder
         */
        public Builder setProductParameters(final Map<String, String> productParameters);

        /**
        * Set the callback function for this request.
        *
        * @param contentCallback AdobeCallback<String> which will get called with the returning content
        * @return this builder
        */
        public Builder setContentCallback(final AdobeCallback<String> contentCallback);

        /**
         * Build the TargetRequest.
         *
         * @return TargetRequest the target request object
         */
        public TargetRequest build();
    }
}
```

### TargetPrefetch

Here is a code sample for this class in Android:

```java
public class TargetPrefetch extends TargetObject {
    private TargetPrefetch() {}

    /**
     * Builder used to construct a TargetPrefetch object
     */
    public static class Builder {
        private TargetPrefetch targetPrefetch;

        /**
         * Create a TargetPrefetch Builder.
         *
         * @param mboxName String mbox name for this request
         */
         public Builder(final String mboxName);

        /**
         * Set mbox parameters for this request.
         *
         * @param mboxParameters Map<String, String> mbox parameters
         * @return this builder
         */
         public Builder setMboxParameters(final Map<String, String> mboxParameters);

        /**
         * Set order parameters for this request.
         *
         * @param orderParameters Map<String, String> order parameters
         * @return this builder
         */
         public Builder setOrderParameters(final Map<String, Object> orderParameters);

        /**
         * Set product parameters for this request.
         *
         * @param productParameters Map<String, String> product parameters
         * @return this builder
         */
         public Builder setProductParameters(final Map<String, String> productParameters);

        /**
         * Build and return TargetPrefetch
         *
         * @return TargetPrefetch the target prefetch object
         */
         public TargetPrefetch build();
    }

}
```

