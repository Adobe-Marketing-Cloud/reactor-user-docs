# Environments

An _environment_ is a destination for deployment. An environment has a 1:1 relationship with an embed code.

Similar to the way a library is a set of instructions for how you want your website to behave, an environment is a set of instructions for:

* Where you want your build to be deployed
* The file format for the build
* The embed code for browsers to retrieve the build

Once a library has been assigned to an environment, any builds that are created for that library are completed according to the configuration specified by that environment.

The publishing workflow encompasses multiple environments. At a minimum, you will have:

* One Development environment
* One Staging environment
* One Production environment

Tip: You can create multiple development environments if it is useful for you. This is most common on larger teams with multiple developers working on different projects at the same time.

## Create an environment

1. Open the Environments tab.
2. Click Create New Environment.
3. Select the type of environment you want to create.
   * Development

     The environment where you create and edit, events, configurations, and so on.

   * Staging

     The environment where you test and approve your changes.

   * Production

     The environment where your embed codes are placed in the pages or applications that are available to the public.
4. Select your adapter.
5. \(Optional\) Select the archive format if you want your build delivered as a .zip package.
6. Click Create.

   The embed code for your environment is displayed.

7. Click Save.
8. Repeat for each environment in your development, approval, and publishing change.

After the environments are created, you are ready to publish.

## Embed code

The embed code is a `<script>` tag that you put on the pages of your site to load and execute the code you build in Launch.

You can choose to have this tag be synchronous or [asynchronous](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/administration/async.md).

The embed code is generated for you based on the environment configuration, so the only required action for you is to copy and paste them into your site on the pages where you want Launch to run.

Embed codes are generated and updated when you save the environment.

### Synchronous

If you load the library synchronously, when the browser reads the embed code, it retrieves the Launch library and executes it before continuing to load the page. This is also how [DTM](https://marketing.adobe.com/resources/help/en_US/dtm/) works.

In a synchronous deployment, the embed code consists of two `<script>` tags that you need to put within the HTML of your website. One `<script>` tag goes in the `<head>` and one goes at the footer in the bottom of the .

### Asynchronous

If you load the library asynchronously, the browser continues to load the page, retrieves the Launch library, and executes it in parallel. In this case, there is only one embed code, which you put in the `<head>`. Depending on what's in your Launch library, the switch from sync to async can change the behavior of your rules and other elements, so be sure to thoroughly test any changes.

For more information about asynchronous deployment, see [Asynchronous Deployment of Experience Cloud JavaScript](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/administration/async.md).

### Switching embed codes

The paths contained in the embed code depend on the configuration of the environment, so if you update the environment configuration, it is possible the embed codes will change.

Configuration changes that change your embed codes are:

* Switching from an Akamai adapter to an SFTP adapter \(or vice versa\)
* Marking the Archive box
* Updating the path field \(the embed code changes in real time as you update the path\)

When the embed code changes in Launch, you'll need to update the embed codes in your HTML. For obvious reasons, many people try to avoid changing embed codes after they've been implemented.

