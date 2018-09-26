# Open URL Consequence Detail Definition

For more information about Consequences and associated Detail Objects, see [Defining Rules](rules-json.md).

## Object Details

| **Friendly Name** | **Key** | **Type** | **Definition** |
| :--- | :--- | :--- | :--- |
| URL | url | string | **Required**. URL that will be opened by the target platform. This might be a URL for a web site or a deeplink to an app. |

## Usage Example

The following example provides a concept of the object, and object is a full Consequence Object that contains the detail definitions.

```text
{
    "id"        : "48181acd22b3edaebc8a447868a7df7ce629920a",
    "type"      : "url",
    "detail"    : {
        "url" : "https://www.endpoint.com/{%~sdkver%}"
    }
}
```

