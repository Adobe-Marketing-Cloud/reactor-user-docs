# Self-hosting Libraries

Everything you do in Launch has the ultimate goal of producing a set of files to control the behavior of your application at run-time. This set of files is called a [Build](builds.md).

Builds need to be hosted somewhere so that client devices can retrieve them at run-time as needed.

Launch can either manage the hosting of these files for you or you can do it yourself.

## Managed by Adobe

Adobe does not actually host the builds for you, instead they are delivered to a 3rd party CDN that Adobe has contracted with.

Today, the primary CDN provider is Akamai. Files hosted on Akamai will have a domain of [assets.adobedtm.com](https://assets.adobedtm.com).

### Why use managed hosting?

The primary reason to use managed hosting is convenience. It is easier to create the required adapter and you don't have to worry about maintenance.

### About Akamai

Akamai is robust when serving content to a global, high-volume audience of Web visitors. Akamai runs redundant networks of load-balanced, geo-optimized nodes to serve content as quickly as possible to visitors wherever they are located throughout the world.

Specifically, Akamai runs more than 137,000 servers in 87 countries within more than 1,150 networks. In terms of redundancy, Akamai does not just route from one server to another, Akamai routes from one node of servers to another node of servers as-needed. In other words, each node consists of multiple servers for redundancy within a node, so a box going down is not an issue because the other boxes in the node take over. If a node goes down, Akamai serves from the next closest one, with the same cached content. Nodes are dynamically selected based on visitor location, traffic load, and other factors so content is consistently served from the best local node for each visitor.

Akamai also has access to nodes in China, so end-users in China will still get traffic from nodes that are geographically close to them.

#### Can I avoid errors in case of CDN unavailability?

No. Launch can do nothing from the client side if the library is unavailable.

#### CDN cache control headers

When you choose to have Adobe manage your hosting, you do not have control over the headers on the response, so inherit the Adobe defaults. There is no way to get custom headers when you have Adobe manage your hosting.

The cache control headers Adobe uses for managed hosting are as follows:

* Production builds: Cache control headers are set to 60 minutes
* Staging builds with "-staging" in the filename: Cache control headers are set to 0 minutes
* Dev builds with "-development" in the filename: Cache control headers are set to 0 minutes

Note: It is up to browsers to receive and respect the cache control headers. Some browsers might ignore them.

Important: Cache control headers were added in Spring of 2018. Environments that do not have "-development" or "-staging" in their Environment embed codes were created prior to that time. These environments will need to be recreated if you want to take advantage of these new cache control headers. If you don't re-create the environments, you'll have the same 60-minute cache control as the production libraries.

### How to use managed hosting

In order to have Adobe manage your hosting you need to create a Managed by Adobe adapter, then assign your environments to use this adapter. See [Adapters](adapters.md) for more info.

## Self-hosting

If you don't want Adobe to manage your hosted files, you must host them yourself. In order to accomplish this, you'll need to get the completed builds from Launch and be responsible for getting the files through your company's release cycle onto company managed servers.

### Why use self-hosting?

There are a number of reasons to choose to host your own build files.

1. Some browsers block the assets.adobedtm.com domain based on the privacy settings the end-user has configured
2. Self-hosting reduces the required number of DNS lookups
3. You require use of HTTP/2
4. You have specific headers you need to set for security
5. Your cache control requirements differ from the Adobe default settings
6. You want more control over the location of edge nodes
7. Your organization has security and legal requirements that prevent you from using the Adobe-managed option

### How to self-host

There are two methods you can use to acquire completed builds so that you can self-host.

1. Download
2. Direct Delivery

#### Download

You can have Launch deliver builds as a packaged .zip file \(encryption optional\). You can then unzip the package and insert the contents into your release cycle to get them live on your own servers.

In order to do this, you can using a [Managed by Adobe](adapters.md#managed-by-adobe) adapter and selecting the [Archive](environments.md#archive) option on your environment. The environment will provide you with a download link and whenever a build is created, you can retrieve it from the provided download link.

#### Direct Delivery

You can have Launch deliver builds directly to an SFTP server that you have created. You take responsibility to get these filed into your release cycle and push them live.

In order to do direct delivery, you should create an [SFTP adapter](adapters.md#sftp) and assign that adapter to your environment. Whenever you build a library in that environment, the files will be delivered to your SFTP server.

