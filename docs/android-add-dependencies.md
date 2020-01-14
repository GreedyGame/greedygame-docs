### **Dependency Libraries**
Include the following in the `app` level `build.gradle`. (excerpt)
```gradle
implementation 'com.google.android.gms:play-services-ads:16.0.0'
implementation 'com.google.android.gms:play-services-location:16.0.0' //Recommended but optional
```
GreedyGame SDK has been tested to work correctly with 16.x series of the Google Play Services. Support for future versions is experimental.

!!! WARNING
    * <font size="3" color="red">**Ensure that Play Services version is 16**</font>
