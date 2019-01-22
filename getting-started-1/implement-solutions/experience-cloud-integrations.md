# Experience Cloud integrations

This tutorial reviews the key integrations between the solutions you have implemented. If you have completed the earlier tutorials, you have already implemented the code-aspects of the integrations. You don't need to do any additional work in this tutorial besides reading and validating.

## Objectives

At the end of this lesson, you will be able to:

* Explain the use cases for Audience Sharing, Analytics for Target \(A4T\), and Customer Attributes integrations
* Validate the basic client-side implementation aspects of these integrations

## Prerequisites

You should complete all of the previous Launch implementation tutorials before following the instructions in this tutorial.

**Note:** There are many user-permissions requirements, account configurations, and provisioning steps that are required to fully use these integrations and which are beyond the scope of this tutorial. If you are not already using these integrations in your current implementation of the Experience Cloud, you should consider the following:

* Review the full requirements of the [Core Services integrations](https://marketing.adobe.com/resources/help/en_US/mcloud/core_services.html)
* Review the full requirements of the [Analytics for Target integration](https://marketing.adobe.com/resources/help/en_US/target/a4t/c_before_implement.html)
* Have an Administrator of your Experience Cloud Organization [request provisioning of these integrations](https://www.adobe.com/go/audiences)

## Audiences

[Audiences](https://marketing.adobe.com/resources/help/en_US/mcloud/audience_library.html) are part of the People core service. They allow you to share audiences between solutions. For example, you can create an audience in Audience Manager and use it to deliver personalized content with Target.

The main requirements to implement A4T, which you have already done, are to:

* Implement the Experience Cloud Id Service
* Implement Audience Manager
* Implement other solutions that you would like to receive or create audiences, such as Target and Analytics

### Validate the Audiences integration

The best way to validate the Audiences integration is to build an audience, share it to another solution, and then use it in the other solution. For example, confirm that a visitor who qualifies for an AAM segment can qualify for a Target activity targeted to that segment. However, this is beyond the scope of this tutorial.

These validation steps focus on the critical part visible in the client-side implementation: the Visitor ID.

1. Open the [We.Retail site](https://aem.enablementadobe.com/content/we-retail/us/en.html).
2. Make sure the Debugger is mapping the Launch property to your Development environment, as described in the earlier lesson.

   ![](../../.gitbook/assets/switchenvironments-debuggeronweretail2%20%281%29.png)

3. Go to the Network tab of the Debugger, then click **Clear All Requests** to clean things up.
4. Reload the We.Retail page, making sure that you see both the Target and Analytics requests in the Debugger.
5. Reload the We.Retail page again. You should now see four requests in the Network tab of the Debugger—two for Target and two for Analytics.
6. Look in the row labeled "Experience Cloud Visitor ID." The IDs in every request by every solution should always be the same.

   ![](../../.gitbook/assets/integrations-matchingecids.png)

   The IDs are unique per visitor, which you can confirm by asking a co-worker to repeat these steps.

## Analytics for Target \(A4T\)

The [Analytics for Target \(A4T\)](https://marketing.adobe.com/resources/help/en_US/target/a4t/a4t.html) integration allows you to leverage your Analytics data as the source for reporting metrics in Target.

The main requirements to implement A4T, which you have already done, are to:

* Implement the Experience Cloud ID Service
* Fire the global mbox before the Analytics page view beacon

A4T works by stitching together a server-side request from Target to Analytics with the Analytics page view beacon, referred to as "hit-stitching." Hit-stitching requires that the Target request that delivers the activity \(or increments a Target-based goal metric\) have a parameter that matches a parameter in the Analytics page view beacon. This parameter is called the supplemental data ID \(SDID\).

### Validate the A4T Implementation

The best way to validate the A4T integration is to build a Target activity using A4T and validate the reporting data. This is beyond the scope of this tutorial. This tutorial shows how to confirm that the supplemental data IDs match between the solution calls.

1. Open the [We.Retail site](https://aem.enablementadobe.com/content/we-retail/us/en.html).
2. Make sure the Debugger is mapping the Launch property to your Development environment, as described in the earlier lesson.

   ![](../../.gitbook/assets/switchenvironments-debuggeronweretail2%20%281%29.png)

3. Go to the Network tab of the Debugger.
4. Click **Clear All Requests** to clean things up.
5. Reload the We.Retail page, making sure that you see both the Target and Analytics requests in the Debugger.
6. Reload the We.Retail page again. You should see four requests in the Network tab of the Debugger, two for Target and two for Analytics.
7. Look in the row labeled "Supplemental Data ID."

   The IDs from the first page load should match between Target and Analytics. The IDs from the second page load should also match, but be different from the first page load.

   ![](../../.gitbook/assets/integrations-matchingsdids.png)

If you make additional Target requests in the scope of a page load \(not including single-page apps\) that are part of A4T activities, give them unique names \(not target-global-mbox\) so that they continue to have the same SDIDs of the initial Target and Analytics requests.

## Customer attributes

[Customer Attributes](https://marketing.adobe.com/resources/help/en_US/mcloud/attributes.html) are a part of the People core service that allows you to upload data from your customer relationship management \(CRM\) database and leverage it in Adobe Analytics and Adobe Target.

The main requirements to implement Customer Attributes, which you have already done, are to:

* Implement the Experience Cloud ID Service
* Set Customer IDs via the Id Service before Target and Analytics fire their requests, which you accomplished using the rule ordering feature in Launch

### Validate the Customer Attributes implementation

You validated that the Customer IDs are passed to both the ID Service and to Target in earlier tutorials. You can also validate the Customer ID in the Analytics hit as well. At this time, the Customer ID is one of the few parameters that does not show up in the Experience Cloud Debugger, but you can use the browser's JavaScript Console to view it.

1. Open the We.Retail site.
2. Open your browser's developer tools.
3. Go to the Network tab.
4. In the filter field, type b/ss, which limits what you see to the Adobe Analytics requests.

   ![](../../.gitbook/assets/aam-openthejsconsole.png)

5. Click the **LOGIN** link in the top right corner of the site, enter `test@adobe.com` as the username, and enter `test` as the password, then click **Login**.

   You are returned to the home page, which triggers a beacon that you can see in the developer tools.

6. Click on the request and select the Headers tab.
7. Scroll down until you see some nested parameters:
   * `cid`: The standard delimiter for the Customer ID portion of the request
   * `crm_id`: The custom integration code, which you specified in the ID Service lesson
   * `id`: The Customer ID value coming from your Email \(Hashed\) data element
   * `as`: The Authentication State, with "1" meaning logged in

![](../../.gitbook/assets/integrations-analyticscustomeridvalidation.png)

