# Builds

A build is the set of files containing all the code that runs on your website.

It is a composite of the changes you specified within a library, as well as everything that has been submitted, approved, or published before it.

The build consists of one or more JavaScript files that reference each other. These files are delivered to your hosting location using the environment and adapter that you have chosen for the library. The embed code that you deploy on your site points to this same location so the files can load in a browser when a user accesses your site.

## File format

The default file format for builds is a package of .js files that contain all the required code for your extensions, data elements, and rules to run in the way that you want them to.

However, in certain cases, you might prefer a .zip archive of the files rather than the executable JavaScript file. To create the .zip file, every environment has an Archive option. If you click this box, your builds are delivered as a .zip archive rather than as executable files. However, the build is still delivered to the location specified by the adapter.

To complete a build, select a library and click the Build option that is available at that level of the publishing process \(Build for Development, Build for Staging, and so on..

## Minification

Minification lowers bandwidth costs and improves speed by stripping data that isn't required for execution from a file.

To increase performance, Launch minifies everything, including:

* The main Launch library
* Module code provided by extension developers as part of an extension
* Custom code provided by Launch users

Note: If your module code and custom code are already minified, Launch minifies it again. This second minification doesn't provide additional benefits, but it doesn't cause any harm and it makes Launch less complex and easier to maintain.

Any embed codes provided in Launch point to the minified version of code, as seen in the file names, which follow the standard naming convention for minified files:

`launch-%environment_id%.min.js`

If you want to see the unminified code, remove .min from the file name:

`launch-%environment_id%.js`

If an extension developer provides minified code with their extension, Launch does not provide unminified code in the unminified build. Launch only provides what the extension developer delivers to Adobe. Similarly, if a Launch user puts minified code into a custom code box, that code is minified in unminified builds. Launch does not maxify anything.

For more information about minification, see [https://blog.stackpath.com/glossary/minification/](https://blog.stackpath.com/glossary/minification/).

