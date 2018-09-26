# Events Dispatched by SDK Core

## Configuration Response Content

The data property in this event is used by each module to modify its current settings. Each module is responsible to read out the part of the data property for which it is concerned.

This event will be generated in the following scenarios:

* Initial config requested by the customer
* Configuration modified \(remote update or local developer action\)
* In response to a configuration request event with data key `config.getData`

### Data Payload Definition

Here are the key-value pairs in this event:

| **Extension** | **Key** | **Value Type** | **Description** |
| :--- | :--- | :--- | :--- |
| **Analytics** | analytics.aamForwardingEnabled | boolean | If set to `true`, Analytics data collection servers will attempt to forward data to Audience Manager on the back end. |
|  | analytics.batchLimit | number | Indicates to Analytics the number of hits that should be stored until these hits are sent in succession. |
|  | analytics.offlineEnabled | boolean | If set to `true`, Analytics will store its data when the device is offline. |
|  | analytics.referrerTimeout | number | Amount of time the Analytics module will wait for acquisition data before sending an install hit. |
|  | analytics.rsids | string | Contains a comma-delimited list of report suites to which the Analytics data should be sent. |
|  | analytics.server | string | Contains the server endpoint used to collect Analytics data for this customer's report suite. |
| **Audience Manager** | audience.server | string | Contains the server endpoint used to collect Audience Manager data. |
|  | audience.timeout | number | Amount of time, in seconds, to wait for a response from Audience Manager before timing out. |
| **Campaign** | campaign.pkey | string | App Identifier in the Campaign database. |
|  | campaign.server | string | Contains the server endpoint used to communicate with Campaign. |
| **Global** | global.privacy | string | Contains the default setting that the user requested regarding data privacy. |
|  | global.ssl | boolean | If set to `true`, network requests should be dispatched with HTTPS. If `false`, network requests should be dispatched with HTTP. |
| **Identity** | experienceCloud.org | string | Experience Cloud Org Identifier |
|  | experienceCloud.server | string | Custom endpoint to be used for Visitor ID Service network requests. |
|  | identity.adidEnabled | boolean | If set to `true`, indicates that the Mobile SDK should expect a call to `setAdvertisingIdentifier`. |
| **Lifecycle** | lifecycle.backdateSessionInfo | boolean | If set to `true`, Analytics requests that contain session info or crash events will be backdated to one second after the last hit was sent. If `false`, this data will be attached to the first hit of the subsequent session. |
|  | lifecycle.sessionTimeout | number | Number of seconds since the user backgrounded the app, so that a  subsequent app launch \(or resume\)  will be considered a new lifecycle session. |
| **Rules Engine** | rules.url | string\[\] | List of Rules endpoints that are represented as strings, in the order of preference. |
| **Target** | target.clientCode | string | Special identifier given to the customer by Target. |
|  | target.environmentId | string | Indicates the Environment ID for the Target customer. |
|  | target.timeout | string | Amount of time, in seconds, to wait for a response from Target before timing out. |

## Configuration Request Content

The purpose of this event is to allow the end user to specify to the SDK from where it should retrieve a JSON definition of its configuration. The event is triggered by the developer by using the public APIs. This event results in the Configuration module publishing a [Configuration Response Content](events-dispatched-by-sdk-core.md#configuration-response-content) event.

This event will be generated in the following scenarios:

* `SetAppId` API, when the customer requests that the configuration is loaded by using the application identifier.
* `ConfigureWithFileInPath` API, when the customer requests that the configuration be loaded by using the local file.
* `UpdateConfiguration` API, when the customer requests updates to specific configuration parameters.
* `SetPrivacyStatus` API, which calls `UpdateConfiguration`.
* `GetPrivacyStatus` API, when customer requests the currently configured `global.privacy` parameter.
* Internally when the `start` method is called to request that the configuration is refreshed by the application identifier.
* Internally by a `LIFECYCLE` event type and a `REQUEST_CONTENT` source to request that the configuration is refreshed by the application identifier.

### Data Payload Definition

Each of the data payload keys in the table should use the _config_ prefix. All of the possible keys in the payload are optional, but at least one key must be present so that the SDK Core extension can fetch a configuration.

The underlying methods prioritize each option in the following order:

1. Application ID
2. File Path
3. Configuration Update
4. Retrive Config

Here are the key-value pairs in this event:

| **Name** | **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- | :--- |
| Application ID | config.appId | string | true | The Application ID given to this app by A**dobe Mobile Services**. The Configuration Module attempts to retrieve the SDK configuration from a remote server that is owned and maintained by Adobe for the provided _appId._ |
| File Path | config.filePath | string | true | A path and file name from which the Configuration Module will attempt to retrieve and SDK configuration.   The path is absolute. |
| Configuration Update | config.update | Map | true | A Hashmap with the parameters that needs to be updated in the Configuration. |
| Retrieve Config | config.getData | Boolean | true | A request for a [Configuration Response Content](https://launch.gitbook.io/marketing-mobile-sdk-v5-by-adobe-documentation/~/edit/drafts/-LLAyhl1fBC81Z6OmIeS/build-your-own-extension/events/sdk-core/events-dispatched-by-sdk-core#configuration-response-content) event with the SDK's current configuration. |

## Hub Shared State

The shared state event is dispatched by the event hub after a shared state is created or updated. The event data contains the event owner and the name of the module to which the shared state belongs.

### Event Details

| Event Type | Event Source | Paired | Direction |
| :--- | :--- | :--- | :--- |
| com.adobe.eventType.hub | com.adobe.eventSource.sharedState | No | N/A |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| stateowner | String | No | The name of the module that owns this shared state and generates a new state or updates an existing state. |

## Analytics Track request

This event is dispatched to track analytics action and state.

#### Event Details

| **Event Type** | **Event Source** | **Paired** |
| :--- | :--- | :--- |
| com.adobe.eventType.generic.track | com.adobe.eventSource.requestContent | No |

#### Data Payload Definition

The payload definition is composed of the following:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| action | String | Yes | The action name value. |
| state | String | Yes | The state name value. |
| contextdata | Map&lt;String, String&gt; | Yes | The additional context data parameters. |

## Lifecycle Request

This event is dispatched to notify the SDK about a lifecycle start or pause

### Event Details

| Event Type | Event Source | Paired |
| :--- | :--- | :--- |
| com.adobe.eventType.generic.lifecycle | com.adobe.eventSource.requestContent | No |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| action | String | No | Represents the lifecycle action type and can be one of these values: `start`/`pause` |
| additionalcontextdata | Map | Yes | Map containing the user supplied context data. |

## Identity Request

This event is dispatched to notify the SDK about new Push Identifiers or Advertising Identifier changes

### Event Details

| Event Type | Event Source | Paired |
| :--- | :--- | :--- |
| com.adobe.eventType.generic.identity | com.adobe.eventSource.requestContent | No |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| pushid | String | Yes |  |
| advertisingid | String | Yes |  |

## Collect PII Request

This event is dispatched to notify the SDK of a collect PII request

### Event Details

| Event Type | Event Source | Paired |
| :--- | :--- | :--- |
| com.adobe.eventType.generic.pii | com.adobe.eventSource.requestContent | No |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| contextdata | String | No | Map containing the user supplied context data. This field is required. |

