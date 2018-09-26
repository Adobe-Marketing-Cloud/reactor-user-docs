# Events Handled by Signals

## Rules Content Response

Signals extension listens for Rules Content Response events to process an open URL request, to trigger a postback, or to send personaly identifiable information \(PII\) data to a third-party destination.

### Event Details

| Event Type | Event Source | Paired | Direction |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.rulesEngine | com.adobe.eventSource.responseContent | No | N/A |

For more details on this event, refer [Events Dispatched by SDK Core - Rules Content Response](https://github.com/jiabingeng/sdk-v5-docs/tree/ae885c7e75a70290105e00a6fe48c1a1d321dac7/build-your-own-extension/events/rules-engine/events-dispatched-by-the-rules-engine.html#rules-content-response).

## Configuration Content Response

Signals extension listens for Configuration Content Response events to detect whether the privacy status was changed.

### Event Details

| Event Type | Event Source | Paired | Direction |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.configuration | com.adobe.eventSource.responseContent | No | N/A |

For more details on this event, refer [Events Dispatched by SDK Core - Configuration Response Content](https://github.com/jiabingeng/sdk-v5-docs/tree/ae885c7e75a70290105e00a6fe48c1a1d321dac7/build-your-own-extension/events/sdk-core/events-dispatched-by-sdk-core.html#configuration-response-content).

