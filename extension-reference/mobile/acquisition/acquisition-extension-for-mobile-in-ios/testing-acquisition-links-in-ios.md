# Testing Acquisition Links in iOS

## Testing Marketing Link Acquisition in iOS

The following instructions help you roundtrip an acquisition campaign with a marketing link that is based on a device fingerprint.

1. Complete the prerequisite tasks in _Mobile App Acquisition_.
2. In the Adobe Mobile Services UI, click **Marketing Links Builder** and generate an acquisition marketing link URL that sets the App Store as the destination for iOS devices.

   For example:

   [https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a\_dl=57477650072932ec6d3a470f](https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f)

3. Open the generated link on the iOS device and then open `http://c00.adobe.com/v3/<appid>/end`.

   You should see the contextData in the JSON response:

   ```javascript
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":

   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}

   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

4. Verify that the following settings in your config file are correct:

   | **Setting** | **Value** |
   | :--- | :--- |
   | acquisition | The server should be `c00.adobe.com`, and the `appid` should equal the in your acquisition link. |
   | analytics | `referrerTimeout` should have a value greater than 0. |

5. \(Conditional\) If the SSL setting in your app's config file is false, update your acquisition link to use the HTTP protocol instead of HTTPS.
6. Click the generated link from the mobile device on which you want to install the app.
7. Adobe's servers \(c00.adobe.com\) store the fingerprint and redirect to the App Store.  The app does not need to be downloaded for testing.
8. Launch the application for the first time from the same mobile device that you used in step 6.
9. You can delete and install the app again, if necessary.

Remember the following information:

* The acquisition server provides an attribution match that based on the IP address and user-agent information that was recorded in the link click \(step 6\) and when the app is launched \(step 7\).  You should be on the same network when you click the URL and when you open the app.
* By using HTTP monitoring tools, hits that are sent from the app can be monitored to provide verification of the acquisition attribution.  You should see one `/v3//start` request and one `/v3//end` request that are sent to the acquisition server.
* Variations in the user-agent sent might cause attribution to fail.  Ensure that [http://c00.adobe.com/v3/](http://c00.adobe.com/v3/)/start and [http://c00.adobe.com/v3/](http://c00.adobe.com/v3/)/end have the same user-agent values.
* The acquisition link and the hit from the SDK should be using the same HTTP/HTTPS protocol. If the link and the hit are using different protocols \(for example, the link uses HTTP and the SDK uses HTTPS\) the IP address might differ for each request \(on some carriers\). This could cause the attribution to fail.
* The marketing links are cached on the server side with a ten-minutes expiration time.  When you make changes to marketing links, you should wait about 10 minutes before using the links. 

## Testing V3 Acquisition in iOS

This information helps you roundtrip a V3 acquisition campaign link based on a device fingerprint.

**Important:** V3 Acquisition refers to the acquisition links that you create with the Acquisition Builder in the Adobe Mobile Services UI. To use this feature, you must upgrade to iOS SDK version 4.6.0 or later.

If the mobile app is not yet in the App Store, when you create the campaign link, select any mobile app as a destination. This only affects the app to which the acquisition server redirects you after you click the acquisition link, but does not affect the ability to test the link.

1. Complete the prerequisite tasks in _Mobile App Acquisition_.
2. Navigate to the **Acquisition Builder** in the Adobe Mobile Services UI and generate an acquisition campaign URL.

   For example:

   ```text
   http://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode
   ```

   If you refer to both iOS and Android apps in the acquisition link, use the Apple Store as the default store.

3. Open the generated link in a desktop browser and go to `http://c00.adobe.com/v3/<appid>/end`.

   You should see the contextData in the JSON response:

   ```javascript
   {"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}
   ```

   If you do not see contextData, or some of it is missing, ensure that the acquisition URL follows the format that is specified in Create Acquisition Link Manually.

4. Verify that the following settings in your config file are correct:

   | Setting | Value |
   | :--- | :--- |
   | acquisition | The server should be `c00.adobe.com`, and the `appid` should equal the in your acquisition link. |
   | analytics | `referrerTimeout` should have a value greater than 0. |

5. \(Conditional\) If the ssl setting in your app's config file is true, update your acquisition link to use the HTTPS protocol.
6. Click the generated link from the mobile device on which you will install the app.
7. Adobe's servers \(c00.adobe.com\) store the fingerprint and redirect to the App Store.  The app does not need to be downloaded for testing.
8. Launch the application for the first time from the same mobile device that you used in step 6.
9. You can delete and install the app again, if necessary.

Remember the following information:

* The acquisition server provides an attribution match that is based on the IP address and user-agent information that is recorded in the link click \(step 6\) and when the app is launched \(step 7\).  You should be on the same network when you click the URL and when you open the app.
* By using HTTP monitoring tools, hits sent from the app can be monitored to provide verification of the acquisition attribution. You should see one `/v3//start` request and one `/v3//end` request sent to the acquisition server. Variations in the user-agent sent might cause attribution to fail.
* Ensure that [http://c00.adobe.com/v3//start](http://c00.adobe.com/v3//start) and [http://c00.adobe.com/v3//end](http://c00.adobe.com/v3//end) have the same user-agent values.
* The acquisition link and the hit from the SDK should be using the same HTTP/HTTPS protocol.  If they are using different protocols \(for example, the link uses HTTP and the SDK uses HTTPS\), the IP address might differ for each request \(on some carriers\), and the attribution might fail.

## Testing Legacy Acquisition in iOS

The following information helps you roundtrip an legacy acquisition campaign link that is based on a device fingerprint.

If the mobile app is not yet in Apple Store, you can select any mobile app as a destination when creating the campaign link. This only affects which app the acquisition server redirects you to, after you click the acquisition link, not the ability to test the acquisition link.

1. Navigate to _Use Legacy Acquisition Links_ in Adobe Mobile Services and generate an acquisition campaign URL.
2. From the mobile device on which you will install the app, click the generated link. Adobe's servers \(c00.adobe.com\) store the fingerprint and then redirect to the App Store. The app does not have to be downloaded for testing.
3. On the same mobile device that you used in step 2, launch the application for the first time.

The easiest way to ensure that this happens is to delete and install the app again.

Remember the following information:

* The acquisition server provides an attribution match that is based on IP address and user-agent information that recorded in the link click \(step 2\) and when the app is launched \(step 3\).
* By using HTTP monitoring tools, hits that are sent from the app can be monitored to provide verification of the acquisition attribution.
* Ensure that [http://c00.adobe.com/v3//start](http://c00.adobe.com/v3//start) and [http://c00.adobe.com/v3//end](http://c00.adobe.com/v3//end) have the same user-agent values.

