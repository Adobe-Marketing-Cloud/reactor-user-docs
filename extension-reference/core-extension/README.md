# Core Extension

The Core extension is the default extension released with Launch.

Use this reference for information about the options available when using this extension to build a rule.

## Core extension event types

This topic describes the event types available in the Core extension.

For information about options that can be set for several different event types, see [Options](./#options).

### Browser

#### Tab Blur

Trigger the action when a tab loses the focus.

There are no settings for this event type.

#### Tab Focus

Trigger the action when a tab gains the focus.

There are no settings for this event type.

### Form

#### Blur

Trigger the action when a form loses the focus.

See [Options](./#options), below.

#### Focus

Trigger the action when a form gains the focus.

See [Options](./#options), below.

#### Submit

Trigger the action when a form is submitted.

See [Options](./#options), below.

### Keyboard

#### Key Press

Trigger the event if a key is pressed.

See [Options](./#options), below.

### Media

#### Media Ended

Trigger the event when the media ends.

See [Options](./#options), below.

#### Media Loaded Data

Trigger the event when the media loads data.

See [Options](./#options), below.

#### Media Pause

Trigger the event when the media is paused.

See [Options](./#options), below.

#### Media Play

Trigger the even when the media is played.

See [Options](./#options), below.

#### Media Stalled

Trigger the event if the media stalls.

See [Options](./#options), below.

#### Media Time Played

Trigger the event if the media is played for a specified length of time.

See [Options](./#options), below.

In addition, specify that the event is triggered after a specific amount of time.

#### Media Volume Changed

Trigger the event if the volume is raised or lowered.

See [Options](./#options), below.

### Mobile

#### Orientation Change

Trigger the event if the device's orientation changes.

There are no settings for this event type.

In addition, specify that the event is triggered after a specific amount of time.

#### Zoom Change

Trigger the event if the user zooms in or out.

There are no settings for this event type.

### Mouse

#### Click

Trigger the event if the specified element is clicked.

See [Options](./#options), below.

You can also specify whether to delay navigation until the rule runs if the element is a link.

In addition, specify that the event is triggered after a specific amount of time.

#### Hover

Trigger the event if the user hovers over a specified element.

See [Options](./#options), below.

In addition, configure whether the rule is triggered immediately or after a specified number of milliseconds.

### Other

#### Custom Event

Trigger the event if a custom event type occurs.

You can name a JavaScript function that you've defined elsewhere and use it for the event.

Specify the name of the custom event type, then configure the other settings as described in [Options](./#options), below.

#### Data Element Changed

Trigger the event if a specified data element changes.

Enter the data element name. You can select the data element from a list by clicking the icon and then selecting the data element.

#### Direct Call

Designed to bypass event detection and lookup systems.

Direct call rules are ideal for situations where you want to tell Launch exactly what is happening. Also, they are ideal when Launch cannot detect an event in the DOM, such as with Adobe Flash.

Specify the `_satellite.track` string.

#### Element Exists

Trigger the event if a specified element exists.

See [Options](./#options), below.

#### Enters Viewport

Trigger the event if the specified element enters the viewport (the user's visible area of a web page).

See [Options](./#options), below.

You can also specify whether the rule is triggered the first time the element enters the viewport or every time the element enters the viewport.

In addition, configure whether the rule is triggered immediately or after a specified number of milliseconds.

#### History Change

Trigger the event if a pushState or hashchange occurs.

There are no settings for this event type.

#### Time Spent on Page

Trigger the event if the user remains on the page for a specified number of seconds.

Specify the number of seconds that must pass before the event is triggered.

### Page load

#### DOM Ready

Trigger when the DOM is ready.

There are no settings for this event type.

#### On Load

Trigger the event when the page loads.

There are no settings for this event type.

#### Page Bottom

Trigger the event if the user reaches the bottom of the page

There are no settings for this event type.

### Options

Each of the form event types uses the following settings:

#### Specific Elements \| Any Element

* If you choose Specific Elements, the options to select the elements and property values appear.
* If you choose Any Element, there are no further options required to narrow down the elements.

#### Elements matching the CSS selector

Enter the CSS selector that identifies the elements that trigger the event.

#### And having certain property values

If you select this option, the following parameters become available:

* `property=value`

  Specify the value for the property

* Regex

  Enable if the `property=value` is a regular expression.

* Add

  Add another `property=value` pair.

#### Advanced options \(Bubbling\)

* Run this rule even when the event originates from a descendant element
* Allow this rule to run even if the event already triggered a rule targeting a descendant element
* After the rule runs, prevent the event from triggering rules targeting ancestor elements

## Core extension condition types

This section describes the condition types available in the Core extension.

### Data

#### Cookie

Specify the cookie name and value that must exist for an event to trigger an action.

1. Specify a cookie name.
2. Enter the value that must exist in the cookie if the event is to trigger an action.
3. \(Optional\) Enable Regex if this is a regular expression.

#### Cookie Opt-out

Specify whether the user has opted out of cookies.

Set whether the user accepts cookies.

#### Custom Code

Specify any custom code that must exist as a condition of the event. Use the built-in code editor to enter the custom code.

1. Click Open Editor.
2. Type the custom code.
3. Click Save.

#### Value Comparison

Compares two values to determine whether this condition returns true.

If you have a rule with multiple conditions, it is possible that this condition will return true, but the rule will still not fire because the other conditions evaluate as false or one of the exceptions evaluates as true. 					

1. Provide a value.
2. Select the operator. Refer to the list of  value comparison operators, below, for more details.
3. \(Where required\) Select whether the comparison should be case-insensitive. 					  
4. Provide another value for the comparison.

The following value comparison operators are available:

**Equal:** The condition returns true if the two values are equal using a non-strict comparison \(in JavaScript, the == operator\). The values may be of any type. When typing a word like _true_,  _false_,  _null_, or  _undefined_ into a value field, the word is compared as a string and is not be converted to its JavaScript equivalent. 

**Does Not Equal:**  The condition returns true if the two values are not equalusing a non-strict comparison \(in JavaScript, the != operator\). The values may be of any type. When typing a word like _true_, _false_, _null_, or _undefined_ into a value field, the word is compared as a string and is not be converted to its JavaScript equivalent. 

**Contains:** The condition returns true if the first value contains the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not Contain:** The condition returns true if the first value does not contain the second value. Numbers are converted to strings. Any value other than a number or string will result in the condition returning true. 

**Starts With:** The condition returns true if the first value starts with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not Start With:** The condition returns true if the first value does not start with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning true. 

**Ends With:** The condition returns true if the first value ends with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not End With:** The condition returns true if the first value does not end with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning true. 

**Matches Regex:** The condition returns true if the first value matches the regular expression. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not Match Regex:** The condition returns true if the first value does not match the regular expression. Numbers are converted to strings. Any value other than a number or string results in the condition returning true. 

**Is Less Than:** The condition returns true if the first value is less than the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is Less Than Or Equal To:** The condition returns true if the first value is less than or equal to the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is Greater Than:** The condition returns true if the first value is greater than the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is Greater Than Or Equal To:** The condition returns true if the first value is greater than or equal to the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is True:** The condition returns true if the value is a boolean with the value of true. The value you provide is not converted to a boolean if it is any other type. Any value other than a boolean with the value of true results in the condition returning false. 

**Is Truthy:** The condition returns true if the value is true after being converted to a boolean. See [MDN's Truthy documentation](https://developer.mozilla.org/en-US/docs/Glossary/Truthy) for examples of truthy values. 

**Is False:** The condition returns true if the value is a boolean with the value of false. The value you provide is not converted to a boolean if it is any other type. Any value other than a boolean with the value of false results in the condition returning false. 

**Is Falsy:** The condition returns true if the value is false after being converted to a boolean. See [MDN's Falsy documentation](https://developer.mozilla.org/en-US/docs/Glossary/Falsy) for examples of falsy values.	

#### Variable

Specify the JavaScript variable name and value that must exist for an event to trigger an action.

1. Specify the JavaScript variable name.
2. Specify the variable value that must exist as a condition for the event.
3. \(Optional\) Enable Regex if this is a regular expression.

### Engagement

#### Landing Page

Specify the page the user must land on to trigger the event.

1. Specify the landing page.
2. \(Optional\) Enable Regex if this is a regular expression.

#### New/Returning Visitor

Specify whether the visitor should be a new visitor or a returning visitor for an event to trigger an action.

Select one of the following:

* New Visitor
* Returning Visitor

#### Page Views

Configure the number of times the visitor must view the page before the action is triggered.

1. Select whether the number of page views must be greater than, equal to, or less than the specified value.
2. Specify the number of page views that determines whether the condition is met.
3. Configure when the page views are counted by selecting one of the following:
   * Lifetime
   * Current Session

#### Sessions

Trigger the action if the user's number of sessions meets the specified criteria.

1. Select whether the number of sessions must be greater than, equal to, or less than the specified value.
2. Specify the number of sessions that determines whether the condition is met.

#### Time On Site

Trigger the action if the user's number of sessions meets the specified criteria.

Configure how long the visitor must be on the site before the action is triggered.

1. Select whether the number of minutes the visitor is on the site must be greater than, equal to, or less than the specified value.
2. Specify the number of minutes that determines whether the condition is met.

#### Traffic Source

Trigger the action if the user's number of sessions meets the specified criteria.

Specify the source of the visitor's traffic that must be true for the action to be triggered.

1. Specify the traffic source.
2. \(Optional\) Enable Regex if this is a regular expression.

### Other

#### Date Range

Specify a date range. Choose the date and time the event occurs after, the date it occurs before, and the time zone.

#### Max Frequency

Specify the maximum number of times the condition returns true. You can select from the following options:

* Page view
* Sessions
* Visitor
* Seconds
* Minutes
* Days
* Weeks
* Months

#### Sampling

Specify the percentage of the time the condition returns true.

### Technology

#### Browser

Select the browser the visitor must use for the action to be triggered.

Select one or more of the following browsers:

* Chrome
* Firefox
* Internet Explorer/Edge
* Internet Explorer Mobile
* Mobile Safari
* OmniWeb
* Opera
* Opera Mini
* Opera Mobile
* Safari

#### Device Type

Select the device type the visitor must use for the action to be triggered.

Select one or more of the following device types:

* Android
* Blackberry
* Desktop
* iPad
* iPhone
* iPod
* Nokia
* Windows Phone

#### Operating System

Select the operating system the visitor must use for the action to be triggered.

Select one or more of the following operating systems:

* Android
* Blackberry
* iOS
* Linux
* MacOS
* Maemo
* Symbian OS
* Unix
* Windows

#### Screen Resolution

Select the screen resolution visitors must use on their devices for the action to be triggered.

1. Select whether the screen resolution width of the visitor's device must be greater than, equal to, or less than the specified value.
2. Specify the number of pixels required for the screen resolution width.
3. Select whether the screen resolution height of the visitor's device must be greater than, equal to, or less than the specified value.
4. Specify the number of pixels required for the screen resolution height.

#### Window Size

Select the window size visitors must use on their devices for the action to be triggered.

1. Select whether the window size width of the visitor's device must be greater than, equal to, or less than the specified value.
2. Specify the number of pixels required for the window size width.
3. Select whether the window size height of the visitor's device must be greater than, equal to, or less than the specified value.
4. Specify the number of pixels required for the window size height.

### URL

#### Domain

Specify the visitor's domain.

#### Hash

Specify one or more hash patterns that must exist in the URL.

Note: Multiple hash patterns are joined by an OR.

1. Specify the hash pattern.
2. \(Optional\) Enable Regex if this is a regular expression.
3. Add any other hash patterns.

#### Path

Specify one or more paths that must exist in the URL.

Note: Multiple paths are joined by an OR.

1. Specify the path.
2. \(Optional\) Enable Regex if this is a regular expression.
3. Add any other paths.

#### Protocol

Specify the protocol used in the URL.

Select one of the following:

* HTTP
* HTTPS

#### Subdomain

Specify one or more subdomains that must exist in the URL.

Note: Multiple subdomains are joined by an OR.

1. Specify the subdomain.
2. \(Optional\) Enable Regex if this is a regular expression.
3. Add any other subdomains.

#### URL Parameter

Specify URL parameter used in the URL.

1. Specify a URL parameter name.
2. Specify the value used for the URL parameter.
3. \(Optional\) Enable Regex if this is a regular expression.

## Core extension exception types

This section describes the exception types available in the Core extension.

### Data

#### Cookie

Specify the cookie name and value that can't exist for an event to trigger an action.

1. Specify a cookie name.
2. Enter the value that must not exist in the cookie if the event is to trigger an action.
3. \(Optional\) Enable Regex if this is a regular expression.

#### Cookie Opt-out

Specify whether the user has opted out of cookies.

Set whether the user accepts cookies.

#### Custom Code

Specify any custom code that must exist as a condition of the event. Use the built-in code editor to enter the custom code.

1. Click Open Editor.
2. Type the custom code.
3. Click Save.

#### Value Comparison

Compares two values to determine whether this exception returns true.

If you have a rule with multiple conditions, it is possible that this condition will return true, but the rule will still not fire because the other conditions evaluate as false or one of the exceptions evaluates as true. 	 					

1. Provide a value.
2. Select the operator. Refer to the list of  value comparison operators, below, for more details.
3. \(Where required\) Select whether the comparison should be case-insensitive. 					  
4. Provide another value for the comparison.

The following value comparison operators are available:

**Equal:** The condition returns true if the two values are equal using a non-strict comparison \(in JavaScript, the == operator\). The values may be of any type. When typing a word like _true_,  _false_,  _null_, or  _undefined_ into a value field, the word is compared as a string and is not be converted to its JavaScript equivalent. 

**Does Not Equal:**  The condition returns true if the two values are not equalusing a non-strict comparison \(in JavaScript, the != operator\). The values may be of any type. When typing a word like _true_, _false_, _null_, or _undefined_ into a value field, the word is compared as a string and is not be converted to its JavaScript equivalent. 

**Contains:** The condition returns true if the first value contains the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not Contain:** The condition returns true if the first value does not contain the second value. Numbers are converted to strings. Any value other than a number or string will result in the condition returning true. 

**Starts With:** The condition returns true if the first value starts with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not Start With:** The condition returns true if the first value does not start with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning true. 

**Ends With:** The condition returns true if the first value ends with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not End With:** The condition returns true if the first value does not end with the second value. Numbers are converted to strings. Any value other than a number or string results in the condition returning true. 

**Matches Regex:** The condition returns true if the first value matches the regular expression. Numbers are converted to strings. Any value other than a number or string results in the condition returning false. 

**Does Not Match Regex:** The condition returns true if the first value does not match the regular expression. Numbers are converted to strings. Any value other than a number or string results in the condition returning true. 

**Is Less Than:** The condition returns true if the first value is less than the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is Less Than Or Equal To:** The condition returns true if the first value is less than or equal to the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is Greater Than:** The condition returns true if the first value is greater than the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is Greater Than Or Equal To:** The condition returns true if the first value is greater than or equal to the second value. Strings representing numbers are converted to numbers. Any value other than a number or a convertible string result in the condition returning false. 

**Is True:** The condition returns true if the value is a boolean with the value of true. The value you provide is not converted to a boolean if it is any other type. Any value other than a boolean with the value of true results in the condition returning false. 

**Is Truthy:** The condition returns true if the value is true after being converted to a boolean. See [MDN's Truthy documentation](https://developer.mozilla.org/en-US/docs/Glossary/Truthy) for examples of truthy values. 

**Is False:** The condition returns true if the value is a boolean with the value of false. The value you provide is not converted to a boolean if it is any other type. Any value other than a boolean with the value of false results in the condition returning false. 

**Is Falsy:** The condition returns true if the value is false after being converted to a boolean. See [MDN's Falsy documentation](https://developer.mozilla.org/en-US/docs/Glossary/Falsy) for examples of falsy values.	

#### Variable

Specify the JavaScript variable name and value that must not exist for an event to trigger an action.

1. Specify the JavaScript variable name.
2. Specify the variable value that must not exist as a condition for the event.
3. \(Optional\) Enable Regex if this is a regular expression.

### Engagement

#### Landing Page

Specify the page the user must not land on to trigger the event.

1. Specify the landing page.
2. \(Optional\) Enable Regex if this is a regular expression.

#### New/Returning Visitor

Specify whether the visitor should not be a new visitor or a returning visitor for an event to trigger an action.

Select one of the following:

* New Visitor
* Returning Visitor

#### Page Views

Configure the number of times the visitor must view the page to keep the action from being triggered.

1. Select whether the number of page views must be greater than, equal to, or less than the specified value.
2. Specify the number of page views that determines whether the exception is met.
3. Configure when the page views are counted by selecting one of the following:
   * Lifetime
   * Current Session

#### Sessions

Do not trigger the action if the user's number of sessions meets the specified criteria.

1. Select whether the number of sessions must be greater than, equal to, or less than the specified value.
2. Specify the number of sessions that determines whether the condition is met.

#### Time On Site

Configure how long the visitor must be on the site to prevent the action from being triggered.

1. Select whether the number of minutes the visitor is on the site must be greater than, equal to, or less than the specified value.
2. Specify the number of minutes that determines whether the condition is met.

#### Traffic Source

Specify the source of the visitor's traffic that must be true to prevent the action from being triggered.

1. Specify the traffic source.
2. \(Optional\) Enable Regex if this is a regular expression.

### Other

#### Date Range

Specify a date range. Choose the date and time the event occurs after, the date it occurs before, and the time zone.

#### Max Frequency

Specify the maximum number of times the condition returns true. You can select from the following options:

* Page view
* Sessions
* Visitor
* Seconds
* Minutes
* Days
* Weeks
* Months

#### Sampling

Specify the percentage of the time the condition returns true.

### Technology

#### Browser

Select the browser the visitor must not use for the action to be triggered.

Select one or more of the following browsers:

* Chrome
* Firefox
* Internet Explorer/Edge
* Internet Explorer Mobile
* Mobile Safari
* OmniWeb
* Opera
* Opera Mini
* Opera Mobile
* Safari

#### Device Type

Select the device type the visitor must not use for the action to be triggered.

Select one or more of the following device types:

* Android
* Blackberry
* Desktop
* iPad
* iPhone
* iPod
* Nokia
* Windows Phone

#### Operating System

Select the operating system the visitor must not use for the action to be triggered.

Select one or more of the following operating systems:

* Android
* Blackberry
* iOS
* Linux
* MacOS
* Maemo
* Symbian OS
* Unix
* Windows

#### Screen Resolution

Select the screen resolution visitors must not use on their devices for the action to be triggered.

1. Select whether the screen resolution width of the visitor's device must be greater than, equal to, or less than the specified value.
2. Specify the number of pixels required for the screen resolution width.
3. Select whether the screen resolution height of the visitor's device must be greater than, equal to, or less than the specified value.
4. Specify the number of pixels required for the screen resolution height.

#### Window Size

Select the window size visitors must not use on their devices for the action to be triggered.

1. Select whether the window size width of the visitor's device must be greater than, equal to, or less than the specified value.
2. Specify the number of pixels required for the window size width.
3. Select whether the window size height of the visitor's device must be greater than, equal to, or less than the specified value.
4. Specify the number of pixels required for the window size height.

### URL

#### Domain

Specify the visitor's domain that will prevent the action from being triggered.

#### Hash

Specify one or more hash patterns that must not exist in the URL.

Note: Multiple hash patterns are joined by an OR.

1. Specify the hash pattern.
2. \(Optional\) Enable Regex if this is a regular expression.
3. Add any other hash patterns.

#### Path

Specify one or more paths that must not exist in the URL.

Note: Multiple paths are joined by an OR.

1. Specify the path.
2. \(Optional\) Enable Regex if this is a regular expression.
3. Add any other paths.

#### Protocol

Specify the protocol that cannot be used in the URL.

Select one of the following:

* HTTP
* HTTPS

#### Subdomain

Specify one or more subdomains that must not exist in the URL.

Note: Multiple subdomains are joined by an OR.

1. Specify the subdomain.
2. \(Optional\) Enable Regex if this is a regular expression.
3. Add any other subdomains.

#### URL Parameter

Specify URL parameter that cannot be used in the URL.

1. Specify a URL parameter name.
2. Specify the value used for the URL parameter.
3. \(Optional\) Enable Regex if this is a regular expression.

## Core extension action types

This section describes the action types available in the Core extension.

### Custom Code

Provide the code that runs after the event is triggered and conditions are evaluated.

1. Name the action code.
2. Select the language used to define the action:
   * JavaScript
   * HTML
3. Select whether to execute the action code globally.
4. Click Open Editor.
5. Edit the code, then click Save.

### Custom Code action processing

The Core extension, available to all Launch users, contains a Custom Code action for executing user-provided JavaScript or HTML. It is often helpful for users to understand how rules with Custom Code actions are processed.

#### Rules using the page top or page bottom events

Code from custom actions is embedded in the main Launch library. The code is written to the document using document.write. If a rule has multiple Custom Code actions, the code is written in the order configured in the rule.

#### Rules using any event other than page top or page bottom

Code from custom actions is loaded from the server and written to the document using [Postscribe](https://github.com/krux/postscribe). If a rule has multiple Custom Code actions, the code is loaded in parallel from the server, but written in the order configured in the rule.

While using document.write after a page has loaded would typically present problems, this is not an issue for code provided through Custom Code actions. You may use document.write within Custom Code actions regardless of when the code will be executed.

#### Custom Code Validation

The validator used in the Launch code editor is designed to identify issues with developer-written code. Code that has gone through a minification process--such as the AppMeasurement.js code downloaded from the Code Manager--might be falsely flagged as having issues by the Launch validator, which can usually be ignored.

