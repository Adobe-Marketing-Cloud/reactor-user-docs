# Launch Object Reference

## Launch Object Reference

This reference documents the `_satellite` object and the things you can do with it.

### track

#### Code

```javascript
_satellite.track(identifier: string [, detail: *] )
```

#### Example

```javascript
_satellite.track('contact_submit', { name: 'John Doe' });
```

Fires all rules using the Direct Call event type from the Core extension that has been configured with the given identifier. The above example triggers all rules using a Direct Call event type where the configured identifier is `contact_submit`. An optional object containing related information is also passed. The detail object can be accessed by entering `%event.detail%` within a text field in a condition or action or `event.detail` inside the code editor in a Custom Code condition or action.

### getVar

#### Code

```javascript
_satellite.getVar(name: string) => *
```

#### Example

```javascript
var product = _satellite.getVar('product');
```

If a data element exists with a matching name, the data element's value will be returned. If no matching data element exists, it will then check to see if a custom variable with a matching name has previously been set using `_satellite.setVar()`. If a matching custom variable is found, its value will be returned.

Note that in many form fields in the Launch user interface, you can use the `%%` syntax to reference variables, reducing the need to call `_satellite.getVar()`. For example, using %product% will access the value of the product data element or custom variable.

### setVar

#### Code

```javascript
_satellite.setVar(name: string, value: *)
```

#### Example

```javascript
_satellite.setVar('product', 'Circuit Pro');
```

Sets a custom variable with a given name and value. The value of the variable can later be accessed using `_satellite.getVar()`.

You may optionally set multiple variables at once by passing an object where the keys are variable names and the values are the respective variable values.

```javascript
_satellite.setVar({ 'product': 'Circuit Pro', 'category': 'hobby' });
```

### getVisitorId

#### Code

```javascript
_satellite.getVisitorId() => Object
```

#### Example

```javascript
var visitorIdInstance = _satellite.getVisitorId();
```

