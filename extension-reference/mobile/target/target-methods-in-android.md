# Target Methods in Android

## getThirdPartyId

Gets the custom visitor ID for Target. The callback will be invoked to return the `thirdPartyId` value, or if no third-party ID is set, `null` is returned.

### Syntax

```java
public static void getThirdPartyId(final AdobeCallback<String> callback)
```

### Example

```java
Target.getThirdPartyId(new AdobeCallback<String>() {                    
    @Override
    public void call(String thirdPartyID) {
                // read target's thirdPartyID
    }
});
```

## setThirdPartyId

Sets the custom visitor ID for Target. This ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall or when `resetExperience` API is called.

### Syntax

```java
public static void setThirdPartyId(final String thirdPartyId)
```

### Example

```java
Target.setThirdPartyId("third-party-id");
```

## resetExperience

Resets the user's experience by removing the visitor identifiers. This method also removes previously set third-party and Target IDs from persistent storage.

### Syntax

```java
public static void resetExperience()
```

### Example

```java
Target.resetExperience();
```

## getTntId

Gets the Target user identifier. The callback will be invoked to return the `tntId` value, o, if no Target ID is set, `null` is returned.

Target returns `tntId` upon a successful call to `loadRequests` or `prefetchContent`. Once set in the SDK, this ID is preserved between app upgrades, is saved and restored during the standard application backup process, and is removed at uninstall or when `resetExperience` API is called.

### Syntax

```java
public static void getTntId(final AdobeCallback<String> callback)
```

### Example

```java
Target.getTntId(new AdobeCallback<String>() {
    @Override
    public void call(String value) {
        // read target's tntid
    }
});
```

## TargetRequest Builder

`TargetRequest` builder helps to create a `TargetRequest` instance. The returned instance can be used with `loadRequests`, which accepts a `TargetRequest` object list to retrieve offers for the specified mbox locations.

### Syntax

```java
TargetRequest request = new TargetRequest.Builder("mboxName","defaultContent")
                .setMboxParameters(new HashMap<String, String>())
                .setOrderParameters(new HashMap<String, Object>())
                .setProductParameters(new HashMap<String, String>())
                .setContentCallback(new AdobeCallback<String>() {
                    @Override
                    public void call(String value) {
                        // do something with target content.
                    }
                }).build();
```

## loadRequests

Sends a batch request to your configured Target server for multiple mbox locations that are specified in the `TargetRequest` list. Each object in the array contains a callback function, which will be invoked when content is available for its given mbox location.

### Syntax

```java
public static void loadRequests(final List<TargetRequest> requestArray,
                                    final Map<String, Object> profileParameters);
```

### Example

```java
// define parameters for first request
Map<String, Object> mboxParameters1 = new HashMap<>();
mboxParameters1.put("status", "platinum");

// define parameters for second request
Map<String, Object> mboxParameters2 = new HashMap<>();
mboxParameters2.put("userType", "paid");

List<String> purchasedIds = new ArrayList<String>();
purchasedIds.add("34");
purchasedIds.add("125"); 

Map<String, Object> orderParameters2 = new HashMap<>();
orderParameters2.put("id", "ADCKKIM");
orderParameters2.put("total", "344.30");
orderParameters2.put("purchasedProductIds",  purchasedIds);

Map<String, Object> productParameters2 = new HashMap<>();
productParameters2.put("id", "24D3412");
productParameters2.put("categoryId","Books");

TargetRequest request1 = new TargetRequest.Builder("mboxName1", "defaultContent1")
                .setMboxParameters(mboxParameters1)
                .setContentCallback(new AdobeCallback<String>() {
                    @Override
                    public void call(String value) {
                        // do something with target content.
                    }
                }).build();

TargetRequest request2 = new TargetRequest.Builder("mboxName2", "defaultContent2")
                .setMboxParameters(mboxParameters2)
                .setOrderParameters(orderParameters2)
                .setProductParameters(productParameters2)
                .setContentCallback(new AdobeCallback<String>() {
                    @Override
                    public void call(String value) {
                        // do something with target content.
                    }
                }).build();

// Creating Array of Request Objects
List<TargetRequest> locationRequests = new ArrayList<>();
locationRequests.add(request1);
locationRequests.add(request2);

 // Define the profile parameters map.
Map<String, Object> profileParameters = new HashMap<>();
profileParameters.put("ageGroup", "20-32");

// Call the targetLoadRequests API.
Target.loadRequests(locationRequests, profileParameters);
```

## locationClicked

Sends a click notification to configured Target server for a prefetched or regular mbox location. Click metric should be enabled for the provided location name in Target. If notification is sent for a prefetched mbox, its contents should already have been requested with `loadRequests` indicating that the mbox was viewed.

### Syntax:

```java
public static void locationClicked(final String mboxName,
                                    final Map<String, String> mboxParameters
                                    final Map<String, String> productParameters
                                    final Map<String, Object> orderParameters
                                    final Map<String, String> profileParameters);
```

### Example

```java
// Define Mbox parameters
Map<String, Object> mboxParameters = new HashMap<>();
mboxParameters.put("membership", "prime");

// Define Product parameters
Map<String, Object> productParameters = new HashMap<>();
productParameters.put("id", "CEDFJC");
productParameters.put("categoryId","Electronics");

List<String> purchasedIds = new ArrayList<String>();
purchasedIds.add("81");
purchasedIds.add("123"); 
purchasedIds.add("190");

// Define Order parameters
Map<String, Object> orderParameters = new HashMap<>();
orderParameters.put("id", "NJJICK");
orderParameters.put("total", "650");
orderParameters.put("purchasedProductIds",  purchasedIds);

// Creating Profile parameters
Map<String, Object> profileParameters = new HashMap<>();
profileParameters.put("ageGroup", "20-32");

Target.locationClicked("cartLocation", mboxParameters, productParameters, orderParameters, profileParameters);
```

