# Postback Consequence Detail Definiton

For more information about Consequences and associated Detail Objects, see [Defining Rules](rules-json.md).

## Object Details

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Friendly Name</b>
      </th>
      <th style="text-align:left"><b>Key</b>
      </th>
      <th style="text-align:left"><b>Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Destination URL</td>
      <td style="text-align:left">templateurl</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left"><b>Required</b>. Destination URL to which the postback signal will be
        sent.</td>
    </tr>
    <tr>
      <td style="text-align:left">Request Body</td>
      <td style="text-align:left">templatebody</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p><b>Optional</b>. A string that contains the post-body to be sent. If this
          value exists, the postback will be sent as a <code>POST</code>, instead
          of a <code>GET</code>, request.</p>
        <p><b>Tip</b>: If necessary, the string should be appropriately json escaped.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Content Type</td>
      <td style="text-align:left">contenttype</td>
      <td style="text-align:left">string</td>
      <td style="text-align:left"><b>Optional</b>. If this value exists, the postback will be sent as a <code>POST</code>,
        instead of a <code>GET</code>, request. If the value is not supplied, but
        a request body is found, the default is <code>application/x-www-form-urlencoded</code>.</td>
    </tr>
    <tr>
      <td style="text-align:left">Connection Timeout</td>
      <td style="text-align:left">timeout</td>
      <td style="text-align:left">number</td>
      <td style="text-align:left"><b>Optional</b>. Timeout for postback connection in seconds. The default
        value is <code>2</code>.</td>
    </tr>
  </tbody>
</table>## Usage Examples

The objects in the following usage examples are full Consequence Objects that contain the detail definition on which this document focuses.

### Simple Postback

```text
{
    "id"        : "48181acd22b3edaebc8a447868a7df7ce629920a",
    "type"      : "pb",
    "detail"    : {
        "templateurl" : "https://www.endpoint.com/{%~sdkver%}"
    }
}
```

This postback sends the payload `{“jsonkey”:“jsonvalue”,“sdkkey”:""}`. The expansion will be replaced with the SDK version at time of postback. For more information, see [Matching and Retrieving Values by Keys](rules-json.md#matching-and-retrieving-values-by-keys).

```text
{
    "id"        : "9d40f5665d5bdbe96dcb3a24f4e4fe98d686a602",
    "type"      : "pb",
    "detail"    : {
        "templateurl"   : "https://www.endpoint.com/post/{%urlenc(~sdkver)%}",
        "templatebody"  : "{\"jsonkey\":\"jsonvalue\",\"sdkkey\":\"{%~sdkver%}\"}",
        "contenttype"   : "application/json",
        "timeout"       : 5
    }
}
```

