# Approval Workflow

The Approval workflow refers to the process of creating libraries, testing builds, and approving them for production.

The available actions depend on the state of the library and the level of permission you have.

## Permissions

There are three levels of permission that are important for the approval workflow:

* **The develop right:** Includes the ability to create libraries, build for development, and submit for approval
* **The approve right:** Includes the ability to build for staging and approve
* **The publish right:** Includes the ability to publish an approved library

The rights are not inclusive. For a single person to perform the workflow from start to finish, that person must be granted all three rights within a given property.

## Library state

There are four basic states that a library can be in. Specific actions must be taken to move a library between these states. These four states are represented as columns within the Publishing tab.

* [Development](approval-workflow.md#development)
* [Submitted](approval-workflow.md#submitted)
* [Approved](approval-workflow.md#approved)
* [Published](approval-workflow.md#published)

![](https://github.com/Aaronius/gitbooktest/tree/190c7c3dc0fbdc5a9ed48e7927383d3e9f032d78/images/library-state.png)

## Development

Libraries are created in Development. Any changes to a library must be made while the library is in Development. When development and testing are completed, the library is submitted.

Available actions for a library in Development state are:

* Edit

  Use the library Edit screen to add or remove components from a library.

* Build for Development

  Create a build for the library. The build is compiled and deployed to the environment the library is assigned to. This step fails if the library has not been assigned to an environment.

* Submit for Approval

  Unassigns the library from its development environment and moves the library to the submitted column for an Approver to work on.

## Submitted

An Approver tests the library in a staging environment. When testing is completed, the library is approved or rejected. Rejected builds go back to Development so changes can be made before the approval flow starts over again.

Available actions for a library in Submitted state are:

* Open

  View the contents of the library. Changes are not allowed. If changes are needed, the library should be rejected so changes can be made in Development.

* Build for Staging

  Assigns the library to the staging environment and deploys it.

* Approve for Publishing

  Moves the library to the Approved column for a Publisher to publish

* Reject

  Unassigns the library from the staging environment and moves the library to the Development column for changes.

## Approved

The library is waiting to be published. A Publisher can publish or reject the library. Rejected builds go back to Development so that changes can be made before the approval flow begins again.

Available actions for a library in Approved state are:

* Open

  View the contents of the library. Changes are not allowed. If changes are needed, the library should be rejected so changes can be made in Development.

* Build and Publish to Production

  Unassigns the library from the staging environment, assigns the library to the production environment, and deploys it.

  Important: When this option is selected, your library becomes live in your production environment, so be sure before you click the button.

* Reject

  Unassigns the library from the staging environment and moves the library to the Development column for changes.

## Published

The library is live in the production environment. This column shows which libraries have been published and their publish dates. You can look at these libraries, but you cannot make changes. If you want to change what's in your production environment, you'll need to create a new library and push it through the approval process.

