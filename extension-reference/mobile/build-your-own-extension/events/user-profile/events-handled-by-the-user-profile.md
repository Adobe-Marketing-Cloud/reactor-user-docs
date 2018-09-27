# Events Handled by the User Profile

## USER\_PROFILE : REQUEST\_PROFILE

The event is used to put a user profile attribute update action on the Event Hub. This will be consumed by the [User Profile](https://wiki.corp.adobe.com/display/ADMSMobile/V5+Module+-+User+Profile) module.

This event will be generated iwhen an `updateUserAttribute` call is made by the SDK client.

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| userprofileupdatekey | Map&lt;String, Object&gt; | no | A map of all the attributes and the attribute values that the client wants to update/add to the User Profile that is managed by the Adobe Cloud Platform SDK. An existing attribute name will end up updating the attribute in the SDK, and a new attribute name will add a new attribute to the profile.The value of an attribute can be null, in which case the attribute will be deleted from the profileCurrently supported object types are String, Integer, Double, Boolean, Map and VectorAll the other types will be ignored while processing |

### Example

Here is a code sample of the `USER_PROFILE : REQUEST_PROFILE` event:

```text
{
    EventName : "UserProfileUpdate"
    EventType : "com.adobe.eventType.userProfile",
    EventSource : "com.adobe.eventSource.requestProfile",
    EventData: {
            "userProfileupdatekey":
                     {
                        "userName": "JohnDoe",
                        "creditPoints": 255,
                        "isPaidUser": true
                     }
                }
}
```

## USERPROFILE : REQUEST\_RESET {#title-text}

This event clears the specified key from the User Profile extension and is generated when the `removeUserAttributes` public API is called.

### Data Payload Definition

| Key/Key Type | Value Type | Optional | Description |
| :--- | :--- | :--- | :--- |
| userprofileremovekey | String | No | The attribute key which has to be deleted |

### Example

Here is a code sample of the `USERPROFILE : REQUEST_RESET` event:

```text
{
    EventName : "RemoveUserProfile"
    EventType : "com.adobe.eventType.userProfile",
    EventSource : "com.adobe.eventSource.requestReset",
    EventData: {
                "userprofileremovekey": "userName"
               }
}
```

