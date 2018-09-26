# Profile Consequence Detail Definition

For more information about Consequences and associated Detail Objects, see [Defining Rules](rules-json.md).

## Object Details

| **Friendly Name** | **Key** | **Type** | **Description** |
| :--- | :--- | :--- | :--- |
|  Operation to perform | operation | string |**Required**. Determines the type of operation to be performed on the profile:   **write**, which saves value into given key in shared state and local profile. If an associated value for key already exists, the existing value will be overwritten. **delete**, which removes key from shared state and from local profile. |
| Device-Side Profile Key | Key | String | **Required**. Key In the device-side profile on which to perform the requested operation.This key will be accessible later through the shared state from the UserProfile extension. For more information about how to access the shared state key, see [Matching and retrieving values by keys](rules-json.md). |
| Device-Side Profile Value | value | string or number | **Required** for write operations. New value to write to key. |

Write operation:

```text
"consequences" : [
    {
         "id": "71ae026c-c2ed-482f-9dff-9c0bea03dca1",
          "type": "csp",
          "detail": {
             "operation": "write",
             "key": "UserStateKey",
             "value": "UserStateValue"
          }
     }
]
```

Delete operation:

```text
"consequences" : [
    {
         "id": "71ae026c-c2ed-482f-9dff-9c0bea03dca1",
          "type": "csp",
          "detail": {
             "operation": "delete",
             "key": "UserStateKey"
          }
     }
]
```

