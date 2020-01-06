### **Update your AndroidManifest.xml**

Add the following `<activity>` declaration inside `<application>` tag of the Manifest.
```xml hl_lines="6 14 22" 
<activity
   android:name="com.greedygame.android.core.campaign.uii.web.GGWebActivity"
   android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
   android:hardwareAccelerated="true"
   android:launchMode="singleTask"
   android:screenOrientation="landscape"
   android:theme="@style/Theme.GGTransparent"/>

<activity
   android:name="com.greedygame.android.core.mediation.greedygame.GGS2SActivity"
   android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
   android:hardwareAccelerated="true"
   android:launchMode="singleTask"
   android:screenOrientation="landscape"
   android:theme="@style/Theme.GGTransparent"/>

<activity
   android:name="com.greedygame.android.core.mediation.admob.GGAdMobActivity"
   android:configChanges="keyboardHidden|orientation|screenSize|screenLayout|layoutDirection"
   android:hardwareAccelerated="true"
   android:launchMode="singleTask"
   android:screenOrientation="landscape"
   android:theme="@style/Theme.GGTransparent"/>

```

Also, note the highlighted line where you can change the orientation of the `screenOrientation` property based on which orientation you want to open the engagment. All the allowed values can be found in <a target="_blank" rel="noopener noreferrer" href="https://developer.android.com/guide/topics/manifest/activity-element#screen">Android Documentation</a>.

!!! WARNING
    * <font size="3" color="red">**Ensure that you have added all the Activities**</font>
    <font size="3" color="red"></font>
    
    * <font size="3" color="red">**Ensure that you have changed the orientation according to your app's orientation**</font>
