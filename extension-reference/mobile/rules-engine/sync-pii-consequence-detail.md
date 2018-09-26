# Detail Object for Consequences of the Sync PII

To learn more about Consequences and associated Detail Objects, see [Defining Rules](rules-json.md).

## Object Details

Sync PII object details mirror the [Postback Consequence Detail Definition](postback-consequence-detail.md) with one difference.

| **Friendly Name** | **Key** | **Type** | **Description** |
| :--- | :--- | :--- | :--- |
| Destination URL | templateurl | string | **Required**. Destination URL to which the postback signal will be sent.   **Important**: The URL **must be** HTTPS, and non HTTPS URLs will be ignored. |
| Request Body | templatebody | string | **Optional**. base64-encoded blob that contains the post-body to be sent. If this value exists, the postback will be sent as a `POST`, instead of as a `GET`, request. |
| Content Type | contenttype | string | **Optional**. If this value exists the postback will be sent as a `POST`, instead of as a `GET`, request. If the value is not supplied, but a request body is found, the default will be `application/x-www-form-urlencoded`. |
| Connection Timeout | timeout | number | **Optional**. Timeout for postback connection in seconds. The default value is `2`. |

## Usage Example

```text
"consequences" : [
    {
         "id": "71ae026c-c2ed-482f-9dff-9c0bea03dca1",
          "type": "pii",
          "detail": {
             "templateurl": "https://www.endpoint.com/{%~sdkver%}",
             "templatebody": "{\"allJsonKey\":\"{%~all_json%}\"}",
             "contenttype": "application/json",
             "timeout": 10
          }
     }
]
```

