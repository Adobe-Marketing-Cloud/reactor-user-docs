# Overview

Launch is the next-generation of tag management capabilities from Adobe. Launch gives customers a simple way to deploy and manage all of the analytics, marketing, and advertising tags necessary to power relevant customer experiences.

Launch empowers anyone to build and maintain their own integrations with Launch, called Extensions. These extensions are available to Launch customers in an app-store experience so they can quickly install, configure, and deploy their tags.

Launch is offered to Adobe Experience Cloud customers as an included, value-add feature. Launch is an entirely new product with a new code base, designed to replace the previous Dynamic Tag Management \(DTM\) service. However, DTM will continue to be supported for the foreseeable future. Adobe will continue to fix any significant bugs and ensure consistent performance. At this time, no major feature enhancements are planned for legacy DTM.

## Key benefits

* Faster time to value
* Trustworthy data through centralized collection, organization, and delivery using data elements
* Compelling experiences through the integration of data and marketing technology using rule builder

## Key features

### Extensions

An extension is a package of code \(JavaScript, HTML, and CSS\) that extends the Launch UI and client functionality. ​Build, manage, and update your integrations using a virtually self-service interface. You can think of Launch as an operating system, and extensions are the apps you use to achieve your tasks.

### Extension Catalog

Browse, configure, and deploy marketing/advertising tools built and maintained by independent software vendors.

### Rule Builder

Create robust rules that combine multiple events, sequenced in the way that you determine using if/then logic with conditions and exceptions. Extensions provide options for:

* Events
* Conditions
* Exceptions
* Actions

The rule builder includes real-time error checking and syntax highlighting for your custom code.

When the criteria outlined in your rules are met and conditions are satisfied, the actions you define are executed in order.

### Data Elements

Collect, organize, and deliver data across web-based marketing and advertising technology.

### Enterprise Publishing

The publishing process enables teams to publish code to pages. Different people can create an implementation, approve it, and publish it to your pages.

* Changes to your code are encapsulated within libraries you define ​
* You specify where and when you want your code deployed ​
* Multiple libraries can be built in parallel by different teams ​
* Unlimited development environments ​
* Deliberate, permissioned process for merging libraries together ​

### Open APIs

Automate implementations of individual technologies, or a group of technologies.

* Launch interacts with the Reactor APIs ​
* Deployments can be automated through APIs ​
* Integrate the Launch APIs with your own internal systems ​
* You can build your own user interface, if desired ​

### Light, Modular Container tag

The Launch container tag is 60% lighter than DTM and 40% lighter than Google Tag Manager. The content of your container is minified, including your custom code. Everything is modular. If you don't need an item, it is not included in your library. The result is an implementation that is fast and compact. See [Minification](https://github.com/Aaronius/gitbooktest/tree/987ef7c271fb08eafc6c7a4f04e167de2bae6a31/build.md).

## Other highlights

Launch provides several improvements over similar systems, including:

* No use of `document.write ()` where Chrome doesn't allow it ​
* The Page Top and Page Bottom rules are bundled into the main library to minimize unnecessary HTTP calls ​ ​
* Custom action scripts within a rule can be loaded in parallel, but are executed sequentially ​
* If you avoid Page Top and Page Bottom rules, the code is mostly asynchronous, with a path to getting fully async ​

## Requirements

Launch requires the following:

* You must be an Adobe Experience Cloud customer.
* You must deploy the Launch or DTM embed code on your web pages.

## Adobe Launch FAQ

Frequently asked questions about dynamic tag management.

A FAQ about the new version of dynamic tag management, announced in March 2017.

### What is Launch?

Launch is the next-generation of the Adobe tag-management capability, built into the Adobe Cloud Platform. Launch enables clients to:

* Deploy client-side web products using integrations called _extensions_
* Consistently capture, define, manage, and share data between marketing and advertising products from other vendors and from Adobe

Launch is an advanced JavaScript delivery system that evaluates conditions and executed actions to efficiently and effectively deploy client-side libraries and products. It provides a highly scalable approach to managing and building extensions, together with a robust set of APIs for programmatic interaction with the Adobe Cloud Platform.

### Is Launch just an updated DTM?

No. Launch is an entirely new product with a new code base. The system has been redesigned from scratch using modern front-end development practices and an API-first approach. Everything is built on a robust set of APIs, which makes the system very powerful and highly flexible.

### Will the current DTM product remain available?

Yes, legacy DTM \(the existing production version\) will continue to be supported for the foreseeable future. Adobe will continue to fix any significant bugs and ensure consistent performance. At this time, no major feature enhancements are planned for legacy DTM.

The Launch team is working to make the migration process from legacy DTM to Launch as easy as possible so customers can take advantage of more than twenty new features, extensions, and APIs that Launch provides.

### How much does Launch cost?

There is no additional charge for Launch. It is available for any Adobe Experience Cloud customer.

### Will I have to change the embed codes in my current DTM implementation?

