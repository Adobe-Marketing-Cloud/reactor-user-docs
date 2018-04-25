# Adobe Audience Manager Extension

With the Audience Manager extension, you can integrate the DIL code used by Audience Manager with your properties in Adobe Launch.

Use this reference for information about the options available when using this extension to build a rule.

Note: This extension is not meant to be used for server-side forwarding of Adobe Analytics data. For server-side forwarding, use the [Adobe Analytics extension](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/extension-reference/c_extension-analytics.md).

## Configure the Adobe Audience Manager extension

If the Adobe Audience Manager extension is not yet installed, open your property, then click Extensions &gt; Catalog, hover over the Adobe Audience Manager extension, and click Install.

To configure the extension, open the Extensions tab, hover over the extension, and then click Configure.

### DIL Settings

Configure your DIL settings. The following configuration options are available:

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/ext-aam-config.png)

#### DIL Version

Shows the Data Integration Library \(DIL\) version.

This setting cannot be changed.

#### Exclude Specific Paths

If the URL matches any of the excluded paths, the extension is not loaded.

Click Add Path to specify an excluded URL.

Enable Regex if the URL is a regular expression.

#### Use DIL Site Catalyst Module

The [SiteCatalyst module](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_sc_init.html) works with DIL to send Analytics tag elements to Audience Manager.

Use the Code Editor to configure the siteCatalyst.init file.

You can also create a note containing information about this configuration.

#### Use DIL Google Analytics Module

Enable the [Google Analytics module](https://marketing.adobe.com/resources/help/en_US/aam/dil-google-universal-analytics.html).

#### DIL.create Initialization Properties

Add initialization properties used by [DIL.create](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_create.html) and the namespace subproperty for the [visitorService object](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_visitor_service.html). Two sample use cases are included in the code comments, in the Code Editor.

Click Choose an Item to add additional properties.

Hover over the "i" icons to learn what each property does. You can find more information for the properties in the [Audience Manager DIL documentation](https://marketing.adobe.com/resources/help/en_US/aam/r_dil_create.html).

Click Save when you have finished configuring the extension.

## Adobe Audience Manager extension action types

This topic describes the action types available in the Audience Manager extension.

The Adobe Audience Manager extension provides the following actions in the Then portion of a rule:

### Run Custom Code

**Description**

Run the custom code configured in the code editor.

**Settings**

Enter the desired code in the Code Editor, then provide a name for the code. This code will become available in the Then portion of the rule builder.

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/ext-aam-then.png)

You can also add a note with information about the configuration.

