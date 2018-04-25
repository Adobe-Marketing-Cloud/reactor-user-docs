# Adobe Analytics Extension

Use this reference for information about configuring the Adobe Analytics extension, and the options available when using this extension to build a rule.

## Configure the Adobe Analytics extension

This section provides a reference for the options available when configuring the Adobe Analytics extension.

If the Adobe Analytics extension is not yet installed, open your property, then click Extensions &gt; Catalog, hover over the Adobe Analytics extension, and click Install.

To configure the extension, open the Extensions tab, hover over the extension, and then click Configure.

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/ext-analytics-config.png)

### Library Management

Select an option from the Library Management section of the configuration page. The following configuration options are available:

#### Manage the library for me

**Report Suites**

Specify one or more report suites for each of the following environments:

* Development
* Staging
* Production

#### Use the library already installed on the page

**Set the following report suites on tracker**

If you select this option, specify one or more report suites for each of the following environments:

* Development
* Staging
* Production

**Tracker is accessible on the global variable named**

Specify a global variable.

#### Load the library from a custom URL

**HTTP URL**

Specify the URL where the library is located.

**HTTPS URL**

Specify the URL where the library is located.

**Set the following report suites on tracker**

If you select this option, specify one or more report suites for each of the following environments:

* Development
* Staging
* Production

**Tracker is accessible on the global variable named**

Specify a global variable.

#### Let me provide custom library code

**Open Editor**

