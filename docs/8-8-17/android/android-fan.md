## **Enable Facebook Audience Network (FAN) Ads**

GreedyGame SDK sources Ads from multiple Ad Demand Partners using GreedyGame's Mediation Platform  directly which requires no additional setup.

But to serve FAN ads, GreedyGame requires you to enable FAN in the initialization script.

### Update your Manifest.xml
Add the following `<activity>` declaration inside `<application>` tag of the Manifest.
```xml hl_lines="6 14 22" 
     <activity
        android:name="com.greedygame.android.core.mediation.facebook.GGFacebookActivity"
        android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
        android:hardwareAccelerated="true"
        android:launchMode="singleTask"
        android:screenOrientation="landscape"
        android:theme="@style/Theme.GGTransparent"/>
```
### Add Dependency
Follow the guide [here from Facebook](https://developers.facebook.com/docs/audience-network/guides/adding-sdk).
Our SDK is tested against SDK Version 5.6.1 Support for any future versions is experimental.
### Enable Facebook Mediation in `GreedyGameAgent`
To enable `FAN Ads` call `enableFacebook(true)` on the `GreedyGameAgent.Builder` instance.

```Java tab= hl_lines="4"
GreedyGameAgent greedyGameAgent = new GreedyGameAgent.Builder(activity) // or Context
    .setGameId(GAME_ID_CREATED) //e.g 00100100
    .addUnitId(ADUNIT_CREATED) //e.g slot-1000
    .enableFacebook(true)
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
