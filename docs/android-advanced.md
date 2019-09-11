In this section we are going to see how to integrate GreedyGame Native Ads in Android native projects.

### **Importing GreedyGame Native Ads SDK**

Games built with Android Studio can easily integrate with <a target="_blank" rel="noopener noreferrer" href="https://gradle.org">Gradle</a>.

**Add the following to the app level** `build.gradle`. (excerpt)

```gradle hl_lines="6"
dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation 'com.android.support:appcompat-v7:26.1.0'
    ...............
    //greedygame sdk
    implementation 'com.greedygame:core:9.0.0'
}
```

### **Dependency Libraries**
Include the following in the `app` level `build.gradle`. (excerpt)
```gradle
implementation 'com.google.android.gms:play-services-ads:16.0.1'
implementation 'com.squareup.moshi:moshi:1.8.0'
```

### **Update your AndroidManifest.xml**

Add the following `<activity>` declaration inside `<application>` tag of the Manifest.
```xml hl_lines="6"
<activity
    android:name="com.greedygame.android.core.campaign.uii.GreedyGameActivity"
    android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
    android:hardwareAccelerated="true"
    android:launchMode="singleTask"
    android:screenOrientation="portrait"
    android:theme="@style/Theme.GGTransparent">
</activity>
```

Also, note the highlighted line where you can change the orientation of the `screenOrientation` property based on which orientation you want to open the engagment. All the allowed values can be found in <a target="_blank" rel="noopener noreferrer" href="https://developer.android.com/guide/topics/manifest/activity-element#screen">Android Documentation</a>.

### **Adding Permissions**

GreedyGame SDK needs the following permissions to work with.

**Recommended permissions**

```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
```

!!! tip
    `ACCESS_COARSE_LOCATION` permission will help improving the revenue because of doing better ad targetting.

### **Creating Ad Units**
Adunits are ad assets that are rendered as a native component to the app.

**Follow the below steps to create an Ad Unit ID.**

* Goto **<a target="_blank" rel="noopener noreferrer" href="https://integration.greedygame.com">Integration Panel</a>**
* Select an App you have created previously.
* Click on **`Create Unit`** inside the **`Ad units in app`** Card.
* Enter all the fields and click **`Save`**.

![Image](img/android/unit-creation.png)

Follow the same procedure to create multiple Ad Units inside the app.

!!! note ""
    Best practices about the Unit Dimensions can be found under **<a target="_blank" rel="noopener noreferrer" href="/best_practices/#creating-units">Best Practices</a>** section.


### **Initializing GreedyGameAds**

`GreedyGameAds` is the entry point to fetching Native Ads from GreedyGame SDK. Create `GreedyGameAds` instance in the `onCreate` of the Activity.

```Java tab=
GreedyGameAds greedyGame = new GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .addUnitId(ADUNIT_CREATED) //e.g slot-1002
    .withAdListener(new AdListener() {
        @Override
        public void onUnavailable() {

        }

        @Override
        public void onAvailable(@NotNull String adId) {

        }

        @Override
        public void onError(@NotNull String error) {

        }
    })
    .build();
```                        

```Java tab="Kotlin"
val greedyGameAds = GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .addUnitId(ADUNIT_CREATED) //e.g slot-1002
    .withAdListener(object: AdListener() {

        override fun onUnavailable() {

        }

        override fun onAvailable(advId: String) {

        }

        override fun onError(error: String) {

        }
    })
    .build()
```

### **AdListener methods**

| Methods      | Definition                                      |
| ------------ | ----------------------------------------------- |
| `onAvailable(adId)`  | SDK fetched an ad|
| `onUnavailable()`    | Failed to fetch next ad                          |
| `onError(error)`     | SDK not able to initialize. Check the `error` message.|

### **Custom Rendering Native Ads**
Custom rendering allows you to render Native Ads by fetching the image's local path and rendering it with your own `ImageView`.
Follow the example to do the same.

**To fetch the Ad**

To fetch the Ad for a unit you need to call `getPath(unitId)` in `GreedyGameAds` instance.

```Java tab=
ImageView adUnitIV = new ImageView(context) // AdUnit ImageView to render ad
// Game logics
String unitPath = greedyGame.getPath(ADUNIT_CREATED);
if(!TextUtils.isEmpty(unitPath)) {
    // GreedyGameAds has an ad that can be rendered for this Unit id.
    String adBitmap = BitmapHelper.getBitmap(unitPath); // getBitmap() can be of any method which you use to create a Bitmap object out of image file path.
    adUnitIV.setBitmap(adBitmap);
} else {
    // GreedyGame does not have a valid Ad for this Unit id at the moment
}
```

