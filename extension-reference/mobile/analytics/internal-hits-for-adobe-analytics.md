# Internal Hits for Adobe Analytics

In addition to the Analytics hits that are sent as a result of the track call, the Adobe Cloud Platform SDKs also tracks some internal hits that are based on the communication with other extensions.

Here is a list of the hits by extension:

## Lifecycle Extension

Here are the Analytics hits in the Lifecycle extension:

### Install Hit

The SDK tracks the application install details when lifecycle is enabled. These details include the install date and the daily engaged/monthly engaged user badges.

### Launch Hit

The SDK tracks every new launch of the application when lifecycle is enabled.

A launch is considered to be new when the following conditions are met:

* The application is reopened from the background after the configured session timeout.
* The application is opened after a force close.

Launch data includes information about the application's number of launches, days since first run, days since last use, user daily/monthly engaged badges along with other lifecycle metrics.

We also track the application version upgrades.

### Crash Hit

If your application is terminated without having first been backgrounded, the SDK reports a crash the next time your app is launched.

This will be sent as an individual hit if the `backdateSessionInfo` flag is enabled in your configuration, otherwise it will be sent as part of the launch hit.

### SessionInfo

This hit contains information about the previous launch session, more specifically the session length.

This will be sent as an individual hit if backdateSessionInfo flag is enabled in your configuration, otherwise it will be sent as part of the launch hit.

## Identity Extension

Here are the Analytics hits that are triggered when the Identity extension is enabled:

* Push

The SDK tracks changes in the user's push notifications preference. A new hit is sent whenever the user opt-in/opt-out for push notifications.

## Target Extension

Here is the Analytics hit in the Target extension:

* AnalyticsForTarget

  The SDK forwards Target's data to analytics when A4T is enabled in Target Services.

