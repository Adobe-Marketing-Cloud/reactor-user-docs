```
---
description: >-
  This section helps app developers understand how other modules can be integrated with Analytics.
---
```

# Analytics Integration

There are several Adobe provided extensions that can be integrated with Analytics. This document will cover the use cases on integrating with Analytics. The following integrations are all optional, except for Identity which is required by Analytics.

## Acquisition

**Application First Install:** The first time a user installs and opens you app the Analytics module is responsible for sending an install hit containing the referrer information from Acquisition if available.

## Lifecycle

**Application First Install:** The first time a user installs and opens you app the Analytics module is responsible for sending an install hit containing the install, launch, and crash information from Lifecycle if available.

**Application Launch: ** Upon launch of your application, the Analytics extension receives an event from Lifecycle which contains the install, launch, crash information. Analytics then sends a first hit containing this information. For more information, see Adobe Lifecycle.

For more information, see [Lifecycle](https://docs.adobelaunch.com/extension-reference/mobile/lifecycle).

## Target

**Target with Analytics (A4T):** To see the performance of your Target activities for certain segments you can set up the Analytics for Target \(A4T\) cross-solution integration by enabling the A4T campaigns. This integration allows you to use Analytics reports to examine your results. If you use Analytics as the reporting source for an activity, all reporting and segmentation for that activity is based on Analytics data collection. For more information, see [Target](https://marketing.adobe.com/resources/help/en_US/target/a4t/a4t.html).

## Identity

**Identity Information:** Identity is required when using Analytics. Identity contains the key `global.privacy` and this determines if a user is opted-in or out and decides if Analytics hits are sent out. Further, Analytics also reads other configuration keys from Identity which are used in Analytics hits, such as `experienceCloud.org`. For more information, see [Identity](https://docs.adobelaunch.com/extension-reference/mobile/identity).

## Rules and Messages

**Rule Based Messages:** Using the Mobile Rules Engine you can define rules based on Analytics events that can trigger messages, alerts, and local notifications. For more information on configurting your own rules, see [Mobile Rules Engine](https://docs.adobelaunch.com/extension-reference/mobile/rules-engine).

