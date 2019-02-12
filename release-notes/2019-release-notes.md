# 2019 Release Notes

## February 12, 2019

### Features

* Cross-property Copy - You can now copy resources from one property to another.  After selecting a resource and clicking the **Copy** button, you can select a target property to copy to.  This is available on Extensions, Data elements, and Rules.  Read more about copying resources [here](../launch-reference/managing-resources/copying-resources.md).

## January 29, 2019

### Features

* Revision Compare - You can now compare one version of a resource with older versions.  This is available on Extensions, Data Elements, and Rules.  Read more about this new feature [here](../launch-reference/managing-resources/compare-resource-revisions.md).

## January 17, 2019

### Updates

* Builds should be running ~15% faster than before.  Large builds \(hundreds of resources\) will have more dramatic improvements.

## January 8, 2019

### Core Extension 1.4.2

* The `Enters Viewport` event is now configurable to trigger each time that the element enters the viewport instead of just the first time.
* Custom Events can now contain extra contextual data that can be used in conditions and actions.
* Link Delay on the Click event will now trigger on descendants of the anchor and not just the anchor itself.

### Updates

* Properties that are configured for Extension Development now have a small tag next to the Property Name.
* OrgID is now available on the \_satellite object.
* Use of the Launch UI is no longer supported in IE11, you'll receive a warning if you login with IE 11.

### Bug Fixes

* Better support for long Library names in your Active Library and the Publishing view.
* In certain scenarios, when you saved a library, the dependency checker would prompt you to add a new revision of an extension that was already in your Library. It doesn't do that anymore.
* Tooltips will now reliably show up in Safari.
* Searches in the search bar will now trigger a bit faster than before.

