---
description: >-
  Details about the specific differences between your DTM property and the
  upgraded version in Launch.
---

# Upgrade Preparation Guide

Launch, by Adobe, is an entirely different system than DTM. Conceptually, they achieve the same goal, but the way they do so is different. The`_satellite`object looks different in Launch than it does in DTM. The relationships between extensions, rules, and data elements are also different than before. Some things that exist in both systems have moved to different locations or are accessed in different ways.

The Upgrade Assistant creates a Launch property that is as close as possible to the on-page behavior that you had in DTM. Refer to the following information about what moves and where it moves to in cases where the behavior differs from what you might expect.

Examples of differences that are further defined below:

1. Rule Components and Data Elements that aren't doing anything in your DTM property are not copied to Launch. Example: `Data Element` conditions defined by a data element that does not exist are not copied.
2. Many conditions have been updated so the options available in the condition are slightly different in Launch. Example: The `Operating System` condition no longer supports Blackberry.
3. Many resources are called something new in Launch, so they are copied with the new name. Example: `Page Top` events move to `Library Load` events.
4. Many very specific conditions have been replaced by a more generic `Value Comparison` condition in Launch. This enables more options, provides consistency with all the comparison operators, and simplifies maintainance as well. Example: the `Cart Amount` condition has been replaced by the `Value Comparison` condition.

## Properties {#properties}

### Name {#name}

The name of your DTM property is copied to Launch. "**\(DTM - yyyy-mm-dd hh:mm:ss\)"** is added to the end of the Launch property name so you know exactly when it was migrated. You can remove this from your Launch property name.

### Domains {#domains}

The domains on your DTM property are copied to Launch.

If you have the same domain listed multiple times in DTM, it only appears on your Launch property once. Domains in Launch appear in lower case.

If you don't have at least one valid domain defined on your DTM property, it is not copied.

### Advanced Settings {#advanced-settings}

The advanced settings on your DTM property are copied to Launch.

### Tools {#tools}

When you upgrade to Launch, the most commonly used DTM tools are converted into an installed Launch extension on your property.

### Adobe Analytics Tool {#adobe-analytics-tool}

#### Tool Selection {#tool-selection}

DTM allows you to install multiple instances of the Analytics tool to your property. Launch only allows a single instance of each Extension to be installed. Thus, only one Analytics tool is copied to Launch during the upgrade.

The tool instance that is copied is determined by transforming the names to lower case, then sorting alphabetically. Whichever tool comes first is the one that is copied.

You can control which tool instance to copy by changing the name of the tool.

#### App Measurement Version {#app-measurement-version}

DTM gives you several different options to deploy App Measurement. Each is supported in Launch, so whichever method you use, you'll get the same method in Launch.

If you're using `Managed by Adobe` in the DTM tool, be aware that it lets you select any of the five most recent versions of App Measurement. The Adobe Analytics Launch extension uses the latest version of App Measurement, so depending on your selection there, copying to Launch may result in a different version of App Measurement being used. If you want the version to match, modify your DTM tool to use the same version as Launch before you upgrade.

#### Initial Beacon {#initial-beacon}

In DTM, an Analytics beacon is fired on every page when App Measurement loads, even if no rules have been defined. In Launch, this beacon call is controlled by a rule and does not happen automatically. The Upgrade process creates this rule for you unless you are using the `Page code is already present` option in DTM. This rule is called **Migrated from DTM: Adobe Analytics - Send beacon on every page** and has the following definition:

* Event: `Page Bottom` \(This most closely matches the DTM behavior even though Launch recommends`Library Load` rather than `Page Bottom` in most cases.\)
* Conditions: None
* Exceptions: None
* Actions: `Adobe Analytics - Send Beacon`

The Upgrade Assistant creates this rule in Launch, as long as an Analytics tool is installed in DTM. If you were using a `return false` inside custom code in DTM to suppress the initial beacon call, then you should leave the Launch rule out of your library \(or delete it\) after the upgrade is done.

#### Other {#other}

Analytics tools that don't define a production report suite are not copied to Launch.

Evars that don't match the pattern of **eVar\#\#** are not copied to Launch.

### Experience Cloud ID Tool {#experience-cloud-id-tool}

