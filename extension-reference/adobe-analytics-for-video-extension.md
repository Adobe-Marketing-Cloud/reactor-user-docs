# Adobe Analytics for Video Extension

Use this documentation for information on installing, configuring, and implementing the Adobe Analytics for Video Extension. Included are the options available when using this extension to build a rule, along with examples and links to samples.

The Adobe Analytics for Video Extension \(VA Launch Extension\) adds the core VA JavaScript library \(VideoHeartbeat 2.x SDK\). This extension provides the functionality for adding the `MediaHeartbeat` tracker instance to a Launch site or project. The VA Launch Extension requires two additional extensions:

* [Analytics Extension](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/67a59a7519514467a713016adfe46d999fe330d8/extension-reference/c_extension-analytics.md)
* [Experience Cloud ID Extension](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/67a59a7519514467a713016adfe46d999fe330d8/extension-reference/c_extension-mcid.md)

After you have included all three of the extensions mentioned above in your Launch project, you must then include or build a player-specific extension, which maps specific video player API events to the Video Analytics events on the `MediaHeartbeat` tracker instance exposed through the VA Launch Extension.

## Install and Configure the VA Launch Extension

**Install -** To install the VA Launch Extension, open your extension property, then click Extensions &gt; Catalog, hover over the Adobe Analytics for Video extension, and click Install.

**Configure -** To configure the VA Launch Extension, open the Extensions tab, hover over the extension, and then click Configure:

![](../.gitbook/assets/ext-va-config.jpg)

#### Configuation Options

| Option | Description |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Tracking Server | Defines the server for tracking media heartbeats.This is not the same server as your analytics tracking server. |
| Application Version | The version of the video player app/SDK. |
| Player Name | Name of the video player in use. E.g.: "AVPlayer", "HTML5 Player", "My Custom VideoPlayer" |
| Channel | Channel name property |
| Online Video Provider | Name of the online video platform through which content gets distributed |
| Debug Logging | Preferred debug log output |
| Enable SSL | Enable / Disable sending pings over HTTPS. |

**Important:** The VA Analytics Launch Extension requires the presence of the [Adobe Analytics](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/67a59a7519514467a713016adfe46d999fe330d8/extension-reference/c_extension-analytics.md) and [Experience Cloud ID](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/67a59a7519514467a713016adfe46d999fe330d8/extension-reference/c_extension-mcid.md) extensions. Customers must also add these extensions to their extension property and configure them.

## Using the VA Launch Extension

**Important:** Currently, the only way to leverage the VA Launch Extension is through the use of "shared modules" which you can only access from other Launch extensions. That is, a webpage/JS app cannot access or declare `getMediaHeartbeatInstance`, or use `turbine` \(see code sample below\) outside of a Launch Extension.

### Using the VA Launch Extension from other Launch Extensions

