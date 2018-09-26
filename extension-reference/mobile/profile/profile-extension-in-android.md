---
description: >-
  This section helps app developers understand how the Mobile Services SDKs for
  Android interact with Adobe Profile Extension.
---

# Usage Examples for Profile in Android

## Creating a user attribute

For example, you want to update the `userID` of a user that was obtained in the log in page:

```java
UserProfile.updateUserAttribute("userID","Tustin_Jimberlake");
```

## Creating a Batch of User Attributes

For example, a video streaming service wants to store the details of the user's last watched video:

```java
HashMap<String, Object> lastSeenVideo = new HashMap<>();
lastSeenVideo.put("VideoName","Unbreaking Good");
lastSeenVideo.put("Episode",5);
lastSeenVideo.put("DidComplete",false); 
UserProfile.updateUserAttributes(lastSeenVideo);
```

## Updating a User Attribute

Updating a user attribute can be done by calling the public API with the update value for the same key.

For example, a music service wants to update the user type from unsubscribed to premium:

```java
// Creating a user attribute
UserProfile.updateUserAttribute("UserType","Unsubscribed"); 

// Updating a user attribute
UserProfile.updateUserAttribute("UserType","Premium");
```

## Removing User Attribute

To remove an user attribute that has been already set, select one of the following options:

* Option 1: Use the `removeUserAttribute` API with the attribute key that needs to be removed. 
* Option 2: Update the user attribute key with a nil/null value. 

For example, a retail appilication wants to remove the `itemsAddedToCart` user data after the product is purchased:

```java
// Creating a user attribute
UserProfile.updateUserAttribute("itemsAddedToCart","Book: Learn C++ in 5 days");

// Deleting a user attribute
UserProfile.removeUserAttribute("itemsAddedToCart");
UserProfile.updateUserAttribute("itemsAddedToCart", null);
```