The Experience Cloud ID tool is copied to Launch. There are a few things you should know about that tool.

#### Extension Configuration {#extension-configuration}

Some variables in the DTM tool are not supported in the Launch extension. The following variables are copied to Launch:

* audienceManagerServer
* audienceManagerServerSecure
* cookieDomain
* cookieLifetime
* cookieName
* disableThirdPartyCalls
* idSyncAfterIDCallResult
* idSyncAttachIframeOnWindowLoad
* idSyncContainerID
* idSyncDisable3rdPartySyncing
* disableThirdPartyCookies
* idSyncDisableSyncs
* disableIdSyncs
* idSyncIDCallResult
* idSyncSSLUseAkamai
* isCoopSafe
* loadSSL
* loadTimeout
* marketingCloudServer
* marketingCloudServerSecure
* overwriteCrossDomainMCIDAndAID
* resetBeforeVersion
* sdidParamExpiry
* serverState
* sessionCookieName
* takeTimeoutMetrics
* trackingServer
* trackingServerSecure
* whitelistIframeDomains
* whitelistParentDomain

Variables that do not have a value are not copied to Launch.

#### Set Customer IDs {#set-customer-ids}

If the ECID tool configuration in DTM contains data in the `Customer Settings` section, that data is copied into a Launch rule. The Launch rule has the following definition:

* Event: `Library Loaded`
* Conditions: None
* Exceptions: None
* Actions: `Experience Cloud ID - Set Customer IDs`

Customer IDs that don't have names or values are not copied.

If no valid customer IDs are found, no Launch rule is created.

### Google Universal Analytics {#google-universal-analytics}

#### Tool Selection {#tool-selection-1}

DTM allows you to install multiple instances of the Google Universal Analytics tool to your property. Launch only allows a single instance of each extension to be installed. Thus, only one tool is copied to Launch during the upgrade.

The tool instance that is copied is determined by transforming the names to lower case, then sorting alphabetically. Whichever tool comes first is the one that is copied over.

You can control which tool instance to copy by changing the name of the tool.

#### Initial Beacon {#initial-beacon-1}

In DTM, a beacon is fired on every page even if no rules are defined. In Launch, this beacon call is controlled by a rule and does not happen automatically. The Upgrade process creates this rule for you unless you use the `Google Universal Analytics page code is already present` option. This rule is called **Migrated from DTM: Google Universal Analytics - Send beacon on every page** and has the following definition:

* Event: `Core - Page Bottom` \(This most closely matches the DTM behavior even though Launch recommends`Library Load` rather than `Page Bottom` in most cases.\)
* Conditions: None
* Exceptions: None
* Actions: `Google Univeral Analytics - Send Page View`

#### Hit Callback {#hit-callback}

If you have added any JavaScript code in the Hit Callback section inside the Google Universal Analytics tool, the Upgrade Assistant creates a matching rule for you in Launch. The rule is called `Migrated from DTM: Google Universal Analytics - Hit Callback` and has the following definition:

* Event: `Google Universal Analytics - Hit Callback`
* Conditions: None
* Exceptions: None
* Actions: `Core - Custom Code`

#### Rules Definition {#rules-definition}

If you have defined rules in DTM where **Event Category** or **Event Action** are missing from the rule definition, these event details are not copied to Launch.

If you have defined rules in DTM where **Event Value** is not a number, these event details are not copied to Launch.

### Tools that are not copied {#tools-that-are-not-copied}

The following DTM tools installed on your property are not copied to Launch extensions.

* Adobe Audience Manager
* Adobe Media Optimizer
* Adobe Target
* AEM ContextHub
* Nielsen
* Google Analytics

## Data Elements {#data-elements}

### Cookie {#cookie}

`Cookie` data element types that don't contain a cookie name are not copied to Launch.

### CSS Selector {#css-selector}

In Launch, the CSS Selector data element type is called DOM Attribute, so your CSS Selector data elements types are copied into DOM Attribute data element types.

`CSS Selector` data element types that don't contain a selector are not copied to Launch.

`CSS Selector` data element types that use the `get the value of Other Attribute`, but have specified an empty string, are not copied to Launch.

### JS Object {#js-object}

