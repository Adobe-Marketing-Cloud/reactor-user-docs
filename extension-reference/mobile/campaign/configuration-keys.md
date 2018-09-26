# Configuration Keys

## signals.url

Endpoint for Signal messages that were configured for the app.

Here is the definition for the callback message template:

```text
"payload": {
"templateurl": "", // required - will be token-expanded prior to being sent
"templatebody": "", // optional - if this length > 0 POST will be used as transport method. This is a base64 encoded blob, which will be decoded and token-expanded prior to being sent.
"contenttype": "", // optional - if this is length > 0 and POST type is selected this will be set as the Content-Type header. If this is not supplied for a POST request, the default will be "application/x-www-form-urlencoded" "timeout": 0 // optional - number of seconds to wait before timing out. Default is 2. "application/x-www-form-urlencoded"
"timeout": 0 // optional - number of seconds to wait before timing out. Default is 2. }`
```

