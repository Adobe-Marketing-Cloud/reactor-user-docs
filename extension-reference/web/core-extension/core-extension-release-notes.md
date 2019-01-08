# Core Extension Release Notes

## January 8, 2019

* **Enters Viewport event** Previously the Enters Viewport event would only trigger one time per page.  This behavior has been changed so that it now triggers each time the element enters the viewport.
* **Custom Event event** Custom Events can now contain contextual data that can be used inside of conditions and actions.
* **Click event** When you set  a link delay on the Click event, that will now register properly for descendants of the anchor and not just on the anchor itself.

## November 8, 2018

* **Persist Cohort option** The option to persist a cohort has been added to the Sampling condition. This has the effect of keeping a user in or out of the sample cohort across sessions. For example, if the “persist cohort” checkbox is checked and the condition returns true the first time it is run for a given visitor, it will return true on all subsequent runs of the condition for the same visitor. Similarly, if the “persist cohort” checkbox is checked and the condition returns false the first time it is run for a given visitor, it will return false on all subsequent runs of the condition for the same visitor.
* **Bug Fix** Fixed an issue where a rule using a Page Bottom event and a Custom Code action on a page where Launch was being loaded synchronously but improperly installed \(no call to `_satellite.pageBottom()`\) would clear website content.
* **Bug Fix** Fixed an issue where the Enters Viewport would not function if the Launch library was loaded asynchronously and finished loading after the browser's DOMContentLoaded event was fired.

## May 24, 2018 <a id="may-24-2018"></a>

### Features <a id="features"></a>

* Added a Value Comparison condition, this compares two values using any of several available operators. This replaces the functionality of several older conditions that were far too specific.
* Added a Max Frequency condition, this condition allows you to specify the number of times the condition should return true within a time period or event occurrence. Examples: 5 times per Day, 2 times per Visit.

## April 11, 2018 <a id="april-11-2018"></a>

### Features <a id="features-1"></a>

* Data elements can now reference other data elements.

## March 20, 2018 <a id="march-20-2018"></a>

### Bug Fixes <a id="bug-fixes"></a>

* Custom code windows were throwing `document.write` errors and not executing in async deployments
* Main modules were not included in a library
* Problems occurred with min and max values on the Random Number data element

## January 10, 2018 <a id="january-10-2018"></a>

### Features <a id="features-2"></a>

* The following have been added to the core extension:
  * Random Number Data Element
  * Page Info Data Element
  * Date Condition
  * Sampling Condition

