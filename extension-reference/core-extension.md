# Core Extension

The Core extension is the default extension released with Launch.

Use this reference for information about the options available when using this extension to build a rule.

## Core extension event types

This topic describes the event types available in the Core extension.

Event types are divided into the following categories:

* [Browser](core-extension.md#browser)
* [Form](core-extension.md#form)
* [Keyboard](core-extension.md#keyboard)
* [Media](core-extension.md#media)
* [Mobile](core-extension.md#mobile)
* [Mouse](core-extension.md#mouse)
* [Other](core-extension.md#other)
* [Page load](core-extension.md#page-load)

For information about options that can be set for several different event types, see [Options](core-extension.md#options).

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

See [Options](core-extension.md#options), below.

#### Focus

Trigger the action when a form gains the focus.

See [Options](core-extension.md#options), below.

#### Submit

Trigger the action when a form is submitted.

See [Options](core-extension.md#options), below.

### Keyboard

#### Key Press

Trigger the event if a key is pressed.

See [Options](core-extension.md#options), below.

### Media

#### Media Ended

Trigger the event when the media ends.

See [Options](core-extension.md#options), below.

#### Media Loaded Data

Trigger the event when the media loads data.

See [Options](core-extension.md#options), below.

#### Media Pause

Trigger the event when the media is paused.

See [Options](core-extension.md#options), below.

#### Media Play

Trigger the even when the media is played.

See [Options](core-extension.md#options), below.

#### Media Stalled

Trigger the event if the media stalls.

See [Options](core-extension.md#options), below.

#### Media Time Played

Trigger the event if the media is played for a specified length of time.

See [Options](core-extension.md#options), below.

In addition, specify that the event is triggered after a specific amount of time.

#### Media Volume Changed

Trigger the event if the volume is raised or lowered.

See [Options](core-extension.md#options), below.

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

See [Options](core-extension.md#options), below.

You can also specify whether to delay navigation until the rule runs if the element is a link.

In addition, specify that the event is triggered after a specific amount of time.

#### Hover

Trigger the event if the user hovers over a specified element.

See [Options](core-extension.md#options), below.

In addition, configure whether the rule is triggered immediately or after a specified number of milliseconds.

### Other

#### Custom Event

Trigger the event if a custom event type occurs.

You can name a JavaScript function that you've defined elsewhere and use it for the event.

Specify the name of the custom event type, then configure the other settings as described in [Options](core-extension.md#options), below.

#### Data Element Changed

Trigger the event if a specified data element changes.

Enter the data element name. You can select the data element from a list by clicking the icon and then selecting the data element.

#### Direct Call

Designed to bypass event detection and lookup systems.

Direct call rules are ideal for situations where you want to tell Launch exactly what is happening. Also, they are ideal when Launch cannot detect an event in the DOM, such as with Adobe Flash.

Specify the `_satellite.track` string.

#### Element Exists

Trigger the event if a specified element exists.

See [Options](core-extension.md#options), below.

#### Enters Viewport

Trigger the event if the user enters a specified viewport.

See [Options](core-extension.md#options), below.

In addition, configure whether the rule is triggered immediately or after a specified number of milliseconds.

#### pushState or hashchange

Trigger the event if a pushState or hashchange occurs.

**Settings**

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

Event condition types are divided into the following categories:

* [Data](core-extension.md#data-cond)
* [Engagement](core-extension.md#engagement-cond)
* [Technology](core-extension.md#technology-cond)
* [URL](core-extension.md#url-cond)

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

#### Data Element

Specify if a data element requires a specific value for the event to trigger an action.

1. Select a data element.

   Type the data element in the box, or click the icon and select a data element.

2. Specify the value that must exist as a condition for the event.
3. \(Optional\) Enable Regex if this is a regular expression.

#### Variable

Specify the JavaScript variable name and value that must exist for an event to trigger an action.

1. Specify the JavaScript variable name.
2. Specify the variable value that must exist as a condition for the event.
3. \(Optional\) Enable Regex if this is a regular expression.

### Engagement

#### Cart Amount

Configure a shopping cart amount that must be true for the event to trigger an action.

1. Select a data element.

   Type the data element in the box, or click the icon and select a data element.

2. Select whether the amount must be greater than, equal to, or less than the specified amount.
3. Specify the amount to complete the condition.

#### Cart Item Quantity

Configure the number of items that must be in the shopping cart for the event to trigger an action.

1. Select a data element.

   Type the data element in the box, or click the icon and select a data element.

2. Select whether the number of items must be greater than, equal to, or less than the specified value.
3. Specify the value to complete the condition.

#### Landing Page

Specify the page the user must land on to trigger the event.

1. Specify the landing page.
2. \(Optional\) Enable Regex if this is a regular expression.

#### Logged In

Specify the data element that indicates whether the user is logged in.

Select a data element.

Type the data element in the box, or click the icon and select a data element.

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

#### Previous Converter

Trigger the action if the visitor has converted before.

Select a data element.

Type the data element in the box, or click the icon and select a data element.

#### Registered User

Trigger the action if the visitor is a registered user.

Select a data element.

Type the data element in the box, or click the icon and select a data element.

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

Event condition types are divided into the following categories:

* [Data](core-extension.md#data-ext)
* [Engagement](core-extension.md#engagement-ext)
* [Technology](core-extension.md#technology-ext)
* [URL](core-extension.md#url-ext)

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

#### Data Element

Specify if a data element requires that a specific value does not exist for the event to trigger an action.

1. Select a data element.

   Type the data element in the box, or click the icon and select a data element.

2. Specify the value that must not exist as a condition for the event.
3. \(Optional\) Enable Regex if this is a regular expression.

#### Variable

Specify the JavaScript variable name and value that must not exist for an event to trigger an action.

1. Specify the JavaScript variable name.
2. Specify the variable value that must not exist as a condition for the event.
3. \(Optional\) Enable Regex if this is a regular expression.

### Engagement

#### Cart Amount

Configure a shopping cart amount that must not be true for the event to trigger an action.

1. Select a data element.

   Type the data element in the box, or click the icon and select a data element.

2. Select whether the amount must not be greater than, equal to, or less than the specified amount.
3. Specify the amount to complete the condition.

#### Cart Item Quantity

Configure the number of items that must not be in the shopping cart for the event to trigger an action.

1. Select a data element.

   Type the data element in the box, or click the icon and select a data element.

2. Select whether the number of items must not be greater than, equal to, or less than the specified value.
3. Specify the value to complete the condition.

#### Landing Page

Specify the page the user must not land on to trigger the event.

1. Specify the landing page.
2. \(Optional\) Enable Regex if this is a regular expression.

#### Logged In

Specify the data element that indicates whether the user is logged in.

Select a data element.

Type the data element in the box, or click the icon and select a data element.

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

#### Previous Converter

Do not trigger the action if the visitor has converted before.

Select a data element.

Type the data element in the box, or click the icon and select a data element.

#### Registered User

Do not trigger the action if the visitor is a registered user.

1. Select a data element.
2. Type the data element in the box, or click the icon and select a data element.

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

