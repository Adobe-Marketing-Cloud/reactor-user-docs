# Mobile

Launch is the next generation of Adobe's website tag and mobile SDK management technology, built on the Adobe Experience Platform. It is built from the ground up to support an open and sustainable ecosystem where anyone can build their own integrations that Adobe customers can deploy to their websites and mobile applciations. It is an API first application so anything you can do through the UI you can also do programmatically through an API.

The basic Launch workflow:

1. [Set up groups and users](mobile.md#1-set-up-groups-and-users). 
2. [Log in](mobile.md#2-log-in).
3. [Create a property](mobile.md#3-create-a-property).
4. [Install Extensions](mobile.md#4-install-extensions).
5. [Create data elements and rules](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/getting-started/README.md#5-create-data-elements-and-rules).
6. [Test in your dev environment](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/getting-started/README.md#6-test-in-your-dev-environment).
7. [Add the SDKs to and intialize them in your app project](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/getting-started/mobile/README.md#7-add-sdks-to-and-intialize-them-in-your-app-project)
8. [Implement Solution APIs](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/getting-started/mobile/README.md#8-implement-solution-apis).
9. [Promote to Production](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/getting-started/mobile/README.md#9-promote-to-production).

For an introductory video, see [Introduction to Launch, by Adobe](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/getting-started/videos/README.md).

## 1. Set up groups and users

Launch is fully integrated with your Adobe ID. User permissions are managed through the Admin Console with other Adobe products and solutions from the Creative Cloud, Document Cloud, and Experience Cloud.

Unlike DTM, which has a role-based user management, Launch has rights-based user management. This means that instead of getting a role that implies a certain set of rights, individual rights must be explicitly granted. These rights are assigned to groups, and to gain access, users are added to the appropriate groups. Even if your company has access to Launch, users cannot complete any tasks until an Org Administrator explicitly grants them some rights.

For more information about how to create groups and add users for Launch, see [Users](https://github.com/jiabingeng/mobile-launch/tree/99e9070fe9a3f19319363a0299dd4c8ead31fb10/administration/users.md).

## 2. Log in

After Launch rights have been added to your Adobe ID, you need to log in to Launch by going to [https://launch.adobe.com](https://launch.adobe.com) or by logging in to the [Experience Cloud \(https://experiencecloud.adobe.com\)](https://experiencecloud.adobe.com), navigating to the Activation page, and clicking on Launch.

## 3. Create a property

In Launch, your first task is to create a property.

A property is a container that you fill with extensions, rules, data elements, and libraries to deploy tags to your site and configuration parameters to your mobile apps. Some users create a property for each website \(or group of closely related sites\) where they want to deploy the same set of tags. For mobile applications, a new property can contain multiple applications or one application depending on the need for different configurations.

For more about creating properties, see [Create a property](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/administration/companies-and-properties/README.md#create-a-property).

## 4. Install extensions

Extensions are one of the core features of Launch. An extension is an integration built by Adobe or an Adobe partner that adds new and endless options for the tags that you can deploy to your sites. If you think of Launch as an operating system, extensions are the apps that you install so that Launch can do the things you need it to do.

Launch is truly unique among other tag and mobile SDK management systems is because extensions can be built by anyone.

Here are some issues to consider when installing extensions:

* Do you need to drop a Facebook remarketing pixel on your site?

  Check out the extension that Facebook built. Do you want the same for Twitter or LinkedIn? Use those extensions.

* Do you need to run a survey? Look at Question Pro or Foresee.
* Do you need to manage privacy and consent from your end users to help out with GDPR?

  Take a good look at Evidon and Trust Arc.

* Would you like to see really granular insight into the behavior of individual users on your site? Take a look at Clicktale, and for mobile attribution, look at Branch.

  For more information about installing extensions, exapnd the [Mobile](https://launch.gitbook.io/launch-adobe-mobile-sdk-beta/v/staging/extension-reference/mobile) node.

## 5. Create data elements and rules

**Important**: This step is required for Mobile users **only** if you want to use Adobe Campaign.

**Data elements** are pointers to the information that you want to collect and send to different places on your page and include the following:

* A defined data layer in JSON
* DOM elements
* Cookies
* Session and local storage
* Just about everything else

Once defined in a data element, you can use the element anywhere in Launch for any extension. For more information, see [Data Elements](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/managing-resources/data-elements/README.md).

**Rules** are at the logical core of your implementation and control the what, when, where, and how. With rules, you can define an event, set conditions and exceptions, define the actions and order, and publish your changes to see the results. For more information, see [Rules](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/managing-resources/rules/README.md).

## 6. Test in your Dev environment

### Libraries and builds

Nothing in Launch is published automatically. Each set of changes you make is encapsulated into a [library](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/publishing/web/libraries/README.md). Each library you create automatically inherits anything upstream \(published, approved, or submitted\) as a baseline, so all you need to do is define the changes that you want to make. This library serves as the blueprint for a [build](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/publishing/web/builds/README.md). A build for a web property is the actual set of JavaScript files that are deployed and used on your site. A build for a mobile property is the JSON file used to configure your SDK and a manifest file that can be used with a dependency manager such as Maven, Carthage, or CocoaPods to bundle in extensions.

### Adapters

An adapter is a connection between Launch and your hosted configuration endpoint. When you generate a build, Launch connects to the server and published changes to the configuration.

For more information, see [Adapters](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/administration/adapters/README.md).

### Environments

Each library is created in an environment, and an environment defines how you build and test configuration changes to your applications. For each environment created you will specify a name and choose the Adobe Hosted adapater that was pre-created for you. You can add as many developemtn environments as you wish, but you can only define a single stage and production environement.

### Publish a build to Dev

Now that you understand the basic components, the publishing process should make more sense.

To publish, you need to complete the following tasks:

1. Create an adapter.
2. Create a dev environment by using the adapter you created.
3. Copy the configuration code snippets from your dev environment to initialize the SDK in your development app.
4. Create a library and assign it to the dev environment you created.
5. Build your library.

## 7. Add the SDKs to and intialize them in your app project

Complete the following steps:

1. Add the SDKs and dependencies to your project by completing one of the following tasks:

   a. Add the SDKs through dependency managers

   b. Add the SDKs manually.

2. Import the SDK headers in your app project.
3. Register your extensions with the SDK Core extension.
4. Initiate the SDKs wiht the Launch app/environment IDs.
5. Implement logging

   The following logging levels are supported in the Adobe Experience Plaform SDKs:

   * Error
   * Debug
   * Trace
   * Verbose

   Logging for each level is cumulative with the level above it. For example, the Trace level includes the Error and Debug levels, and the Verbose level includes the Trace, Debug, and Error levels.

6. Implement Lifecycle Metrics
   * For more information about Lifecycle start and stop, see [Lifecycle Methods](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/lifecycle/lifecycle-methods/README.md). 
   * For information about when Lifecycle should be implemented, see [Lifecycle Extension in Android](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/lifecycle/lifecycle-extension-in-android/README.md) and [Lifecycle Extension in iOS](https://github.com/jiabingeng/mobile-launch/tree/85c595c9e56c9a817ba5da8d71e656d20c5f558e/getting-started/lifecycle/lifecycle-extension-in-ios/README.md).

## 8. Implement the solution APIs

Implement the solution APIs in the following order:

1. Implement Adobe Analytics
2. Implement Adobe Audience Manager.
3. Implement Adobe Campaign
4. Implement Adobe Target.

## 9. Promote to production

After you test your build in your dev environment, the promotion process is simple. Before you try it out, ensure that you create your stage and production environments and put the embed codes in the necessary places.

**Tip**: You can reuse existing adapters.

Promoting a library all the way through to production will typically require coordination among the following roles:

1. A **Developer** has Develop rights and submits the library, which moves the library to the Submitted state.
2. An **Approver** has Approve rights, can build the library to the stage environment, and approve it after testing. This process moves the library to the approved state, but only one library can be submitted and approved at a time.
3. A **Publisher** has Publish rights and can build the library to the production environment.

You can assign all these rights to one person. For more information about the different states and options that are available during the publishing process, see [Approval Workflow](https://github.com/jiabingeng/mobile-launch/tree/7726cc3834e27087359af611628068ee90aab955/launch-adobe-mobile-sdk-beta/v/doc-dev-rekha/publishing/web/approval-workflow/README.md).

## Additional resources

To learn more about Launch, see the following resources:

* ​[**Launch Community**](https://forums.adobe.com/community/experience-cloud/platform/launch)**:** Ask and answer questions, submit ideas, vote on the ideas of others. Log in with your Adobe ID.
* ​[**Launch Webinars**](https://adobe.com/go/launchme)**:** Sign up for upcoming webinars and watch recordings of past webinars.
* ​[**Developer Docs**](http://developer.adobelaunch.com/)**:** Get involved with the Launch developer community to build extensions or use the Launch APIs
* ​[**Videos**](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/67a59a7519514467a713016adfe46d999fe330d8/getting-started/videos.html)​

  These videos introduce you to Launch concepts and tasks.

