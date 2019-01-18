# Extension Upgrade

Extension developers continually add new features to their extensions, and frequently fix bugs. These updates are packaged into new versions of an extension and made available in the Launch catalog as upgrades.

## Extension Catalog

When an extension developer has provided a new version of the extension, that new version becomes available in the extension catalog. The catalog only shows the most recent version of an extension. You cannot install any extension version other than `latest`.

When you install an extension to your property, the currently available version is installed and your property remains with that specific version from that point forward, even if newer versions are added to the catalog.

## Upgrade Notifications

When you have installed an extension to your property, and a newer version is available in the catalog, you will see an Upgrade button on the extension card when you view the Installed Extensions page.

You'll also see a notice when editing resources that are provided by that extension.

## Upgrades are Permanent

If you want to upgrade to a newer version available in the catalog, you must install that upgrade yourself. An upgrade is a "change" that must be added to a library, tested, and published before it impacts your deployed tags.

Upgrading should not be taken lightly. You should not upgrade unless you are prepared to test the new extension and are ready to deploy it. Once the upgrade has been added to your property, it \_mus\_t be included in all libraries. Any library that does not include the upgraded extension will fail at build time.

There is currently no capability to downgrade your extension to a previous version. Once you've upgraded \(whether you publish or not\), the new extension version is on your property to stay.

## Upgrade Process

Installing an upgrade is pretty much the same as [installing the extension](./#add-a-new-extension) for the first time.

1. Click the Upgrade button to go to the Extension Configuration screen.
2. Make any configuration changes you'd like to make.
3. Click Save.

The upgrade is not actually performed until you hit Save. At any time previous to that, you can click Cancel and stay with the currently installed version. Clicking Save is the point of no return.

## Publishing an Upgrade

Once the upgraded extension is installed on your property, you must include it in all Libraries from that point forward. A build failure message displays for any libraries that do not include it.

Beyond that, adding the upgraded extension to your library is the same as [adding any other change](../../publishing/libraries.md#add-to-a-library) to a library.

From the Edit Library screen, you can use the "Add All Changed Resources" button or you can use the "Add a Resource" button and select the upgraded extension on its own.

Once you have added the extension upgrade to your Library, you can follow the steps outlined in [Approval Workflow](../../publishing/approval-workflow.md) to publish your library through to Production.

