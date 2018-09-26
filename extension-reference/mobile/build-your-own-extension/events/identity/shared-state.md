# Shared State

**MODULE\_NAME**: `com.adobe.module.identity`

The Identity module shared state is created at the following times:

* When the module first loads and is initialized
* After setting the user ID \(Visitor ID\)
* When handling a sync request, regardless if the actual sync occurs.   Occurs when setting the push ID, advertising ID, or customer's custom identifiers.
* When a successful sync request occurs, the shared state is updated after receiving a response from the Visitor ID service.

| Key | Value | Type | Description |
| :--- | :--- | :--- | :--- |
| mid |  | String | MID is a unique ID for that visitor for the given Experience Cloud organization ID. |
| vid |  | String | The user identifier. |
| advertisingidentifier |  | String | iOS: the IDFA from retrieved Apple APIsAndroid: The Advertising Identifier that is returned from Google Play Services |
| pushidentifier |  | String | The SHA1 hashed push Identifier |
| blob |  | String | The Blob value |
| locationhint |  | String | The Experience Cloud ID service region ID. A region ID \(or location hint\), is a numeric identifier for the geographic location of a particular ID service data center |
| visitoridslist |  | List/ Array | The list of all the customer's custom identifiers |
| lastsync |  | long | Last timestamp sync with Visitor ID service occured. |

