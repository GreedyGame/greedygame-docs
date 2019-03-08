If you were on any versions of GreedyGame prior to version 9.0 please follow the steps below 


## **Removing previous plugin files**
### Delete the following folders/files from your project
* Assets > Editor > GreedyGame.Editor.dll
* Assets > Plugins > GreedyGame folder.
!!! warn
    If you have any custom renderer scripts created inside this folder please make sure that you copy them before deleting
* Assets > Android > libs > r-android-sdk ( delete any files (aar's) which start with this name)

### Remove declarations from manifest 
Remove the following activities from manifest 
```xml
<activity
    android:name="com.greedygame.android.core.campaign.uii.web.GGWebActivity"
    android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
    android:hardwareAccelerated="true"
    android:launchMode="singleTask"
    android:screenOrientation="landscape"
    android:theme="@style/Theme.GGTransparent">
</activity>

<activity
    android:name="com.greedygame.android.core.mediation.greedygame.GGS2SActivity"
    android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
    android:hardwareAccelerated="true"
    android:launchMode="singleTask"
    android:screenOrientation="landscape"
    android:theme="@style/Theme.GGTransparent">
</activity>

<activity
    android:name="com.greedygame.android.core.mediation.admob.GGAdMobActivity"
    android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
    android:hardwareAccelerated="true"
    android:launchMode="singleTask"
    android:screenOrientation="landscape"
    android:theme="@style/Theme.GGTransparent">
 </activity>
```


