# Events Handled by Lifecycle

## Lifecycle Content Request

This event represents a request to the Lifecycle extension to start or pause collecting data and is generated when the `lifecycleStart` and `lifecyclePause` APIs are used.

### Event Details

| Event Type | Event Source | Paired | Direction |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.lifecycle | com.adobe.eventSource.requestContent | No | N/A |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| action | String | No | Represents the lifecycle action type and can be one of these values: `start`/`pause` |
| additionalcontextdata | Map | Yes | Map containing the user supplied context data. |

### Data Sample - Start Lifecycle Request

Here is an example of event data for Lifecycle start request

```javascript
{
    "action": "start",
    "additionalcontextdata":{
        "key1" : "value1",
        "key2" : "value2"
    }
}
```

### Data Sample - Pause Lifecycle Request

```javascript
{
    "action": "pause"
}
```

## Hub Shared State

Lifecycle listens for the Configuration Shared State events.

For more details about the Shared State events, see [Events Dispatched by SDK Core - Hub Shared State](../sdk-core/events-dispatched-by-sdk-core.md#hub-shared-state)

