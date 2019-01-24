# Data Elements

Data elements are the building blocks for your data dictionary \(or data map\). Use data elements to collect, organize, and deliver data across marketing and ad technology.

A single data element is a variable whose value can be mapped to query strings, URLs, cookie values, JavaScript variables, and so on. You can reference this value by its variable name throughout Launch. This collection of data elements becomes the dictionary of defined data that you can use to build your rules \(events, conditions, and actions\). This data dictionary is shared across all of Launch for use with any extension you've added to your property.

**Important:** Changes do not take effect until they are [published](../publishing/).

Use data elements as widely as possible throughout rule creation to consolidate the definition of dynamic data and to improve the efficiency of your tagging process. You define data rules once and then use them in multiple places.

The concept of reusable data elements is very powerful and you should use them as best practice.

For example, if there is a particular way that you reference page names or product IDs, or grab information from query string parameters from an affiliate marketing link or from AdWords, and so forth, you can create a data dictionary \(data elements\) by getting information from its source and then using this data in various Launch rules.

Using page name as an example, suppose you use a particular page-name schema by referencing a data layer, `document.title` element, or a title tag within the website. In Launch, you can create a data element as a single point of reference for that particular point of data. You can then use this data element in any rule that needs to reference the page name. If for some reason in the future you decide to change the way you reference page name \(for example, you have been referencing `document.title` but you now want to reference a particular data layer\), you don't need to edit many different rules to change that reference. You simply change the reference once in the data element and all rules that reference that data element automatically update.

**Note:** If a data element is not referenced in a rule, it is not loaded on any page unless specifically called in custom script

Data elements are populated with data when they are used in rules or when manually called in a script. At a high level, you:

1. [Create a data element](data-elements.md#create-a-data-element), if you haven't done so already.
2. Use the data element in a [rule](rules.md) or a custom script.

For an introductory video, see [Data elements](../../getting-started/videos.md).

## Data element usage

### In Rules

You can use data elements in the rule editing interface by using the search box to find the name of your data element.

### In Custom Script

You can use data elements in custom scripts by using the `_satellite` object syntax:

`_satellite.getVar('data element name');`

## Create a data element

Data elements are the building blocks for rules. Data elements let you create a data dictionary \(or data map\) of commonly used items on a page, regardless of where they originate \(query strings, URLs, or cookie values\) for any object that is contained on your site.

1. From a Property page, open the Data Elements tab, then click Add Data Element.
2. Name the data element.
3. Select an extension and type.

   The available data element types are determined by the extension. For information about the types available with the Launch Core extension, refer to [Types of data elements](data-elements.md#types-of-data-elements).

4. Provide any requested information about the chosen type in the fields provided.
5. \(Optional\) Enter a default value.

   If you do not provide a value, no value is sent. Some people choose to enter something like "none" or "n/a" so they can determine what is sent if there isn't a value. Different solutions deal with an empty variable differently. This creates consistency even if a value doesn't exist.

6. Select whether to force a lowercase value and whether to remove line breaks and spaces.
7. Select whether to use clean text. The Clean Text option removes any whitespace from the beginning and end and replaces any successive spaces in the middle with single spaces. Use this option to normalize element values for easier matching.
8. Select a duration.

   The available choices are:

   * None
     * The value is not stored.
   * Page view
     * The value is held in a JavaScript variable until the page is refreshed or a new page is loaded.
     * Can be created and set in scripts using `_satellite` object syntax:

       `_satellite.setVar('data_element_name')`
   * Session
     * Values persist in the browser's session storage until the browser tab is closed.
     * Available throughout the site visit.
   * Visitor
     * The value is stored indefinitely in the brower's local storage.

9. Click Save.

When creating or editing elements, you can save and build to your [active library](../publishing/libraries.md#active-library). This immediately saves your change to your library and executes a build. The status of the build is displayed. You can also create a new library from the Active Library drop down.

## Built-in data elements

If you used any of the following data elements in the past, you must create a custom data element in Launch:

* URI
* Protocol
* Hostname