Lets you [insert core AppMeasurement code](https://marketing.adobe.com/resources/help/en_US/sc/implement/dtm/t_appmeasurement-code.html). This code is populated automatically when using the automatic configuration method.

Note: The validator used in the Launch code editor is designed to identify issues with developer-written code. Code that has gone through a minification process--such as the AppMeasurement.js code downloaded from the Code Manager--might be falsely flagged as having issues by the Launch validator, which can usually be ignored.

**Set the following report suites on tracker**

If you select this option, specify one or more report suites for each of the following environments:

* Development
* Staging
* Production

**Tracker is accessible on the global variable named**

Specify a global variable.

### General

Select an option from the General section of the configuration page. The following configuration options are available:

#### Enable EU compliance for Adobe Analytics

Enables or disables tracking based on the EU privacy cookie.

When a page is loaded, the system checks to see if a cookie called sat\_track is set \(or the custom cookie name specified on the Edit Property page\). Consider the following information:

* If the cookie does not exist or if the cookie exists and is set to anything but true, the loading of the tool is skipped when this setting is enabled. Meaning, any portion of a rule that uses the tool will not apply. If a rule has analytics with EU compliance on and third-party code, and the cookie is set to false, the third-party code still runs. However, the analytics variables will not be set.
* If the cookie exists but it is set to true, the tool loads normally.

You are responsible for setting the sat\_track \(or custom named\) cookie to false if a visitor opts out. You can accomplish this using custom code:

```javascript
_satellite.setCookie("sat_track", "false");
```

You must also have a mechanism to set that cookie to true if you want a visitor to be able to opt in later:

```javascript
_satellite.setCookie("sat_track", "true");
```

#### Character Set

Choose the character set used by Analytics.

You can select a preset character set or specify a custom character set.

For more information about character sets, see the [Multi-Byte Character Sets whitepaper](https://marketing.adobe.com/resources/help/en_US/whitepapers/multibyte/multibyte_encodings.html).

#### Currency Code

Choose the currency code used by Analytics.

You can select a preset currency code or specify a custom currency code.

For more information about the supported currency codes, see the [Multi-Currency Support whitepaper](https://marketing.adobe.com/resources/help/en_US/whitepapers/currency/currency_codes.html).

#### Tracking Server

The domain at which the image request and cookie is written.

See [trackingServer](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServer.html) in the Adobe Analytics Implementation guide.

#### SSL Tracking Server

The domain at which the image request and cookie is written. Used for secure pages. If not defined, SSL data goes to trackingServer.

See [trackingServerSecure](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackingServerSecure.html).

### Global Variables

Use this section to set up [eVars and Props](https://marketing.adobe.com/resources/help/en_US/sc/implement/props_eVars.html), and to create hierarchies.

Global variables are variables that are set on the Analytics tracking object when that object is initialized on the page. Any variables you set here will be set when the tracking object is created on each page. Once these variables are set, they are just like any other variables set any other way. Specifically, this means that a rule can modify, change, or clear these variables.

If your web application typically sends one beacon per page, this section can help make it simple to set your variables in one place. If your application sends more than one beacon per page \(such as in a single-page application\), and you need to clear your variables and reset them using the same tracking object, it is simpler to rely on rules to set and clear your variables.

### Link Tracking

Select an option from the Link Tracking section of the configuration page. The following configuration options are available:

#### Enable ClickMap

[ClickMap](https://marketing.adobe.com/resources/help/en_US/sc/user/clickmap.html) is a plug-in for Internet Explorer and Firefox, and a module of Reports & Analytics.

#### Track download links

Tracks links to downloadable files on your site.

See [s.trackDownLoadLinks](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackDownloadLinks.html).

#### Download Extensions

If the Track Download Links option is enabled, you can select the extensions of file links that are included in the Downloads Report If your site contains links to files with any of the listed extensions, the URLs of these links will appear in reporting.

See [s.linkDownloadFileTypes](https://marketing.adobe.com/resources/help/en_US/sc/implement/linkDownloadFileTypes.html).

#### Track outbound links

Determines whether any link clicked is an exit link.

See [s.trackExternalLinks](https://marketing.adobe.com/resources/help/en_US/sc/implement/trackExternalLinks.html).

**Single-Page App Considerations:** Because of the way some SPA websites are coded, an internal link to a page on the SPA site might look like it is an outbound link.

You can use one of the following methods to track outbound links from SPA sites:

* If you do not want to track any outbound links from your SPA, insert an entry into the Never Track section.

  For example, [http://testsite.com/spa/\#](http://testsite.com/spa/#)

  All \# links to this host are ignored. All outbound links to other hosts are tracked, such as [http://www.google.com](http://www.google.com).

* If there are some links that you want to track on your SPA, use the Always Track section.

  For example, if you have a spa/\#/about page, you could put "about" in the Always Track section.

  The "about" page is the only outbound link that is tracked. Any other links on the page \(for example, [http://www.google.com](http://www.google.com)\) are not tracked.

Note that these two options are mutually exclusive.

#### Keep URL Parameters

Preserves query strings.

See [s.linkLeaveQueryString](https://marketing.adobe.com/resources/help/en_US/sc/implement/linkLeaveQueryString.html).

### Cookies

Configure field descriptions for the Cookies global settings used for deploying the Adobe Analytics extension. The following configuration options are available:

#### Visitor ID

Unique value that represents a customer in both the online and offline systems.

See [visitorID](https://marketing.adobe.com/resources/help/en_US/sc/implement/visitorID.html).

#### Visitor Namespace

Variable to identify the domain with which cookies are set.

See [visitorNamespace](https://marketing.adobe.com/resources/help/en_US/sc/implement/visitorNamespace.html).

#### Domain Periods

The domain on which the Analytics cookie `s_cc` and `s_sq` are set by determining the number of periods in the domain of the page URL. This variable is also used by some plug-ins in determining the correct domain to set the plug-in's cookie.

See [s.cookieDomainPeriods](https://marketing.adobe.com/resources/help/en_US/sc/implement/cookiedomainperiods.html).

#### First-Party Domain Periods

The `fpCookieDomainPeriods` variable is for cookies set by JavaScript \(`s_sq`, `s_cc`, plug-ins\) that are inherently first-party cookies, even if your implementation uses the third-party 2o7.net or omtrdc.net domains.

See [s.fpCookieDomainPeriods](https://marketing.adobe.com/resources/help/en_US/sc/implement/fpCookieDomainPeriods.html).

#### Cookie Lifetime

Determines the life span of a cookie.

See [s.cookieLifetime](https://marketing.adobe.com/resources/help/en_US/sc/implement/cookielifetime.html).

### Customize Page Code

Use the editor to customize your page code.

## Analytics extension action types

This section describes the action types available in the Analytics extension.

The Analytics extension provides the following actions:

* [Set Variables](adobe-analytics-extension.md#set-variables)
* [Send Beacon](adobe-analytics-extension.md#send-beacon)
* [Clear Variables](adobe-analytics-extension.md#clear-variables)

### Set Variables

Important: Using a "set variables" action won't send the beacon. You must use the "send beacon" action.

#### eVars

**Description**

Set one or more [eVars](https://marketing.adobe.com/resources/help/en_US/sc/implement/props_eVars.html).

**Settings**

1. Select an eVar from the dropdown.
2. Specify whether you want to set the eVar as the value \(Set As\) or copy \(Duplicate From\) another eVar.
3. Provide a Set As value, or select the eVar you want to duplicate.
4. \(Optional\) Click Add eVar to set more eVars.
5. Click Keep Changes.

#### Props

**Description**

Set one or more [props](https://marketing.adobe.com/resources/help/en_US/sc/implement/props_eVars.html).

**Settings**

1. Select a prop from the dropdown.
2. Specify whether you want to set the prop as the value \(Set As\) or copy \(Duplicate From\) another eVar.
3. Provide a Set As value, or select the eVar you want to duplicate the prop from.
4. \(Optional\) Click Add prop to set more props.
5. Click Keep Changes.

#### Events

**Description**

Set one or more [events](https://marketing.adobe.com/resources/help/en_US/sc/implement/ref-events.html).

**Settings**

1. Select an event from the dropdown.
2. \(Optional\) Select or specify a data element used for [event serialization](https://marketing.adobe.com/resources/help/en_US/sc/implement/event_serialization_impl.html).
3. \(Optional\) Click Add event to set more props.
4. Click Keep Changes.

#### Hierarchy

**Description**

Set the Analytics [Hierarchy](https://marketing.adobe.com/resources/help/en_US/reference/hierarchy.html) variable.

**Settings**

Specify each level in the hierarchy.

If desired, configure additional hierarchies.

#### Other information

**Description**

Specify other information used by your pages.

**Settings**

These settings include:

* Page Name
* Page URL
* Server
* Channel
* Referrer
* Campaign

  Specify either a value or a query parameter

* State
* Zip
* Transaction ID

#### Custom Page Code

**Description**

Use the editor to specify your custom page code.

**Settings**

1. Click Open Editor.
2. Type the custom code.
3. Click Save.

### Send Beacon

#### Increment a pageview - s.t\(\)

**Description**

Select if you want to increment a pageview.

#### Do not increment a pageview - s.t\(\)

**Description**

Select if you do not want to increment a pageview.

**Settings**

1. Select a link type.

   You can select one of the following:

   * Custom Link
   * Download Link
   * Exit Link

2. Set the parameter for the selected link.
   * Custom Link: Specify the link name.
   * Download Link: Specify a file name.
   * Exit Link: Specify the destination URL.
3. Click Keep Changes.

### Clear Variables

There are no configuration options if the Clear Variables action type is selected.

