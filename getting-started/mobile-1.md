# Mobile

To get started in Mobile, complete the following tasks:

* [Create and Deploy Configurations in Adobe Launch](mobile-1.md#create-and-deploy-configurations-in-adobe-launch)
* [Install the Adobe Cloud Platform SDKs in an Android or iOS App](mobile-1.md#install-the-adobe-cloud-platform-sdks-in-an-android-or-ios-app)
* [Use the Adobe Cloud Platform SDKs in an Android App](mobile-1.md#use-the-adobe-cloud-platform-sdks-in-an-android-app)
* [Use the Adobe Cloud Platform SDKs in an iOS App](mobile-1.md#use-the-adobe-experience-cloud-platform-sdks-in-an-ios-app)

## Create and Deploy Configurations in Adobe Launch

1. Click **New Property**. 
2. Create a new property and select **Mobile** as the platform.
3. Find the new property in the Properties list and click to open it.
4. Go to the **Extensions** tab.

   Mobile Core and Profile extensions are installed by default.

5. Click **Catalog**, and install additional extensions needed.
6. Go to the **Data Elements** tab and add any data elements needed.
7. Go to the **Rules** tab and add any rules needed.
8. Go to the **Environments** tab.

   Production, Staging, and Development environments have been added by default.

9. Click **Add Environment**, and add any additional development environments needed.

   Additional Production and Staging environments cannot be added.

10. Go to the **Publishing** tab to publish the configuration.

    This process involves creating a library of changes and then deploying the library:

    a. Click on **Add New Library** under the **Development** section of the publishing workflow.

    b. Specify any name for the library and select a development environment from the **Environment** dropdown.

    c. Add the configuration changes to be deployed.

    d. Click **Add All Changed Resources** \(or to add only some changes, click **Add a Resource**\).

    e. Click **Save & Build for Development**.

    The library will build and then show under the **Development** section of the publishing workflow.

11. Click on the down arrow for the library and select **Submit for Approval**.

    The configuration contained in the library will then be deployed to the Development environment and the library will show under the Submitted section of the publishing workflow. Later, the library can be deployed to Staging and Production environments using the rest of the publishing workflow. For now, testing can be done using the configuration in the Development environment.

## Install the Adobe Cloud Platform SDKs in an Android or iOS App

1. Open the mobile property in Launch and go to the **Environments** tab to get the install instructions for adding the SDK to an app.
2. Find the environment needed in the table and click on the box icon under the **Install** column.
3. On the **Mobile Install Instructions** pop-up, choose **Android** or **iOS**.
4. Follow the instructions for using Grade with Android or CocoaPods with iOS. They necessary dependecy and initialization code can be copied from the pop-up to the app project.

## Use the Adobe Cloud Platform SDKs in an Android App

**Important:** This version of the Adobe Experience Cloud Platform SDKs supports **Android 4.0 \(API 14\) or later.**

The SDK configuration should be retrieved remotely from Launch:

1. Get the App ID from Adobe Launch.
2. Create MainActivity.java in the app.
3. Add the following line:

   ```text
   MobileCore.configureWithAppID("YOUR_APP_ID");
   ```

4. Launch the app and it will send a remote config request to the Adobe Launch servers and configure the app using the remote config.

## Use the Adobe Cloud Platform SDKs in an iOS App

**Important:** This version of the Adobe Cloud Platform SDKs supports **iOS 10 or later.**

The SDK configuration should be retrieved remotely from Launch:

1. Get the App ID from Adobe Launch. 
2. Within your app, open AppDelegate.swift \(or AppDelegate.m if developing in Objective-C\). 
3. Add this line in your `didFinishLaunchingWithOptions` method:

   ```text
   ACPCore.configure(withAppId: "YOUR_APP_ID") // swift

   [ACPCore configureWithAppId:@"YOUR_APP_ID"]; // obj-c 
   ```

4. Launch the app and it will send a remote config request to the Adobe Launch servers and configure the app using the remote config.

For more information about the mobile extensions, see [Mobile]().

