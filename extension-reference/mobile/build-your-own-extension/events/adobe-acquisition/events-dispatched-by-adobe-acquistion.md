# Events Dispatched by Adobe Acquistion

## Acquisition Content Response

This event is a response from the Acquistion module to notify the acquisition data.

This event is generated in the following scenarios:

* During the app launch when the public API gets called with the launch data.
* When the public API is used to track a deep link.

### Data Payload Definition

Here is the definition of the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| contextdata | Map | No | The acquisition data. |

## Analytics Content Request

This event is a request to Analytics to track the click-through data.

This event will be generated when:

* The app is launched from a push message click through.
* The app is launched from a local notification click through.

### Data Payload Definition

Here is the definition of the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| action | String | No | The action name for push message click through or local notification click through. |
| trackinternal | Bool | No | The value is always `true`. |
| contextdata | Map | No | The data needs to be tracked by Analytics. |

