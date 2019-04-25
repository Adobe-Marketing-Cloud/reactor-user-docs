# Deleting resources

Deleting a resource is a permanent removal of that resource from Launch. If you still want the resource to appear in Launch, but not be in your library, see [Remove Resources from a Library](remove-resources-from-library.md).

You can delete data elements, rules, extensions, adapters, environments, and properties. Once deleted, these resources are not recoverable.

Resources that are added to libraries \(data elements, rules, and extensions\) have special considerations when you delete them.

## Prepare a resource for deletion

Resources exist in different states and they depend on one another. Before you delete a resource, you must make sure it is in a state where it can be deleted.

Preparing a resource for deletion consists of two basic steps:

1. Resolve Dependencies
2. Remove from Libraries

### Resolve dependencies

Rules, data elements, and extensions are interdependent, so most of the time when you delete one, there is a cascading effect and you have other things you need to clean up.

#### Rules

Rules depend on other resources \(extensions and data elements\), but they do not have any resources that depend on them. Deleting a rule means you can no longer use it in a library or even view it, but you won't have any dependencies to clean up afterwards.

#### Data elements

Data elements depend on extensions, but unlike rules, data elements can have rules and extensions which depend on them. If you delete a data element, any rules or extensions which depend on this data element will be affected.

Once deleted, the data element no longer returns the correct value at run-time. It either returns an empty string or the name of the deleted data element wrapped in %% \(example: `%data-element-name%`\). This behavior is configurable within Property Settings.

You can resolve these dependencies before or after you delete the data element.

#### Extensions

All other resources \(rules, rule components, and data elements\) are provided by extensions.

Rule components and data elements depend on extensions for their behavior, but also just to be displayed in the Launch interface. If you delete the extension before you resolve dependencies, you'll no longer be able to view these orphaned resources. These orphaned resources appear in list views, but you'll receive an error when you try to open the detail view.

For this reason, you should be very careful when deleting extensions and you should resolve dependencies before you delete them.

### Remove from libraries

Before you can delete a resource, you must remove it from any libraries that contain it. This process is different depending on the state of the library.

#### Development

1. Open the library
2. Remove the resource
3. Save the library
4. Delete the resource

#### Submitted or approved

1. Reject the library \(moves it back to Development\)
2. Follow the above steps to remove a resource from a development library

#### Production

1. Disable the resource
2. Publish the disabled resource through to Production
3. Delete the resource

## Delete a resource

From the appropriate list view, select the resource you want to delete, then click **Delete**.

