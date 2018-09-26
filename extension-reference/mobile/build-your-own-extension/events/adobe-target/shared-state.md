# Shared State

**MODULE\_NAME**: `com.adobe.module.target`

Shared state for this module is updated whenever the ID's are set/reset from either public or target servers.

| Key | Type | Description |
| :--- | :--- | :--- |
| tntid | String | This is the primary identifier in Target for an individual user. Also known as PCID or  mboxPCID.  The `tntId` is not returned in the target API response if a `thirdPartyId` or `experienceCloudVisitorId` is provided in the request. |
| thirdpartyid | String | Client-provided visitor ID for Target. |