The VA Launch Extension exposes the `get-instance` and `media-heartbeat` shared modules. \(For additional information on Shared Modules, see [Shared Modules documentation](https://developer.adobelaunch.com/guides/extensions/shared-modules/).\)

* `get-instance`

  **Params:**

  1. A valid delegate object exposing these functions:

     | Method | Description | Required |
     | --- | --- | --- |
     | getQoSObject\(\) | Returns theMediaObject instance that contains the current QoS information. This method will be called multiple times during a playback session. Player implementation must always return the most recently available QoS data. | Yes |
     | getCurrentPlaybackTime\(\) | Returns the current position of the playhead.For VOD tracking, the value is specified in seconds from the beginning of the media item.For LIVE/LIVE tracking, the value is specified in seconds from the beginning of the program. | Yes |

  2. An optional config object exposing these properties:

     | Property | Description | Required | Value |
     | --- | --- | --- | --- |
     | Online Video Provider | Name of the online video platform through which content gets distributed. | No. If present overrides the value defined during Extension configuration. | Empty String |
     | Player Name | Name of the video player in use.E.g.: "AVPlayer", "HTML5 Player", "My Custom VideoPlayer" | No. If present overrides the value defined during Extension configuration. | Empty String |
     | Channel | Channel name property | No. If present overrides the value defined during Extension configuration. | Empty String |

     **Return Value:** A promise which either resolves with a `MediaHeartbeat` instance or rejects with an error message.

* `media-heartbeat`

  This module exposes all of the constants from this class: [https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/MediaHeartbeat.html).

  1. Implemement the shared Media Heartbeat instance as follows:

     ```javascript
      var getMediaHeartbeatInstance =
        turbine.getSharedModule('adobe-video-analytics', 'get-instance');

      var MediaHeartbeat =
        turbine.getSharedModule('adobe-video-analytics', 'media-heartbeat');
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
          // Do Tracking using the MediaHeartbeat instance.
      }).catch(function(err){
          // Getting MediaHeartbeat instance failed.
      });

      ...
     ```

  2. Using the Media Heartbeat instance, follow the [VHL SDK JS documentation](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/js_2.0/) and [JS API documentation](https://adobe-marketing-cloud.github.io/video-heartbeat-v2/reference/javascript/index.html) to implement video tracking.

**Note: Testing -** For this release, to test your extension you must upload it to [Adobe Launch](https://github.com/Adobe-Marketing-Cloud/reactor-user-docs/tree/67a59a7519514467a713016adfe46d999fe330d8/extension-reference/launch.adobe.com), where you have access to all dependent extensions.

## Leveraging the Sample HTML5 Player

You can obtain the VA Launch HTML5 sample player here: [HTML5 Sample Player](https://github.com/adobe/reactor-adobe-va-sample-player). The sample player acts as a reference to create video player extensions and to showcase using the VA Launch Extension to support Adobe Analytics for Video.

## Sample Player extension action types

This section describes the action types available in the Sample Player extension.

### Open Video

The Open Video action provides various configurations for creating and customizing a HTML5 player, providing a video to play and enabling/disabling Adobe Video Analytics tracking.

**Action Configuration / Player Settings:** Note the CSS Selector setting which specifics the `<div>` in the web page where the player is added. Note also that the "Enable Adobe Analytics" checkbox is checked in the Analytics Settings pane.

![](../.gitbook/assets/ext-va-sp-action.png)

![](../.gitbook/assets/ext-va-sp-action1.png)

* [https://github.com/adobe/reactor-adobe-va-sample-player/blob/master/src/view/actions/openVideo/openVideo.jsx](https://github.com/adobe/reactor-adobe-va-sample-player/blob/master/src/view/actions/openVideo/openVideo.jsx) - UI Code to configure the Action is defined here.
* [https://github.com/adobe/reactor-adobe-va-sample-player/blob/master/src/lib/actions/openVideo.js](https://github.com/adobe/reactor-adobe-va-sample-player/blob/master/src/lib/actions/openVideo.js) - This file exports a function that gets executed when the Action is triggered as part of the launch rule.

  This is a code snippet from `openVideo.js` where the openVideo Action is executed:

  ```javascript
    function openVideo(settings) {
      let player;
      try {
        Logger.info(LOG_TAG, `Executing action with ${JSON.stringify(settings)}`);

        player = new PlayerFacade(settings);
        PlayerStore.registerPlayer(player);
        player.load(settings.media);
      } catch (ex) {
        Logger.error(LOG_TAG, `Creating player for action openVideo failed with error ${ex.message}`);

        // Cleanup from DOM.
        if (player) {
          player.destroy();
        }
      }
    }
    ...
  ```

* [https://github.com/adobe/reactor-adobe-va-sample-player/blob/master/src/lib/helpers/analytics/adobeAnalyticsProvider.js](https://github.com/adobe/reactor-adobe-va-sample-player/blob/master/src/lib/helpers/analytics/adobeAnalyticsProvider.js) - This file implements Video Analytics tracking by using Shared Modules exposed by the VA Launch Extension.

## Sample Player extension basic deployment

Once the Sample Player Extension is installed, you'll need to create at least one rule to properly deploy it. The Image below shows a sample rule that opens the specified video when the core extension fires the `DOMLoaded` event.

![](../.gitbook/assets/ext-va-sp-rule.png)

Once you have saved this rule, you'll need to add it to a Library and build/deploy so that you can test the behavior.

**Important:** Currently, if you have a custom player that doesn't have a Launch extension, you have to write your own extension to make use of the VA Launch Extension.

