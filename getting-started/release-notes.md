# Release Notes

## April 3, 2018

### Features

#### Interface improvements

* Active Library has been moved to the top right to make more space for content
* Action buttons moved to the top right
* Bulk Edit now lists smarter actions, collapsed into a More menu on smaller screens
* Form fields now have default focus

## March 20, 2018

### Features

#### Analytics Extension 1.2.0

* Updates AppMeasurement.js to 2.8.0
* Adds support for server-side forwarding

#### Adobe Analytics for Video Extension 1.0.0

The [Adobe Analytics for Video Extension](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/getting-started/c_extension-va.md) adds the core Video Analytics JavaScript library. This library provides the functionality for adding the mediaHeartbeat instance to a Launch site or project. The Adobe Analytics for Video Extension \(VA Extension\) requires two additional extensions:

* Analytics Extension
* Experience Cloud ID Extension

#### Experience Cloud ID Extension 3.1.0

* Updates visitor.js to 3.1.0
* Adds two configuration properties: `resetBeforeVersion` and `serverState`

#### Exchange Link on Extension Cards \(Support for future use\)

Support was added to extension cards on the catalog page for future Learn More links to more information on the Extension Detail page on adobeexchange.com

#### Client-side enhancement

Event details are copied to the top-level event object \(`%event.detail%` in text fields and `event.detail` in custom code\)

### Bug fixes

Fixed the following issues in the Core extension:

* Custom code windows were throwing `document.write` errors and not executing in async deployments
* Main modules were not included in a library
* Problems occurred with min and max values on the Random Number data element

## March 13, 2018

### Features

#### Delete resources

You can delete data elements, rules, and extensions. See [Delete Resources](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/getting-started/delete.md).

#### Link DTM Embed Code to Launch

When you link your DTM embed code to Launch, you can keep your DTM production embed code on a page, but serve Launch files there instead of DTM. See [Link DTM Embed Code to Launch](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/getting-started/embed-code-link.md).

## March 6, 2018

### Enhancements

#### User interface changes

This release includes several interface enhancements:

* Rebranding of Marketing Cloud to Experience Cloud
* Element styling

### Bug fixes

Fixed an issue that caused a database query to take a long time to run and cause occasional 502 errors on API queries

## February 22, 2018

### Features

#### Adobe Target Extension 0.4.1

* Added Adobe Exchange listing to extension.json
* Added checks to see if Target is disabled and if Authoring is enabled

### Bug fixes

* Fixed an error in the Adobe Target Extension that prevented the Visual Experience Composer from unhiding the page when deployed through Launch.

## February 8, 2018

### Features

#### Adobe Analytics Extension 1.1

* AppMeasurement has been updated to version 2.6
* The initialized Analytics tracker is now exposed through a shared module in the Launch extension so other extensions can include code to interact with it.

#### Adobe Target Extension 0.4.0

* Updated views in extension configuration screens
* at.js has been updated to version 1.2.3 \(adds support for JSON offers\)

#### Active Library enhancements

* Enable/Disable actions ask if you want to add to your Active Library
* Create a new library from the Active Library drop down

### Bug fixes

Fixed an error in the Adobe Analytics Extension that caused "Error, missing Report Suite ID in AppMeasurement initialization" to appear in the browser console.

## February 1, 2018

### Features

#### Akamai Cache Control Headers

Cache control headers are now automatically set for libraries hosted on Akamai \(assets.adobedtm.com\). Previously, we did not set cache control headers for any files hosted on assets.adobedtm.com.

* Production builds: Cache control headers are set to 60 minutes
* Staging builds with "-staging" in the filename: Cache control headers are set to 0 minutes
* Dev builds with "-development" in the filename: Cache control headers are set to 0 minutes
* Launch Staging builds without "-staging" in the filename: The default of 60 minutes is inherited
* Launch Development builds without "-development" in the filename: The default of 60 minutes is inherited

Note: It is up to browsers to receive and respect the cache control headers. Some browsers might ignore them.

Important: Launch developers who do not have "-development" or "-staging" in their Environment embed codes need to re-create their Development and Staging environments to get the 0 cache control header. If you don't re-create the environments, you'll have the same 60-minute cache control as the production libraries.

## January 18, 2018

### Features

#### Rule Ordering

Events in rules can now be assigned an order. When an event is triggered, any rules that use that event are executed in the order defined. Lower numbers run first \(1 comes before 10\). See [Rule ordering](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/getting-started/rules.md) for more information.

#### Set Active Library

Set a new or existing library as your active library. When creating/editing rules, data elements, or extensions, you'll now have an option to save and build to your active library. This will immediately save your change to your library and execute a build. The status of the build can also be seen.

#### Multiple arguments in the logger

