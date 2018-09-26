# Shared State

MODULE\_NAME: `com.adobe.module.audience`

Shared state for this module is updated on the following occasion.

* **On Initialization:** After the module is initialized, it will update the shared state by reading the previously set value from persistence.
* **On Audience Public API Calls:** The Shared stare is updated when the `submitsignal` API is called.

| Key | Type | Description |
| :--- | :--- | :--- |
| uuid | String | The UUID assigned by the Audience server |
| aamprofile | Dictionary/Map | The matching visitorprofile segments associated with the user |

