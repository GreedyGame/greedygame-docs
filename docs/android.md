# **Android**
In this section we are going to see how to integrate GreedyGame Native Ads in Android native projects.

### **Importing GreedyGame Native Ads SDK**

Games built with Android Studio can easily integrate with [Gradle](https://gradle.org).

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

Also, note the highlighted line where you canchange the orientation of the `screenOrientation` property based on which orientation you want to open the engagment. Allowed values can be found in [Android Documentation](https://developer.android.com/guide/topics/manifest/activity-element#screen).

### **Adding Permissions**

GreedyGame SDK needs the following permissions to work with.

**Mandatory permissions**

```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE"/>
<uses-permission android:name="android.permission.INTERNET"/>
```

**Optional permissions**

```xml
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```

!!! tip
    `ACCESS_COARSE_LOCATION` permission will help improving the revenue because of better ad targetting.

### **Creating Game ID**
Game ID is an unique identifier for your game.

**Follow the below steps to create a Game ID.**

* Goto [https://integration.greedygame.com](https://integration.greedygame.com).
* Login with your GreedyGame's Publisher account.
* Click on **`ADD NEW GAME`** button.
* Select the **`Android`** Platform.
* Enter **`Game name`** and **`Package name`** of the game.
* Click on **`Save`**.


### **Creating Ad Units**
Adunits are ad assets that are rendered as a native component to the game.

**Follow the below steps to create an Ad Unit ID.**

* Goto **[Integration panel](https://integration.greedygame.com)**.
* Select the Game you have created in the previous step.
* Click on **`Create Unit`** inside the **`Ad units in game`** Card.
* Enter all the fields and click **`Save`**.

Follow the same procedure to create multiple Ad Units inside the game.

!!! note ""
    Best practices about the Unit Dimensions can be found under **[Resources](http://127.0.0.1:8000/best_practices/)** tab.

### **Initializing GreedyGameAds**

`GreedyGameAds` is the entry point of fetching Native Ads from GreedyGame SDK. Create `GreedyGameAds` instance in the `onCreate` of the Activity.

```Java tab=
GreedyGameAds greedyGame = new GreedyGameAds.Builder(activity)
                .gameId(GAME_ID_CREATED) //e.g 00100100
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
                .gameId(GAME_ID_CREATED) //e.g 00100100
                .addUnitId(ADUNIT_CREATED) //e.g slot-1000
                .addUnitId(ADUNIT_CREATED) //e.g slot-1002
                .withAdListener(object: AdListener() {
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
                .build()
```

### **AdListener methods**

| Methods      | Definition                                      |
| ------------ | ----------------------------------------------- |
| `onAvailable(adId)`  | SDK fetched an ad|
| `onUnavailable()`    | Failed to fetch next ad                          |
| `onError(error)`     | SDK not able to initialize. Check the `error` message.|

### **Rendering Native Ads**
To render Native Ads add the 'NativeAdView' inside any of the activity in which you want to show Native Ads.

```XML tab=
<RelativeLayout>
    ----------
    other views
    ----------
    <com.greedygame.android.adview.NativeAdView
            android:id="@+id/ggad"
            app:unitId="ADUNIT_CREATED"
            android:layout_width="match_parent"
            android:layout_height="150dp"/>
    ----------
    other views
    ----------
</RelativeLayout>
```

```Java tab=
NativeAdView nativeAdView = new NativeAdView(this, ADUNIT_CREATED);
LinearLayout.LayoutParams params = new LinearLayout.LayoutParams(LinearLayout.LayoutParams.MATCH_PARENT, AD_UNIT_SIZE_IN_PIXELS);
LinearLayout linearLayout = (LinearLayout) findViewById(R.id.parent);
linearLayout.addView(nativeAdView, params);
```

```Java tab="Kotlin"
val nativeAdView = NativeAdView(this, ADUNIT_CREATED)
val params = LinearLayout.LayoutParams(LinearLayout.LayoutParams.MATCH_PARENT, AD_UNIT_SIZE_IN_PIXELS)
val linearLayout = findViewById(R.id.parent) as? LinearLayout
linearLayout?.addView(nativeAdView, params)
```

## **AdView events**
To get AdView events register for `AdViewListener` by the following way.

```Java tab=
final NativeAdView nativeAdView = (NativeAdView) findViewById(R.id.ggad);
nativeAdView.setAdViewListener(new NativeAdView.AdViewListener() {
    @Override
    public void onImpression() {
        Log.d(TAG, "Impression fired for unit id: " + nativeAdView.getUnitId());
    }
});
```

```java tab="Kotlin"
val nativeAdView = findViewById(R.id.ggad) as NativeAdView
nativeAdView.adViewListener = object: NativeAdView.AdViewListener() {
    fun onImpression() {
        Log.d(TAG, "Impression fired for unit id: " + nativeAdView.unitId);
    }
}
```