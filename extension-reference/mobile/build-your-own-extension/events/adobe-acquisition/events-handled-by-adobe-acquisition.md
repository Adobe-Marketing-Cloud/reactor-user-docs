# Events Handled by Adobe Acquisition

## Acquistion Request Content

This event will request the Acquisition module to send a Campaign start to the V3 Acquisition server or to track an Adobe deep link. To start processing this event, the handler will check whether it has the `ACQUISITION` event type, the `REQUEST_CONTENT` event source, and the `Map<String, AdobeObject>` event parameter that is not null or empty.

This event is generated in the following scenarios:

* When the public API is used to signal a campaign start.
* When the public API is used to track a deep link.

### Data Payload Definition

Here are the key-value pairs in this event:

#### Campaign Start Event

| **Key + Key Type** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| ADB\_APP\_ID\(String\) | String | False | The app ID. |
| &lt;CUSTOMER\_KEY&gt;\(String\) | String | True | The customer supplied Acquisition data that is sent to the V3 Acquisition server as part of the Campaign start request. |

#### Track Deep Link Event

| **Key + Key Type** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| deepLink \(String\) | String | False | Deep link query parameters as String. |

## Acquistion OS

This event contains the data that is collected from the system during the app launch. depending on how the app is launched, for example, from a deep link, from message click through, or launched from icon tag, different data can be included.

This event is generated during the app launch when the public API gets called with the launch data.

### Data Payload Definition

Here are the key-value pairs in this event:

#### Campaign Start Event

| **Key + Key Type** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| deeplink | String | True | The deep link URL. |
| acquisitiontype | String | True | Indicates whether it is an install or a retention. |
| pushmessageid | String | True | The ID of the push message. |
| notificationid | String | True | The ID of the local notification message. |
| receivedreferrerdata | String | True | The data that is associated with the acquisition. |

