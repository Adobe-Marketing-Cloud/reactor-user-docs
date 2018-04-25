# Link DTM Embed Code

When you link your DTM embed code to Launch, you can keep your DTM production embed code on a page, but serve Launch files there instead of DTM.

Before you link your embed code, DTM publishes files to your web host. When a user visits your site in a browser, it requests the file from the server and loads it onto your web page.

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/dtm_publishing.png)

With linking, you can publish a Launch file, with the same file name, to the same place where DTM is hosting a file. The Launch file overwrites the DTM file, so when visitors browse to your site, they see the Launch file.

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/launch_publishing.png)

Important: If you use this functionality, be aware that when you publish from Launch, Launch overwrites whatever was in the destination already. Likewise, if you publish from DTM, DTM overwrites whatever was there already. You have two systems publishing to the same location. This means you don't have to change the code on your page, but it also means you need to be really careful when you publish.

## Recommended process

If you use embed code linking, the process is mostly the same as without it, but with a couple highlighted differences:

1. Create your property, install an extension, create data elements, and create rules in Launch, as you normally would.
2. Create your Development and Staging environments in Launch as usual
3. **Create your Prod environment in Launch and use the **[**Link Your DTM Embed Code**](link-dtm-embed-code.md#embed-code-link)** option.**
4. Create your library in Launch as usual.
5. Test in Dev, submit, then test in Stage, as usual
6. Publish.
7. **Disable your DTM property to prevent accidentally publishing the DTM file over the top of the Launch file.**

## Link the embed code

Before you link your embed code:

* Your DTM company must be connected to the Experience Cloud.
* Your user account must have the Manage Environments right in Launch and the Admin right in DTM.
* In Launch, go to Environments.
* Create a Prod environment. You can only have one Prod environment. If you already have one, delete it and create a linked Prod environment.

  Important: You cannot get your old Prod Environment back if you delete it.

  * Use the Link Your DTM Embed Code toggle.
    * Paste your Prod Embed Code from DTM into the appropriate text field in Launch.

* Finish configuring your Prod environment.
* Click Save.

