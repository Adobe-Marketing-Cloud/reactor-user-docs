# Web

This section contains informnation to help you understand the publishing process for Web extensions.

For an introductory video, see [Publishing workflow](https://github.com/jiabingeng/mobile-launch/tree/b27aaefdfe0684053c696a8d3ba01c6dd6ef4903/publishing/getting-started/videos.md).

There are a few components and relationships that are important to understand in order to take full advantage of the publishing workflow. These are:

* [Libraries](https://github.com/jiabingeng/mobile-launch/tree/b27aaefdfe0684053c696a8d3ba01c6dd6ef4903/publishing/web/web/libraries.md)

  A library is a set of instructions for how extensions, data elements, and rules will interact with one another and with your website. Libraries are compiled into builds. A library can contain as many changes as you are comfortable making or testing at once.

* [Builds](https://github.com/jiabingeng/mobile-launch/tree/b27aaefdfe0684053c696a8d3ba01c6dd6ef4903/publishing/web/web/builds.md)

  A build is the actual set of files containing the code that is delivered to each user's browser when that user views your site.

* [Environments](https://github.com/jiabingeng/mobile-launch/tree/b27aaefdfe0684053c696a8d3ba01c6dd6ef4903/publishing/web/web/environments.md)

  An environment is a set of deployment instructions that tells Launch what format you'd like your build in and where you'd like that build delivered.

* [Adapters](https://github.com/jiabingeng/mobile-launch/tree/b27aaefdfe0684053c696a8d3ba01c6dd6ef4903/publishing/web/web/adapters.md)

  An adapter represents the connection details for the environment to deliver the build. You can choose to let Launch manage the hosting of your build, or you can provide information for your own host servers.

* [Embed Code](https://github.com/jiabingeng/mobile-launch/tree/b27aaefdfe0684053c696a8d3ba01c6dd6ef4903/publishing/web/web/environments.md#embed-code)

  The embed code is the set of script tags that you place within the HTML on your site. These tags tell each browser where to retrieve the build. The embed code is attached to an environment and can change when you make changes to your environment configuration.

The publishing process consists of:

1. Creating and editing libraries.
2. Testing the functionality of those libraries where you need to test them.
3. Deploying those libraries to your production site.

![](https://github.com/jiabingeng/mobile-launch/tree/b27aaefdfe0684053c696a8d3ba01c6dd6ef4903/publishing/.gitbook/assets/publishing.jpg)

For example, if you create a new checkout event, create a revenue data element related to that event, and make a change to the Adobe Analytics extension configuration to support the new event and data element, you can save them all at once to a checkout library, then test, approve, and publish them as a group.

