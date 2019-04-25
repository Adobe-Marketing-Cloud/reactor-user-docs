# Overview

Launch empowers anyone to build and maintain their own integrations with Launch, called extensions. These extensions are available to web and mobile Launch customers in an app-store experience, so customers can quickly install, configure, and deploy their integrations.

### Extension catalog

### Rule builder

### Data elements

### Enterprise publishing

### Light, modular container tag

Performance is very important to Adobe. Launch is designed to deliver and run marketing and advertising technologies on your web site as efficiently as possible using today's best practices. Adobe technologies deployed together through Launch are faster than any other deployment method. You can read more about performance and our perspective in the [Performance Whitepaper](https://medium.com/launch-by-adobe/adobe-web-browser-technology-performance-477c2bfeaa98).

These are the questions received most often from customers and partners since the Launch announcement. If you have other questions, please ask in the Adobe Community on the main Launch page located at [https://adobe.com/go/launchme](https://adobe.com/go/launchme).

Launch is the next generation of website tag and mobile SDK management capabilities from Adobe. Launch gives customers a simple way to deploy and manage all of the analytics, marketing, and advertising integrations necessary to power relevant customer experiences.

Launch empowers anyone to build and maintain their own integrations with Launch, called Extensions. These extensions are available to web and mobile Launch customers in an app-store experience, so customers can quickly install, configure, and deploy their integrations.

## Key benefits

Here are the benefits for using Adobe Launch:

* Faster time to value with the ability to dynamically deploy changes to your website or mobile app
* Trustworthy data through centralized collection, organization, and delivery using data elements
* Compelling experiences through the integration of data and marketing technology using rule builder

## Key features

Here are the key features that are available in Launch:

### Extensions

* **Web**

  An extension is a package of code \(JavaScript, HTML, and CSS\) that extends the Launch UI and client functionality. You can build, manage, and update your integrations using a virtually self-service interface. You can think of Launch as an operating system, and extensions are the apps you use to achieve your tasks.

* **Mobile**

  Mobile extensions are comprised of a Launch UI configuration screen and native SDK components that work with the core Adobe Experience Platform SDKs to deliver functionality to mobile apps.

**Important**: In Android and iOS extensions, only contents on secure http connections \(`https`\) are served. When a URL that contains `http://` is passed in, the connections are blocked.

### Extension Catalog

Browse, configure, and deploy marketing/advertising tools built and maintained by independent software vendors.

### Rule Builder

Create robust rules that combine multiple events, sequenced in the way that you determine using if/then logic with conditions and exceptions. Extensions provide options for:

* Events
* Conditions
* Exceptions
* Actions

### Data Elements

Collect, organize, and deliver data across web-based marketing and advertising technology.

### Enterprise Publishing

The publishing process enables teams to dynamically publish updates to both web pages and applications. Different people can create an implementation, approve it, and publish.

Here are some benefits to this publishing process:

* Changes to your implementation are encapsulated within libraries you define ​
* You specify where and when you want your changes deployed ​
* Multiple libraries can be built in parallel by different teams ​
* Unlimited development environments ​
* Deliberate, permissioned process for merging libraries together ​

### Open APIs

Automate implementations of individual technologies, or a group of technologies.

* Launch interacts with the Reactor APIs ​
* Deployments can be automated through APIs ​
* Integrate the Launch APIs with your own internal systems ​
* You can build your own user interface, if desired ​

## Requirements

Launch requires the following:

* You must be an Adobe Experience Cloud customer.
* You must deploy the Launch or DTM embed code on your web pages.
* For mobile, you must integrate the Adobe Experience Platform Mobile SDKs into your application.

## Additional highlights for Web

### Light, Modular Container tag

The Launch container tag is 60% lighter than DTM and 40% lighter than Google Tag Manager. The content of your container is minified, including your custom code. Everything is modular. If you don't need an item, it is not included in your library. The result is an implementation that is fast and compact. See [Minification](launch-reference/publishing/builds.md).

Launch provides several improvements over similar systems, including:

* No use of `document.write ()` where Chrome doesn't allow it ​
* The Page Top and Page Bottom rules are bundled into the main library to minimize unnecessary HTTP calls ​ ​
* Custom action scripts within a rule can be loaded in parallel, but are executed sequentially ​
* If you avoid Page Top and Page Bottom rules, the code is mostly asynchronous, with a path to getting fully async ​

## Adobe Launch FAQ

#### What is Launch?

Launch is the next-generation of the Adobe tag-management capability, built into the Adobe Experience Cloud. Launch enables clients to:

* Deploy client-side web products using integrations called _extensions_
* Consistently capture, define, manage, and share data between marketing and advertising products from other vendors and from Adobe

Launch is an advanced JavaScript delivery system that evaluates conditions and executed actions to efficiently and effectively deploy client-side libraries and products. It provides a highly scalable approach to managing and building extensions, together with a robust set of APIs for programmatic interaction with the Adobe Experience Cloud.

#### Is Launch just an updated DTM?

No. Launch is an entirely new product with a new code base. The system has been redesigned from scratch using modern front-end development practices and an API-first approach. Everything is built on a robust set of APIs, which makes the system very powerful and highly flexible.

#### Will the current DTM product remain available?

Yes, legacy DTM \(the existing production version\) will continue to be supported until the end of 2020. Adobe will continue to fix any significant bugs and ensure consistent performance. At this time, no major feature enhancements are planned for legacy DTM.

For information about the DTM sunsetting schedule, see [DTM Plans for a Sunset](https://forums.adobe.com/community/experience-cloud/platform/launch/blog/2018/10/05/dtm-plans-for-a-sunset) in the Adobe community forums.

Many customers see Launch implementations as an opportunity to start from scratch and cleanup many issues they have with current implementations. If this does not describe you, you can copy an existing DTM property into Launch and save yourself a bunch of effort. [See the Upgrade FAQ](launch-reference/upgrade-from-dtm-to-launch/upgrade-faq.md) for more information.

#### How much does Launch cost?

There is no additional charge for Launch. It is available for any Adobe Experience Cloud customer.

#### Will I have to change the embed codes in my current DTM implementation?

No, you won't have to change your production embed codes if you're currently using the existing \(legacy\) DTM system. You can continue to work in your current DTM Company and Web Properties without worrying about changing that embed code.

If you'd like, you can link your DTM Production embed code with your Launch Production embed code so you don't have to change your page tags. See [Link DTM Embed Code](launch-reference/upgrade-from-dtm-to-launch/link-dtm-embed-code.md) for more information.

#### I heard there are plug-ins now. What's that about?

Launch uses plug-ins called [Extensions](./#extensions). Launch is built into the Adobe Experience Cloud and it is fully extensible. Customers, Adobe Partners, agencies, and marketing or advertising technology vendors will soon be able to build Launch extensions that add new functionality or modify existing functionality. The system allows partners and clients to build, manage, and update their own integrations. This is just one way Adobe is opening up the Adobe Experience Cloud so customers and partners can build products and businesses on the Platform, and so everyone can more easily connect Adobe technology to the marketing and advertising technologies from other vendors.

#### Will all third-party extensions be available right away?

Extensions are available for all Adobe solutions and for a growing number of independent vendors. New extensions are always under development and more are added to the catalog every week.

Each extension developer maintains their own roadmap and schedule for their extensions, the Launch team does not have control or influence.

#### When will clients or partners be able to build extensions?

Anyone can build an extension now. To get started, go to [developer docs](https://developer.adobelaunch.com/guides/extensions/). Currently, all extensions are open to all Launch users, but later this year Adobe will add the ability to build an extension that can only be seen by your company and a whitelist of others that you specify.

#### Will Launch meet my company's security standards?

Launch is SOC-2 and Gramm-Leach-Bliley Act ready. Launch also offers the capability of being self-hosted. The JavaScript libraries can be served from your own servers, or the CDN of your choice. For IT and security teams, this gives you the ability to run automated testing, to check the files into your own version control system, and to fully comply with any internal production migration processes, security-related or otherwise.

#### I have a project coming up very soon. Should I use Launch or DTM?

Launch. Any new deployments done with DTM will need to be migrated eventually as DTM reaches its sunset phase.

#### Does Launch support single page apps \(SPAs\) and my favorite framework?

Yes. Launch has capabilities to give users and extension developers flexibility in collecting, managing, and distributing data within single page application experiences or Ajax-heavy pages or sites. This applies regardless of your development framework preferences, whether that's Angular, React.js, Ember, Meteor, etc.

Read more about the benefits of using Launch for your SPAs on the [Launch blog](https://medium.com/launch-by-adobe/the-top-5-reasons-that-launch-is-better-for-single-page-applications-5a7b9880939f).

#### Does Launch support dynamic data layers?

Yes. Launch includes an extension that specializes in listening for changes in dynamic data layers.

#### Which event types does Launch support?

Event types are available through extensions. The Launch Core extension includes 30 built-in event types. Other extensions add additional event types. For example, the YouTube extension includes four video event types: play, pause, end, and time played. Through extensions, Launch can support any other browser event types or synthetic event types, such as specific visitor activity sequences.

#### Will the new Launch speed up \(or slow down\) my web site?

Performance is very important to us. Launch is designed to deliver and run marketing and advertising technologies on your web site as efficiently as possible using today's best practices. Adobe technologies deployed together through Launch are faster than any other deployment method. You can read more about performance and our perspective in the [Performance Whitepaper](https://medium.com/launch-by-adobe/adobe-web-browser-technology-performance-477c2bfeaa98).

#### Which browsers will Launch support?

Browser support in the Launch client-side libraries:

* Chrome: latest
* Safari: latest
* Firefox: latest
* Internet Explorer: 10 and above \(support for IE 10 will be dropped in summer of 2019\)
* iOS Safari: latest
* Android Chrome: latest

Browser support in the Launch application interface:

* Chrome: latest
* Safari: latest
* Firefox: latest
* Edge: latest

Legacy DTM supported older versions of Internet Explorer, but over the last few years, the percentage of overall web users with older, outdated browsers has dropped to a small segment for our clients. Most Adobe clients now leverage more modern web platform features in current browsers and create better user experiences, including single page applications and interactive Ajax-heavy web sites and pages. As most clients move to more modern approaches with their sites, they demand a solution like Launch that enables those approaches.

#### What if I have other questions?

These are the questions we've received most often from customers and partners since the Launch announcement. If you have other questions, please ask in the Adobe Community on the main Launch page located at [https://adobe.com/go/launchme](https://adobe.com/go/launchme).

Launch is just one example of where our platform is headed: more open, more integrated and as always dedicated to customer success.

