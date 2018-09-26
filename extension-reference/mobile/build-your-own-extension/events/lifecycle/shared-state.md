# Shared State

**MODULE\_NAME**: `com.adobe.module.lifecycle`

Lifecycle shares its context data with the other extensions using a shared state. Lifecycle creates its shared state after the extension is first initialized and on every Lifecycle Start event. The shared state's `EventData` contains one String Map that is keyed to `lifecyclecontextdata`.

| Key | SubKey | Type | Definition |
| :--- | :--- | :--- | :--- |
| lifecyclecontextdata | installevent | String | Set at the first run after installation or re-installation with value `InstallEvent`. This key will not exist for the subsequent launches of the app. |
| launchevent | String | Set on every run, including crashes and installs. Also triggered when the app is resumed from the background after the lifecycle session timeout is exceeded. This key will be present with the string value `LaunchEvent`. |  |
| crashevent | String | Set when the application is not backgrounded before closing. This key will exist when the application is started again after the crash. Its set with a string value `CrashEvent`. |  |
| upgradeevent | String | Set at the first run after upgrade or anytime the version number changes. Its set with a string value `UpgradeEvent`. |  |
| dailyenguserevent | String | Set when the application is used on a particular day. Its set with a string value `DailyEngUserEvent`. |  |
| monthlyenguserevent | String | Set when the application is used during a particular month. Its set with a string value `MonthlyEngUserEvent`. |  |
| installdate | String | Date of first launch after installation. The date format is MM/DD/YYYY. |  |
| launches | String | Number of times the application was launched or brought out of the background. |  |
| prevsessionlength | String | The number of seconds that a previous application session lasted based on how long the application was open and in the foreground. |  |
| ignoredsessionlength | String |  |  |
| dayssincefirstuse | String | Number of days since the first run. |  |
| dayssincelastuse | String | Number of days since the last use. |  |
| hourofday | String | Measures the hour the app was launched.   This key uses the 24-hour numerical format. |  |
| dayofweek | String | Number of the week day the app was launched. |  |
| osversion | String | The operating system on the device formatted as `[OS_NAME OS_VERSION]`. |  |
| appID | String | The `ApplicationID` provided by platform and is formatted as \[ `APP_NAME + APP_VERSION + APP_VERSION_CODE]`. |  |
| dayssincelastupgrade | String | Number of days since the application version number has changed. |  |
| launchessinceupgrade | String | Number of launches since the application version number has changed. |  |
| devicename | String | The device name provided by platform |  |
| resolution | String | The resolution of the current device, which is measured  \[Width x Height\] in actual pixels. |  |
| carriername | String | The mobile carrier name. |  |
| locale | String | The active locale. |  |
| runmode | String | The SDK running mode, for example, Application or Extension. |  |

