# Builds

A build is the set of files containing all the code that runs on the client device.

It is a composite of the changes you specified within your Library, as well as everything that has been submitted, approved, or published before it.

The build consists of client-side code files that reference each other. These files are delivered to your hosting location using the environment and host that you have chosen for the library. The code that you deploy on your site points to this same location so the files can load when a user accesses your site or application.

## File Contents

A Library defines a discreet set of Launch resources \(Extensions, Rules, and Data Elements\) that should be included within it.

A Build contains all the module code \(provided by the extension developers\) and the configuration \(entered by you\) that is needed to power the resources contained within the Library. For example, if an extension provides actions that are not used within your rules, then the code to perform those actions is not contained within the Build.

Builds are divided into the main library file and potentially many smaller files. The main library file is referenced in your embed code and loaded onto the page at run-time. It contains:

* The rules engine
* All Extension configuration
* All Data Element code and configuration
* All Rule Event code and configuration
* All Condition code and configuration
* Event code and configuration for any rules that have Library Loaded or Page Bottom as the event \(since we know we'll need that right away\).

The smaller files contain code and configuration for individual Actions that are loaded onto the page as needed. When a Rule is triggered and its Conditions are evaluated such that the Actions need to be executed, the necessary code and configuration for that specific action is retrieved from one of the smaller files. This means that only the code needed to perform the necessary Actions is ever loaded onto the page, making the main library as small as possible.

## File Format

The default file format for builds is a package of files that contain all the required code for your extensions, data elements, and rules to run in the way that you want them to.

However, in certain cases, you might prefer a .zip archive of the files rather than the executable client-side code file. For example, you might want to create an archive if you host your build yourself and want to use the build in another deployment. If you provide anything in the self-hosted path to library field, you can save your environment. Along with your new code, a link to the archived download becomes available. Launch still builds your library and deploys it, but instead of deploying a bunch of code files, you can deploy a zip file to Akamai, and download it from assets.adobedtm.com/...

**Note:** Nothing exists in that location until you make a build.

Regardless of file format, the build is always delivered to the location specified by the Host.

To complete a build, select a library and click the Build option that is available at that level of the publishing process \(Build for Development, Build for Staging, and so on..

## Minification

Minification lowers bandwidth costs and improves speed by stripping data that isn't required for execution from a file.

To increase performance, Launch minifies everything, including:

* The main Launch library
* Module code provided by extension developers as part of an extension
* Custom code provided by Launch users

**Note:** If your module code and custom code are already minified, Launch minifies it again. This second minification doesn't provide additional benefits, but it doesn't cause any harm and it makes Launch less complex and easier to maintain.

Any client-side code provided in Launch points to the minified version of code, as seen in the file names, which follow the standard naming convention for minified files:

`launch-%environment_id%.min.js`

If you want to see the unminified code, remove .min from the file name:

`launch-%environment_id%.js`

If an extension developer provides minified code with their extension, Launch does not provide unminified code in the unminified build. Launch only provides what the extension developer delivers to Adobe. Similarly, if a Launch user puts minified code into a custom code box, that code is still minified in unminified builds. Launch does not maxify anything.

For more information about minification, see [https://blog.stackpath.com/glossary/minification/](https://blog.stackpath.com/glossary/minification/).

When performing a build, Launch will construct the unminified library first, then minify the entire library all at once.

