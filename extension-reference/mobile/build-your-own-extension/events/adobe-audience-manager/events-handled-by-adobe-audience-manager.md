# Events Handled by Adobe Audience Manager

## Audience Manager Content Request

This event updates the profile for Audience Manager and is generated when the `audienceSignalWithData` API is called to send content to Audience Manager.

### Event Details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.audienceManager | com.adobe.eventSource.requestContent | Yes | [Audience Manager Content Response](events-dispatched-by-adobe-audience-manager.md#audience-manager-content-response) |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key or Key Type** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| aamtraits | String Map | No | The data payload will contain the traits \(key-value pairs\) that were sent by the customer. |

## Audience Manager Identity Request

This event is a request to retrieve the visitor profile from Audience Manager and is generated when the parent application requests audience visitor profile by using the public interface`audienceGetVisitorProfile`

### Event Details

| Event Type | Event Source | Paired | Paired Event |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.audienceManager | com.adobe.eventSource.requestIdentity | Yes | [Audience Manager Identity Response](events-dispatched-by-adobe-audience-manager.md#audience-manager-identity-response) |

### Data Payload Definition

There are no key-value pair for this event:

## Audience Manager Reset Request

This event clears the Audience Manager profile on the device and is generated when the `audienceReset` API is called to clear the Audience Manager profile.

### Event Details

| Event Type | Event Source | Paired | Paired Event |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.audienceManager | com.adobe.eventSource.requestReset | No | N/A |

### Data Payload Definition

There are no key-value pairs in this event.

## Hub Shared State

Audience extension listens for the Configuration Shared State events.

For more details about the Shared State events, see [Events Dispatched by SDK Core - Hub Shared State](../sdk-core/events-dispatched-by-sdk-core.md#hub-shared-state)

## Configuration Content Response

The Audience Manager extension listens for Configuration Content Response events to detect whether the privacy status was changed or the audience configuration was updated.

For more details about the this event, see [Events Dispatched by SDK Core - Configuration Response Content](../sdk-core/events-dispatched-by-sdk-core.md#configuration-response-content)

## Lifecycle Content Response

The Audience Manager extension listens for the Lifecycle Content Response event that is generated when there is a lifecycle session update such as a launch event, upgrade, and so on, and sends a new signal to Audience Manager with the lifecycle context data.

For more details about the this event, see [Events Dispatched by Lifecycle - Lifecycle Response Content](../lifecycle/events-dispatched-by-lifecycle.md#lifecycle-data-content-response).

## Analytics Content Response

Audience Manager listens for Analytics Response events, which are sent when audience forwarding is enabled, processes the events, and extracts the destinations where the new signals will be sent.

For more details about this event, see [Events Dispatched by Analytics - Analytics Response Content](../adobe-analytics/events-dispatched-by-adobe-analytics.md#analytics-content-response).