You can now pass actual objects to the log function and view them as objects in the browser console when using `_satellite.debug()`. This makes the Launch logger behave a lot more like console.log. To enable this change, there is no longer a persistent history attached to the `_satellite.debug()` function, so when you call it for the first time, you'll no longer see a history of past events. You will see any debug messages from that point forward.

## January 10, 2018

### Features

#### Asynchronous Deploy of Launch

* On-page

  The Launch library now includes support for running asynchronously. There are important ramifications for how this changes what happens in your library. You should read the [Async documentation](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/getting-started/async.md) before you do anything.

* Async Toggle on Environments

  When retrieving the embed code for an environment, you can now flip a toggle switch to get the embed code if you want the library to load asynchronously.

#### Core Extension enhancements

The following have been added to the core extension:

* Random Number Data Element
* Page Info Data Element
* Date Condition
* Sampling Condition

#### User interface enhancements

* Information Videos on Empty List Pages
* Persistent filters

### Other changes

The following changes were made to be more descriptive of the actual behavior in sync and async scenarios:

* Page Top is now called Library Loaded
* On Load is now called Window Loaded

### Bug fixes and enhancements

* Fixed an issue where the Launch library would load twice in certain edge cases.
* There are now audit log entries for Property Delete.
* Improved the load speed of the Revision Selector when you quickly click from one entry to another.
* Help links now open in a new tab.

## Initial release

Release date: **November 8, 2017**

Important: Launch is being rolled out incrementally to Adobe Experience Cloud customers. If you have would like a chance to get early access, please put let us know by entering the required information in the [Launch Release Form](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?WVFJ3K).

This is the first release of Launch.

Launch is the next-generation of tag management capabilities from Adobe. Launch gives customers a simple way to deploy and manage all of the analytics, marketing, and advertising tags necessary to power relevant customer experiences.

Launch empowers anyone to build and maintain their own integrations with Launch, called Extensions. These extensions are available to Launch customers in an app-store experience so they can quickly install, configure, and deploy their tags.

Launch enables you to:

Launch is offered to Adobe Marketing Cloud customers as an included, value-add feature. Launch is an entirely new product with a new code base, designed to replace the previous Dynamic Tag Management \(DTM\) service. However, DTM will continue to be supported for the foreseeable future. Adobe will continue to fix any significant bugs and ensure consistent performance. At this time, no major feature enhancements are planned for legacy DTM.

### Key benefits

* Faster time to value
* Trustworthy data through centralized collection, organization, and delivery using data elements
* Compelling experiences through the integration of data and marketing technology using rule builder

### Key features

#### Extensions

An extension is a package of code \(JavaScript, HTML, and CSS\) that extends the Launch UI and client functionality. ​Build, manage, and update your integrations using a virtually self-service interface. You can think of Launch as an operating system, and extensions are the apps you use to achieve your tasks.

#### Extension Catalog

Browse, configure, and deploy marketing/advertising tools built and maintained by independent software vendors.

#### Rule Builder

Create robust rules that combine multiple events, sequenced in the way that you determine using if/then logic with conditions and exceptions. Extensions provide options for:

* Events
* Conditions
* Exceptions
* Actions

The rule builder includes real-time error checking and syntax highlighting for your custom code.

When the criteria outlined in your rules are met and conditions are satisfied, the actions you define are executed in order.

#### Data Elements

Collect, organize, and deliver data across web-based marketing and advertising technology.

#### Enterprise Publishing

The publishing process enables teams to publish code to pages. Different people can create an implementation, approve it, and publish it to your pages.

* Changes to your code are encapsulated within libraries you define ​
* You specify where and when you want your code deployed ​
* Multiple libraries can be built in parallel by different teams ​
* Unlimited development environments ​
* Deliberate, permissioned process for merging libraries together ​

#### Open APIs

Automate implementations of individual technologies, or a group of technologies.

* Launch interacts with the Reactor APIs ​
* Deployments can be automated through APIs ​
* Integrate the Launch APIs with your own internal systems ​
* You can build your own user interface, if desired ​

#### Light, Modular Container tag

The Launch container tag is 60% lighter than Adobe Tag Manager and 40% lighter than Google Tag Manager. The content of your container is minified, including your custom code. Everything is modular. If you don't need an item, it is not included in your library. The result is an implementation that is fast and compact.

## Other highlights

Launch provides several improvements over similar systems, including:

* No use of `document.write ()` where Chrome doesn't allow it ​
* The Page Top and Page Bottom rules are bundled into the main library to minimize unnecessary HTTP calls ​ ​
* Custom action scripts within a rule can be loaded in parallel, but are executed sequentially ​
* If you avoid Page Top and Page Bottom rules, the code is mostly asynchronous, with a path to getting fully async ​

