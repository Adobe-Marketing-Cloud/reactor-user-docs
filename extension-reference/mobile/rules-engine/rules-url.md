# Rules URLs

Since the Rules Engine can support multiple end-point URLs from where to fetch rules, the URLs are prioritized based on the following scheme:

```text
{
   "rules.url" : [
        "https://url/endpoint1",
        "https://url/endpoint2",
        ..
    ]
}
```

The Adobe Cloud Platform SDKs process the URLs based on the order in which they are specified. Both endpoints are URLs that point to a zipped rules collection that contains a _rules.json_ file, an asset folder that contains images, and HTMLs that are used by the rules. For more information about rules, see [Defining Rules](rules-json.md).

After downloading and extracting rules, the contents of this compressed file are stored in the cache. To trigger an update/download of the rules, see [Rules Engine Methods in Android](https://github.com/jiabingeng/sdk-v5-docs/tree/ece930399ffb1a7605b3aa13ed0e6633c8a8a481/rules-engine/rules-api-in-android.md) or [Rules Engine Methods in iOS](https://github.com/jiabingeng/sdk-v5-docs/tree/ece930399ffb1a7605b3aa13ed0e6633c8a8a481/rules-engine/rules-api-in-ios.md).

