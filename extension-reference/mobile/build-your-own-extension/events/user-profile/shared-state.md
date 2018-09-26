# Shared State

**MODULE\_NAME**: `com.adobe.module.userProfile`

Shared state for this module is updated on the following occasion.

* **On Initialization:** After the module is initialized, it will update the shared state by reading the previously set value from persistence.
* **On Every UserProfile Attribute Create/Update:** Shared stare is update whenever there is a change in the user attribute data either from public API or by other triggers \(Rules Engine\).

| Key | Value Type | Description |
| :--- | :--- | :--- |
| userprofiledata | Map | Map containing all the key-value pairs of the user profile attributes |

**IAM Table**

When the `UserProfile` module receives a request to write to profile for these special keys \(`a.triggered`, `a.clicked`, and `a.viewed`\) , it will update the client-side profile with the count of the number of times this key was seen for each value, which is usually the message ID. It maintains a table and increments the count when each time there is a view/click/ trigger of an In-App Message.

## Data Format

| key | Subkey | messageID | count |
| :--- | :--- | :--- | :--- |
| userProfileData | a.clicked | messageID2 | 3 |
| a.viewed | messageID2 | 4 |  |
| messageID3 | 1 |  |  |
| a.triggered | messageID1 | 5 |  |
| messageID2 | 3 |  |  |
| messageID3 | 4 |  |  |

