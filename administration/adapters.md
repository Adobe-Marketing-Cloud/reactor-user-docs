# Adapters

When you create a build, Launch delivers that build to a location determined by the adapter assigned to the environment.

You can choose to have Launch manage that location for you or to manage it yourself.

## Adobe-managed adapter

If you choose to have Launch manage the hosting for your build, Launch delivers the build to the Akamai Edge CDN. The embed code references the delivery location of these files so a browser can retrieve the files as needed.

This is the easiest, quickest, way to create an adapter for your environments.

### Create Akamai adapter

1. Open the Adapters tab.
2. Create the new adapter.
3. Name the adapter.
4. Select Akamai as the adapter type.
5. Click Save.

### About Akamai

Akamai is the primary external hosting option. Akamai provides you with a reliable hosting experience and is the simplest option to implement. Akamai provides the greatest third-party infrastructure dependencies, such as DNS lookup, faster load times, and faster round-trip delivery times.

* [Why choose Akamai hosting for library files?](adapters.md#why-choose-akamai-hosting-for-library-files)
* [Can I avoid errors in case of Akamai unavailability?](adapters.md#can-i-avoid-errors-in-case-of-akamai-unavailability)
* [Akamai cache control headers](adapters.md#akamai-cache-control-headers)

### Why choose Akamai hosting for library files?

When you choose the Akamai option, it means that your Launch library files are served to your visitors from Adobe’s Edge CDN, which runs on Akamai architecture.

Akamai is robust when serving content to a global, high-volume audience of Web visitors. Akamai runs redundant networks of load-balanced, geo-optimized nodes to serve content as quickly as possible to visitors wherever they are located throughout the world.

Specifically, Akamai runs more than 137,000 servers in 87 countries within more than 1,150 networks. In terms of redundancy, Akamai does not just route from one server to another, Akamai routes from one node of servers to another node of servers as-needed. In other words, each node consists of multiple servers for redundancy within a node, so a box going down is not an issue because he other boxes in the node take over. If a node goes down, Akamai serves from the next closest one, with the same cached content. Nodes are dynamically selected based on visitor location, traffic load, and other factors so content is consistently served from the best local node for each visitor.

### Can I avoid errors in case of Akamai unavailability?

No. Launch can do nothing from the client side if the library is unavailable. However, it is extremely unlikely that Akamai would be unavailable.

### Akamai cache control headers

Cache control headers are automatically set for libraries hosted on Akamai \(assets.adobedtm.com\).

* Production builds: Cache control headers are set to 60 minutes
* Staging builds with "-staging" in the filename: Cache control headers are set to 0 minutes
* Dev builds with "-development" in the filename: Cache control headers are set to 0 minutes
* Launch Staging builds without "-staging" in the filename: The default of 60 minutes is inherited
* Launch Development builds without "-development" in the filename: The default of 60 minutes is inherited

Note: It is up to browsers to receive and respect the cache control headers. Some browsers might ignore them.

Important: Launch developers who do not have "-development" or "-staging" in their Environment embed codes need to re-create their Development and Staging environments to get the 0 cache control header. If you don't re-create the environments, you'll have the same 60-minute cache control as the production libraries.

## Self-managed adapter

There are a number of reasons to choose to host your own build files.

* Organizations have a number of security and legal requirements that might make cloud-hosting a less-desirable or impossible option.
* You can reduce the number of required DNS lookups by hosting your own files.
* You might prefer to have more control over edge locations, caching, and so on.

To meet these requirements, Launch allows you to push your completed builds to an SFTP destination.

Launch connects to an SFTP site using an encrypted key. To use this connection type:

* Your SFTP server must generate a key
* You must provide the username and encrypted private key during the adapter setup process

If you select an SFTP adapter for your environment, there is an additional path variable that you'll need to provide to the environment. This path field is the HTTP path to where your build files are stored relative to your web site. This field is required because the different files in the build reference one another. Launch needs to know where they will are so the files can reference each other properly.

### Create an SFTP adapter

1. Open the Adapters tab.
2. Create the new Adapter.
3. Name your adapter.
4. Select SFTP as the adapter type.
5. Enter the host, path, port, username, and encrypted private key.
6. Click Save.

