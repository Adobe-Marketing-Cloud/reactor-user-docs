# Adobe Target Release Notes

## February 12, 2019

### Adobe Target Extension 0.9.1

#### **Features**

* Updated Extension to use at.js 1.7.0 that has Opt-in privacy functionality supported via Adobe Launch to control how and when the Target tag is fired. Please check Launch Documentation on how to setup your implementation of Opt-in. Added possibility to customize if an mbox parameter that has an empty value should be sent to Target or not.


## January 23, 2019

* Updated at.js to version 1.6.4
* Extension UI migrated to Adobe Spectrum

## November 15, 2018

* Updated at.js to version 1.6.3

## October 24, 2018

* Updated at.js to version 1.6.2

## August 23, 2018

* Updated at.js to version 1.6.0

## August 10, 2018

* Minor changes
* Updated the `exchangeUrl` property in the `extension.json` file

## August 1, 2018

* Minor fixes

## June 16, 2018

* Updated at.js version to 1.5.0
* Fixed an issue where Media Optimizer threw a null reference error in IE 11

## June 15, 2018

### Adobe Target Extension 0.6.0

#### **Features**

* Target Extension has been updated to use at.js v1.3.1. When you deploy Target with Analytics, we now wait until all Target calls have resolved \(including redirect offers\) before Analytics fires, resolving the race condition that previously existed.

## February 22, 2018

### Adobe Target Extension 0.4.1

#### **Features**

* Added Adobe Exchange listing to extension.json
* Added checks to see if Target is disabled and if Authoring is enabled

#### **Bug fixes**

* Fixed an error in the Adobe Target Extension that prevented the Visual Experience Composer from unhiding the page when deployed through Launch.

## February 8, 2018

### Adobe Target Extension 0.4.0

#### **Features**

* Updated views in extension configuration screens
* at.js has been updated to version 1.2.3 \(adds support for JSON offers\)