`JS Object` data element types that don't contain a path are not copied to Launch.

### URL Parameter {#url-parameter}

`URL Parameter` data element types that don't contain a parameter name are not copied to Launch.

## Rule Events {#rule-events}

### Page Top {#page-top}

In Launch, the `Page Top` event type is called `Library Load`, so all your rules with `Page Top` events in DTM become rules with a `Library Load` event in Launch.

## Rule Conditions {#rule-conditions}

### Browser {#browser}

The Browser condition in Launch has removed support for some older browsers that were supported in DTM. Only supported values are copied to Launch.

Supported values in Launch:

* Chrome
* IE
* Firefox
* Safari
* Mobile Safari

Unsupported values in Launch:

* Opera
* IE Mobile
* Opera Mini
* Opera Mobile
* OmniWeb

If you use a Browser condition that contains only values that are now unsupported, the condition is not copied to Launch.

### Cart Amount {#cart-amount}

The DTM `Cart Amount` condition has been replaced by the `Value Comparison` condition in Launch, so any `Cart Amount` conditions are copied to Launch as `Value Comparison` conditions.

`Cart Amount` conditions in DTM that don't define a data element, or that define a data element that no longer exists, are not copied to Launch.

### Cart Item Quantity {#cart-item-quantity}

The DTM `Cart Item Quantity` condition has been replaced by the `Value Comparison` condition in Launch, so any `Cart Item Quantity` conditions are copied to Launch as `Value Comparison` conditions.

`Cart Item Quantity` conditions in DTM that don't define a data element, or that define a data element that no longer exists, are not copied to Launch.

### Data Element {#data-element}

The DTM `Data Element` condition has been replaced by the `Value Comparison` condition in Launch, so any `Data Element` conditions are copied to Launch as `Value Comparison` conditions.

`Data Element` conditions in DTM that don't define a data element \(or that define a data element that no longer exists\) are not copied to Launch.

### Device {#device}

This condition does not exist in Launch and is not copied over.

### Logged In {#logged-in}

The DTM `Logged In` condition has been replaced by the `Value Comparison` condition in Launch, so any `Logged In` conditions are copied to Launch as `Value Comparison` conditions.

`Logged In` conditions in DTM that don't define a data element, or that define a data element that no longer exists, are not copied to Launch.

### Operating System {#operating-system}

The Operating System condition in Launch has removed support for some older operating systems that were supported in DTM. Only supported values are copied over to Launch.

Supported values in Launch:

* Windows
* MacOS
* Linux
* iOS
* Android
* Unix

Unsupported values in Launch:

* Symbian OS
* Maemo
* Blackberry

If you use an Operating System condition that contained only values that are now unsupported, the condition is not copied to Launch.

### Previous Converter {#previous-converter}

The DTM `Previous Converter` condition has been replaced by the `Value Comparison` condition in Launch, so any `Previous Converter` conditions are copied to Launch as `Value Comparison` conditions.

### Registered User {#registered-user}

The DTM `Registered User` condition has been replaced by the `Value Comparison` condition in Launch, so any `Registered User` conditions are copied to Launch as `Value Comparison` conditions.

## Rule Actions {#rule-actions}

### Custom Scripts {#custom-scripts}

The contents of custom scripts will be copied over as is.  We will not introspect the code and try to determine it's purpose, we will simply copy it over to custom code in Launch.  There are a few things you should know about this process.

1. Any custom script in DTM \(Non-sequential, Sequential JS, Sequential HTML\) without content is not copied to Launch.
2. ES6 is not supported in Launch. It's not supported in DTM either, but the compiler wouldn't catch it because it didn't exist when the DTM compiler was developed. If you are using ES6 code in DTM, the code is copied to Launch, but your build will fail with compile errors when you make a build. You can fix this before or after you upgrade.
3. In custom code, it is common to reference the `_satellite` object and various properties and functions that it provides.  Launch `satellite` object, but it is not structured the same as before.  Functions and properties that were supported in DTM have made the move to Launch, but many of the ones that were unsupported did not.  If you were using any of these functions, it is likely that your custom code will need to be updated.  Please see the Launch Object Reference to see what is supported on the new Launch `satellite` object.



