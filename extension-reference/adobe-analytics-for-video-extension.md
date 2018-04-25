# Adobe Analytics for Video Extension

Use this documentation for information on installing, configuring, and implementing the VA Extension. Included are the options available when using this extension to build a rule, along with examples and links to samples.

The Adobe Analytics for Video Extension adds the core Video Analytics JavaScript library. This library provides the functionality for adding the mediaHeartbeat instance to a Launch site or project. The Adobe Analytics for Video Extension \(VA Extension\) requires two additional extensions:

* [Analytics Extension](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/extension-reference/c_extension-analytics.md)
* [Experience Cloud ID Extension](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/extension-reference/c_extension-mcid.md)

After you have included all three of the extensions mentioned above in your Launch project, you must then include custom JavaScript, or build a player-specific extension, to map specific video player API events to the Video Analytics events exposed through the VA Extension.

## Install and Configure the VA Extension

**Install -** To install the Video Analytics \(VA\) Extension, open your extension property, then click Extensions &gt; Catalog, hover over the Adobe Analytics for Video extension, and click Install.

**Configure -** To configure the VA extension, open the Extensions tab, hover over the extension, and then click Configure:

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/VA%20Launch%20Doc%20-%20Google%20Docs.jpg)

### Tracking Server

Defines the server for tracking media heartbeats.

Note: This is not the same server as your analytics tracking server.

### Application Version

The version of the video player app/SDK.

### Player Name

Name of the video player in use. E.g.: "AVPlayer", "HTML5 Player", "My Custom VideoPlayer"

### Channel

Channel name property

### Online Video Provider

Name of the online video platform through which content gets distributed

### Debug Logging

Preferred debug log output

### Enable SSL

Enable / Disable sending pings over HTTPS.

Important: The VA Analytics extension requires the presence of the [Adobe Analytics](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/extension-reference/c_extension-analytics.md) and [Experience Cloud ID](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/extension-reference/c_extension-mcid.md) extensions. Customers must also add these extensions to their extension property and configure them.

## Working With the Shared Modules

### `get-instance`

This module exposes a function to create a MediaHeartbeat instance. \([https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html)\)

The following sections show the available parameters.

#### A valid `delegate` object exposing these functions:

**getQoSObject\(\)**

Returns the MediaObject instance that contains the current QoS information. This method will be called multiple times during a playback session. Player implementation must always return the most recently available QoS data.

**Required:** Yes

**getCurrentPlaybackTime\(\)**

Returns the current position of the playhead.

For VOD tracking, the value is specified in seconds from the beginning of the media item.

For LIVE/LIVE tracking, the value is specified in seconds from the beginning of the program.

**Required:** Yes

#### An optional config object exposing these properties:

**Online Video Provider**

Name of the online video platform through which content gets distributed.

**Required:** No. If present overrides the value defined during Extension configuration.

**Value:** Empty String

**Player Name**

Name of the video player in use.

E.g.: "AVPlayer", "HTML5 Player", "My Custom VideoPlayer"

**Required:** No. If present overrides the value defined during Extension configuration.

**Value:** Empty String

**Channel**

Channel name property

**Required:** No. If present overrides the value defined during Extension configuration.

**Value:** Empty String

**Return Value:** A promise which either resolves with a MediaHeartbeat instance or rejects with an error message.

### `media-heartbeat`

This module exposes all of the constants from this class: [https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html).

**Implementation**

1. Implemement the shared Media Heartbeat instance as follows:

   ```javascript
   var getMediaHeartbeatInstance =
     turbine.getSharedModule('adobe-video-analytics', '**get-instance**');

   var MediaHeartbeat =
     turbine.getSharedModule('adobe-video-analytics', '**media-heartbeat**');
       ...

       var delegate = {
           getCurrentPlaybackTime: this._getCurrentPlaybackTime.bind(this),
           getQoSObject: this._getQoSObject.bind(this),
       }

       var config = {
           playerName: "Custom Player",
           ovp: "Custom OVP",
           channel: "Custom Channel"
       }
       ...

       var self = this;
       getMediaHeartbeatInstance(delegate, config).then(function(instance) {
           self._mediaHeartbeat = instance;
           ...
           // Do Tracking using the Media Heartbeat instance.
       });
   }
   ...
   ```

2. Using the Media Heartbeat instance, follow the [VHL SDK JS documentation](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/js_2.0/) and [JS API documentation](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/index.html) to implement video tracking.

Note: **Testing -** For this release, to test your extension you must upload it to [Adobe Launch](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/extension-reference/launch.adobe.com), where you have access to all dependent extensions.

