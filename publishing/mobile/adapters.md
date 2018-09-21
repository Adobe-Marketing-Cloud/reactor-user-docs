# Adapters

Extensions, rules, and data elements are building blocks. When you want to make your application do something, these building blocks are added to libraries and then a library is "built" into a build. Those builds are delivered to a hosted location.

Adapters define available destinations where the builds can be delivered. For mobile extensions, the **Managed by Adobe** adapter is selected by default. 

The same adapter can be used for multiple environments in a property.

## Managed by Adobe

This adapter type is the default selection and is simplest to manage.

When you choose the Adobe-managed option, libraries that Launch builds will be delivered to a 3rd party CDN that Adobe has contracted with. These CDNs operate independently from Adobe, so even when Launch has maintenance or downtime, the tags deployed to your sites and applications continue to function as normal. The embed code references the main library file on the CDN so a browser can retrieve the files at run-time.

Today, the primary CDN provider is Akamai. Files hosted on Akamai will have a domain of [assets.adobedtm.com](https://assets.adobedtm.com). This can be referenced securely or not securely \(http:// or https://\) based on how you call it in your `<script>` tag.

When you create a new property through the Launch UI, a default adapter of this type is created for you.

