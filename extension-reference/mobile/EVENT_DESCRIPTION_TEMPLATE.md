---
description: This page contains tips&templates about the event page structure.
---

# Event Description Template

**Note:** This page contains tips&templates about the event page structure. 

Currently the events are splitted into two markdown files for each module - one is for the events dispatched by a specific module and one is for the events handled by the module (dispatched by the same module/another module). E.g.:

- events-dispatched-by-adobe-analytics.md
- events-handled-by-adobe-analytics.md

## Event dispatched by this module

### Event Description

Describe the situations when this event will be generated. You can use plain text or bullet points to enumerate them:

- mention any public API call that can generate this event
- rule match
- configuration update etc

### Event Details

| **Event Type**                                        | **Event Source**                                        | **Paired**                                                   | **Paired Event**                                             |
| :---------------------------------------------------- | :------------------------------------------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| com.adobe.eventType.exampleType                       | com.adobe.eventSource.exampleSource                     | Yes / No                                                     | [Link To The Paired Event](../link/to/the/eventpage/andsection) |
| event type value exactly as it is represented in code | event source value exactly as it is represented in code | Indicates if this event is a request/response for another event | Link to the git book page where the event is described       |

### Data Payload Definition

Here are the key-value pairs in this event:

| **Key**                                                      | **Value Type**                    | **Optional**                                                 | **Description**               |
| :----------------------------------------------------------- | :-------------------------------- | :----------------------------------------------------------- | :---------------------------- |
| example.key                                                  | String/ Bool/ Map<String, String> | Yes / No                                                     | Short description of this key |
| Event data key exactly as it is used in the code (case sensitive) | Event Data value type             | Indicates if this key may be meesing from the event in some situations |                               |

### Event Data Example

```json
{
    "example.key": {
        "key1" : "string",
        "key2" : 124
    },
    "second.key": false
}
```

## Handling events dispatched by another module

Short description about why this module listens for this event and a link to the detailed description of this event. This way we won't duplicate documentation about the same event in multiple modules and when an event is changed, the information will be updated ascross modules.

For more details about the this event see  [Link to the event page](../example/path)