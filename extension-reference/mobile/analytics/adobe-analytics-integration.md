# Analytics Integration

```text
---
description: >-
  This section helps app developers understand how other modules can be integrated with Analytics.
---
```

## Analytics Integration

There are several Adobe provided extensions that can be integrated with Analytics. This document will cover the use cases on integrating with Analytics. The following integrations are all optional, except for Identity which is required by Analytics.

### Identity

Identity is required when using Analytics. This integration will enable Analytics to send the Experience Cloud Organization ID \(MID\) and any additional identifiers that you synced before using the `syncIdentifiers` APIs within the analytics hits. For more information, see [Identity](../identity/).

### Audience Manager

If you want to share the Analytics Data with Adobe Audience Manager, you can enable this in Launch UI in the Analytics extension, by selecting “Audience Manager Forwarding” option and installing the Audience Manager extension. For more details, please consult the [Audience Manager](../audience-manager/) section.

### Lifecycle

In order to track the application lifecycle details, you need to properly configure the lifecycle data collection. This will enable you to track information about application installs or upgrades, application crash events, application launch details \(for example: number of launches, session length\). In addition to that, every analytics hit will contain the default lifecycle metrics, which include information about the device being used, operating system, device resolution etc. For more details please check the [Lifecycle section](../lifecycle/) and the [Lifecycle metrics](../lifecycle/lifecycle-metrics.md) page.

### Target

To see the performance of your Target activities for certain segments you can set up the Analytics for Target \(A4T\) cross-solution integration by enabling the A4T campaigns. This integration allows you to use Analytics reports to examine your results. If you use Analytics as the reporting source for an activity, all reporting and segmentation for that activity is based on Analytics data collection. For more information, see [Target](https://marketing.adobe.com/resources/help/en_US/target/a4t/a4t.html).

