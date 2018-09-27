# Events Dispatched by Adobe Audience Manager

## Audience Manager Content Response

The purpose of this event is to:

* Deliver the Audience Manager profile to the original requester.
* Deliver the Audience Manager profile to any module that might be listening for updates.

The event is generated in the following scenarios:

* When a request is made to update the Audience manager profile.
* When a request is made to retrieve the current Audience manager profile.

### Event Details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.audienceManager | com.adobe.eventSource.responseContent | Yes | [Audience Manager Content Request](events-handled-by-adobe-audience-manager.md#audience-manager-content-request) |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| aamprofile | String Map | Yes | The Data payload will contain the Customer key value pairs. The Data Payload will be populated using the CV and CN values in the Audience Manager Stuff array. |

## Audience Manager Identity Response

The purpose of this event is to:

* Deliver the Audience Manager profile to the original requester.
* Deliver the Audience Manager profile to any module that might be listening for updates.

The event is generated in the following scenarios:

* When a request is made to update the Audience manager profile.

### Event Details

| **Event Type** | **Event Source** | **Paired** | **Paired Event** |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.audienceManager | com.adobe.eventSource.responseIdentity | Yes | [Audience Manager Identity  Request](events-handled-by-adobe-audience-manager.md#audience-manager-identity-request) |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| aamprofile | String Map | No | Audience Manager Visitor Profile |