```Java tab="Kotlin"
val adUnitIV = ImageView(context) // AdUnit ImageView to render ad
// Game logics
val unitPath = greedyGame.getPath(ADUNIT_CREATED)
if(unitPath.isNotEmpty()) {
    // GreedyGameAds has an ad that can be rendered for this Unit id.
    val adBitmap = BitmapHelper.getBitmap(unitPath)
    adUnitIV.bitmap = adBitmap
} else {
    // GreedyGame does not have a valid Ad for this Unit id at the moment
}
```

!!! warning
    
    It's the publisher responsibility to call `getPath(unitId)` at relevant places to render the ads. For example, in `onAvailable()` callback of the `AdListener` and when you are changing the `Activity` or `Scene` calling `getPath(unitId)` at the start of the scene will help you resolve

## **Load an Ad**
To load Native Ads call the `load()` method from `GreedyGameAds` instance created before.

```Java tab= hl_lines="6"
GreedyGameAds greedyGame = new GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
     ---"other builder methods"---
    .build();
greedyGame.load();
```

```Java tab="Kotlin" hl_lines="6"
val greedyGame = GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
     ---"other builder methods"---
    .build()
greedyGame.load()
```

!!! tip "When to load the GreedyGame's Native Ad?"
    Load the ads by calling `GreedyGameAds.load()` as early as possible to get the benefits of getting an Ad early. An ideal place would be to call this on `onCreate()` method of `Splash screen` of the game or `Menu screen` of the game.

Once `load()` method called GreedyGame SDK will fetch ads from directly from GreedyGame's demand or it will fetch from any of the Mediation's enabled.

## **Destroy Ad**

When you are done with the ads and do not want to display it call `destroy()` on `GreedyGameAds` instance.

```Java tab=
greedyGame.destroy();
```

```java tab="Kotlin"
greedyGame.destroy()
```

Detroying ads will automatically remove the Ads created with `NativeAdView`. You can also register for Ad destroy events by the following way.

```Java tab=
greedyGame.setAdDestroyListener(new AdDestroyListener() {
    @Override
    public void onDestroy() {

    }
});
```

```java tab="Kotlin"
greedyGame.setAdDestroyListener(object: AdDestroyListener() {
    override fun onDestroy() {

    }
});
```

## **Admob Mediation support**
GreedyGame SDK can source Ads from GreedyGame directly or it can also fetch demand from `Admob` also.

To enable `Admob Mediation` call `enableAdmob(true)` on the `GreedyGameAds.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAds greedyGame = new GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableAdmob(true)
     ---"other builder methods"---
    .build();
greedyGame.load();
```

```Java tab="Kotlin" hl_lines="4"
val greedyGame = GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableAdmob(true)
     ---"other builder methods"---
    .build()
greedyGame.load()
```

## **Compliance with GDPR**
To enable GDPR privacy settings for GreedyGame's Native Android SDK you can create the instance of `PrivacyOptions` and passing it to `GreedyGameAds` insance before calling `load()`.

```Java tab=
// User has given a consent to protect their privacy
PrivacyOptions privacyOptions = new PrivacyOptions(true); // By passing true means that the User has given consent to protect their privacy.
greedyGame.withPrivacyOptions(privacyOptions);
greedyGame.load();
```

```Java tab="Kotlin"
// User has given a consent to protect their privacy
val privacyOptions = PrivacyOptions(true) // By passing true means that the User has given consent to protect their privacy.
greedyGame.withPrivacyOptions(privacyOptions)
greedyGame.load()
```

!!! note
    Load GreedyGameAds only after the user has given the consent. If `load()` is called before receiving the consent then the current app session will be considered as a consent of using privacy information. 

    Admob's SDK will also receive the Consent passed from you in case if you are using `Admob Mediation`.

## **Compliance with COPPA**

To enable COPPA filter in GreedyGame's Native Android SDK you can enable it by calling the method `enableCoppa(true)` in `GreedyGameAds.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAds greedyGame = new GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build();
```

```Java tab="Kotlin" hl_lines="4"
val greedyGame = GreedyGameAds.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableCoppa(true)
     ---"other builder methods"---
    .build()
```

## **Test Ads**

Now you have successfully integrated with GreedyGame Native Ads now is the time to test the integration.

GreedyGame recommends an easy way to test the ads by following the below steps

* Goto **<a target="_blank" rel="noopener noreferrer" href="https://integration.greedygame.com">Integration Panel</a>**
* Select an App in which you want to check the test ads.
* Click `SCAN QR` under the test Ads section and follow the stpes mentioned to get the test ads.
