# Events Dispatched by the Rules Engine

## Rules Content Response

The rules event is used to indicate which rules \(as defined in the configuration\) are matched based on the key values in current hit. Potential listeners, such as the messaging module and postbacks module can handle these events to take the appropriate action.

This event will be generated in the following scenarios:

* When the rules, as defined in the configuration, are downloaded and parsed.
* When the rules, as defined in the messages configuration, are matched.

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key** | **Value Types** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| LoadedConsequence | List&lt;Map&gt; | yes | Loaded Consequence details in the map. |
| TriggeredConsequence | Map&lt;String, Object&gt; | yes | Triggered Consequence details in the map. |

#### Loaded Consequence Definiton

The `LoadedConsequence` key contains a list of consequences, and each item in the list corresponds to the `TriggeredConsequence` definition.

Triggered Consequence Definition

| **Key** | **Value Type** | **Optional** | **Description** |
| :--- | :--- | :--- | :--- |
| id | String | No | String that contains a unique identifier for this consequence.For more information, see [Consequence Object Definition](../../../rules-engine/rules-json.md#consequence-object-definition). |
| type | String | No | A Consequence Type describing the type of consequence.For more information, see [Consequence Object Definition](../../../rules-engine/rules-json.md#consequence-object-definition) |
| detail | Map | No | The detail map that contains the individual definitions of the consequence based on what consequence type it is.For more information, see [Consequence Object Definition](../../../rules-engine/rules-json.md#consequence-object-definition). |

The following consequence types are supported:

| **Name** | **Value** | **Description** |
| :--- | :--- | :--- |
| Analytics | an | Sends data to analytics. |
| In-App Message | iam | In-App Message |
| Postback | pb | Send Postback\(s\) |
| Client Side Profile | csp | Create/Delete operations against Client-Side Profile. |

**Tip**: Third-party extensions can add their own types that will be sent by the Rules Engine.

