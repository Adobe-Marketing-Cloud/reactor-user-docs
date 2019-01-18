# Adapters

Extensions, rules, and data elements are building blocks. When you want to make your application do something, these building blocks are added to libraries and then a library is "built" into a build. Those builds are delivered to a hosted location.

Adapters define available destinations where the builds can be delivered. They come in two types:

1. Managed by Adobe
2. SFTP

The same adapter can be used for multiple environments within a property.

## Managed by Adobe

This adapter type is the default selection and is simplest to manage.

When you choose the Adobe-managed option, libraries that Launch builds will be delivered to a 3rd party CDN that Adobe has contracted with. These CDNs operate independently from Adobe, so even when Launch has maintenance or downtime, the tags deployed to your sites and applications continue to function as normal. The embed code references the main library file on the CDN so a browser can retrieve the files at run-time.

Today, the primary CDN provider is Akamai. Files hosted on Akamai will have a domain of [assets.adobedtm.com](https://assets.adobedtm.com). This can be referenced securely or not securely \(http:// or https://\) based on how you call it in your `<script>` tag.

When you create a new property through the Launch UI, a default adapter of this type is created for you.

### Create Managed by Adobe adapter

1. Open the Adapters tab.
2. Create the new adapter.
3. Name the adapter.
4. Select Managed by Adobe as the adapter type.
5. Click Save.

## SFTP

If you do not want your builds delivered to Akamai, your other option is to have Launch deliver builds to a secured SFTP server that you host.

Launch connects to your SFTP site using an encrypted key. There are a few steps to set this up correctly:

1. You must have a public/private key pair installed on your SFTP server.  You can generate these keys on your server or generate them somewhere else and install them to your server.  See [here ](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#generating-a-new-ssh-key)for an example of how to generate keys.
2. You must encrypt the private key with Launch's public GPG key so that you can provide your private key to Launch during the SFTP adapter creation process.  See [here](https://developer.adobelaunch.com/guides/api/encrypting_values/) for instructions and Launch's public GPG keys.  Unless you _know_ you need a different one, use the Production Environment's GPG key.  Finally, you can encrypt your private key form any  machine, you do not need to install GPG on your server in order to complete this step.
3. You may need to whitelist the Launch IP address with your company firewall to allow Launch to be able to reach your SFTP server and connect to it.

### Create an SFTP adapter

1. Open the Adapters tab.
2. Create the new Adapter.
3. Name your adapter.
4. Select SFTP as the adapter type.
5. Enter the host, path, port, username, and encrypted private key.
6. Click Save.

When you click Save, Launch will test whether it is able to connect to your SFTP server and tell you whether it was able to connect.

