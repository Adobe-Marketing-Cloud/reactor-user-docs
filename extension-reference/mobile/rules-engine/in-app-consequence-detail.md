# In-App Consequence Detail Definition

To learn more about Consequences and associated Detail Objects, see [Defining Rules](rules-json.md).

## Object Details

The following table provides additional details about this object:

| **Friendly Name** | **Key** | **Type** | **Description** |
| :--- | :--- | :--- | :--- |
| Confirmation URL | url | string | **Optional**. Is only used by alert messages with the `confirm` key.  String that defines the URL to trigger if the **Confirm** button of an alert dialog is triggered. Is typically used for deep-linking scenarios but can also be used to trigger external sites and apps. |
| Confirm Button Text | confirm | string | **Optional**. Is only used by alert messages.  String that defines the text on the **Confirm** button in the OS-operated dialog. |
| Remote assets | remoteAssets | array | **Optional**. Is  only used by fullscreen messages.   Array of strings of remote assets that should be cached by the client. These strings should be full-URL strings with HTTPS transport. When the in-app message is first loaded by the SDK, these assets are downloaded and locally cached. When an in-app message is displayed, a find and replace is done on these URLs in the HTML context, and they are replaced with the locally-cached asset. |
| Category | category | string | _Optional_ and is only used by local notification message type.    A category ID for this notification. |
| Custom User Data | userData | dictionary | _Optional_ and is only used by the local notification message type.   A custom dictionary of key-value pairs that will be attached to the payload of the notification. |
| Deep Link | adb\_deeplink | string | _Optional_ and is only used by the local notification message type.   Deep link URL to attach to the payload of the notification, which allows users who click-through the notification to be redirected to the provided URL. |
| Fire Date | date | number | _Optional_ and is only used by the local notification message type.   Represented as number of seconds since the **Epoch** field indicates a specific time perioid in which to deliver the local notification.    **Tip**: The **Epoch** field has precedence over the **Wait** field. |
| Sound | sound | string | _Optional_ and is only used by the local notification message type.   The name of a custom sound to use when this notification is delivered. |
| Wait Time | wait | number | _Optional_ and is only used by the local notification message type.   Total number of seconds to delay the triggering of a local notification. The default value is  to `0` \(immediate\).     **Tip**: If a date is provided in this detail, the **Wait** field is ignored. |
| Message Content | content | string | _Required_ for alert and local type messages.   String that defines the content of the alert or local notification. |
| Cancel Button Text | cancel | string | _Required_ for the alert message type.   String that defines the text for the **Cancel** button in the OS-operated dialog. |
| Message Title | title | string | _Required_ for the alert message type. String that defines the title of the alert message. |
| Full-screen message | html | string | _Required_ for the full-screen message type.Filename of the HTML content to load for a full-screen, in-app message. This file will be sourced from the same zip file from which the consequence was retrieved in the `assets/` folder. The base path \(`assets/`\) should not be included in this value. |
| In-App Template | template | string | _Required_   Determines the display method of the in-app message. |

The currently supported in-app template types are:

* **fullscreen** is a full-screen takeover experience, where the message's html/css/js content is displayed in an embedded webview.
* **alert** is a system-dialog driven experience.
* **local** is a local notification that behaves like a push notification but is triggered and controlled entirely on the device.

## Usage Examples

The following examples provide a concept of the object, and these objects are full Consequence Objects that contain the detail definitions.

### Fullscreen Message

```text
 {
    "id"        : "48181acd22b3edaebc8a447868a7df7ce629920a",
    "type"      : "iam",
    "detail"    : {
        "template"  : "fullscreen",
        "html"      : "48181acd22b3edaebc8a447868a7df7ce629920a.html"
    }
}
```

### Alert Message

```text
 {
    "id"        : "9d40f5665d5bdbe96dcb3a24f4e4fe98d686a602",
    "type"      : "iam",
    "detail"    : {
        "template" : "alert",
        "title"    : "I interrupted you on purpose.",
        "content"  : "This is an alert dialog message, alerting you to something dialog-worthy.",
        "confirm"  : "Ok",
        "cancel"   : "Cancel",
        "url"      : "myappscheme://launchPage"
    }
}
```

### Local Notification

```text
 {
    "id"        : "71335c64ae133c890603a73fd01f2df70119bb42",
    "type"      : "iam",
    "detail"    : {
        "template"  : "local",
        "content"   : "Welcome to the store!",
        "delay"     : 5
    }
}
```

