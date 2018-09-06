# Environments

The publishing workflow encompasses multiple environments. At a minimum, you will have:

* One Development environment
* One Staging environment
* One Production environment

Tip: You can create multiple development environments if it is useful for you. This is most common on larger teams with multiple developers working on different projects at the same time.

## Destination

Extensions, rules, and data elements are building blocks. When you want to make your application do something, these building blocks are added to libraries and then a library is "built" into a build.

When you create a library, you must assign it to an environment.  When the library is built, Launch uses the settings from the assigned environment to determine the following:

1. Destination - This is the location where you want your build to be deployed. It is controlled by selecting an adapter for the environment to use.
2. File Format - You can get a deployable set of files or have it zipped up in an archive format. This is controlled by the archive settings.
3. Embed Code - This is the code you'll use to deploy your build at run-time and will be different based on property type.
4. Open the Environments tab.
5. Click Create New Environment.
6. Select the type of environment you want to create.
   * Development

     The environment where you create and edit, events, configurations, and so on.

   * Staging

     The environment where you test and approve your changes.

   * Production

     The environment where your embed codes are placed in the pages or applications that are available to the public.
7. Select your adapter.
8. \(Optional\) Enable Create Archive if you want your build delivered as a .zip package. If you want to encrypt the .zip file, enable Encrypt Archive and enter an encryption password. Enter the location where the library is hosted. The path can be either a full URL or a relative path that can be used across multiple domains.
9. Click Save.
10. In the Web Install Instructions dialog box, select whether to load the library asynchronously. If you choose to load the library asynchronously, copy the embed code provided in the dialog box.  You can also install your embed code later by clicking the Install icon for that environment in your Environments list.  Refer to the information below.
11. Repeat for each environment in your development, approval, and publishing change.

After the environments are created, you are ready to publish.

## Install the embed code

On the environment screen, you have a drop-down menu to select from the existing adapters on your property.

When a build is created, Launch will deliver that build to whatever location you've specified with the assigned adapter.

## Archive

Most builds consist of multiple files. Multi-file drafts contain a main library file \(linked in the embed code\) that contains internal references to the other files. Those other files are pulled in as needed.

By default, the archive option is `off`, and the build is delivered in a format that executes at run-time as is.  For Web properties, this is .js.  For Mobile properties, this is .json.

If you use the archive option, all build files are delivered as a .zip file \(optionally encrypted\).  This can be useful if:

1. You are self-hosting the library, but don't want to set up the SFTP adapter for delivery.
2. You need to run code analysis on the build prior to deployment.
3. You just want to look at the build contents to see what's in it.

## Embed code

The embed code is a `<script>` tag that you put on the pages of your site to load and execute the code you build in Launch.

You can choose to have this tag be synchronous or [asynchronous](../client-side-information/asynchronous-deployment.md).

The embed code is generated for you based on the environment configuration, so the only required action for you is to copy and paste them into your site on the pages where you want Launch to run.

Embed codes are generated and updated when you save the environment.

### Synchronous

If you load the library synchronously, when the browser reads the embed code, it retrieves the Launch library and executes it before continuing to load the page. This is also how [DTM](https://marketing.adobe.com/resources/help/en_US/dtm/) works.

In a synchronous deployment, the embed code consists of two `<script>` tags that you need to put within the HTML of your website. One `<script>` tag goes in the `<head>` and one goes at the footer in the bottom of the .

### Asynchronous

If you load the library asynchronously, the browser continues to load the page, retrieves the Launch library, and executes it in parallel. In this case, there is only one embed code, which you put in the `<head>`. Depending on what's in your Launch library, the switch from sync to async can change the behavior of your rules and other elements, so be sure to thoroughly test any changes.

For more information about asynchronous deployment, see [Asynchronous Deployment of Experience Cloud JavaScript](../client-side-information/asynchronous-deployment.md).

### Switching embed codes

The paths contained in the embed code depend on the configuration of the environment, so if you update the environment configuration, it is possible the embed codes will change.

Configuration changes that change your embed codes are:

* Switching from an Akamai adapter to an SFTP adapter \(or vice versa\)
* Marking the Archive box
* Updating the path field \(the embed code changes in real time as you update the path\)

## Create an Environment

When the embed code changes in Launch, you'll need to update the embed codes in your HTML. For obvious reasons, many people try to avoid changing embed codes after they've been implemented.Create an environment

