# Adobe Analytics Release Notes

## November 9, 2018

### Adobe Analytics Extension 1.5.1

#### **Bug fixes**

* Downgraded the DIL module to 7.0 to fix an issue that was causing problems with analytics beacons not firing

## November 5, 2018

### Adobe Analytics Extension 1.5

#### **Features**

* Updated the Adobe Analytics extension to support DIL 8.0 in Audience Manager
* Separated the "Serialize from value" field into two, "Event ID" and "Event Value". This will fix the issue that was assigning a value instead of serializing an event
  * Please note: if you are using the current field to add an ID by using a string \(ex. Event7=3:abc123\) you will need to update your input to reflect the ID in the "Event ID" field

#### **Bug fixes**

* Fixed a bug that wasn't allowing the currency code to populate correctly

## October 11, 2018

### Adobe Analytics Extension 1.4

#### **Features**

* Migrated the tracking cookie name to the extension configuration.

#### **Bug Fixes**

* Fixed a bug so set variables don't crash when no trackerProperties object is available.

## June 5, 2018

### Adobe Analytics Extension 1.3

#### **Features**

* Updated Adobe Analytics extension to support [AppMeasurement 2.9](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/release/c_release_notes_mjs.html).
* Added "Make tracker globally accessible" feature in the Adobe Analytics extension, which enables the tracker to be scoped globally under `windows.s`.

#### **Bug Fixes**

* Fixed a bug that caused list view to reset when returning from detail view
* Fixed a few bugs to improve loading of resources in the revision selector
* Fixed a bug where multiple rules were overwriting s.events in the Adobe Analytics extension

## March 20, 2018

### Adobe Analytics Extension 1.2

#### **Features**

* Updates AppMeasurement.js to 2.8.0
* Adds support for server-side forwarding

## February 8, 2018

### Adobe Analytics Extension 1.1

#### **Features**

* AppMeasurement has been updated to version 2.6
* The initialized Analytics tracker is now exposed through a shared module in the Launch extension so other extensions can include code to interact with it.

#### **Bug fixes**

* Fixed an error in the Adobe Analytics Extension that caused "Error, missing Report Suite ID in AppMeasurement initialization" to appear in the browser console.

