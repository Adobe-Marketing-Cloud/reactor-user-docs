# Deploy JavaScript tags to opt in to Launch

The combination of the European Union [General Data Protection Regulation \(GDPR\)](https://gdpr-info.eu/art-7-gdpr/) and [ePrivacy](https://medium.com/mydata/consent-lost-gdpr-and-found-eprivacy-e85cf881ffb) legislation requires companies to be able to manage consent for their users.  Adobe customers may require visitors to opt-in before Adobe solutions execute for any given visitor. Visitors should have the ability to manage their opt-in and opt-out status.

Adobe Experience Cloud customers require a variety of implementations of these requirements. Some use  enterprise-level consent managers and others build their own.

For Launch, extension developers use extensions and the rule builder to define opt-in and opt-out solutions.

This document contains information about how to prevent Adobe tags from firing until consent is acquired.

## Advertising Cloud

Launch does not fire Advertising Cloud automatically. Advertising Cloud only fires if you specifically tell it to in a rule action. Use the rule conditions to determine when and what to fire. For example, to use cookies to determine opt-in status, set a data element to read that cookie and use it as a condition in the rule to determine when to fire the Track Conversion action.

Integrations with consent managers \(such as OneTrust\) can set and track the consent cookies for customers, which can then be used in the rule builder.

## Analytics

In the Link Tracking section of the Analytics extension's configuration settings, make sure the following are _not_ selected: 

* Track download links
* Track outbound links

When these settings are not selected, Launch does not fire Adobe Analytics automatically. Analytics fires only if you specifically tell it to in a rule action. Use the rule conditions to determine when and what to fire. For example, to use cookies to determine opt-in status, set a data element to read that cookie and use it as a condition in the rule to determine when to fire the Send Beacon action. 

Integrations with consent managers \(such as OneTrust\) can set and track the consent cookies for customers, which can then be used in the rule builder.

## Audience Manager

DIL is currently set to fire automatically if it is placed on a customer page. There is currently no way to stop it from firing. Adobe is developing a way to pause the DIL from automatically firing while maintaining the correct cross-solution sequencing. This will be released soon.

Adobe recommends that you use server-side forwarding within Analytics.

## Experience Cloud ID

Experience Cloud ID currently fires automatically if it is placed on a customer page. At this time, there is no way to stop it from firing. Adobe is developing a way to pause Experience Cloud ID from automatically firing while maintaining the correct cross-solution sequencing. This will be released soon.

## Target

Launch does not fire Target automatically. Target fires only if you specifically tell it to in a rule action. Use the rule conditions to determine when and what to fire. For example, to use cookies to determine opt-in status, set a data element to read that cookie and use it as a condition in the rule to determine when to fire the Load Target action.

Integrations with consent managers \(such as OneTrust\) can set and track the consent cookies for customers, which can then be used in the rule builder.

