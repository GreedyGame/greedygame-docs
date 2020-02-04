## **Enable MoPub Ads**

GreedyGame SDK sources Ads from multiple Ad Demand Partners using GreedyGame's Mediation Platform  directly which requires no additional setup.

But to serve MoPub ads, GreedyGame requires you to enable MoPub in the initialization script.

### Update your Manifest.xml
Add the following `<activity>` declaration inside `<application>` tag of the Manifest.
```xml hl_lines="6 14 22" 
      <activity
            android:name="com.greedygame.android.core.mediation.mopub.GGMoPubActivity"
            android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
            android:hardwareAccelerated="true"
            android:launchMode="singleTask"
            android:screenOrientation="landscape"
            android:theme="@style/Theme.GGTransparent"/>

        <activity android:name="com.mopub.common.MoPubBrowser"
            android:configChanges="keyboardHidden|orientation|screenSize"/>

            <!-- Required only if you want video ads-->
            <activity
            android:name="com.mopub.mobileads.MraidVideoPlayerActivity"
            android:configChanges="keyboardHidden|orientation|screenSize"
            />
```
### Add Dependency
Follow the guide [here from Mopub](https://developers.mopub.com/publishers/android/integrate/).
Our SDK is tested against MoPub SDK Version 5.3. You can use Support for any future versions is experimental
### Enable Facebook Mediation in `GreedyGameAgent`
In your app level `build.gradle` add the MoPub library.

```gradle 
compile('com.mopub:mopub-sdk-native-static:5.3.0@aar') {
        transitive = true
        exclude module: 'libAvid-mopub' // To exclude AVID
        exclude module: 'moat-mobile-app-kit' // To exclude Moat
        exclude group: 'com.google.android.gms'
    }
```
<center> or </center>

```gradle 
//this includes mopub-sdk-native-static
compile('com.mopub:mopub-sdk-native-video:5.3.0@aar') {
        transitive = true
        exclude module: 'libAvid-mopub' // To exclude AVID
        exclude module: 'moat-mobile-app-kit' // To exclude Moat
        exclude group: 'com.google.android.gms'
    }
```
Now call `enableMopub(true)` on the `GreedyGameAgent.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAgent greedyGameAgent = new GreedyGameAgent.Builder(activity) // or Context
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableMopub(true)
     ---"other builder methods"---
    .build();
greedyGameAgent.init();
```

<!-- ```Java tab="Kotlin" hl_lines="4"
val greedyGame = GreedyGameAgent.Builder(activity)
    .appId(APP_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableAdmob(true)
     ---"other builder methods"---
    .build()
greedyGame.load()
``` -->