If the Adobe Experience Cloud ID extension is installed on the property, this method returns the Visitor ID instance. See the [Experience Cloud ID Service documentation](https://forums.adobe.com/external-link.jspa?url=https%3A%2F%2Fmarketing.adobe.com%2Fresources%2Fhelp%2Fen_US%2Fmcvid%2F) for more information.

### logger

#### Code

```javascript
_satellite.logger.log(message: string)
```

```javascript
_satellite.logger.info(message: string)
```

```javascript
_satellite.logger.warn(message: string)
```

```javascript
_satellite.logger.error(message: string)
```

#### Example

```javascript
_satellite.logger.error('No product ID found.');
```

Logs a message to the browser console. The message will only be displayed if Launch debugging is enabled by the user \(by calling `_satellite.setDebug(true)` or using an appropriate browser extension\).

### cookie

#### Code

```javascript
_satellite.cookie.set(name: string, value: string[, attributes: Object])
```

```javascript
_satellite.cookie.get(name: string) => string
```

```javascript
_satellite.cookie.remove(name: string)
```

#### Example

```javascript
// Writing a cookie that expires in one week.
_satellite.cookie.set('product', 'Circuit Pro', { expires: 7 });
```

```javascript
// Reading a previously set cookie.
var product = _satellite.cookie.get('product');
```

```javascript
// Removing a previously set cookie.
_satellite.cookie.remove('product');
```

A utility for reading and writing cookies. This is an exposed copy of the third-party library js-cookie. For more advanced usage, please review the [js-cookie usage documentation](https://forums.adobe.com/external-link.jspa?url=https%3A%2F%2Fwww.npmjs.com%2Fpackage%2Fjs-cookie%23basic-usage).

### buildInfo

#### Code

```javascript
_satellite.buildInfo
```

This object contains information about the build of the current Launch runtime library. The object contains the following properties:

#### turbineVersion

The [Turbine](https://www.npmjs.com/package/@adobe/reactor-turbine) version used inside the current library.

#### turbineBuildDate

The ISO 8601 date when the version of [Turbine](https://www.npmjs.com/package/@adobe/reactor-turbine) used inside the container was built.

#### buildDate

The ISO 8601 date when the current library was built.

#### environment

The environment for which this library was built. The possible values are:

* development
* staging
* production

This example demonstrates the object values:

```javascript
{
  turbineVersion: "14.0.0",
  turbineBuildDate: "2016-07-01T18:10:34Z",
  buildDate: "2016-03-30T16:27:10Z",
  environment: "development"
}
```

### notify

#### Code

```javascript
_satellite.notify(message: string[, level: number])
```

#### Example

Note: This method has been deprecated. Please use `_satellite.logger.log()` instead.

```javascript
_satellite.notify('Hello world!');
```

Logs a message to the browser console. The message will only be displayed if Launch debugging is enabled by the user \(by calling `_satellite.setDebug(true)` or using an appropriate browser extension\).

An optional logging level can be passed which will affect styling and filtering of the message being logged. Supported levels are as follows:

3 - Informational messages.

4 - Warning messages.

5 - Error messages.

If you do not provide a logging level or pass any other level value, the message will be logged as a regular message.

### setCookie

#### Code

```javascript
_satellite.setCookie(name: string, value: string, days: number)
```

#### Example

Note: This method has been deprecated. Please use `_satellite.cookie.set()` instead.

```javascript
_satellite.setCookie('product', 'Circuit Pro', 3);
```

Sets a cookie in the user's browser. The cookie will persist for the number of days specified.

### readCookie

#### Code

```javascript
_satellite.getCookie(name: string) => string
```

#### Example

Note: This method has been deprecated. Please use `_satellite.cookie.get()` instead.

```javascript
var product = _satellite.getCookie('product');
```

Reads a cookie from the user's browser.

### removeCookie

#### Code

```javascript
_satellite.removeCookie(name: string)
```

#### Example

Note: This method has been deprecated. Please use `_satellite.cookie.remove()` instead.

```javascript
_satellite.removeCookie('product');
```

Removes a cookie from the user's browser.

## Debugging Functions

The following functions should not be accessed from production code. They are intended only for debugging purposes and will change over time as needed.

### container

#### Code

```javascript
_satellite._container
```

#### Example

Important: This function should not be accessed from production code. It is intended only for debugging purposes and will change over time as needed.

### monitor

#### Code

```javascript
_satellite._monitors
```

#### Example

Important: This function should not be accessed from production code. It is intended only for debugging purposes and will change over time as needed.

### Sample

On your web page running a Launch library, add a snippet of code to your HTML. Typically, the code is placed in the `<head>` tag before the `<script>` tag that loads the Launch library. This allows the monitor to catch the earliest system events that occur in the Launch library. For example:

```markup
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
  <script>
    window._satellite = window._satellite || {};
    window._satellite._monitors = window._satellite._monitors || [];
    window._satellite._monitors.push({
      ruleTriggered: function (event) {
        console.log(
          'rule triggered',
          event.rule
        );
      },
      ruleCompleted: function (event) {
        console.log(
          'rule completed',
          event.rule
        );
      },
      ruleConditionFailed: function (event) {
        console.log(
          'rule condition failed',
          event.rule,
          event.condition
        );
      }
    });
  </script>
  <script src="//assets.adobedtm.com/launch-EN5bfa516febde4b22b3e7c6f96f6b439f.min.js"
          async></script>
</head>
<body>
  <h1>Click me!</h1>
</body>
</html>
```

In the first script tag, because the Launch library has not been loaded yet, the initial `_satellite` object is created and an array on `_satellite._monitors` is initialized. The script then adds a monitor object to that array. The monitor object can specify the following methods which will later be called by the Launch library:

#### ruleTriggered

Called after an event triggers a rule but before the rule's conditions and actions have been processed. The event object passed to `ruleTriggered` contains information about the rule that was triggered.

#### ruleCompleted

Called after a rule has been fully processed. In other words, the event has occurred, all conditions have passed, and all actions have executed. The event object passed to `ruleCompleted` contains information about the rule that completed.

#### ruleConditionFailed

Called after a rule has been triggered and one of its conditions has failed. The event object passed to `ruleConditionFailed` contains information about the rule that was triggered and the condition that failed.

If `ruleTriggered` is called, either `ruleCompleted` or `ruleConditionFailed` will be called shortly thereafter.

Note: A monitor doesn't have to specify all three methods \(`ruleTriggered`, `ruleCompleted`, and `ruleConditionFailed`\). Launch works with whatever supported methods have been provided by the monitor.

### Testing the Monitor

The example above specifies all three methods in the monitor. When they're called, the monitor logs out relevant information. To test this, set up two rules in the Launch library:

1. A rule that has a click event and a browser condition that passes only if the browser is Chrome.
2. A rule that has a click event and a browser condition that passes only if the browser is Firefox.

If you open the page in Chrome, open the browser console, and click the page, the following appears in the console:

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/debug.png)

Additional hooks or additional information might be added to theses handlers as needed.

