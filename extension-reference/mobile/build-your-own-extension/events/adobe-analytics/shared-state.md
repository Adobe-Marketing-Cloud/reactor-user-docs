# Shared State

**MODULE\_NAME**: `com.adobe.module.analytics`

Analytics module shares the following properties as a part of the shared state event data:

| Key | Value | Type | Description |
| :--- | :--- | :--- | :--- |
| aid |  | String | Retrieved from the Analytics server if the identity is not enabled. As a fallback, we generate this value locally in the server response is invalid. |

