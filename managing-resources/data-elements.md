# Data Elements

Data elements are the building blocks for your data dictionary \(or data map\). Use data elements to collect, organize, and deliver data across marketing and ad technology.

A single data element is a variable who's value can be mapped to query strings, URLs, cookie values, JavaScript variables, and so on. You can reference this value by its variable name throughout Launch. This collection of data elements becomes the dictionary of defined data that you can use to build your rules \(events, conditions, and actions\). This data dictionary is shared across all of Launch for use with any extension you've added to your property.

Data Elements &gt; Edit.

Important: Changes do not take effect until they are [published](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/managing-resources/c_publishing.md).

Use data elements as widely as possible throughout rule creation to consolidate the definition of dynamic data and to improve the efficiency of your tagging process. You define data rules once and then use them in multiple places.

The concept of reusable data elements is very powerful and you should use them as best practice.

For example, if there is a particular way that you reference page names or product IDs, or grab information from query string parameters from an affiliate marketing link or from AdWords, and so forth, you can create a data dictionary \(data elements\) by getting information from its source and then using this data in various Launch rules.

Using page name as an example, suppose you use a particular page-name schema by referencing a data layer, `document.title` element, or a title tag within the website. In Launch, you can create a data element as a single point of reference for that particular point of data. You can then use this data element in any rule that needs to reference the page name. If for some reason in the future you decide to change the way you reference page name \(for example, you have been referencing `document.title` but you now want to reference a particular data layer\), you don't need to edit many different rules to change that reference. You simply change the reference once in the data element and all rules that reference that data element automatically update.

Note: If a data element is not referenced in a rule, it is not loaded on any page unless specifically called in custom script

Data elements are populated with data when they are used in rules or when manually called in a script. At a high level, you:

1. [Create a data element](data-elements.md#data-element-create), if you haven't done so already.
2. Use the data element in a [rule](rules.md) or a custom script.

For an introductory video, see [Data elements](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/managing-resources/videos.md).

## Data element usage

### In Rules

You can use data elements in the rule editing interface by using the search box to find the name of your data element.

### In Custom Script

You can use data elements in custom scripts by using the `_satellite` object syntax:

`_satellite.getVar('data element name');`

## Create a data element

Data elements are the building blocks for rules. Data elements let you create a data dictionary \(or data map\) of commonly used items on a page, regardless of where they originate \(query strings, URLs, or cookie values\) for any object that is contained on your site.

1. From a Property page, open the Data Elements tab, then click Create New Data Element.
2. Name the data element.
3. Select an extension and type.

   The available data element types are determined by the extension. For information about the types available with the Launch Core extension, refer to [Types of data elements](data-elements.md#data-element-types).

4. Provide any requested information about the chosen type in the fields provided.
5. \(Optional\) Enter a default value.

   If you do not provide a value, no value is sent. Some people choose to enter something like "none" or "n/a" so they can determine what is sent if there isn't a value. Different solutions deal with an empty variable differently. This creates consistency even if a value doesn't exist.

6. Select whether to force a lowercase value and whether to remove line breaks and spaces.
7. Select a duration.

   The available choices are:

   * Page view
     * Available only while the page persists.
     * Can be created and set in scripts using `_satellite` object syntax:

       `_satellite.setVar('data_element_name')`
   * Session
     * Sets a session-level cookie in the browser.
     * Available throughout the site visit.
   * Visitor
     * Sets a 2-year cookie.

8. Click Save.

When creating or editing elements, you can save and build to your [active library](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/managing-resources/library.md). This immediately saves your change to your library and executes a build. The status of the build is displayed. You can also create a new library from the Active Library drop down.

## Types of data elements

Data Element types are determined by the extension. There is no limit to the types that can be created.

The following sections describe the types of data elements available in the Core extension. Other extensions use other types of data elements.

### JavaScript Variable

Any available JavaScript object or variable can be referenced using the path field.

When you have JavaScript variables, or object properties in your markup, and you want to collect those values in Launch to use with any of your extensions or rules, one way to capture those values is to use Data Elements in Launch. This way, you can refer to the Data Element throughout your Rules, and if the source of the data ever changes, you only need to change your reference to the source \(the Data Element\) in one place in Launch.

For example, let's say your markup contains a JavaScript variable called `Page_Name`, like this:

```markup
<script>
  //data layer
  var Page_Name = "Homepage"
</script>
```

When you create the Data Element in Launch, simply provide the path to that variable.

If you use a data collector object as party of your data layer, simply use dot notation in the Path to reference the object and property you want to capture into the Data Element, like `_myData.pageName`, or `digitalData.pageName`, etc.

#### Example:

`window.document.title`

### DOM Attribute

Any element value can be retrieved, such as a div or H1 tag.

#### Example:

CSS Selector Chain:

`id#dc logo img`

Get the value of:

`src`

### Cookie

Any available domain cookie can be referenced in the cookie name field.

#### Example:

`cookieName`

### URL Querystring Parameter

Specify a single URL parameter in the URL Parameter field.

Only the name section is necessary and any special designators like "?" or "=" should be omitted

#### Example:

`contentType`

### Custom Script

Custom JavaScript can be entered into the UI by clicking Open Editor and inserting code into the editor window.

A return statement is necessary in the editor window in order to indicate what value should be set as the data element value. If a return statement is not included, the default value or an empty string will be returned as the data element value.

#### Example:

```javascript
var pageType = $('div.page-wrapper').attr('class').split('')[1];
if (window.location.pathname == '/') {
  return 'homepage';
} else {
  return pageType;
}
```

## Built-in data elements

If you used any of the following data elements in the past, you must create custom data elements in Launch:

* URI
* Protocol
* Hostname

