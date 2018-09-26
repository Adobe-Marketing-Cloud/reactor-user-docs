---
description: 'Here are the variables in the ADBMobileConfig.json config file:'
---

# Configuration Keys

## global.privacy

The default value is `optunknown`, and here are the other values:

* For `optedin`, the hits are sent immediately.
* For `optedout`, the hits are discarded.
* For `optunknown`, if your report suite is timestamp-enabled, hits are saved until the privacy status changes to opt in \(hits are sent\) or opt out \(hits are discarded\).

If your report suite is not timestamp-enabled, hits are discarded until the privacy status changes to opt in. This only sets the initial value. If this value is set or changed in the code, the new value is used until it is changed again, or when the app is uninstalled and reinstalled.

## global.timezone

Contains the abbreviation for the designated time zone for the app. For a list of time zone abbreviations, see [https://en.wikipedia.org/wiki/List\_of\_time\_zone\_abbreviations](https://en.wikipedia.org/wiki/List_of_time_zone_abbreviations).

**Tip**: This configuration key affects all of the modules.

## global.timezoneOffset

Difference, in minutes, between the current time zone and UTC.

**Tip**: This configuration key affects all of the modules.

## marketingCloud.server

Custom endpoint to be used for the Experience Cloud ID service network requests.

## marketingCloud.org

Specifies the Experience Cloud organization ID for the ID service.