No, you won't have to change your production embed codes if you're currently using the existing \(legacy\) DTM system. You can continue to work in your current DTM Company and Web Properties without worrying about changing that embed code. The product team has not finalized the migration process just yet, but they are working to make it as easy and automated as possible. For more details, see the [Launch help docs](https://marketing.adobe.com/resources/help/en_US/experience-cloud/launch/embed-code-link.html), and this [blog post](https://medium.com/launch-by-adobe/migrating-from-dtm-to-launch-57548251a86d).

### I heard there are plug-ins now. What's that about?

Launch is built into the Adobe Cloud Platform and it is fully extensible. Customers, Adobe Partners, agencies, and marketing or advertising technology vendors will soon be able to build Launch extensions that add new functionality or modify existing functionality. The system allows partners and clients to build, manage, and update their own integrations. This is just one way Adobe is opening up the Adobe Cloud Platform so customers and partners can build products and businesses on the Platform, and so everyone can more easily connect Adobe technology to the marketing and advertising technologies from other vendors. Over time, this will be the place for customers to install and configure all of their client-side technologies.

### Will all third-party extensions be available right away?

Extensions will be available for all Adobe solutions and for a select group of independent vendors when Launch is released. The product team is working closely with several technology partners to ensure the availability of these extensions upon release. After that initial release of Launch, the product team will work to expand the number of extensions as quickly as possible. Because extensions can be built, managed, and updated by the Extension developer, vendors won't have to wait for Adobe engineering to build them, so this should be a very rapid process going forward.

### When will clients or partners be able to build extensions?

After general availability, Launch will open its virtually self-service portal that extension developers can use to build their own integrations with the Adobe Cloud Platform.

### Will Launch meet my company's security standards?

Launch is SOC-2 and Gramm-Leach-Bliley Act ready. Launch also offers the capability of being self-hosted. The JavaScript libraries can be served from your own servers, or the CDN of your choice. For I.T. and security teams, this gives you the ability to run automated testing, to check the files into your own version control system, and to fully comply with any internal production migration processes, security-related or otherwise.

### I have a project coming up very soon. Should I wait for Launch?

If you are already using legacy DTM, or are currently deploying DTM, you should continue to do so. Don't wait. Move your projects forward using the current DTM. Then, when you're ready to move to Launch, the migration process will make it as easy and automated as possible \(no on-page embed code changes, and automated migration of Rules and Data Elements\).

### Which capabilities exist in Launch that don't exist in legacy DTM?

Launch will offer four major capabilities that aren't comparable to legacy DTM:

* Deploy non-Adobe client-side browser technologies quickly and easily

  Using extensions, clients and partners can easily control in-browser technologies in the interface, without managing custom code.

* Enterprise-grade publishing

  Compartmentalize and control each piece of your libraries to deploy precisely what you need, where you need it, and when you need it.

* Robust approval workflows

  Flexible approval workflows allow custom processes to match your existing internal approval processes.

* Granular rights management

  Administrators will designate which extensions users can, and can't use. They will also control which areas within Launch are accessible to certain users.

### Does Launch support single page apps and my favorite framework?

Yes. Launch has capabilities to give users and extension developers flexibility in collecting, managing, and distributing data within single page application experiences or Ajax-heavy pages or sites. This applies regardless of your development framework preferences, whether that's Angular, React.js, Ember, Meteor, etc.

### Does Launch support dynamic data layers?

Yes. Launch includes an extension that specializes in listening for changes in dynamic data layers.

### Which event types does Launch support?

Event types are available through extensions. The pre-loaded DTM extension includes 30 built-in event types. Other extensions could add additional event types. For example, the YouTube extension includes four video event types: play, pause, end, and time played. Through extensions, Launch can support any other browser event types or synthetic event types, such as specific visitor activity sequences.

### Will the new Launch speed up \(or slow down\) my web site?

Launch is designed to deliver and run marketing and advertising technologies on your web site as efficiently as possible using today's best practices. When used properly, Launch has proven to improve performance of web sites over alternative methods of providing similar functionality.

### Which browsers will Launch support?

Browser support in the Launch client-side libraries:

* Chrome \(latest\)
* Safari \(latest\)
* Firefox \(latest\)
* Internet Explorer \(9 and above\)
* iOS Safari \(latest\)
* Android Chrome \(latest\)

Browser support in the Launch application interface:

* Chrome \(latest\)
* Safari \(latest\)
* Firefox \(latest\)
* Internet Explorer \(11 and above\)

Legacy DTM supported older versions of Internet Explorer, but over the last few years, the percentage of overall web users with older, outdated browsers has dropped to a small segment for our clients. Most Adobe clients now leverage more modern web platform features in current browsers and create better user experiences, including single page applications and interactive Ajax-heavy web sites and pages. As most clients move to more modern approaches with their sites, they demand a solution like Launch that enables those approaches.

### Does the new Launch work on native mobile apps?

Adobe continues to recommend the [Mobile Services App SDK](http://www.adobe.com/solutions/digital-marketing/mobile-services/app-sdk.html) to implement data collection and delivery in a native mobile app environment. With Adobe mobile services, the process is streamlined with a single SDK that works with multiple Adobe Cloud Platform solutions. Going forward, you will see additional tag management-like functionality in the Mobile Services interface as the Launch and Mobile teams continue working closely together for more seamless Cloud Platform access and user experiences.

### What if I have other questions?

These are the questions we've received most often from customers and partners since the Launch announcement. If you have other questions, please ask in the Adobe Community on the main Launch page located at [https://adobe.com/go/launchme](https://adobe.com/go/launchme).

Launch is just one example of where our platform is headed: more open, more integrated and as always dedicated to customer success.

