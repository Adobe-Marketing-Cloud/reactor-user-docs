# Profile Methods in Android

# Enabling the UserProfile Extension for your App

1. Add the UserProfile library to your project using the app's gradle file.

2. Import the UserProfile library (and any other SDK library) in your application's main activity.

   ```
   import com.adobe.marketing.mobile.*;
   ```

# Set the Application Context and Register the UserProfile Extensions

**Required:** The `setApplication()` method must be called once in the `onCreate()` method of your main activity. For more details, see [Initial Configuration](https://launch.gitbook.io/marketing-mobile-sdk-v5-by-adobe-documentation/sdk-core/configuration-methods-in-android)

1. The UserProfile extensions must be registered with the SDK core before calling any Target API.

   This may be done after calling the `setApplication()` method in the `onCreate()` method. Here is code sample which calls these setup methods:



   ```
   public class MobileApp extends Application {
   
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
   
        try {
            UserProfile.registerExtension();
        } catch (Exception e) {
            //Log the exception
        }
    }
   }
   ```

#  

# Public Classes

Here are the public classes in the UserProfile extension: 

## updateUserAttribute

Allows you to create/update a batch of user profile attributes:

* If the attribute does not exist, it will be created.
* If the attribute exists, the value will be updated. 
* A null attribute value removes the attribute.

### Syntax

```java
public static void updateUserAttribute(String attributeName, 
                                       Object attributeValue)
```

### Example

```java
UserProfile.updateUserAttribute("username", "Will Smith");
```

## updateUserAttributes

Sets the user profile attributes key and value.

Allows you to create/update a batch of user profile attributes:

* String, Integer, Boolean, Double, Array, Map are valid type of user profile attributes.
* We do not allow custom objects to be saved as a `UserProfile` attribute.
* If the attribute does not exist, it will be created.
* If the attribute already exists, then the value will be updated. 
* A null attribute value will remove the attribute.

### Syntax

```java
public static void updateUserAttributes(Map<String, Object> attributeMap)
```

### Example

```java
HashMap<String, Object> profileMap = new HashMap<>();
profileMap.put("username","Will Smith");
profileMap.put("usertype","Actor");
UserProfile.updateUserAttributes(profileMap);
```

## removeUserAttribute

Removes the given attribute name.

### Syntax

```java
public static void removeUserAttribute(String attributeName)
```

### Example

```java
UserProfile.removeUserAttribute("itemsAddedToCart");
```

