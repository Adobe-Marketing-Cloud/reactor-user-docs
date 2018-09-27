# Events Handled by the Rules Engine

## Rules Content Request

The rules event is used to indicate the `downloadRules` API call. This event is listened to and handled by the Rules Engine extension.

This event will be generated in the Core extension when the `downloadRules` API is called.

### Data Payload Definition

Here are the key-value pairs in this event:

| Key | Value Type | Optional | Description |
| :--- | :--- | :--- | :--- |
| RULES\_REQUEST\_CONTENT\_DOWNLOAD\_RULES\("download\_rules"\) | boolean | Yes | Key that indicates that the Request Content event is specifically for the module to download rules from the rules url that is present in the latest configuration. |

## Configuration Response Content

The data property in the Configuration Response Content event is used by each module to modify its current settings. Each module is responsible to read out the part of the data property for which it is concerned.

This event will be generated in the following scenarios:

* By the initial config that is requested by the customer.
* When the configuration is modified as the result of a remote update or a local developer action.
* In response to a configuration request event with the `config.getData` data key.

### Data Payload Definition

Here are the key-value pairs in this event:

| **Extension** | **Key** | **Value Type** | **Description** |
| :--- | :--- | :--- | :--- |
| **Acquisition** | acquisition.appid | string | Application ID assigned by the Adobe Cloud Platform SDKs |
|  | acquisition.server | string | Server address for the fingerprinter. |
| **Analytics** | analytics.aamForwardingEnabled | boolean | If set to true, Analytics data collection servers will attempt to forward data to Audience Manager on the back end. |
|  | analytics.batchLimit | number | Indicates to Analytics the number of hits that should be stored until they are all sent in succession. |
|  | analytics.offlineEnabled | boolean | If set to true, Analytics will store its data even while the device is offline. |
|  | analytics.referrerTimeout | number | Amount of time the Analytics module will wait for acquisition data prior to sending an install hit |
|  | analytics.rsids | string | Contains a comma-delimited list of report suites to which the Analytics data should be sent |
|  | analytics.server | string | Contains the server endpoint used to collect Analytics data for this customer's report suite. |
| **Audience Manager** | audience.server | string | Contains the server endpoint used to collect Audience Manager data. |
|  | audience.timeout | number | Amount of time, in seconds, to wait for a response from Audience Manager before timing out. |
| **Campaign** | campaign.pkey | string | App Identifier in the Campaign database |
|  | campaign.server | string | Contains the server endpoint used to communicate with Campaign. |
| **Global** | global.privacy | string | Contains the default setting that the user has request with regards to data privacy. |
|  | global.ssl | boolean | If set to true, network requests should be dispatched via HTTPS. If false, network requests should be dispatched via HTTP. |
| **Identity** | experienceCloud.org | string | Experience Cloud Org Identifier |
|  | experienceCloud.server | string | Custom endpoint to be used for Visitor ID Service network requests. |
|  | identity.adidEnabled | boolean | If set to true, indicates that the SDK should expect a call to `setAdvertisingIdentifier` . |
| **Lifecycle** | lifecycle.backdateSessionInfo | boolean | If set to true, Analytics requests containing session info or crash events will be backdated to one second after the last hit was sent. If false, this data will be attached to the first hit of the subsequent session. |
|  | lifecycle.sessionTimeout | number | Number of seconds since the user background the app that must pass in order for the subsequent app launch \(or resume\) to be considered a new lifecycle session. |
| **Rules Engine** | rules.url | string\[\] | List of Rules endpoints \(represented as strings\), in order of preference. |
| **Target** | target.clientCode | string | Special identifier given to the customer by the Target product. |
|  | target.environmentId | string | Indicates the Environment ID for the Target customer. |
|  | target.timeout | string | Amount of time, in seconds, to wait for a response from Target before timing out. |

## WildCard Listener

Wildcard Listeners are responsible for ingesting all events that flow through the Event Hub and for passing these events to the associated service.

