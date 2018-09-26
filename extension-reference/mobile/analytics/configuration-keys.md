# Configuration Keys

## analytics.server

**Important**: This variable is required by Analytics.

The Analytics server is based on the parent node. This variable should be populated with the server domain, without an `http://` or `https://` protocol prefix. This prefix is handled automatically by the library and is based on the ssl variable. If `global.ssl` is `true`, a secure connection is made to this server. If `global.ssl` is `false`, a non-secure connection is made to this server.

## analytics.rsids

Contains a comma-delimited list of report suites to which the Analytics data should be sent.

**Important**: This variable is required by Analytics.

Requires one or more report suites to receive Analytics data. Multiple report suite IDs should be comma-separated with no space between. For example:

`"rsids" : "rsid" "rsids" : "rsid1,rsid2"`

## analytics.batchLimit

Threshold for number of hits to be sent in consecutive calls. For example, if `batchLimit` is set to 10, each hit before the 10th hit will be stored in the queue. When the 10th hit comes in, all 10 hits will be sent consecutively.

Remember the following information:

* Default value is 0, which means that batching is not enabled.
* Requires `offlineEnabled` = `true`.

## analytics.aamForwardingEnabled

If set to `true`, Analytics data collection servers will attempt to forward data to Audience Manager on the back end. The default value is `false`.

The property in the `audienceManager` object. If Audience Manager is configured, and `analyticsForwardingEnabled` is set to `true`, and all Analytics traffic is also forwarded to Audience Manager.

## analytics.offlineEnabled

When enabled, hits are queued while the device is offline and sent later when the device is online. Your report suite must be timestamp-enabled to use offline tracking. The default value is `false`.

**Important**: If timestamps are enabled on your report suite, your `offlineEnabled` configuration property must be true. if your report suite is not timestamp enabled, your `offlineEnabled` configuration property must be false. If this is not configured correctly, data will be lost. If you are not sure whether a report suite is timestamp enabled, contact Customer Care or download the configuration file from Adobe Launch.

If you are currently reporting `AppMeasurement` data to a report suite that also collects data from JavaScript, you might need to set up a separate report suite for mobile data or include a custom timestamp on all JavaScript hits that use the `s.timestamp` variable.

## analytics.backdatePreviousSessionInfo

If set to `true`, the lifecycle session information or crash events will be backdated to one second after the last hit was sent. If set to `false`, this data will be attached to the first hit of the subsequent session. By default, this key is set to `false`.

