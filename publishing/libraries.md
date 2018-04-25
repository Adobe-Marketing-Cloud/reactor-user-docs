# Libraries

A library is a set of instructions for how extensions, data elements, and rules will interact with one another once they've been deployed.

When creating a library, you will specify the changes you want to make to your library.

At build time, these changes are combined with everything that has been submitted, approved, or published in previous libraries.

Libraries contain the addition or removal of:

* Rules
* Elements
* Extension configuration

Libraries must be assigned to an environment before they can be compiled into a build.

Libraries are approved or rejected as a whole. You cannot approve or reject individual items within a library.

A library moves between several environments as it makes its way through the publishing workflow.

## Create a library

1. Open the Publishing tab.

   The Publishing page lists the Dev libraries and provides the means to submit them for approval, move them to staging, or publish them to production.

2. Click Add New Library.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/library-create.jpg)

3. Name the library.
4. Assign the library to a Dev environment.
5. Add a change to the library. To add an item, click Add a Change, then choose the items you want to add. Any item that has been edited or deleted is available to add to the chosen library.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/library-add-change.jpg)

   You can add the following to your library:

   * Rules
   * Data elements
   * Extension configurations

6. To add any resources that have changed, click Add All Changed Resources.
7. Click Save or Save and Build for Development.

   Deploying compiles a build and deploys it to the assigned environment.

Once a library is created, use the drop down menu for that library to select one of the following options:

* Edit

  Change the library configuration.

* Build for Development

  Compiles a build and deploy it to the assigned environment.

* Submit for Approval

  Make the library available for an Approver to move it to the next step in the publishing process

* Delete

  Remove that library from the publishing process.

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/library-menu.png)

## Add to a library

1. Install the [extensions](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/publishing/extensions.md) you want to add.
2. Create the [data elements](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/publishing/data-elements.md) and rules you want to add.
3. Open the Publishing tab.
4. Select the [library](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/publishing/library.md) you want to change, then click Edit.
5. Use the rules, data elements, and extensions buttons to select the items you want to add to the library.
6. Save.

Changes to the library are shown in the Library Contents change log.

Note: Data elements can depend upon extensions. Rules can depend on both data elements and extensions. If you do not include all the necessary components in your library, the build will fail at build time and you'll need to add the necessary components before you complete a successful build. A future release will check dependencies when making changes to a library.

## Remove from a library

To remove something from a library, you must deactivate it and then publish the deactivated state.

1. Disable the extensions you want to remove, along with any data elements and rules that depend on those extensions.
2. Disable the data elements and rules you want to remove.
3. Open the Publishing tab.
4. Select the library you want to change.
5. Use the rules, data elements, and extensions buttons to select the disabled items you want to remove from the library.
6. Save.

## Manage library changes

1. Click on a library and select Edit to view library changes. All changes are shown in the Library Contents list.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/library-contents.jpg)

2. Click a change to view and select a revision.

   ![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/library-contents-revision.jpg)

3. Select whether to show all items or changed items.
4. Click the revision, then click Select Revision.
5. Click either Add a Change or Add All Changed Resources.

## Active Library

Libraries encapsulate a set of changes you'd like to make to your deployed code. Active Library makes this easier, allowing you to rapidly iterate through changes and see the impact.

You can save new and existing extensions, rules, and data elements directly to the library you're working on and, if desired, immediately kick off a build. You can also create a new library from the Active Library drop down.

1. [Create a new library](libraries.md#library-create).
2. Go to [Rules](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/publishing/rules.md), [Data Elements](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/publishing/data-elements.md), or [Extensions](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/publishing/extensions.md).
3. Select your Active Library.
4. Make your changes, then save and build the library.
5. Test your changes, and repeat these steps as needed.

