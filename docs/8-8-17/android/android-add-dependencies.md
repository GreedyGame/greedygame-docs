### **Dependency Libraries**
Include the following in the `app` level `build.gradle`. (excerpt)
```gradle
implementation 'com.google.android.gms:play-services-ads:17.2.1'
implementation 'com.google.android.gms:play-services-location:16.0.0' //Recommended but optional
```
GreedyGame SDK has been tested to work correctly with 15.x to 17.x series of the Google Play Services Ads. Support for future versions is experimental.

!!! NOTE
    The minimum play-services-ads version supported is 15.0.0 and the maximum is 17.2.1.

!!! WARNING
    * <font size="3" color="red">**Ensure that Play Services version is in between 15.0.0 and 17.2.1**</font>
