# Users

This topic describes the user management process and available rights.

* [Assign user permissions](users.md#permissions)
* [Rights details](users.md#rights)

The following video tutorial provides an overview:

[https://www.youtube.com/embed/ba28BHX8cwU](https://www.youtube.com/embed/ba28BHX8cwU)

## Assign user permissions

Launch user permissions are managed in the Admin Console like other Adobe Experience Cloud products.

Every company that signs a contract with Adobe has at least one organization administrator \(org admin\) who is responsible for giving their users access to the right products. The org admin can add other org admins, and can also delegate to product admins who can assign permissions to individual products.

The steps below guide you through the process of assigning permissions. Steps 1-3 below can be bypassed by navigating directly to [Adobe Admin Console](https://adminconsole.adobe.com/enterprise/products). If you belong to more than one Organization, be sure to select the correct org from the top nav on the right.

1. Sign in to [http://marketing.adobe.com](http://marketing.adobe.com) with your Adobe ID, then choose the organization to use within Launch from the Navigation menu.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/nav-menu.png)

2. Open the solution picker by clicking the 9-dots icon from the navigation menu, then click Administration.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/choose-admin.png)

   If you can't see this link, both of the following conditions are true:

   * You are not an org admin.
   * You are not a product admin for any Experience Cloud products.

   In either case, ask an org admin to perform these steps for you, or to make you a product admin for Launch so you can do it yourself.

   Note: If you don't know who your org admin is, contact Client Care.

3. Click Launch Admin Console.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/launch-admin-console-button.png)

4. Click the Launch, by Adobe - %Company Name% card.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/launch-card.png)

   You can also click Products in the top nav, then select Launch, by Adobe - %Company Name% from the left nav.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/products-select-launch.png)

   If you do not see a Launch, by Adobe card and or if Launch, by Adobe does not appear in this list, then you are not an Org Admin, but you are a Product Admin for other Experience Cloud products. Because you are not an Administrator for Launch, you will need to find an Org Admin who can perform these steps for you or who can make you a Product Admin for Launch.

   After you select Launch, a list of product profiles displays. Think of these profiles as permission groups. One profile is created for you and is named Launch - %Company Name%.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/product-profiles.png)

5. Choose to edit this product profile, or create a new one.

   If you are editing an existing product profile, skip to Step 9.

6. To create a new product profile, click New Profile.
7. Give your new profile a name and a description, configure whether users should receive emails when they are added or removed from this profile, and then click Done.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-new.png)

8. Select the new product profile from the list, then open the Permissions tab. You can assign permissions across two dimensions: Properties and Rights.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-permissions.png)

9. To assign properties to this group definition, open the Properties section.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-properties-select.png)

   A list shows your Launch properties.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-properties.png)

   By default, new product configurations automatically include properties. This means that all properties \(present and future\) are included in the group definition.

   If Auto-include is disabled, all currently available properties are listed on the left. You can move properties into this group definition by clicking Add.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-properties-add.png)

   Click Save when finished.

10. Assign the rights you want to be part of your group definition. Open the Rights section.

    ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-rights-select.png)

    Rights are not automatically included. You must assign each right to your profile. You can quickly add all rights to this profile by using the + Add All button or you can assign individual rights by using the individual + buttons. For more information on what permissions are associated with each right, see [Rights details](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/administration/user-management.html#task_674BECF0B97C49A98C746B006CB49F0C). Click Save when finished. If Save is not available, you didn't make any changes and the profile won't give you any rights

    ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-rights.png)

    Some important notes:

    * Lack of rights means read-only access.

      If you belong to a product configuration with Auto-include properties and no rights, then you have read-only access to all properties in Launch.

    * If you don't at least assign the Manage Properties right, you won't be able to add any properties when you log in.
    * A user can belong to multiple groups, but the rights from those groups are not combined into a master permission set. That user still has only the rights explicitly granted by each group.

      For example, if Group 1 gives access to Property A with the Develop right and Group 2 gives access to Property B with the Publish right, Develop and Publish rights are not combined for Property A and Property B. You can only develop on Property A and publish on Property B.

11. To assign users to be part of your group, open the Users tab, then click Add User.

    ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/add-user.png)

    Click ... for additional options, such as bulk user operations.

    Note: Being an Org Admin or a Product Admin does not grant you any rights within the Launch product. You must belong to at least one product profile.

12. Search for the user you'd like to add to the group. You can search by name or by email address. This auto-populates from existing users in your Org. Once you have found the user you want, click on their name.

    ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-user.png)

    Once you've added users, they receive an email letting them know that they now have rights to Launch. They can login to Launch at [https://launch.adobe.com](https://launch.adobe.com).

    Note: If the user does not exist, you can simply type their entire email address, then provide a first and last name. The new user receives an email, and when they create an Adobe ID from that email invitation, they are linked together with the user account you created for them. If you are assigning permissions for yourself, you won't have this issue.

### Common issues

* Error loading account. Resolution: Your user does not belong to any Launch product profiles. See the steps above to create a profile and assign rights to it, and to assign a user to a profile.

  ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/profile-error.png)

* Grayed-out property button. Resolution: Your user account does not belong to a product configuration that has the Manage Properties right. Double-check steps 9 and on, above.

## Rights details

Although groups are created for the entire Experience Cloud, you must set up some Launch-specific options.

Launch deploys JavaScript to a web page that has control over site content, impacts load times, and so on. Who has permission to publish things is important to most users

Launch provides different rights that give people different capabilities within the system. Users with access but no assigned rights have read-only access.

The following rights can be set:

* Develop

  The Develop right lets you create rules and data elements. You can also create libraries and builds and deploy them in development environments. This controls what your client-side code does and when. The Develop right only lets you build or deploy to development environments.

* Approve

  Approvers can deploy the existing libraries built by users with the Develop right to the staging environment, and approve them for publishing.

* Publish

  The Publish right lets you take libraries approved by the Approver and publish them to the Production Environment

* Manage Extensions

  Extensions expand the scope and functionality of the code that Launch deploys to a website. For example, if you need to drop a Facebook pixel when certain criteria are met, you can install the Facebook extension and then use the Facebook Pixel action as part of a rule definition. This role could typically belong to IT or Marketing depending on your organization.

* Manage Properties

  A property is a container that has some basic metadata and assigns a universe where all other permissions apply. Typically, there is one property for each website where you want to deploy code. You can include multiple sites within a single property if you want to deploy the same code on multiple sites. Administrators usually perform this role.

* Manage Environments

  An environment describes how code is deployed. Use environments to determine whether code is deployed in Akamai or a private server. You can also configure whether you want deployable code or packaged .zip files \(passwords optional\). You can have one or more development environments, one optional staging environment, and one production environment. This role typically belongs to the IT group.

### Rights scenarios

#### One person show

If you run a small company that has one person in charge of everything, grant this user all rights for all properties.

#### Separation of duties

If you have a medium-sized company has an external consultant that does the work, but can't publish:

1. Create an account for your consultants and grant them only the develop right.
2. The consultant builds and tests within the confines you set.
3. If the consultant wants a new extension, or is ready to go live, a representative from your organization \(with the appropriate rights\), performs those actions.

#### Big company

An enterprise company might have multiple sites divided geographically, with different teams responsible for each geo. Within those teams, different individuals develop and publish.

This is similar to Scenario \#2, but with different geographic areas.

* North America
  * Develop group
  * Publish group
* South America
  * Develop group
  * Publish group
* Europe
  * Develop group
  * Publish group
* ...
  * Develop group
  * Publish group

